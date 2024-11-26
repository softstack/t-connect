---
icon: square-code
---

# Providers

Provider services enable connection to the Tezos and Etherlink networks. Providers are required to connect an application to a Tezos or Etherlink node, as they facilitate access to data queries, sending transactions, and interacting with smart contracts.

TConnect offers three providers. For Etherlink, you must use the `TConnectEvmProvider`, while the `TConnectTezosBeaconProvider` and `TConnectTezosWcProvider` are recommended for Tezos.

### &#x20;Configure TConnectEvmProvider

```
import { EvmWalletApp, TConnectEvmProvider } from '@tconnect.io/evm-provider';

const app: EvmWalletApp = 'metaMask';
const provider = new TConnectEvmProvider({ 
                                 appName: "Example App";
                                 appUrl: "https://domain.io"";
                                 bridgeUrl: "https://bridge.url.io";
                                 walletApp: app,
                                 apiKey: 'PRIVATE_API_KEY' 
                                 });
```

```
TConnectEvmProviderOptions { 
        appName: string;
        appUrl: string;
        bridgeUrl: string;
        apiKey: string; 
        walletApp?: EvmWalletApp; 
    }
```

### Configure TConnectWcProvider

<pre><code><strong>import { TConnectTezosWcProvider } from '@tconnect.io/tezos-wc-provider';
</strong>import { TezosWcWalletApp } from '@tconnect.io/tezos-wc-provider;

const provider = new TConnectTezosWcProvider({
				appName: "Example App";
				appUrl: "https://domain.io"";
				bridgeUrl: "https://bridge.url.io";
				apiKey: 'PRIVATE_API_KEY',
				walletApp,
				network: 'ghostnet',
			});
</code></pre>

```
TConnectTezosWcProviderOptions {
	appName: string;
	appUrl: string;
	bridgeUrl: string;
	apiKey: string;
	network: Network;
	walletApp?: TezosWcWalletApp;
}
```

### Configure TConnectTezosProvider

```
import { TConnectTezosBeaconProvider } from '@tconnect.io/tezos-beacon-provider';
import { TezosBeaconWalletApp } from '@tconnect.io/tezos-beacon-provider;

const provider = new TConnectTezosBeaconProvider({
				appName: "Example App";
				appUrl: "https://domain.io"";
				bridgeUrl: "https://bridge.url.io";
				secretSeed,
				apiKey: 'PRIVATE_API_KEY',
				network: { 
				           type: 'ghostnet',
				           name: 'Ghostnet',
				           rpcUrl: 'https://rpc.ghostnet.teztnets.com'
				          },
				walletApp,
			});
```

```
TConnectTezosBeaconProviderOptions {
    secretSeed: string;
    appName: string;
    appUrl: string;
    bridgeUrl: string;
    apiKey: string;
    network: Network;
    walletApp?: TezosBeaconWalletApp;
}
```

{% hint style="info" %}
If no walletApp is provided when creating the provider, a wallet connection can be established using a connection string. However, if you intend to connect to a wallet represented by the type `EvmWalletApp, TezosBeaconWalletApp or TezosWcWalletApp` it is recommended to provide it explicitly.
{% endhint %}
