---
icon: square-code
---

# Providers

Provider services enable connection to the Tezos and Etherlink networks. Providers are required to connect an application to a Tezos or Etherlink node, as they facilitate access to data queries, sending transactions, and interacting with smart contracts.

TConnect provides two providers, one for each blockchain. For Etherlink, it uses the `TConnectEvmProvider`, while for the Tezos main chain, the `TConnectTezosProvider` is used. While their functionalities are similar, there are differences in the configuration.

### Configure TConnectTezosProvider

The `EvmWalletApp` type is defined as a union type, which allows the variable `app` to be one of the following values: `'bitget'`, `'metaMask'`, `'rainbow'`, `'safePal'`, or `'trust'`. These are the supported wallet applications that can be used with the `TConnectEvmProvider`.

An instance of `TConnectEvmProvider` is created, where `walletApp` is set to the value of `app` (in this case, `'metaMask'`), and an `apiKey` is provided as `'PRIVATE_API_KEY'`. The `TConnectEvmProvider` constructor expects an object that includes at least two properties: `walletApp`, which defines which wallet to connect to, and `apiKey`, which is required for the provider to authenticate with the service.

```
import { EvmWalletApp, TConnectEvmProvider } from '@tconnect.io/evm-provider';

const app: EvmWalletApp = 'metaMask';
const provider = new TConnectEvmProvider({ walletApp: app, apiKey: 'PRIVATE_API_KEY' });
```

### Configure TConnectTezosProvider

The `TezosWalletApp` type defines a union of string literals representing different wallet applications for the Tezos network. In this case, it can either be `'altme'` or `'_generic_'`, which are identifiers for specific Tezos wallet applications that the provider can interact with.

The `TConnectTezosProviderProps` is an object that requires more than just an API key and wallet app. It also includes additional properties like `secretSeed`, and a `network` object that specifies details such as the network type, name, and RPC URL, which are essential for connecting to the Tezos blockchain.

```
import { TConnectTezosProvider, TezosWalletApp } from '@tconnect.io/tezos-provider';

const app: TezosWalletApp = 'altme';
const provider = new TConnectTezosProvider({
    secretSeed,
    apiKey: 'PRIVATE_API_KEY',
    network: { 
        type: 'ghostnet',
        name: 'Ghostnet',
        rpcUrl: 'https://rpc.ghostnet.teztnets.com' },
    walletApp: app,
});
```

### RPC nodes

What to consider when selecting a node:

**Trust**: Choose a node with trusted operators that won’t manipulate or censor your requests.

**Reliability**: Pay attention to the node's uptime. For critical applications, running your own node or using a specialized provider may be beneficial.

**Endpoint Support**: Public nodes offer various endpoints. Check if the necessary endpoints for your app are available.

### Tezos rpc nodes

| provider         | network  | url                                                                      |
| ---------------- | -------- | ------------------------------------------------------------------------ |
| Tezos Foundation | mainnet  | [https://rpc.tzbeta.net/](https://rpc.tzbeta.net/)                       |
| Tezos Foundation | ghostnet | [https://rpc.ghostnet.teztnets.com/](https://rpc.ghostnet.teztnets.com/) |
| ECAD Labs        | mainnet  | [https://mainnet.ecadinfra.com](https://mainnet.ecadinfra.com)           |
| ECAD Labs        | ghostnet | [https://ghostnet.ecadinfra.com](https://ghostnet.ecadinfra.com)         |

### Etherlink rpc nodes

| provider         | network  | url                                                                        |
| ---------------- | -------- | -------------------------------------------------------------------------- |
| Tezos Foundation | mainnet  | [https://node.mainnet.etherlink.com](https://node.mainnet.etherlink.com)   |
| Tezos Foundation | ghostnet | [https://node.ghostnet.etherlink.com](https://node.ghostnet.etherlink.com) |
