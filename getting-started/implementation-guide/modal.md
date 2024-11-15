---
icon: square-code
---

# Modal

### Wallet Connection Modal

**t:connect** provides a built-in Wallet Connection Modal, developed in React, that simplifies the process of connecting users via supported wallets to Tezos and Etherlink. Leveraging React Provider and Hook technology, this ready-to-use modal component facilitates state management and enables seamless integration into the component tree. Developers can easily embed it into their Telegram Mini App, allowing users to securely and effortlessly connect their wallets.

**Features of the Wallet Connection Modal**

* **User-Friendly Interface**: An intuitive UI that guides users through the wallet connection process.
* **Multi-Chain Support**: Supports both Tezos and Etherlink, offering flexibility for various applications.
* **Multiple Wallet Options**: Compatible with a range of wallets like Altme, MetaMask, Trust Wallet, and more.
* **Secure Authentication**: Ensures that user credentials and private keys remain secure during the connection.

### The TConnectModalProvider

The TConnectModalProvider has three options:

<pre><code><strong>apiKey: string; 
</strong></code></pre>

{% hint style="info" %}
Wondering how to obatin an api key? see: [Broken link](broken-reference "mention")
{% endhint %}

```
children?: ReactNode | undefined; 
```

```
onError?: (error: unknown) => void;
```

### The TConnectModal Hook

```
// function to open the modal
openModal: () => void;

// function to clode the modal
closeModal: () => void;

// the evm Provider
evmProvider: TConnectEvmProvider | undefined;

// the tezos-beacon Provider
tezosBeaconProvider: TConnectTezosBeaconProvider | undefined;

// the Tezos WalletConnect Provider
tezosWcProvider: TConnectTezosWcProvider | undefined;

// true if successfully connected
connected: boolean;
```

### How to use the Wallet Connection Modal

{% stepper %}
{% step %}
```
npm install @tconnect.io/modal
```
{% endstep %}

{% step %}
#### Setup the Modal Provider

We recommend first providing the TConnectModalProvider, for example in `Layout.tsx.`&#x20;

```
import { TConnectModalProvider } from '@tconnect.io/modal';
import { App } from './pages/App';

<TConnectModalProvider apiKey="PRIVATE_API_KEY" >			
    <App/>				
</TConnectModalProvider>
```
{% endstep %}

{% step %}
#### Display the Wallet Connection Modal

Now, within the provider, in this example in the `App` component, the `openModal` method can be called to display the modal for wallet selection.

```
import { useTConnectModal } from '@tconnect.io/modal';

export const App = () => {
	const tConnect = useTConnectModal();
	return (
	<button onClick={tConnect.openModal}>open modal</button>
	);
};

App.displayName = 'App';
```
{% endstep %}
{% endstepper %}

### Modal Workflow

{% stepper %}
{% step %}
#### Blockchain  Selection

The modal first provides the option to choose the blockchain  to be used. The user can select between Tezos or Etherlink.

<img src="../../.gitbook/assets/Screenshot 2024-11-05 at 09.24.27.png" alt="" data-size="original">
{% endstep %}

{% step %}
#### Wallet Selection

After selecting the Blockchain, the user is prompted to choose a wallet. The list of available wallets is automatically filtered based on the previously chosen blockchain.

<img src="../../.gitbook/assets/Screenshot 2024-11-05 at 09.24.46.png" alt="" data-size="original">
{% endstep %}

{% step %}
#### Wallet Connection Execution

Once a wallet is selected, the user is redirected to the wallet and prompted to authorize the connection.
{% endstep %}

{% step %}
#### Connection Etablished

After a successful connection, the modal closes, and the developer get the provider from the Modal Hook.&#x20;
{% endstep %}
{% endstepper %}
