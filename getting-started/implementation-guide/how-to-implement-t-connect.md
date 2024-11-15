---
icon: square-code
---

# How to Implement t:connect?

{% stepper %}
{% step %}
## Installing t:connect using npm

Installing the Modal

```
npm install @tconnect.io/modal
```

#### Install the Evm Provider

```
npm install @tconnect.io/evm-provider
```

#### Install the Tezos Beacon Provider

```
npm install @tconnect.io/tezos-beacon-provider
```

#### Install the Tezos Wallet Connect Provider

```
npm install @tconnect.io/tezos-wc-provider
```
{% endstep %}

{% step %}
## Import the Modal in your Telegram Mini App

```
import { TConnectModalProvider, useTConnectModal } from '@tconnect.io/modal';
```
{% endstep %}

{% step %}
## Import a Provider in your Telegram Mini App

```
import { TConnectEvmProvider } from '@tconnect.io/evm-provider';
```

```
import { TConnectTezosBeaconProvider } from '@tconnect.io/tezos-beacon-provider';
```

```
import { TConnectTezosWcProvider } from '@tconnect.io/tezos-wc-provider';
```
{% endstep %}
{% endstepper %}
