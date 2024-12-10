---
icon: square-code
---

# Providers

Provider services enable connection to the Tezos and Etherlink networks. Providers are required to connect an application to a Tezos or Etherlink node, as they facilitate access to data queries, sending transactions, and interacting with smart contracts.

TConnect offers three providers. For Etherlink, you must use the `TConnectEvmProvider`, while the `TConnectTezosBeaconProvider` and `TConnectTezosWcProvider` are recommended for Tezos.

### &#x20;Configure TConnectEvmProvider

The `TConnectEvmProvider` class is a provider implementation that requires specific configuration options passed to its constructor during instantiation. These options are provided as an object of type `TConnectEvmProviderOptions`.

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

async function myAsyncFunction() {
  try {
    // Connect to wallet
    await provider.connect();
  } catch (error) {
    console.error("Error connecting to wallet:", error);
  }
}
```

### Configure TConnectWcProvider

<pre class="language-typescript"><code class="lang-typescript">// Import provider
<strong>import { TConnectTezosWcProvider } from '@tconnect.io/tezos-wc-provider';
</strong>import {TezosWcWalletApp} from '@tconnect.io/tezos-wc-provider';

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
 // Connect to wallet
 await provider.connect();
</code></pre>

```typescript
TConnectTezosWcProviderOptions {
                appName: string;
                appUrl: string;
                appIcon?: string;
                apiKey: string;
                network: Network;
                bridgeUrl: string;
                walletApp?: TezosWcWalletApp;
}
```

### Configure TConnectTezosProvider

```typescript
// Import provider
import { TConnectTezosBeaconProvider } from '@tconnect.io/tezos-beacon-provider';
import { TezosBeaconWalletApp } from '@tconnect.io/tezos-beacon-provider;

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
 // Connect to wallet
 await provider.connect();
```

```typescript
TConnectTezosBeaconProviderOptions {
                appName: string;
                appUrl: string;
                appIcon?: string;
                bridgeUrl: string;
                secretSeed: string;
                apiKey: string;
                network: Network;
                walletApp?: TezosBeaconWalletApp;
}
```

{% hint style="info" %}
If no walletApp is provided when creating the provider, a wallet connection can be established using the connection string. However, if you intend to connect to a wallet represented by the type `EvmWalletApp, TezosBeaconWalletApp or TezosWcWalletApp` it is recommended to provide it explicitly.
{% endhint %}

### Connect via connection string

```typescript
// Import provider
import { TConnectEvmProvider } from '@tconnect.io/evm-provider';

// Initialize provider
const provider = new TConnectEvmProvider({
                appName: "Example App",
                appUrl: "https://your-domain.io",
                bridgeUrl: "https://tconnect.io",
                apiKey: "PRIVATE_API_KEY",
  });
  
 // Listen for 'connectionString' event
 provider.on("connectionString", (connectionString) => {
   console.log(connectionString);
 });
 
 // Connect to wallet
 await provider.connect();
```
