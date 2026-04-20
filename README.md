# 💬 Quick Chat App

A modern, real-time chat application built with React and Node.js, featuring instant messaging, user authentication, and seamless user experience.

![React](https://img.shields.io/badge/React-19.0.0-61DAFB?logo=react)
![Node.js](https://img.shields.io/badge/Node.js-Express-339933?logo=node.js)
![MongoDB](https://img.shields.io/badge/MongoDB-Mongoose-47A248?logo=mongodb)
![Socket.io](https://img.shields.io/badge/Socket.io-4.8.1-010101?logo=socket.io)

## 📋 Table of Contents

- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Prerequisites](#-prerequisites)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Usage](#-usage)
- [Project Structure](#-project-structure)
- [API Documentation](#-api-documentation)
- [Real-time Features](#-realtime-features)
- [Deployment](#-deployment)
- [Contributing](#-contributing)
- [License](#-license)

## ✨ Features

### 🔐 Authentication & User Management
- **User Registration**: Create account with email, password, full name, and bio
- **Secure Login**: JWT-based authentication with password hashing
- **Profile Management**: Update profile picture, name, and bio
- **Protected Routes**: Secure access to authenticated pages

### 💬 Real-time Messaging
- **Instant Messaging**: Send and receive messages in real-time using Socket.io
- **Image Sharing**: Upload and share images via Cloudinary integration
- **Message Status**: Track seen/unseen message status
- **Unread Counts**: Visual indicators for unread messages per user

### 👥 User Experience
- **Online/Offline Status**: Real-time presence indicators
- **User Search**: Search functionality to find users quickly
- **Media Gallery**: View all shared images in a dedicated gallery
- **Responsive Design**: Mobile-friendly interface with adaptive layouts
- **Modern UI**: Beautiful, intuitive interface with Tailwind CSS

## 🛠 Tech Stack

### Frontend
- **React 19** - UI library
- **Vite** - Build tool and dev server
- **Tailwind CSS 4** - Utility-first CSS framework
- **React Router DOM 7** - Client-side routing
- **Socket.io Client 4.8** - Real-time communication
- **Axios** - HTTP client
- **React Hot Toast** - Toast notification

### Backend
- **Node.js** - Runtime environment
- **Express 5** - Web framework
- **MongoDB** - NoSQL database
- **Mongoose 8** - MongoDB object modeling
- **Socket.io 4.8** - Real-time bidirectional communication
- **JWT** - JSON Web Tokens for authentication
- **bcryptjs** - Password hashing
- **Cloudinary** - Cloud-based image management

## 📦 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v18 or higher)
- **npm** or **yarn**
- **MongoDB** (local or cloud instance like MongoDB Atlas)
- **Cloudinary Account** (for image storage)

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone <repository-url>
cd Quick-Chat-App
```

### 2. Install Server Dependencies

```bash
cd server
npm install
```

### 3. Install Client Dependencies

```bash
cd ../client
npm install
```

## ⚙️ Configuration

### Server Environment Variables

Create a `.env` file in the `server` directory:

```env
# MongoDB Connection
MONGODB_URI=mongodb://localhost:27017
# or for MongoDB Atlas:
# MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net

# JWT Secret (use a strong random string)
JWT_SECRET=your_super_secret_jwt_key_here

# Cloudinary Configuration
CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret

# Server Port (optional, defaults to 5000)
PORT=5000

# Node Environment
NODE_ENV=development
```

### Client Environment Variables

Create a `.env` file in the `client` directory:

```env
# Backend API URL
VITE_BACKEND_URL=http://localhost:5000
# For production, use your deployed backend URL:
# VITE_BACKEND_URL=https://your-backend-url.vercel.app
```

### Cloudinary Setup

1. Sign up for a free account at [Cloudinary](https://cloudinary.com/)
2. Navigate to your dashboard
3. Copy your Cloud Name, API Key, and API Secret
4. Add them to your server `.env` file

## 🧩 Local Development Notes

- Use `npm install` in both `client` and `server` folders before running the project.
- Keep your Cloudinary credentials and `JWT_SECRET` secure and never commit real secrets.
- If you use MongoDB Atlas, make sure your IP whitelist includes your current address.

## 💻 Usage

### Development Mode

#### Start the Server

```bash
cd server
npm run server
# or
npm start
```

The server will run on `http://localhost:5000` (or your specified PORT)

#### Start the Client

```bash
cd client
npm run dev
```

The client will run on `http://localhost:5173` (default Vite port)

### Production Build

#### Build the Client

```bash
cd client
npm run build
```

The production build will be in the `client/dist` directory.

#### Start Production Server

```bash
cd server
npm start
```

## 📁 Project Structure

```
Quick-Chat-App/
├── client/                 # Frontend React application
│   ├── public/            # Static assets
│   ├── src/
│   │   ├── assets/        # Images and icons
│   │   ├── components/    # React components
│   │   │   ├── Sidebar.jsx
│   │   │   ├── ChatContainer.jsx
│   │   │   └── RightSidebar.jsx
│   │   ├── context/       # React Context providers
│   │   │   ├── AuthContext.jsx
│   │   │   └── ChatContext.jsx
│   │   ├── lib/           # Utility functions
│   │   ├── pages/         # Page components
│   │   │   ├── HomePage.jsx
│   │   │   ├── LoginPage.jsx
│   │   │   └── ProfilePage.jsx
│   │   ├── App.jsx        # Main app component
│   │   └── main.jsx       # Entry point
│   ├── package.json
│   └── vite.config.js
│
├── server/                # Backend Node.js application
│   ├── controllers/       # Route controllers
│   │   ├── userController.js
│   │   └── messageController.js
│   ├── lib/              # Utility libraries
│   │   ├── db.js         # MongoDB connection
│   │   ├── utils.js      # JWT utilities
│   │   └── cloudinary.js # Cloudinary config
│   ├── middleware/       # Express middleware
│   │   └── auth.js       # JWT authentication
│   ├── models/           # Mongoose models
│   │   ├── User.js
│   │   └── Message.js
│   ├── routes/           # API routes
│   │   ├── userRoutes.js
│   │   └── messageRoutes.js
│   ├── server.js         # Server entry point
│   └── package.json
│
└── README.md
```

## 📡 API Documentation

### Authentication Endpoints

#### Register User
```http
POST /api/auth/signup
Content-Type: application/json

{
  "fullName": "John Doe",
  "email": "john@example.com",
  "password": "password123",
  "bio": "Software developer"
}
```

**Response:**
```json
{
  "success": true,
  "userData": { ... },
  "token": "jwt_token_here",
  "message": "Account created successfully"
}
```

#### Login
```http
POST /api/auth/login
Content-Type: application/json

{
  "email": "john@example.com",
  "password": "password123"
}
```

**Response:**
```json
{
  "success": true,
  "userData": { ... },
  "token": "jwt_token_here",
  "message": "Login successful"
}
```

#### Check Authentication
```http
GET /api/auth/check
Headers: { "token": "jwt_token_here" }
```

#### Update Profile
```http
PUT /api/auth/update-profile
Headers: { "token": "jwt_token_here" }
Content-Type: application/json

{
  "fullName": "John Doe Updated",
  "bio": "Updated bio",
  "profilePic": "base64_image_string" // optional
}
```

### Message Endpoints

#### Get All Users (for Sidebar)
```http
GET /api/messages/users
Headers: { "token": "jwt_token_here" }
```

**Response:**
```json
{
  "success": true,
  "users": [ ... ],
  "unseenMessages": {
    "userId1": 5,
    "userId2": 2
  }
}
```

#### Get Messages with User
```http
GET /api/messages/:id
Headers: { "token": "jwt_token_here" }
```

**Response:**
```json
{
  "success": true,
  "messages": [ ... ]
}
```

#### Send Message
```http
POST /api/messages/send/:id
Headers: { "token": "jwt_token_here" }
Content-Type: application/json

{
  "text": "Hello!",
  "image": "base64_image_string" // optional
}
```

#### Mark Message as Seen
```http
PUT /api/messages/mark/:id
Headers: { "token": "jwt_token_here" }
```

## 🔄 Real-time Features

### Socket.io Events

#### Client → Server

**Connection:**
```javascript
socket = io(backendUrl, {
  query: { userId: userData._id }
});
```

#### Server → Client

**Online Users Update:**
```javascript
socket.on("getOnlineUsers", (userIds) => {
  // userIds: array of online user IDs
});
```

**New Message:**
```javascript
socket.on("newMessage", (newMessage) => {
  // newMessage: message object
});
```

### How It Works

1. **User Connection**: When a user logs in, a Socket.io connection is established with their `userId`
2. **Online Status**: The server maintains a `userSocketMap` mapping `userId` to `socketId`
3. **Real-time Updates**: When a message is sent, the server emits it directly to the receiver's socket
4. **Presence**: Online/offline status is broadcasted to all connected clients

## 🚢 Deployment

### Deploying to Vercel

The project includes `vercel.json` configuration files for both client and server.

#### Deploy Server

1. Install Vercel CLI: `npm i -g vercel`
2. Navigate to `server` directory
3. Run `vercel`
4. Add environment variables in Vercel dashboard

#### Deploy Client

1. Navigate to `client` directory
2. Run `vercel`
3. Update `VITE_BACKEND_URL` in client environment variables

### Environment Variables for Production

Ensure all environment variables are set in your hosting platform:
- MongoDB connection string
- JWT secret
- Cloudinary credentials
- Backend URL (for client)

## 🧪 Testing

### Manual Testing Checklist

- [ ] User registration
- [ ] User login
- [ ] Profile update
- [ ] Send text message
- [ ] Send image message
- [ ] Real-time message delivery
- [ ] Online/offline status
- [ ] Unread message counts
- [ ] Message seen status
- [ ] User search functionality
- [ ] Responsive design on mobile

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Code Style

- Use consistent indentation (2 spaces)
- Follow React best practices
- Write meaningful commit messages
- Add comments for complex logic

## 📝 License

This project is licensed under the ISC License.

## 👤 Author

Your Name - [Your GitHub](https://github.com/yourusername)

## 🙏 Acknowledgments

- [Socket.io](https://socket.io/) for real-time communication
- [Cloudinary](https://cloudinary.com/) for image storage
- [Tailwind CSS](https://tailwindcss.com/) for styling
- [React](https://react.dev/) community

## 📞 Support

If you have any questions or run into issues, please:
- Open an issue on GitHub
- Check existing issues for solutions
- Review the documentation above

---

**Made with ❤️ using React and Node.js**

