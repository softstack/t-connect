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

* create .env file and define NEXT\_PUBLIC\_API\_BASE\_URL (eg. localhost:5000)

```
NEXT_PUBLIC_API_BASE_URL = "YOUR_API_BASE_URL_STRING"
```

### Run the frontend-server in dev mode

```
npm run dev
```

{% hint style="info" %}
The sample app has been developed as a Telegram Mini App. To fully utilize the application, it must be run within the Telegram environment. Some features are limited when used outside of Telegram. For more information on how to host as Telegram Mini App see: [https://github.com/softstack/telegram-mini-app](https://github.com/softstack/telegram-mini-app)
{% endhint %}
