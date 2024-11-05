---
icon: square-code
---

# Modal

### Wallet Connection Modal

**t:connect** provides a built-in **Wallet Connection Modal** that simplifies the process of connecting users to the Tezos and Etherlink blockchains via supported wallets. This modal is a ready-to-use component that developers can integrate into their Telegram Mini Apps, allowing users to securely and effortlessly connect their wallets.

**Features of the Wallet Connection Modal**

* **User-Friendly Interface**: An intuitive UI that guides users through the wallet connection process.
* **Multi-Chain Support**: Supports both Tezos and Etherlink chains, offering flexibility for various applications.
* **Multiple Wallet Options**: Compatible with a range of wallets like MetaMask, Trust Wallet, Altme, and more.
* **Secure Authentication**: Ensures that user credentials and private keys remain secure during the connection.
* **Customizable Appearance**: Developers can tailor the modal's look and feel to match their app's branding.

### How to Implement the Wallet Connection Modal

{% stepper %}
{% step %}
#### Initialize t:connect in Your Mini App

```
// Some code
```
{% endstep %}

{% step %}
#### Display the Wallet Connection Modal

```
// Some code
```
{% endstep %}

{% step %}
#### Customize the Modal (Optional)

```
// Some code
```
{% endstep %}
{% endstepper %}

### Modal Workflow

{% stepper %}
{% step %}
#### Blockchain  Selection

The modal first provides the option to choose the blockchain  to be used. The user can select between Tezos or Etherlink.

<img src="../../.gitbook/assets/Screenshot 2024-11-05 at 09.24.27.png" alt="" data-size="original">
{% endstep %}

{% step %}
#### Wallet Selection

After selecting the Blockchain, the user is prompted to choose a wallet. The list of available wallets is automatically filtered based on the previously chosen blockchain.

<img src="../../.gitbook/assets/Screenshot 2024-11-05 at 09.24.46.png" alt="" data-size="original">
{% endstep %}

{% step %}
#### Wallet Connection Execution

Once a wallet is selected, the `connect()` method is triggered to establish the connection. The user is prompted within the wallet to authorize the connection.

<img src="../../.gitbook/assets/Screenshot 2024-11-05 at 09.32.43.png" alt="" data-size="original">
{% endstep %}

{% step %}
#### Connection Etablished

After a successful connection, the modal closes, and the developer can use the wallet information (e.g., address, wallet name, chain) for further interactions.
{% endstep %}
{% endstepper %}
