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
npm install <tconnect>
```
{% endstep %}

{% step %}
### Import the libary in your Telegram Mini App

The constructor of the `tconnect` class takes an RPC URL as a parameter. It has to be a string. A list of  nodes can be accessed [here](../getting-started/implementation-guide/providers.md).

```
import { tconnect } from '<@tconnect/tconnect>';

const tconnect = new teconnect('https://YOUR_PREFERRED_RPC_URL');
```
{% endstep %}

{% step %}
### Configuration

```
// Some code
```
{% endstep %}
{% endstepper %}

## Examples

```
// Some code
```

