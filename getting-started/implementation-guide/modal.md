---
icon: square-code
---

# Modal

### Wallet Connection Modal

**t:connect** provides a built-in **Wallet Connection Modal** that simplifies the process of connecting users to the Tezos and Etherlink blockchains via supported wallets. This modal is a ready-to-use component that developers can integrate into their Telegram Mini Apps, allowing users to securely and effortlessly connect their wallets.

**Features of the Wallet Connection Modal**

* **User-Friendly Interface**: An intuitive UI that guides users through the wallet connection process.
* **Multi-Chain Support**: Supports both Tezos and Etherlink chains, offering flexibility for various applications.
* **Multiple Wallet Options**: Compatible with a range of wallets like MetaMask, Trust Wallet, Altme, and more.
* **Secure Authentication**: Ensures that user credentials and private keys remain secure during the connection.
* **Customizable Appearance**: Developers can tailor the modal's look and feel to match their app's branding.

### How to Implement the Wallet Connection Modal

{% stepper %}
{% step %}
#### Initialize t:connect in Your Mini App

```
npm install @tconnect/modal
```
{% endstep %}

{% step %}
#### Display the Wallet Connection Modal

To display the modal, the `openModal` method is called within the `useModal` hook inside the `ModalProvider`.

We recommend first providing the TConnectModalProvider, for example in `App.tsx`, and then calling the `openModal` method within a component that is inside the provider.

```
import { TConnectModalProvider, useTConnectModal } from '@tconnect.io/modal';
import { Main } from './pages/Main';

<TConnectModalProvider apiKey="PRIVATE_API_KEY" >			
    <Main/>				
</TConnectModalProvider>
			
```

The `TConnectModalProvider` requires an API key. Additionally, you can optionally specify:

* `children?: ReactNode | undefined;`
* `onError?: (error: unknown) => void;`

Now, within the provider, in this example in the `Main` component, the `openModal` method can be called to display the modal for wallet selection.

```
import { useTConnectModal } from '@tconnect.io/modal';

export const Main = () => {
	const tConnect = useTConnectModal();
	return (
	<button onClick={tConnect.openModal}>open modal</button>
	);
};

Main.displayName = 'Main';
```
{% endstep %}

{% step %}
#### Customize the Modal (Optional)

```
// Some code
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

Once a wallet is selected, the `connect()` method is triggered to establish the connection. The user is prompted within the wallet to authorize the connection.

<img src="../../.gitbook/assets/Screenshot 2024-11-05 at 09.32.43.png" alt="" data-size="original">
{% endstep %}

{% step %}
#### Connection Etablished

After a successful connection, the modal closes, and the developer can use the wallet information (e.g., address, wallet name, chain) for further interactions.
{% endstep %}
{% endstepper %}
