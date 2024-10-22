---
icon: window-restore
---

# How to Deploy

### Clone the Repository

```
git clone https://github.com/softstack/telegram-mini-app-sdk-tezos.git
```

### Navigate to the Proof-of-Concept Directory

```
cd telegram-mini-app-sdk-tezos/proof-of-concept
```

### Navigate to the backend directory

```
cd proofofconcept-backend
```

### Install Dependencies

```
npm install
```

### Configure Environment Variables

* Create a .env file and define MONGO\_URI like:

```
MONGO_URI = "YOUR_MONOGODB_CONNECTION_STRING"
```

* Add your API keys and configuration settings.

### Run the backend-server

```
npm start
```

### Navigate to the frontend directory

```
cd proofofconcept-frontend
```

### Install Dependencies

```
npm install
```

### Configure Enviroment Variables

* create .env file and define API\_BASE\_URL

```
API_BASE_URL = "YOUR_API_BASE_URL_STRING"
```

### Run the frontend-server in dev mode

```
npm run dev
```

