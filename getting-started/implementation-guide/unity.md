---
icon: play
---

# Unity

## Integration of Unity WebGL with the tconnect.io sdk <a href="#integration-of-unity-webgl-with-the-tconnect.io-sdk" id="integration-of-unity-webgl-with-the-tconnect.io-sdk"></a>

This section of the documentation describes the integration of Unity WebGL applications with the tconnect.io SDK. The goal is to enable communication between a Unity WebGL application and a React application utilizing the tconnect.io sdk.

#### Overview <a href="#overview" id="overview"></a>

Unity is a powerful platform for developing 2D and 3D games and applications, including WebGL applications. Unity WebGL builds can be seamlessly embedded in React applications. Using the tconnect.io SDK, Web3 features such as wallet integration can be added to these applications.

#### Use Case <a href="#use-case" id="use-case"></a>

We consider a simple WebGL application with two buttons:

1. **Open Modal:** A button that opens the React modal, part of the tconnect.io sdk, to connect to a wallet.
2. **Display Address:** A button that displays the wallet address connected through the modal in the Unity application.

### Implementation Steps <a href="#implementation-steps" id="implementation-steps"></a>

**Unity Script: `ReactCommunicator`**

The following Unity script manages communication between the Unity application and React:

```typescript
using UnityEngine;
using UnityEngine.UI;
using TMPro;

public class ReactCommunicator : MonoBehaviour
{
    // Text field to display received data
    public TMP_Text displayText;

    // Function called by the button
    public void RequestDataFromReact()
    {
        Debug.Log("Unity: Request sent to React!");
        // Calls the JavaScript function in the WebGL build
        Application.ExternalCall("sendDataToUnity");
    }

    public void openModalUnity()
    {
        Debug.Log("Unity: Open modal");
        Application.ExternalCall("openModalUnity");
    }

    // This function is called by React
    public void ReceiveDataFromReact(string data)
    {
        Debug.Log($"Unity: Data received from React - {data}");
        displayText.text = data;
    }
}
```

## **React Communication Class: `useUnityCommunicator`**

The following React hook manages communication between React and Unity:

```typescript
import { useTConnectModal } from '@tconnect.io/modal';
import { TConnectTezosBeaconProvider } from '@tconnect.io/tezos-beacon-provider';
import { TConnectTezosWcProvider } from '@tconnect.io/tezos-wc-provider';
import { useCallback, useState } from 'react';
import Web3 from 'web3';

// Import necessary dependencies

// Extend the global `window` object to
// include custom properties for Unity communication
declare global {
	interface Window {
		// Opens the TConnect modal from Unity
		openModalUnity: () => void;
		// Sends data to Unity asynchronously
		sendDataToUnity: () => Promise<void>;
	}
}

// Constants for Unity communication
// Name of the Unity GameObject to send messages to
const UNITY_GAMEOBJECT = 'Canvas';
// Unity method to handle received messages
const UNITY_METHOD = 'ReceiveDataFromReact';

// Custom React hook for Unity communication
export const useUnityCommunicator = (
	// Function to send messages to Unity
	sendMessage: (gameObject: string, methodName: string, data: string) => void,
) => {
	// State to store the user's wallet address
	const [address, setAddress] = useState<string | undefined>();

	// Get modal functionality and wallet providers from TConnect
	const { openModal, evmProvider, tezosBeaconProvider, tezosWcProvider } 
	= useTConnectModal();

	// Function to retrieve the user's Etherlink address
	const getAddressEvm = useCallback(async () => {
		if (!evmProvider) return;
		const web3 = new Web3(evmProvider);
		const accounts = await web3.eth.getAccounts();
		const walletAddress = accounts.length > 0 ? accounts[0] : undefined;
		setAddress(walletAddress);
		return walletAddress;
	}, [evmProvider]);

	// Function to retrieve a Tezos wallet address (Beacon or WalletConnect)
	const getAddress = useCallback(
		async (provider: 
			TConnectTezosBeaconProvider |
			 TConnectTezosWcProvider |
			  undefined) => {
			if (!provider) return;
			const address = await provider.getPKH();
			setAddress(address);
			return address;
		},
		[],
	);

	// Function to set up communication between React and Unity
	const setupUnityCommunication = useCallback(() => {
		// Expose the `openModal` functionality to Unity
		// via the global `window` object
		window.openModalUnity = () => {
			openModal(); // Open the TConnect modal
		};

		// Expose the `sendDataToUnity` functionality to Unity 
		// via the global `window` object
		window.sendDataToUnity = async () => {
			// Determine which Tezos provider to use if any
			const activeTezosProvider = tezosBeaconProvider || tezosWcProvider;

			try {
				// Fetch the appropriate address based on the available provider
				const data = evmProvider
					? // If Etherlink provider is available, get the Ethereum address
						await getAddressEvm()
					: activeTezosProvider
						? // Get the Tezos address
							await getAddress(activeTezosProvider)
						: // Fallback if no provider is available
							'not connected';

				// If data is available, send it to Unity
				if (data) {
					// Send the data to Unity
					sendMessage(UNITY_GAMEOBJECT, UNITY_METHOD, data);
				}
			} catch (error) {
				// Log any errors that occur during the process
				console.error(error || 'React: Error sending data to Unity');
			}
		};
	}, [openModal, getAddressEvm, getAddress, sendMessage,
		evmProvider, tezosBeaconProvider, tezosWcProvider]);

	// Return the `setupUnityCommunication` function and the wallet address state
	return {
		setupUnityCommunication,
		address,
	};
};


```

### Embedding Unity in React <a href="#embedding-unity-in-react" id="embedding-unity-in-react"></a>

1. **Embedding the Unity WebGL Build:** The WebGL build can be embedded in React using the [`react-unity-webgl`](https://www.npmjs.com/package/react-unity-webgl)package or as iFrame.
2. **Initializing Communication:** The `useUnityCommunicator` hook is used to set up communication between Unity and React.

```typescript
import React, { useEffect } from 'react';
import { useUnityCommunicator } from './useUnityCommunicator';
import Unity, { UnityContext } from 'react-unity-webgl';

const UnityGame = () => {
    const unityContext = new UnityContext({
        loaderUrl: '/path-to-unity-build/Build/loader.js',
        dataUrl: '/path-to-unity-build/Build/data.data',
        frameworkUrl: '/path-to-unity-build/Build/framework.js',
        codeUrl: '/path-to-unity-build/Build/code.wasm',
    });
    onst { setupUnityCommunication } = useUnityCommunicator(sendMessage);

    useEffect(() => {
        setupUnityCommunication();
    }, [setupUnityCommunication]);

    return (
	<div className="text-center">
		<h1 className="text-4xl font-bold mb-4">Unity React Integration</h1>
		<div className="mx-auto" style={{ width: 350, height: 600 }}>
		    <Unity unityProvider={unityProvider} 
		    style={{ width: '100%', height: '100%' }} />
		</div>
	</div>
    );
};

export default UnityGame;
```

### Conclusion <a href="#conclusion" id="conclusion"></a>

By following these steps, Unity WebGL applications can be seamlessly embedded in React and integrated with the tconnect.io SDK. This enables smooth integration of Web3 features such as wallet connectivity into your Unity applications. Further customizations can be made based on the specific requirements of your application.

{% hint style="info" %}
you can find a demo bot here: [@tconnect\_unity\_bot](https://t.me/tconnect_unity_bot)
{% endhint %}
