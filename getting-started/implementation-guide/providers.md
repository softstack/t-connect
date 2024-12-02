---
icon: square-code
---

# Providers

Provider services enable connection to the Tezos and Etherlink networks. Providers are required to connect an application to a Tezos or Etherlink node, as they facilitate access to data queries, sending transactions, and interacting with smart contracts.

TConnect offers three providers. For Etherlink, you must use the `TConnectEvmProvider`, while the `TConnectTezosBeaconProvider` and `TConnectTezosWcProvider` are recommended for Tezos.

### &#x20;Configure TConnectEvmProvider

```typescript
import { EvmWalletApp, TConnectEvmProvider } from '@tconnect.io/evm-provider';

const app: EvmWalletApp = 'metaMask';
const provider = new TConnectEvmProvider({
              appName: "Example App",
              appUrl: "https://your-domain.io",
              bridgeUrl: "https://tconnect.io",
              apiKey: "PRIVATE_API_KEY",
              walletApp: app,
  });
```

```typescript
TConnectEvmProviderOptions { 
              appName: string;
              appUrl: string;
              appIcon?: string;
              bridgeUrl: string;
              apiKey: string;
              walletApp?: EvmWalletApp;
    }
```

### Configure TConnectWcProvider

<pre class="language-typescript"><code class="lang-typescript"><strong>import { TConnectTezosWcProvider } from '@tconnect.io/tezos-wc-provider';
</strong>import {TezosWcWalletApp} from '@tconnect.io/tezos-wc-provider';

const app: TezosWcWalletApp = "kukai";
const provider = new TConnectTezosWcProvider({
                appName: "Example App",
                appUrl: "https://your-domain.io",
                bridgeUrl: "https://tconnect.io",
                apiKey: "PRIVATE_API_KEY",
                walletApp: app,
                network: "ghostnet",
  });
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
import { TConnectTezosBeaconProvider } from '@tconnect.io/tezos-beacon-provider';
import { TezosBeaconWalletApp } from '@tconnect.io/tezos-beacon-provider;

const app: TezosBeaconWalletApp = "altme";
const secretSeed = "SECRET_SEED";
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
If no walletApp is provided when creating the provider, a wallet connection can be established using a connection string. However, if you intend to connect to a wallet represented by the type `EvmWalletApp, TezosBeaconWalletApp or TezosWcWalletApp` it is recommended to provide it explicitly.
{% endhint %}
