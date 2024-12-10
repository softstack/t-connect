# Connect via connection string

The `TConnectEvmProvider` allows establishing a connection to an Etherlink wallet by providing a `connectionString`. This is particularly useful when the user does not specify a particular wallet application.

### **Example** **Usage of the Connection String**

```typescript
// Import provider
import { TConnectEvmProvider } from '@tconnect.io/evm-provider';

// Initialize provider
const provider = new TConnectEvmProvider({
  appName: "Example App",
  appUrl: "https://your-domain.io",
  bridgeUrl: "https://tconnect.io",
  apiKey: "PRIVATE_API_KEY",
});

// Listen for 'connectionString' event
provider.on("connectionString", (connectionString) => {
  console.log(connectionString);
});
```

### **Explanation**

* **Initialization**: The `TConnectEvmProvider` is initialized with basic configuration options such as `appName`, `appUrl`, `bridgeUrl`, and `apiKey`.
* **Handling the Connection String**: Using the `on("connectionString")` method, developers can access the `connectionString` to use it as needed.
* **Flexibility**: The `connectionString` can be utilized when the `walletApp` parameter is omitted, enabling dynamic and automated wallet connections.

This functionality is not limited to the `TConnectEvmProvider` but is applicable to all providers offered by `TConnect`.
