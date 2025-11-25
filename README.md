# AnonChat Live - Production Ready Anonymous Chat

A real-time, anonymous chat application featuring private messaging, random matchmaking, and group chat lobbies. Built with React (Vite) and Node.js (Socket.IO).

## Features

- **Anonymous Login**: No email required, just pick a username.
- **Real-time Messaging**: Instant delivery with Socket.IO.
- **Random Matching**: Connect with strangers instantly.
- **Private Chats**: Request to chat with specific users from the online list.
- **Responsive Design**: Mobile-first UI with smooth transitions and glassmorphism effects.
- **Secure**: Identity management via JWT/Tokens (simulated in this demo via UUID) and HttpOnly cookies (concept).

---

## 🚀 Setup Guide (Local Development)

### Prerequisites

- **Node.js** (v18 or higher)
- **npm** or **yarn**

### 1. Backend Setup

The backend handles WebSocket connections and user sessions.

1.  Navigate to the server directory:
    ```bash
    cd server
    ```
2.  Install dependencies:
    ```bash
    npm install
    ```
3.  Start the server:
    ```bash
    npm start
    ```
    *The server will run on `http://localhost:3001`*

### 2. Frontend Setup

The frontend is a Vite + React application.

1.  Open a new terminal and navigate to the root directory (where `package.json` for the frontend is located).
2.  Install dependencies:
    ```bash
    npm install
    ```
3.  Start the development server:
    ```bash
    npm run dev
    ```
4.  Open your browser at `http://localhost:5173`.

---

## ☁️ Deployment Guide

### 1. Deploying the Backend (Node.js)

You can deploy the backend to services like **Render**, **Railway**, or **Heroku**.

**Example: Deploying to Render**

1.  Push your code to a GitHub repository.
2.  Create a new **Web Service** on Render.
3.  Connect your repository.
4.  Set the **Root Directory** to `server`.
5.  Set the **Build Command** to `npm install`.
6.  Set the **Start Command** to `node index.js`.
7.  Deploy.
8.  **Copy the URL** provided by Render (e.g., `https://anonchat-backend.onrender.com`).

### 2. Deploying the Frontend (React/Vite)

You can deploy the frontend to **Vercel** or **Netlify**.

**Example: Deploying to Vercel**

1.  Push your code to GitHub.
2.  Import the project into Vercel.
3.  Set the **Root Directory** to `./` (default).
4.  **Environment Variables**:
    You must tell the frontend where your backend lives. Add the following environment variable in the Vercel dashboard:
    
    *   **Name**: `VITE_API_URL`
    *   **Value**: Your Backend URL (e.g., `https://anonchat-backend.onrender.com`) - *Do not add a trailing slash*

5.  Deploy.

### 3. Final Configuration

Ensure your Backend allows CORS from your new Frontend URL.

In `server/index.js`, update the CORS configuration if necessary (currently set to `*` for ease of setup):

```javascript
const io = new Server(server, {
  cors: {
    origin: ["https://your-frontend-app.vercel.app", "http://localhost:5173"],
    methods: ["GET", "POST"]
  }
});
```

---

## 📁 Project Structure

```
├── components/          # React Components
│   ├── ui/              # Reusable UI elements (Button, etc.)
│   ├── ChatWindow.tsx   # Main chat interface
│   ├── Sidebar.tsx      # User list and navigation
│   ├── LoginModal.tsx   # Auth screen
│   └── LandingPage.tsx  # Marketing landing page
├── contexts/            # React Contexts
│   └── AuthContext.tsx  # Authentication logic
├── services/            # Services
│   └── socket.ts        # Socket.IO client wrapper
├── server/              # Backend Code
│   ├── index.js         # Main server file
│   └── package.json     # Backend dependencies
├── App.tsx              # Main Application Component
├── types.ts             # TypeScript interfaces
└── index.html           # Entry HTML
```
