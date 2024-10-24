---
icon: square-code
---

# How to Implement t:connect?

{% stepper %}
{% step %}
### Installing t:connect using npm

```
npm install <tconnect>
```
{% endstep %}

{% step %}
### Import the libary in your Telegram Mini App

The constructor of the `tconnect` class takes an RPC URL as a parameter. It has to be a string. A list of  nodes can be accessed [here](providers.md).

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
