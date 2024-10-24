---
icon: square-code
---

# Providers

Provider services enable connection to the Tezos and Etherlink networks. Providers are required to connect an application to a Tezos or Etherlink node, as they facilitate access to data queries, sending transactions, and interacting with smart contracts.

### Configure provider

```
// Some code
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
