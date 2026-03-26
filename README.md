# Career Guidance MERN Starter (Email/Password + Google OAuth)

This is a full MERN-stack starter that includes:
- **Backend**: Node.js + Express + MongoDB (Mongoose)
- **Auth**: Email/Password (JWT) + **Google OAuth 2.0** (Passport)
- **Frontend**: React (Vite) with **Register** and **Login** pages including Google Sign-In

## 1) Prerequisites
- Node.js 18+
- MongoDB (local or Atlas)
- Google Cloud OAuth Client (Web application)

## 2) Setup

### Backend
```bash
cd server
cp .env.example .env
npm install
npm run dev
```

### Frontend
```bash
cd client
cp .env.example .env
npm install
npm run dev
```

## 3) Environment variables

### server/.env
- `MONGO_URI` - MongoDB connection string
- `JWT_SECRET` - random secret for JWT signing
- `GOOGLE_CLIENT_ID` - Google OAuth client id
- `GOOGLE_CLIENT_SECRET` - Google OAuth client secret
- `GOOGLE_CALLBACK_URL` - e.g. http://localhost:5000/auth/google/callback
- `CLIENT_URL` - e.g. http://localhost:5173

### client/.env
- `VITE_API_URL` - e.g. http://localhost:5000

## 4) How Google Login works (dev-friendly)
- In the React Login/Register pages, the **Continue with Google** button redirects the browser to:
  `http://localhost:5000/auth/google`
- After Google approves, the backend creates/links a user, issues a JWT, then redirects to:
  `http://localhost:5173/oauth-success?token=...`
- The frontend reads the token, stores it in `localStorage`, and routes to `/dashboard`.

## 5) Notes
- This starter is intentionally simple; for production, consider:
  - rotating refresh tokens
  - httpOnly cookies instead of localStorage
  - stricter CORS, rate limiting, CSRF protections
  - email verification and password reset flows.
---

# 📌 Tech Stack

Backend:
- Node.js
- Express.js
- MongoDB + Mongoose
- JWT
- Passport.js (Google OAuth)

Frontend:
- React (Vite)
- Axios
- React Router

---

# 📂 Project Structure

career-guidance-mern/
│
├── server/        # Backend (API + Auth)
│   ├── models/
│   ├── routes/
│   ├── controllers/
│   └── config/
│
├── client/        # Frontend (React App)
│   ├── src/
│   └── components/
│
└── README.md

---

# ⚙️ Prerequisites

- Node.js (v18+)
- MongoDB (Local or Atlas)
- Google OAuth Client (Web App)

---

# 🛠 Setup Instructions

## Clone the Repository
```bash
git clone <your-repo-link>
cd career-guidance-mern
Backend Setup
cd server
cp .env.example .env
npm install
npm run dev
Frontend Setup
cd client
cp .env.example .env
npm install
npm run dev
🔑 Environment Variables

server/.env

MONGO_URI=your_mongodb_connection
JWT_SECRET=your_secret_key
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret
GOOGLE_CALLBACK_URL=http://localhost:5000/auth/google/callback
CLIENT_URL=http://localhost:5173

client/.env

VITE_API_URL=http://localhost:5000
🔐 Authentication Flow

Email/Password:

User registers
Password is hashed
JWT token generated
Used for protected routes

Google OAuth:

Click "Continue with Google"
Redirect → http://localhost:5000/auth/google
Google authenticates
Backend creates/finds user + generates JWT
Redirect → http://localhost:5173/oauth-success?token=
...


