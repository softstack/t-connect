---
icon: bullseye-arrow
---

# Quickstart

We provide four distinct npm packages that can be independently installed and utilized, giving developers the freedom to integrate precisely the functionality they need:

{% tabs %}
{% tab title="React-Modal" %}
Install the React-Modal

The react-modal is supplied as a complete package and includes the required providers

```typescript
npm install @tconnect.io/modal
```

This is a complete React component specifically crafted for blockchain wallet connections. It provides a ready-to-use interface that allows users to connect with supported wallets seamlessly. Once connected, it establishes a React context that enables developers to interact directly with blockchain functionalities. Think of it as a smart, pre-built gateway that simplifies the often complex process of wallet integration and blockchain interaction.
{% endtab %}

{% tab title="Etherlink Provider" %}
Install the Etherlink Provider

```typescript
npm install @tconnect.io/etherlink-provider
```

This provider is exclusively designed for Etherlink, Tezos EVM-compatible sidechain.&#x20;
{% endtab %}

{% tab title="Tezos Beacon Provider" %}
Install the Tezos Beacon Provider

```typescript
npm install @tconnect.io/tezos-beacon-provider
```

A Beacon wallet provider for Tezos ecosystem integrations.
{% endtab %}

{% tab title="Tezos Wallet Connect Provider" %}
Install the Tezos Wallet Connect Provider

```typescript
npm install @tconnect.io/tezos-wc-provider
```

A Wallet Connect provider specifically optimized for Tezos blockchain connections.
{% endtab %}
{% endtabs %}

In our Quickstart documentation, we'll focus on demonstrating the usage of the react-modal as an introductory example. However, our comprehensive documentation will provide in-depth guidance for each package, ensuring developers can leverage the full potential of each component according to their specific project requirements.

#### Setup the React-Modal Provider

We recommend first providing the TConnectModalProvider.

<pre class="language-typescript"><code class="lang-typescript"><strong>// Import the TConnectModalProvider component for managing the TConnect modal
</strong>import { TConnectModalProvider } from "@tconnect.io/modal";
// Import the custom component to be rendered within the modal provider
import { MyComponent } from "./MyComponent";

export default function App() {
  return (
    // Wrap the application with TConnectModalProvider to configure and
    // enable the TConnect modal
    &#x3C;TConnectModalProvider
      appName={"Example App"} // Name of the application
      appUrl={"https://your-domain.io"} // URL of the application
      bridgeUrl={"https://tconnect.io"} // Bridge URL for the TConnect service
      apiKey={"PRIVATE_API_KEY"} // API key for authenticating with TConnect
    >
      // Render the custom component within the TConnect provider
      &#x3C;MyComponent />
    &#x3C;/TConnectModalProvider>
  );
}
</code></pre>

#### Display the Wallet Connection React-Modal

Now, within the provider, in this example in `MyComponent` component, the `openModal` method can be called to display the modal for wallet selection.

```typescript
// Import the useTConnectModal hook to interact with the TConnect modal
import { useTConnectModal } from "@tconnect.io/modal";

// Define a functional React component named MyComponent
export const MyComponent = () => {
  // Initialize the TConnect modal functionality using the custom hook
  const tConnect = useTConnectModal();

  return (
    // Render a button that triggers the TConnect modal when clicked
    <button onClick={tConnect.openModal}>open modal</button>
  );
};
```
