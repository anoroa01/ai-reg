# Auth Flow API

A simple authentication flow built with Express.js, including user registration, login, email verification, and forgot password functionality.

## Features

- User registration with password hashing (bcryptjs)
- JWT-based authentication
- Email verification using Nodemailer
- Forgot password and reset password with secure tokens
- MongoDB database integration
- Input validation

## Tech Stack

- Node.js
- Express.js
- MongoDB with Mongoose
- JSON Web Tokens (JWT)
- Nodemailer for emails
- bcryptjs for password hashing
- validator for input validation

## Installation

1. Clone the repository
2. Install dependencies:
   \`\`\`bash
   npm install
   \`\`\`
3. Copy \`.env.example\` to \`.env\` and fill in your credentials:
   \`\`\`bash
   cp .env.example .env
   \`\`\`
4. Update the \`.env\` file with your:
   - MongoDB URI
   - JWT secret
   - Email configuration (SMTP)
   - Frontend URL

## Usage

Start the development server:
\`\`\`bash
npm run dev
\`\`\`

Start production server:
\`\`\`bash
npm start
\`\`\`

## API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| POST | \`/api/auth/register\` | Register a new user |
| POST | \`/api/auth/login\` | Login user (requires email verification) |
| GET | \`/api/auth/verify-email\` | Verify email with token |
| POST | \`/api/auth/forgot-password\` | Request password reset |
| POST | \`/api/auth/reset-password\` | Reset password with token |

## Request Examples

### Register
\`\`\`json
POST /api/auth/register
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "password123"
}
\`\`\`

### Login
\`\`\`json
POST /api/auth/login
{
  "email": "john@example.com",
  "password": "password123"
}
\`\`\`

### Forgot Password
\`\`\`json
POST /api/auth/forgot-password
{
  "email": "john@example.com"
}
\`\`\`

### Reset Password
\`\`\`json
POST /api/auth/reset-password
{
  "token": "reset_token_here",
  "email": "john@example.com",
  "password": "newpassword123"
}
\`\`\`

### Verify Email
\`\`\`http
GET /api/auth/verify-email?token=verification_token_here&email=john@example.com
\`\`\`

## Security Notes

- Passwords are hashed using bcryptjs
- Tokens are hashed before storing in database
- Email verification required for login
- Password reset tokens expire in 10 minutes
- Email verification tokens expire in 24 hours
- Always use environment variables for sensitive data
# ai-reg
