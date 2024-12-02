---
icon: window-restore
---

# How to Deploy

The Proof of Concept clicker game has been developed using **Next.js** and **Node.js** with **Express.js**, ensuring a smooth and scalable architecture. Both the frontend and backend utilize **TypeScript** for strong type checking and improved developer experience, and **React** powers the frontend for building dynamic and interactive user interfaces.

**Prerequisites**

To get started with development, make sure the following are installed:

* **Node.js** (v14 or later)
* **npm**
* **MongoDB**
* **Git** (for cloning the repository)

### Clone the Repository

```typescript
git clone https://github.com/softstack/telegram-mini-app-sdk-tezos.git
```

### Navigate to the Proof-of-Concept Directory

```typescript
cd telegram-mini-app-sdk-tezos/proof-of-concept
```

### Navigate to the backend directory

```typescript
cd proofofconcept-backend
```

### Install Dependencies

```typescript
npm install
```

### Configure Environment Variables

* Create a .env file and define MONGO\_URI like:

```typescript
MONGO_URI = "YOUR_MONOGODB_CONNECTION_STRING"
```

### Run the backend-server

```typescript
npm start
```

***

### Navigate to the frontend directory

```typescript
cd proofofconcept-frontend
```

### Install Dependencies

```typescript
npm install
```

### Configure Enviroment Variables

* create .env file and define NEXT\_PUBLIC\_API\_BASE\_URL (eg. domain.com/api/v1/)

```typescript
NEXT_PUBLIC_API_BASE_URL = "YOUR_API_BASE_URL_STRING"
```

### Run the frontend-server in dev mode

```typescript
npm run dev
```

{% hint style="info" %}
The sample app has been developed as a Telegram Mini App. To fully utilize the application, it must be run within the Telegram environment. Some features are limited when used outside of Telegram. For more information on how to host as Telegram Mini App see: [https://github.com/softstack/telegram-mini-app](https://github.com/softstack/telegram-mini-app)
{% endhint %}
