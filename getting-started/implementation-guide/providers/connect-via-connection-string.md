# Connect via connection string

The `TConnectEvmProvider` allows establishing a connection to an Etherlink wallet by providing a `connectionString`. This is particularly useful when the user does not specify a particular wallet application.

### **Example** **Usage of the Connection String**

```typescript
// Import provider
import { TConnectEvmProvider } from "@tconnect.io/evm-provider";

import { useCallback, useState } from "react";

function MyComponent() {
  // Define state for connection string
  const [connectionString, setConnectionString] = useState("");

  // Define connect function
  const connect = useCallback(async () => {
    try {
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
        setConnectionString(connectionString);
      });

      // Connect to wallet
      await provider.connect();
    } catch (err) {
      console.log(err);
    }
  }, []);

  // Render component
  return (
    <div className="MyComponent">
      <p>Connection String: {connectionString}</p>
      <button onClick={connect}> get connection string</button>
    </div>
  );
}

export default MyComponent;
```

### **Explanation**

* **Initialization**: The `TConnectEvmProvider` is initialized with basic configuration options such as `appName`, `appUrl`, `bridgeUrl`, and `apiKey`.
* **Handling the Connection String**: Using the `on("connectionString")` method, developers can access the `connectionString` to use it as needed.

This functionality is not limited to the `TConnectEvmProvider` but is applicable to all providers offered by `TConnect`.
