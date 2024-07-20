# Assignment Scenario: Authentication and Authorization Microservice
## Submit By 26th July 2024, 5 PM.

## Overview
You are tasked with creating an authentication and authorization microservice for a web application. This microservice will handle user registration, login, and role-based access control (RBAC). The goal is to ensure that only authenticated users can access certain endpoints and that different roles have different levels of access.

## Backend Requirements

### 1. User Registration
- Implement an endpoint for user registration.
- Users should provide a username, email, and password.
- Store passwords securely using hashing (e.g., bcrypt).

### 2. User Login
- Implement an endpoint for user login.
- Validate the user credentials and return a JSON Web Token (JWT) upon successful authentication.
- The token should include user information and roles.

### 3. Protected Routes
- Create endpoints that are accessible only to authenticated users.
- Use middleware to validate the JWT and extract user information.

### 4. Role-Based Access Control (RBAC)
- Implement roles such as "admin", "user", and "guest".
- Create endpoints that are accessible only to users with specific roles.
- Use middleware to check user roles and authorize access accordingly.

### 5. Token Refresh
- Implement an endpoint to refresh tokens.
- Use refresh tokens to issue new JWTs without requiring users to log in again.

### 6. Logout
- Implement an endpoint for user logout.
- Invalidate the user's token to ensure it can no longer be used.

### 7. Database
- Use a database to store user information and roles.
- Use MySQL Database.

### 8. Documentation
- Provide clear instructions on how to set up and run the microservice.
- Document all endpoints, request/response formats, and error handling.

## Frontend Requirements

### 1. User Interface
- Create a user-friendly interface for registration, login, and accessing protected routes.
- Use a modern front-end framework (e.g., React, Angular, Vue.js).

### 2. Registration Page
- Create a form for user registration with fields for username, email, and password.
- Handle form validation and display appropriate error messages.

### 3. Login Page
- Create a form for user login with fields for email and password.
- Handle form validation and display appropriate error messages.

### 4. Dashboard
- Create a dashboard page that is accessible only to authenticated users.
- Display a welcome message and user information.

### 5. Role-Based Content
- Display different content based on the user's role (e.g., admin, user, guest).
- Implement conditional rendering to show/hide elements based on the user's role.

### 6. Token Management
- Store the JWT securely (e.g., in cookies or localStorage).
- Implement token refresh logic to keep the user logged in.

### 7. Logout
- Provide a logout button that invalidates the user's session and redirects to the login page.

## Technical Stack

- **Backend Framework:** Node.js with Express
- **Database:** PostgreSQL or MongoDB
- **Authentication:** JSON Web Tokens (JWT)
- **Password Hashing:** bcrypt
- **Frontend Framework:** React, Angular, or Vue.js
- **Documentation:** Swagger or Postman

## Endpoints Specification

### User Registration
- **POST** `/api/register`
- **Request:**
  ```json
  {
    "username": "exampleUser",
    "email": "user@example.com",
    "password": "password123"
  }
  ```
- **Response:**
  ```json
  {
    "message": "User registered successfully"
  }
  ```

### User Login
- **POST** `/api/login`
- **Request:**
  ```json
  {
    "email": "user@example.com",
    "password": "password123"
  }
  ```
- **Response:**
  ```json
  {
    "token": "jwt_token_here",
    "refreshToken": "refresh_token_here"
  }
  ```

### Protected Route
- **GET** `/api/protected`
- **Headers:**
  ```json
  {
    "Authorization": "Bearer jwt_token_here"
  }
  ```
- **Response:**
  ```json
  {
    "message": "This is a protected route"
  }
  ```

### Role-Based Route
- **GET** `/api/admin`
- **Headers:**
  ```json
  {
    "Authorization": "Bearer jwt_token_here"
  }
  ```
- **Response:**
  ```json
  {
    "message": "This is an admin route"
  }
  ```

### Token Refresh
- **POST** `/api/token`
- **Request:**
  ```json
  {
    "refreshToken": "refresh_token_here"
  }
  ```
- **Response:**
  ```json
  {
    "token": "new_jwt_token_here"
  }
  ```

### Logout
- **POST** `/api/logout`
- **Headers:**
  ```json
  {
    "Authorization": "Bearer jwt_token_here"
  }
  ```
- **Response:**
  ```json
  {
    "message": "Logged out successfully"
  }
  ```

## Evaluation Criteria

- **Code Quality:** Clean, readable, and well-documented code.
- **Functionality:** The microservice meets the requirements and works as expected.
- **Security:** Proper implementation of authentication, authorization, and secure password storage.
- **Documentation:** Clear and comprehensive documentation of endpoints and setup instructions.
- **User Experience:** The frontend is user-friendly and functions well.
- **Problem-Solving:** Your approach to overcoming challenges faced during development.

---

---
Submission Steps:
- Clone the master branch.
- Create a new branch
- Push your code into the new branch.
- Create documentation.
---
