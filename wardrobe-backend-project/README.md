# Authentication API

A secure backend authentication system built with Node.js, Express.js, and Supabase.

## Features

- User registration with email and password
- Secure login with credential validation
- Token-based logout
- Password hashing and secure storage via Supabase
- JWT-based session management

## Getting Started

### Start the Server

```bash
npm start
```

The server will run on `http://localhost:3000`

## API Endpoints

### 1. Register a New User

**Endpoint:** `POST /api/auth/register`

**Request Body:**
```json
{
  "email": "user@example.com",
  "password": "yourpassword123"
}
```

**Response (201):**
```json
{
  "message": "User registered successfully",
  "user": {
    "id": "uuid",
    "email": "user@example.com"
  },
  "session": {
    "access_token": "jwt_token",
    "refresh_token": "refresh_token"
  }
}
```

### 2. Login

**Endpoint:** `POST /api/auth/login`

**Request Body:**
```json
{
  "email": "user@example.com",
  "password": "yourpassword123"
}
```

**Response (200):**
```json
{
  "message": "Login successful",
  "user": {
    "id": "uuid",
    "email": "user@example.com"
  },
  "session": {
    "access_token": "jwt_token",
    "refresh_token": "refresh_token"
  }
}
```

### 3. Logout

**Endpoint:** `POST /api/auth/logout`

**Headers:**
```
Authorization: Bearer {access_token}
```

**Response (200):**
```json
{
  "message": "Logout successful"
}
```

### 4. Get Current User

**Endpoint:** `GET /api/auth/user`

**Headers:**
```
Authorization: Bearer {access_token}
```

**Response (200):**
```json
{
  "user": {
    "id": "uuid",
    "email": "user@example.com",
    "created_at": "timestamp"
  }
}
```

## Security

- Passwords are hashed using bcrypt via Supabase
- JWT tokens are used for authentication
- All sensitive operations require valid tokens
- CORS is enabled for cross-origin requests

## Testing with cURL

### Register:
```bash
curl -X POST http://localhost:3000/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"email":"test@example.com","password":"password123"}'
```

### Login:
```bash
curl -X POST http://localhost:3000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"test@example.com","password":"password123"}'
```

### Logout:
```bash
curl -X POST http://localhost:3000/api/auth/logout \
  -H "Authorization: Bearer YOUR_ACCESS_TOKEN"
```
