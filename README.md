# JWT Authentication Demo (React + Express)

A simple full-stack project demonstrating **JWT (JSON Web Token) Authentication** using **Express.js** for the backend and **React** for the frontend. Users can log in with valid credentials, receive a JWT token, and use that token to access a protected API endpoint.

---

## Features

- User login authentication
- JWT token generation
- Protected API route
- Authentication middleware
- React frontend with Fetch API
- Login and logout functionality
- Error handling
- Beginner-friendly implementation

---

## Technologies Used

### Backend
- Node.js
- Express.js
- JSON Web Token (jsonwebtoken)
- CORS

### Frontend
- React
- Fetch API
- CSS

---

## Project Structure

```
project/
│
├── backend/
│   └── index.js
│
├── frontend/
│   ├── App.jsx
│   ├── App.css
│   └── main.jsx
│
└── README.md
```

---

## Installation

### 1. Clone the Repository

```bash
git clone <repository-url>
```

### 2. Backend Setup

```bash
cd backend
npm install
node index.js
```

The backend server runs on:

```
http://localhost:5000
```

---

### 3. Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

The frontend runs on:

```
http://localhost:5173
```

---

## Demo Credentials

Use the following credentials to log in:

| Username | Password |
|----------|----------|
| alice | 1234 |

---

## API Endpoints

### Login

**POST** `/login`

#### Request

```json
{
  "username": "alice",
  "password": "1234"
}
```

#### Success Response

```json
{
  "token": "YOUR_JWT_TOKEN"
}
```

#### Error Response

```json
{
  "message": "Invalid username or password"
}
```

---

### Protected Profile

**GET** `/profile`

#### Headers

```
Authorization: Bearer YOUR_JWT_TOKEN
```

#### Success Response

```json
{
  "message": "Welcome back, alice!"
}
```

#### Error Responses

```json
{
  "message": "No token provided"
}
```

or

```json
{
  "message": "Invalid or expired token"
}
```

---

## How JWT Authentication Works

1. The user enters a username and password.
2. React sends the credentials to the `/login` endpoint.
3. Express validates the credentials.
4. If valid, the server generates a JWT token.
5. The token is returned to the frontend.
6. React stores the token in state.
7. When requesting `/profile`, React sends the token in the `Authorization` header.
8. The backend verifies the token using JWT middleware.
9. If the token is valid, the protected route returns the user's profile information.

---

## Authentication Flow

```
User Login
     │
     ▼
POST /login
     │
     ▼
Validate Credentials
     │
     ▼
Generate JWT Token
     │
     ▼
Return Token
     │
     ▼
Store Token in React
     │
     ▼
GET /profile
Authorization: Bearer <token>
     │
     ▼
JWT Middleware Verification
     │
     ├── Invalid → 403 Forbidden
     │
     └── Valid
           │
           ▼
Return Protected Data
```

---

## HTTP Status Codes

| Status Code | Description |
|-------------|-------------|
| 200 | Request Successful |
| 401 | Invalid Login Credentials |
| 403 | Invalid or Expired JWT Token |

---

## Future Enhancements

- User Registration
- Database Integration (MongoDB/MySQL)
- Password Hashing using bcrypt
- Refresh Tokens
- Role-Based Authentication
- Persistent Login using Local Storage
- Environment Variables for JWT Secret
- Secure HttpOnly Cookies
- User Dashboard

---

## Security Notes

This project is for learning purposes only.

For production applications:

- Store the JWT secret in environment variables.
- Hash passwords using bcrypt.
- Use a real database instead of an in-memory object.
- Use HTTPS.
- Store tokens securely (preferably in HttpOnly cookies).
- Implement refresh tokens and token revocation.

---

## Author

**JWT Authentication Demo**

A beginner-friendly project demonstrating how JWT-based authentication works in a full-stack web application using React and Express. This project covers login, token generation, middleware-based authorization, protected routes, and frontend integration using the Fetch API.
