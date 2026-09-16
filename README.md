# Inter-Institutional Portal

A full-stack web application that facilitates collaboration and resource sharing between educational institutions. The platform enables institutions to connect, request services, and manage inter-institutional activities efficiently.

## 📋 Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Running the Application](#running-the-application)
- [API Documentation](#api-documentation)
- [Database Schema](#database-schema)
- [Contributing](#contributing)
- [License](#license)

## ✨ Features

- **Multi-Role Authentication System**
  - Admin, Provider, Consumer, and Institution user roles
  - JWT-based authentication with secure cookie handling
  - Role-based access control (RBAC)

- **Institution Management**
  - Institution registration and profile management
  - Service provider and consumer profiles
  - Inter-institutional collaboration tools

- **Request Management System**
  - Create and manage service requests between institutions
  - Request tracking and status updates
  - Notification system for request updates

- **Activity Logging**
  - Comprehensive activity tracking
  - Audit trail for all system actions

- **File Upload & Management**
  - Document upload functionality
  - Secure file storage
  - Support for PDF and image formats

- **Real-time Notifications**
  - Firebase-integrated notification system
  - Real-time updates for users

- **Responsive UI**
  - Modern, accessible design with Radix UI components
  - Dark/Light theme support
  - Mobile-friendly interface

## 🛠️ Tech Stack

### Backend
- **Runtime**: Node.js
- **Framework**: Express.js
- **Database**: MySQL
- **Authentication**: JWT (JSON Web Tokens)
- **File Upload**: Multer
- **Password Hashing**: bcrypt
- **Environment Variables**: dotenv

### Frontend
- **Framework**: Next.js 15 (React 18)
- **Language**: TypeScript
- **Styling**: Tailwind CSS
- **UI Components**: Radix UI
- **State Management**: React Hooks
- **HTTP Client**: Axios
- **Authentication**: NextAuth.js
- **Real-time**: Firebase
- **Forms**: React Hook Form with Zod validation
- **PDF Generation**: jsPDF
- **Animations**: Framer Motion

## 📁 Project Structure

```
Inter-Institutional-portal/
├── Backend/
│   ├── config/
│   │   └── db.js                 # MySQL database configuration
│   ├── controllers/
│   │   ├── authController.js     # Authentication logic
│   │   ├── adminController.js    # Admin operations
│   │   ├── consumerController.js # Consumer operations
│   │   ├── providerController.js # Provider operations
│   │   ├── institutionController.js
│   │   ├── requestController.js  # Request management
│   │   ├── activityController.js # Activity logging
│   │   ├── notificationsController.js
│   │   └── universalController.js
│   ├── middlewares/
│   │   ├── auth.js               # JWT verification
│   │   ├── role.js               # Role-based access control
│   │   └── log.js                # Request logging
│   ├── routes/
│   │   ├── auth.js               # Authentication routes
│   │   ├── admin.js              # Admin routes
│   │   ├── consumer.js           # Consumer routes
│   │   ├── provider.js           # Provider routes
│   │   ├── institution.js        # Institution routes
│   │   ├── request.js            # Request routes
│   │   ├── activity.js           # Activity routes
│   │   ├── notifications.js      # Notification routes
│   │   ├── universalRoutes.js
│   │   └── universalSetup.js
│   ├── uploads/                  # Uploaded files storage
│   ├── .env                      # Environment variables
│   ├── server.js                 # Express server entry point
│   └── package.json
│
├── Frontend/
│   ├── app/                      # Next.js App Router pages
│   ├── components/               # React components
│   │   ├── ui/                   # Radix UI components
│   │   └── ...                   # Custom components
│   ├── hooks/                    # Custom React hooks
│   ├── lib/                      # Utility functions
│   ├── public/                   # Static assets
│   ├── styles/                   # Global styles
│   ├── .env                      # Frontend environment variables
│   ├── middleware.ts             # Next.js middleware
│   ├── next.config.mjs           # Next.js configuration
│   ├── tailwind.config.ts        # Tailwind CSS configuration
│   └── package.json
│
└── README.md
```

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v18 or higher) - [Download](https://nodejs.org/)
- **npm** or **yarn** - Comes with Node.js
- **MySQL** (v8.0 or higher) - [Download](https://dev.mysql.com/downloads/)
- **Git** - [Download](https://git-scm.com/)

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/inter-institutional-portal.git
cd inter-institutional-portal
```

### 2. Install Backend Dependencies

```bash
cd Backend
npm install
```

### 3. Install Frontend Dependencies

```bash
cd ../Frontend
npm install
```

## ⚙️ Configuration

### Backend Configuration

1. Create a `.env` file in the `Backend` directory:

```env
# Server Configuration
PORT=5000
HOST=localhost

# Database Configuration
DATABASE=mesob
USER=your_mysql_username
PASSWORD=your_mysql_password

# JWT Secret (Generate a secure random string)
JWT_SECRET=your_very_secure_jwt_secret_key_here

# Backend URL (for production deployment)
BACKEND_URL=http://localhost:5000
```

2. **Set up MySQL Database**:

```sql
-- Create database
CREATE DATABASE mesob;

-- Use the database
USE mesob;

-- Create tables (you'll need to run your database schema script here)
-- Example:
-- CREATE TABLE users (...);
-- CREATE TABLE institutions (...);
-- CREATE TABLE requests (...);
```

### Frontend Configuration

1. Create a `.env` file in the `Frontend` directory:

```env
# API Configuration
NEXT_PUBLIC_API_URL=http://localhost:5000

# Firebase Configuration (for notifications and real-time features)
NEXT_PUBLIC_FIREBASE_API_KEY=your_firebase_api_key
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=your-app.firebaseapp.com
NEXT_PUBLIC_FIREBASE_PROJECT_ID=your-project-id
NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=your-app.appspot.com
NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
NEXT_PUBLIC_FIREBASE_APP_ID=your_app_id
```

2. **Firebase Setup** (Optional but recommended for notifications):
   - Go to [Firebase Console](https://console.firebase.google.com/)
   - Create a new project or use an existing one
   - Register your web app
   - Copy the configuration values to your `.env` file

## 🏃 Running the Application

### Development Mode

#### Start the Backend Server

```bash
cd Backend
npm run dev
```

The backend server will start at: `http://localhost:5000`

You should see:
```
Server running at http://localhost:5000
MySQL connected successfully!
```

#### Start the Frontend Development Server

Open a new terminal window:

```bash
cd Frontend
npm run dev
```

The frontend will start at: `http://localhost:3000`

You should see:
```
▲ Next.js 15.5.6
- Local:        http://localhost:3000
- Network:      http://192.168.x.x:3000
✓ Starting...
```

### Production Mode

#### Build and Run Backend

```bash
cd Backend
npm start
```

#### Build and Run Frontend

```bash
cd Frontend
npm run build
npm start
```

## 📚 API Documentation

### Base URL
```
http://localhost:5000
```

### Authentication Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/api/auth/register` | Register new user | No |
| POST | `/api/auth/login` | User login | No |
| POST | `/api/auth/logout` | User logout | Yes |
| GET | `/api/auth/verify` | Verify JWT token | Yes |

### Admin Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/admin/users` | Get all users | Admin |
| PUT | `/api/admin/users/:id` | Update user | Admin |
| DELETE | `/api/admin/users/:id` | Delete user | Admin |

### Institution Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/institutions` | Get all institutions | Yes |
| POST | `/api/institutions` | Create institution | Admin |
| GET | `/api/institutions/:id` | Get institution by ID | Yes |
| PUT | `/api/institutions/:id` | Update institution | Admin |

### Request Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/requests` | Get all requests | Yes |
| POST | `/api/requests` | Create new request | Yes |
| GET | `/api/requests/:id` | Get request by ID | Yes |
| PUT | `/api/requests/:id` | Update request | Yes |
| DELETE | `/api/requests/:id` | Delete request | Yes |

### Provider Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/provider/profile` | Get provider profile | Provider |
| PUT | `/provider/profile` | Update provider profile | Provider |

### Consumer Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/consumer/profile` | Get consumer profile | Consumer |
| PUT | `/consumer/profile` | Update consumer profile | Consumer |

### Activity Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/activity` | Get activity logs | Admin |
| POST | `/api/activity` | Log activity | Yes |

### Notification Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/notifications` | Get user notifications | Yes |
| PUT | `/api/notifications/:id` | Mark as read | Yes |

## 🗄️ Database Schema

The application uses MySQL as the database. Key tables include:

- **users** - User accounts and authentication
- **institutions** - Institution information
- **providers** - Service provider profiles
- **consumers** - Service consumer profiles
- **requests** - Inter-institutional requests
- **activities** - System activity logs
- **notifications** - User notifications

## 🔒 Security Features

- JWT-based authentication
- Password hashing with bcrypt
- CORS configuration for frontend-backend communication
- Cookie-based session management
- Role-based access control (RBAC)
- Input validation and sanitization
- SQL injection prevention with parameterized queries

## 🐛 Troubleshooting

### Backend Issues

**Problem**: `MySQL connection failed`
- **Solution**: Check your MySQL server is running and credentials in `.env` are correct

**Problem**: `Port 5000 already in use`
- **Solution**: 
  ```bash
  # Windows
  netstat -ano | findstr :5000
  taskkill /PID <PID> /F
  
  # Linux/Mac
  lsof -i :5000
  kill -9 <PID>
  ```

**Problem**: `JWT_SECRET not defined`
- **Solution**: Ensure your `.env` file has a `JWT_SECRET` value

### Frontend Issues

**Problem**: `Cannot connect to backend`
- **Solution**: Verify `NEXT_PUBLIC_API_URL` in `.env` matches your backend URL

**Problem**: `Port 3000 already in use`
- **Solution**: Use a different port with `npm run dev -- -p 3001`

**Problem**: Firebase errors
- **Solution**: Check Firebase configuration values in `.env` are correct

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 👥 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📞 Support

For support, please open an issue in the GitHub repository or contact the development team.

---

**Built with ❤️ for educational institutions**
