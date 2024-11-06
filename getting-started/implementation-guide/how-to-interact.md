---
icon: square-code
---

# How to Interact?

### Connecting a Wallet

To connect a wallet, you need to implement a `connect` method and use it within the `TConnectModalProvider`.

Depending on the blockchain and preferred library being used, the `connect` method implementation may vary. Supported options include `ethers.js`, `web3.js`, and the `Taquito` toolkit for Tezos.

In the following example, we’ll establish a connection to the MetaMask wallet using `web3.js` and the `tconnect.io/evm-provider`.

To work with `web3.js`, it’s essential to create a `web3` object, which requires a provider. TConnect provides a `TConnectEvmProvider` for Etherlink and a `TConnectTezosProvider` for Tezos. Here’s how to implement it:

```
import { EvmWalletApp, TConnectEvmProvider } from '@tconnect.io/evm-provider';
import Web3 from 'web3';

const connect = useCallback(async (walletApp?: EvmWalletApp) => {

const provider = new TConnectEvmProvider({ walletApp, apiKey: 'PIVATE_API_KEY' });
await provider.connect();

}, []);
```

The `walletApp` variable has the type:

```
type EvmWalletApp = 'bitget' | 'metaMask' | 'rainbow' | 'safePal' | 'trust';
```

### Get the current balance of an account

Once the wallet connection is established, you can interact with the blockchain. Here’s an example of how to retrieve the ETH balance:

```
const getBalance = async () => {
	if (!provider || !address) {
		return;
	}
	const web3 = new Web3(provider);
	const balance = await web3.eth.getBalance(address);
	}
```

### Sending a Transaction / Transfer balance

<pre><code>const web3 = new Web3(provider);
<strong>const result = await web3.eth.sendTransaction({
</strong>            from: annaAddress,
            to: bobAddress,
            value: web3.utils.toWei('0.1', 'ether')
        });
</code></pre>

### Interact with a smart contract <a href="#interact-with-a-smart-contract" id="interact-with-a-smart-contract"></a>

This code snippet demonstrates how to use `web3.js` and the `TConnectEvmProvider` to fetch the token balance of a given address from an Etherlink contract with a `balanceOf` method. Here’s an explanation of the code:

```
import { EvmWalletApp, TConnectEvmProvider } from '@tconnect.io/evm-p
import Web3 from 'web3';

const app: EvmWalletApp = 'metaMask';
const provider = new TConnectEvmProvider({ walletApp: app, apiKey: 'PIVATE_API_KEY' });
const web3 = new Web3(provider);

// Contract ABI and address
const contractAddress = '0xYourContractAddress';
const abi = [ /* Insert the ABI of the smart contract here */ ];

// Define a type for the contract instance with the balanceOf method
interface TokenContract extends Web3.eth.Contract {
  methods: {
    balanceOf(address: string): {
      call(): Promise<string>;
    };
  };
}

// Create a contract instance
const contract = new web3.eth.Contract(abi, contractAddress) as TokenContract;

// Function to retrieve the token balance for a specific account
async function getTokenBalance(address: string): Promise<void> {
  try {
    const balance = await contract.methods.balanceOf(address).call();
    console.log('Token Balance:', balance);
  } catch (error) {
    console.error('Error:', error);
  }
}

// Example call with a specific wallet address
const address = '0xYourWalletAddress';
getTokenBalance(address);

```

{% hint style="info" %}
For more detailed information on `web3.js` and its providers, you can refer to the official documentation here: [https://docs.web3js.org](https://docs.web3js.org)
{% endhint %}
