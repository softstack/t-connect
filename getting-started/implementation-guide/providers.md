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
const provider = new TConnectEvmProvider({ walletApp: app, apiKey: 'PRIVATE_API_KEY' });
```

```
TConnectEvmProviderOptions { 
        apiKey: string; 
        walletApp?: EvmWalletApp; 
    }
```

### Configure TConnectWcProvider

```
import { TConnectTezosWcProvider } from '@tconnect.io/tezos-wc-provider';
import { TezosWcWalletApp } from '@tconnect.io/tezos-wc-provider;

const provider = new TConnectTezosWcProvider({
				apiKey: 'PRIVATE_API_KEY',
				walletApp,
				network: 'ghostnet',
			});
```

```
TConnectTezosWcProviderOptions {
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
				secretSeed,
				apiKey: 'a',
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
    apiKey: string;
    network: Network;
    walletApp?: TezosBeaconWalletApp;
}
```

{% hint style="info" %}
If no walletApp is provided when creating the provider, a wallet connection can be established using a connection string. However, if you intend to connect to a wallet represented by the type `EvmWalletApp, TezosBeaconWalletApp or TezosWcWalletApp` it is recommended to provide it explicitly.
{% endhint %}
