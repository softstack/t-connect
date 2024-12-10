# TConnectTezosBeaconProvider

## **Configure and Use TConnectTezosBeaconProvider**

The `TConnectTezosBeaconProvider` class is a provider implementation designed to connect Tezos wallets via Beacon. It requires specific configuration options to be passed to its constructor during instantiation. Note that the `bridgeUrl`parameter must always be set to `"https://tconnect.io"`, as this is the hosted location of the bridge.

Here’s the full definition of the `TConnectTezosBeaconProviderOptions` interface:

```typescript
// Interface definition for TConnectTezosBeaconProviderOptions
interface TConnectTezosBeaconProviderOptions {
  // The name of your application.
  appName: string;
  // The URL linking to your application's website or homepage.
  appUrl: string;
  // (Optional) A URL pointing to an icon that represents your application.
  appIcon?: string;
  // The URL of the bridge server used for communication.
  bridgeUrl: string;
  // The secret seed used for generating the wallet.
  secretSeed: string;
  // The API key required for authentication and access to the provider's services.
  apiKey: string;
  // The Tezos network configuration.
  network: Network;
  // (Optional) The wallet application, represented by the `TezosBeaconWalletApp` type.
  walletApp?: TezosBeaconWalletApp;
}
```

### **Understanding the `walletApp` Parameter**

The `walletApp` parameter is optional and specifies the wallet application the user intends to connect to. This parameter uses the `TezosBeaconWalletApp` type, which represents supported Tezos wallet applications. Providing this parameter allows the provider to optimize and streamline the connection process for the specified wallet.

If the `walletApp` parameter is omitted, the provider will attempt to connect to any available wallet. In such cases, the connection can established via a connection string provided by the bridge. _(_[_See more details here._](./#connect-via-connection-string)_)_

### **Example of Initializing the TConnectTezosBeaconProvider**

```typescript
// Import provider
import { TConnectTezosBeaconProvider } from "@tconnect.io/tezos-beacon-provider";
import { TezosBeaconWalletApp } from "@tconnect.io/tezos-beacon-provider";

const app: TezosBeaconWalletApp = "altme";
const secretSeed = "SECRET_SEED";

// Initialize provider
const provider = new TConnectTezosBeaconProvider({
  appName: "Example App",
  appUrl: "https://your-domain.io",
  bridgeUrl: "https://tconnect.io",
  secretSeed,
  apiKey: "PRIVATE_API_KEY",
  network: {
    type: "ghostnet",
    name: "Ghostnet",
    rpcUrl: "https://rpc.ghostnet.teztnets.com",
  },
  walletApp: app,
});
```
