<h1 align="center">💬 Chatbox - Real-Time Chat Application</h1>



<p align="center">
  A modern, full-stack real-time chat application with authentication, email notifications, and cloud-based image uploads.
</p>

---

## 📋 Table of Contents

- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Prerequisites](#-prerequisites)
- [Installation](#-installation)
- [Environment Variables](#-environment-variables)
- [Running the Application](#-running-the-application)
- [API Endpoints](#-api-endpoints)
- [Deployment](#-deployment)
- [Contributing](#-contributing)

---

## ✨ Features

### Authentication & Security
- 🔐 **Custom JWT Authentication** - Secure user authentication without 3rd-party services
- 🔒 **Password Encryption** - BCrypt for secure password hashing
- 🍪 **HTTP-Only Cookies** - Secure token storage
- 🚦 **API Rate-Limiting** - Powered by Arcjet for DDoS protection

### Messaging & Communication
- ⚡ **Real-Time Messaging** - Instant bidirectional communication via Socket.io
- 🟢 **Online/Offline Status** - Live user presence indicators
- ✍️ **Typing Indicators** - See when someone is typing
- 🔔 **Sound Notifications** - Customizable notification and typing sounds (with toggle)
- 📨 **Message History** - Persistent chat history with MongoDB

### Media & Content
- 🗂️ **Image Uploads** - Cloudinary integration for profile pictures and chat images
- 📧 **Welcome Emails** - Automated welcome emails on signup using Resend
- 🎨 **Beautiful UI** - Modern, responsive design with Tailwind CSS & DaisyUI

### User Experience
- 📱 **Responsive Design** - Works seamlessly on desktop, tablet, and mobile
- 🎭 **User Profiles** - Customizable profiles with avatars
- 🔍 **Search Users** - Find and connect with other users
- 💾 **State Management** - Efficient state handling with Zustand

---

## 🛠️ Tech Stack

### Frontend
- **React 19** - Modern UI library
- **Vite** - Lightning-fast build tool
- **Tailwind CSS** - Utility-first CSS framework
- **DaisyUI** - Component library for Tailwind
- **Socket.io Client** - Real-time communication
- **Axios** - HTTP client for API requests
- **Zustand** - Lightweight state management
- **React Router** - Client-side routing
- **Lucide React** - Beautiful icon library
- **React Hot Toast** - Elegant notifications

### Backend
- **Node.js 20+** - JavaScript runtime
- **Express.js** - Web application framework
- **MongoDB** - NoSQL database
- **Mongoose** - MongoDB ODM
- **Socket.io** - Real-time bidirectional communication
- **JWT** - JSON Web Tokens for authentication
- **BCrypt.js** - Password hashing
- **Cloudinary** - Cloud-based image storage
- **Resend** - Email delivery service
- **Arcjet** - Rate limiting and security
- **CORS** - Cross-Origin Resource Sharing
- **Cookie Parser** - Parse HTTP cookies
- **Dotenv** - Environment variable management

---

## 📁 Project Structure

```
chat-app/
├── backend/                      # Backend server
│   ├── src/
│   │   ├── controllers/          # Route controllers
│   │   │   ├── auth.controller.js        # Authentication logic
│   │   │   └── message.controller.js     # Message handling logic
│   │   ├── emails/               # Email templates and handlers
│   │   │   ├── emailHandlers.js          # Email sending logic
│   │   │   └── emailTemplates.js         # HTML email templates
│   │   ├── lib/                  # Utility libraries
│   │   │   ├── arcjet.js                 # Arcjet rate limiting setup
│   │   │   ├── cloudinary.js             # Cloudinary configuration
│   │   │   ├── db.js                     # MongoDB connection
│   │   │   ├── env.js                    # Environment validation
│   │   │   ├── resend.js                 # Resend email setup
│   │   │   ├── socket.js                 # Socket.io setup
│   │   │   └── utils.js                  # Helper functions
│   │   ├── middleware/           # Express middlewares
│   │   │   ├── arcjet.middleware.js      # Rate limiting middleware
│   │   │   ├── auth.middleware.js        # JWT authentication
│   │   │   └── socket.auth.middleware.js # Socket authentication
│   │   ├── models/               # Database models
│   │   │   ├── Message.js                # Message schema
│   │   │   └── User.js                   # User schema
│   │   ├── routes/               # API routes
│   │   │   ├── auth.route.js             # Auth endpoints
│   │   │   └── message.route.js          # Message endpoints
│   │   └── server.js             # Express server entry point
│   ├── .env.example              # Environment variables template
│   ├── package.json              # Backend dependencies
│   └── package-lock.json
│
├── frontend/                     # React frontend
│   ├── public/                   # Public static assets
│   │   ├── sounds/               # Notification sounds
│   │   └── screenshot-for-readme.png
│   ├── src/
│   │   ├── components/           # React components
│   │   │   ├── ActiveTabSwitch.jsx       # Tab switching component
│   │   │   ├── BorderAnimatedContainer.jsx # Animated border effect
│   │   │   ├── ChatContainer.jsx         # Main chat interface
│   │   │   ├── ChatHeader.jsx            # Chat header with user info
│   │   │   ├── ChatsList.jsx             # List of chats
│   │   │   ├── ContactList.jsx           # User contacts list
│   │   │   ├── MessageInput.jsx          # Message input field
│   │   │   ├── MessagesLoadingSkeleton.jsx # Loading state
│   │   │   ├── NoChatHistoryPlaceholder.jsx # Empty state
│   │   │   ├── NoChatsFound.jsx          # No chats state
│   │   │   ├── NoConversationPlaceholder.jsx # No selection state
│   │   │   ├── PageLoader.jsx            # Page loading spinner
│   │   │   ├── ProfileHeader.jsx         # User profile header
│   │   │   └── UsersLoadingSkeleton.jsx  # Users loading state
│   │   ├── hooks/                # Custom React hooks
│   │   │   └── useKeyboardSound.js       # Keyboard sound hook
│   │   ├── lib/                  # Frontend utilities
│   │   │   └── axios.js                  # Axios configuration
│   │   ├── pages/                # Page components
│   │   │   ├── ChatPage.jsx              # Main chat page
│   │   │   ├── LoginPage.jsx             # Login page
│   │   │   └── SignUpPage.jsx            # Registration page
│   │   ├── store/                # Zustand state stores
│   │   │   ├── useAuthStore.js           # Authentication state
│   │   │   └── useChatStore.js           # Chat state
│   │   ├── App.jsx               # Main App component
│   │   ├── index.css             # Global styles
│   │   └── main.jsx              # React entry point
│   ├── eslint.config.js          # ESLint configuration
│   ├── index.html                # HTML template
│   ├── package.json              # Frontend dependencies
│   ├── postcss.config.js         # PostCSS configuration
│   ├── tailwind.config.js        # Tailwind CSS configuration
│   └── vite.config.js            # Vite configuration
│
├── .gitignore                    # Git ignore rules
├── package.json                  # Root package scripts
└── README.MD                     # This file
```

---

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v20.0.0 or higher) - [Download](https://nodejs.org/)
- **npm** (comes with Node.js)
- **MongoDB** - [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) (free tier) or local installation
- **Git** - [Download](https://git-scm.com/)

### Required External Services

You'll need accounts for these free services:

1. **MongoDB Atlas** - Database hosting ([Sign up](https://www.mongodb.com/cloud/atlas/register))
2. **Cloudinary** - Image storage ([Sign up](https://cloudinary.com/users/register/free))
3. **Resend** - Email delivery ([Sign up](https://resend.com/signup))
4. **Arcjet** - Rate limiting ([Sign up](https://app.arcjet.com/))

---

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/paimon-2005/chat_box.git
cd chat_box
```

### 2. Install Dependencies

#### Backend Dependencies
```bash
cd backend
npm install
```

#### Frontend Dependencies
```bash
cd ../frontend
npm install
```

#### Or Install All at Once (from root)
```bash
npm run build
```

---

## 🔐 Environment Variables

### Backend Environment Setup

Create a `.env` file in the `backend` directory:

```bash
cd backend
cp .env.example .env
```

Edit `backend/.env` with your actual values:

```env
# Server Configuration
PORT=3000
NODE_ENV=development

# Database
MONGO_URI=mongodb+srv://username:password@cluster.mongodb.net/chatify?retryWrites=true&w=majority

# JWT Secret (generate a random string)
JWT_SECRET=your_super_secret_jwt_key_here_make_it_long_and_random

# Email Service (Resend)
RESEND_API_KEY=re_xxxxxxxxxxxxxxxxxxxxxxxx
EMAIL_FROM=onboarding@resend.dev
EMAIL_FROM_NAME=Chatify Team

# Frontend URL
CLIENT_URL=http://localhost:5173

# Cloudinary Configuration
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=123456789012345
CLOUDINARY_API_SECRET=your_cloudinary_secret

# Arcjet Rate Limiting
ARCJET_KEY=ajkey_xxxxxxxxxxxxxxxxxxxxxxxx
ARCJET_ENV=development
```

### Frontend Environment (Optional)

If you need to override the API URL, create `frontend/.env`:

```env
VITE_API_URL=http://localhost:3000
```

---

## 🔧 Configuration Details

### MongoDB Setup
1. Create a free cluster on [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Create a database user with password
3. Whitelist your IP address (or use 0.0.0.0/0 for development)
4. Get your connection string and replace in `MONGO_URI`

### Cloudinary Setup
1. Sign up at [Cloudinary](https://cloudinary.com/)
2. Go to Dashboard
3. Copy your Cloud Name, API Key, and API Secret
4. Add them to your `.env` file

### Resend Setup
1. Sign up at [Resend](https://resend.com/)
2. Create an API key
3. Verify your sending domain (or use the sandbox domain for testing)
4. Add API key and email address to `.env`

### Arcjet Setup
1. Sign up at [Arcjet](https://app.arcjet.com/)
2. Create a new site
3. Copy your API key
4. Add to `.env` file

### JWT Secret
Generate a secure random string for `JWT_SECRET`:

```bash
# Using Node.js
node -e "console.log(require('crypto').randomBytes(64).toString('hex'))"

# Or use any password generator with at least 32 characters
```

---

## 🏃‍♂️ Running the Application

### Development Mode

#### Option 1: Run Backend and Frontend Separately

**Terminal 1 - Backend:**
```bash
cd backend
npm run dev
```
The backend will start on `http://localhost:3000`

**Terminal 2 - Frontend:**
```bash
cd frontend
npm run dev
```
The frontend will start on `http://localhost:5173`

#### Option 2: Run from Root (Production Build)

```bash
# Build and start
npm run build
npm start
```

### Production Mode

```bash
# Backend
cd backend
npm start

# Frontend (build first, then serve)
cd frontend
npm run build
npm run preview
```

---

## 🌐 API Endpoints

### Authentication Routes (`/api/auth`)

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/api/auth/signup` | Register new user | ❌ |
| POST | `/api/auth/login` | Login user | ❌ |
| POST | `/api/auth/logout` | Logout user | ✅ |
| PUT | `/api/auth/update-profile` | Update user profile | ✅ |
| GET | `/api/auth/check` | Check auth status | ✅ |

### Message Routes (`/api/messages`)

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/messages/users` | Get all users | ✅ |
| GET | `/api/messages/:userId` | Get messages with a user | ✅ |
| POST | `/api/messages/send/:userId` | Send message to user | ✅ |

### Socket.io Events

**Client → Server:**
- `join` - Join user's room
- `typing` - Notify typing status
- `stop_typing` - Stop typing notification

**Server → Client:**
- `newMessage` - Receive new message
- `userTyping` - User is typing
- `userStoppedTyping` - User stopped typing
- `getOnlineUsers` - Get list of online users

---

## 📦 Dependencies

### Backend Dependencies

```json
{
  "@arcjet/inspect": "^1.0.0-beta.10",
  "@arcjet/node": "^1.0.0-beta.10",
  "bcryptjs": "^2.4.3",
  "cloudinary": "^2.5.1",
  "cookie-parser": "^1.4.7",
  "cors": "^2.8.5",
  "dotenv": "^16.4.7",
  "express": "^4.21.2",
  "jsonwebtoken": "^9.0.2",
  "mongoose": "^8.10.1",
  "resend": "^6.0.2",
  "socket.io": "^4.8.1"
}
```

### Frontend Dependencies

```json
{
  "axios": "^1.11.0",
  "lucide-react": "^0.542.0",
  "react": "^19.1.1",
  "react-dom": "^19.1.1",
  "react-hot-toast": "^2.6.0",
  "react-router": "^7.8.2",
  "socket.io-client": "^4.8.1",
  "zustand": "^5.0.3"
}
```

---

## 🚀 Deployment

### Deploy to Sevalla (Recommended)

1. **Prepare for Production:**
   ```bash
   npm run build
   ```

2. **Push to GitHub:**
   ```bash
   git add .
   git commit -m "Ready for deployment"
   git push origin main
   ```

3. **Deploy on Sevalla:**
   - Sign up at [Sevalla](https://sevalla.com/)
   - Connect your GitHub repository
   - Set environment variables in Sevalla dashboard
   - Deploy!

### Alternative Deployment Platforms

- **Heroku** - [Guide](https://devcenter.heroku.com/articles/deploying-nodejs)
- **Railway** - [Guide](https://docs.railway.app/deploy/deployments)
- **Render** - [Guide](https://render.com/docs/deploy-node-express-app)
- **Vercel** (Frontend only) - [Guide](https://vercel.com/docs)

### Environment Variables in Production

Make sure to set all environment variables on your deployment platform:
- Set `NODE_ENV=production`
- Update `CLIENT_URL` to your production frontend URL
- Use production API keys for all services
- Set `ARCJET_ENV=production`

---

## 🔒 Security Features

- **JWT Authentication** - Secure token-based authentication
- **HTTP-Only Cookies** - Prevents XSS attacks
- **Password Hashing** - BCrypt with salt rounds
- **Rate Limiting** - Arcjet prevents DDoS and brute force attacks
- **CORS Protection** - Configured for specific origins
- **Environment Variables** - Sensitive data kept in `.env`
- **Input Validation** - Server-side validation for all inputs
- **Socket Authentication** - Authenticated Socket.io connections

---

## 🐛 Troubleshooting

### Common Issues

**Backend won't start:**
- Check if MongoDB connection string is correct
- Ensure all environment variables are set
- Verify MongoDB Atlas IP whitelist

**Frontend can't connect:**
- Check if backend is running on port 3000
- Verify CORS settings in backend
- Check `CLIENT_URL` in backend `.env`

**Socket.io not working:**
- Ensure both backend and frontend are running
- Check browser console for Socket errors
- Verify JWT token is being sent

**Images not uploading:**
- Check Cloudinary credentials
- Verify API key permissions
- Check file size limits

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📝 License

This project is licensed under the ISC License.

---

## 👥 Team Members

This project was built with ❤️ by:

- **Paimon** - [@paimon-2005](https://github.com/paimon-2005)
- **Akshita** - [@Akshitakeshav](https://github.com/Akshitakeshav)

---

## 🙏 Acknowledgments

- Icons by [Lucide](https://lucide.dev/)
- UI components by [DaisyUI](https://daisyui.com/)
- Real-time communication by [Socket.io](https://socket.io/)
- Email service by [Resend](https://resend.com/)
- Image storage by [Cloudinary](https://cloudinary.com/)

---

## 📧 Support

If you have any questions or need help, please:
1. Check the [Issues](https://github.com/paimon-2005/chat_box/issues) page
2. Create a new issue if your problem isn't already listed
3. Provide as much detail as possible (error messages, screenshots, etc.)

---

