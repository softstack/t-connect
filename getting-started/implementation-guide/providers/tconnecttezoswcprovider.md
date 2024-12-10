# TConnectTezosWcProvider

## **Configure and Use TConnectTezosWcProvider**

The `TConnectTezosWcProvider` class is a provider implementation designed to connect Tezos wallets via WalletConnect. It requires specific configuration options to be passed to its constructor during instantiation. Note that the `bridgeUrl`parameter must always be set to `"https://tconnect.io"`, as this is the hosted location of the bridge.

Here’s the full definition of the `TConnectTezosWcProviderOptions` interface:

```typescript
// Interface definition for TConnectTezosWcProviderOptions
interface TConnectTezosWcProviderOptions {
  // The name of your application.
  appName: string;
  // The URL linking to your application's website or homepage.
  appUrl: string;
  // (Optional) A URL pointing to an icon that represents your application.
  appIcon?: string;
  // The API key required for authentication and access to the provider's services.
  apiKey: string;
  // The Tezos network to connect to (e.g., "mainnet", "ghostnet").
  network: Network;
  // The URL of the bridge server used for communication.
  bridgeUrl: string;
  // (Optional) The wallet application, represented by the `TezosWcWalletApp` type.
  walletApp?: TezosWcWalletApp;
}
```

### **Understanding the `walletApp` Parameter**

The `walletApp` parameter is optional and specifies the wallet application the user intends to connect to. This parameter uses the `TezosWcWalletApp` type, which represents supported Tezos wallet applications. Providing this parameter allows the provider to optimize and streamline the connection process for the specified wallet.

If the `walletApp` parameter is omitted, the provider will attempt to connect to any available wallet. In such cases, the connection can established via a connection string  provided by the bridge. _(_[_See more details here_](connect-via-connection-string.md)_.)_

### **Example of Initializing the TConnectTezosWcProvider**

```typescript
// Import provider
import { TConnectTezosWcProvider } from "@tconnect.io/tezos-wc-provider";
import { TezosWcWalletApp } from "@tconnect.io/tezos-wc-provider";

const app: TezosWcWalletApp = "kukai";

// Initialize provider
const provider = new TConnectTezosWcProvider({
  appName: "Example App",
  appUrl: "https://your-domain.io",
  bridgeUrl: "https://tconnect.io",
  apiKey: "PRIVATE_API_KEY",
  walletApp: app,
  network: "ghostnet",
});
```
