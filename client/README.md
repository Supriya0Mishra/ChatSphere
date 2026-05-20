# ChatSphere 💬

A full-stack real-time chat application built with Node.js, Express, MongoDB, React, and Socket.io.

## Features

- Real-time one-on-one messaging using Socket.io WebSockets
- JWT-based authentication with protected routes
- Live online/offline user presence tracking
- Unseen message count per user
- User profile management
- Responsive UI with Tailwind CSS

## Tech Stack

**Frontend:** React.js, Tailwind CSS, Socket.io-client, Axios, React Router

**Backend:** Node.js, Express.js, Socket.io, MongoDB, Mongoose, JWT, bcryptjs

## Project Structure

```
ChatSphere/
├── client/         → React frontend (Vite)
│   ├── context/    → Auth and Chat context (state management)
│   ├── src/
│   │   ├── components/   → Sidebar, ChatContainer, RightSidebar
│   │   └── pages/        → HomePage, LoginPage, ProfilePage
│
└── server/         → Node.js backend
    ├── controllers/  → userController, messageController
    ├── middleware/   → JWT auth middleware
    ├── models/       → User, Message schemas
    ├── routes/       → userRoutes, messageRoutes
    └── lib/          → DB connection, JWT utils
```

## Getting Started

### Prerequisites
- Node.js v18+
- MongoDB Atlas account

### Installation

1. Clone the repository:
```bash
git clone https://github.com/Supriya0Mishra/ChatSphere.git
cd ChatSphere
```

2. Install server dependencies:
```bash
cd server
npm install
```

3. Install client dependencies:
```bash
cd ../client
npm install
```

4. Set up environment variables:

Create `server/.env`:
```
PORT=5000
JWT_SECRET=your_jwt_secret
MONGODB_URI=your_mongodb_connection_string
```

Create `client/.env`:
```
VITE_BACKEND_URL=http://localhost:5000
```

### Running the App

Start the backend:
```bash
cd server
node server.js
```

Start the frontend:
```bash
cd client
npm run dev
```

Open `http://localhost:5173` in your browser.

## How It Works

1. User signs up and logs in — JWT token is stored and sent with every request
2. On login, a Socket.io connection is established with the user's ID
3. Server maintains a map of `userId → socketId` for all online users
4. When a message is sent, it's saved to MongoDB and emitted directly to the receiver's socket
5. Online status is broadcast to all clients on connect/disconnect events

## Author

Supriya Mishra  
[GitHub](https://github.com/Supriya0Mishra) 