# TConnectEvmProvider

## Configure and use TConnectEvmProvider

The `TConnectEvmProvider` class is a provider implementation that requires specific configuration options passed to its constructor during instantiation. Note that the `bridgeUrl` parameter must always be set to `"https://tconnect.io"`, as this is the hosted location of the bridge.

Here’s the full definition of the `TConnectEvmProviderOptions` interface:

```typescript
// Interface definition for TConnectEvmProviderOptions
interface TConnectEvmProviderOptions {
  // The name of your application.
  appName: string;
  // The URL linking to your application's website or homepage.
  appUrl: string;
  // (Optional) A URL pointing to an icon that represents your application.
  appIcon?: string;
  // The URL of the bridge server used for communication.
  bridgeUrl: string;
  // The API key required for authentication and access to the provider's services.
  apiKey: string;
  // (Optional) The wallet application, represented by the `EvmWalletApp` type.
  walletApp?: EvmWalletApp;
}
```

### **Understanding the `walletApp` Parameter**

The `walletApp` parameter is optional and specifies the wallet application the user intends to connect to. This parameter uses the `EvmWalletApp` type, which represents supported wallet applications. Providing this parameter allows the provider to optimize and streamline the connection process for the specified wallet.

If the `walletApp` parameter is omitted, the provider will attempt to connect to any available wallet. In such cases, the connection is established via a connection string  provided by the bridge. _(_[_See more details here._](./#connect-via-connection-string)_)_

### Example of initializing the TConnectEvmProvider

```typescript
// Import provider
import { EvmWalletApp, TConnectEvmProvider } from "@tconnect.io/evm-provider";

const app: EvmWalletApp = "metaMask";
// Initialize provider
const provider = new TConnectEvmProvider({
  appName: "Example App",
  appUrl: "https://your-domain.io",
  bridgeUrl: "https://tconnect.io",
  apiKey: "PRIVATE_API_KEY",
  walletApp: app,
});
```

This function demonstrates how to connect to the wallet using the initialized provider and handle potential errors:

```typescript
async function myAsyncFunction() {
  try {
    // Connect to wallet
    await provider.connect();
  } catch (error) {
    console.error("Error connecting to wallet:", error);
  }
}
```
