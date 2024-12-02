---
icon: square-code
---

# How to Implement t:connect?

{% stepper %}
{% step %}
## Installing t:connect using npm

Installing the Modal

```typescript
npm install @tconnect.io/modal
```

#### Install the Evm Provider

```typescript
npm install @tconnect.io/evm-provider
```

#### Install the Tezos Beacon Provider

```typescript
npm install @tconnect.io/tezos-beacon-provider
```

#### Install the Tezos Wallet Connect Provider

```typescript
npm install @tconnect.io/tezos-wc-provider
```
{% endstep %}

{% step %}
## Import the Modal in your Telegram Mini App

```typescript
import { TConnectModalProvider, useTConnectModal } from '@tconnect.io/modal';
```
{% endstep %}

{% step %}
## Import a Provider in your Telegram Mini App

```typescript
import { TConnectEvmProvider } from '@tconnect.io/evm-provider';
```

```typescript
import { TConnectTezosBeaconProvider } from '@tconnect.io/tezos-beacon-provider';
```

```typescript
import { TConnectTezosWcProvider } from '@tconnect.io/tezos-wc-provider';
```
{% endstep %}
{% endstepper %}
