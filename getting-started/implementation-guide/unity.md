---
icon: play
---

# Unity

## Integration of Unity WebGL with the tconnect.io sdk

This section of the documentation describes the integration of Unity WebGL applications with the tconnect.io SDK. The goal is to enable communication between a Unity WebGL application and a React application utilizing the tconnect.io sdk.

### Overview

Unity is a powerful platform for developing 2D and 3D games and applications, including WebGL applications. Unity WebGL builds can be seamlessly embedded in React applications. Using the tconnect.io SDK, Web3 features such as wallet integration can be added to these applications.

### Use Case

We consider a simple WebGL application with two buttons:

1. **Open Modal:** A button that opens the React modal, part of the tconnect.io sdk, to connect to a wallet.
2. **Display Address:** A button that displays the wallet address connected through the modal in the Unity application.

### Implementation Steps

#### Unity Script: `ReactCommunicator`

The following Unity script manages communication between the Unity application and React:

```csharp
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

#### React Communication Class: `useUnityCommunicator`

The following React hook manages communication between React and Unity:

```typescript
import { useTConnectModal } from '@tconnect.io/modal';
import { useCallback, useState } from 'react';
import Web3 from 'web3';

export const useUnityCommunicator = (
sendMessage: (gameObject: string, methodName: string, data: string) => void) => {
    const [address, setAddress] = useState<string | undefined>();
    const { openModal, evmProvider, tezosBeaconProvider, tezosWcProvider } = useTConnectModal();

    const getAddressEvm = useCallback(async () => {
        if (!evmProvider) return;
        const web3 = new Web3(evmProvider);
        const accounts = await web3.eth.getAccounts();
        const walletAddress = accounts.length > 0 ? accounts[0] : undefined;
        setAddress(walletAddress);
        return walletAddress;
    }, [evmProvider]);

    const getAddressBeacon = useCallback(async () => {
        if (!tezosBeaconProvider) return;
        const address = await tezosBeaconProvider.getPKH();
        setAddress(address);
        return address;
    }, [tezosBeaconProvider]);

    const getAddressWc = useCallback(async () => {
        if (!tezosWcProvider) return;
        const address = await tezosWcProvider.getPKH();
        setAddress(address);
        return address;
    }, [tezosWcProvider]);

    const setupUnityCommunication = useCallback(() => {
        (window as any).openModalUnity = () => {
            openModal();
        };

        (window as any).sendDataToUnity = async () => {
            try {
                const data = evmProvider
                    ? await getAddressEvm()
                    : tezosBeaconProvider
                        ? await getAddressBeacon()
                        : tezosWcProvider
                            ? await getAddressWc()
                            : 'not connected';

                if (data) {
                    sendMessage('Canvas', 'ReceiveDataFromReact', data);
                }
            } catch (error) {
                console.error('React: Error calling from:', error);
            }
        };
    }, [openModal, getAddressEvm, getAddressBeacon, getAddressWc, sendMessage]);

    return {
        setupUnityCommunication,
        address,
    };
};
```

### Embedding Unity in React

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

### Conclusion

By following these steps, Unity WebGL applications can be seamlessly embedded in React and integrated with the tconnect.io SDK. This enables smooth integration of Web3 features such as wallet connectivity into your Unity applications. Further customizations can be made based on the specific requirements of your application.

{% hint style="info" %}
you can find a demo bot here: [@tconnect\_unity\_bot](https://t.me/tconnect_unity_bot)
{% endhint %}
