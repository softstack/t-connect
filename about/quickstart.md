---
icon: bullseye-arrow
---

# Quickstart



{% stepper %}
{% step %}
### Installing t:connect using npm

{% hint style="info" %}
The following instructions assume you have a project already created, and you have `npm` installed and operable.
{% endhint %}

```
npm install @tconnect.io/modal
npm install @tconnect.io/evm-provider
npm install @tconnect.io/tezos-wc-provider
npm install @tconnect.io/tezos-beacon-provider
```
{% endstep %}

{% step %}
### Importing

```
import { TConnectModalProvider } from '@tconnect.io/modal';
import { TConnectEvmProvider } from '@tconnect.io/evm-provider';
import { TConnectTezosBeaconProvider } from '@tconnect.io/tezos-beacon-provider';
import { TConnectTezosWcProvider } from '@tconnect.io/tezos-wc-provider';
```
{% endstep %}

{% step %}
### Example using TConnectEvmProvider

```
import { EvmWalletApp, TConnectEvmProvider } from '@tconnect.io/evm-provider';

const app: EvmWalletApp = 'metaMask';
const provider = new TConnectEvmProvider({ 
        walletApp: app,
        apiKey: 'PRIVATE_API_KEY' 
 });
```
{% endstep %}
{% endstepper %}
