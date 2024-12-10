# Connect via connection string

## Connect via connection string

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
