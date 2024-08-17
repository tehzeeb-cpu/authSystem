1. User Logs In
Frontend (Login Component):
The user enters their credentials (email and password) and submits the login form.
The handleSubmit function in Login.js calls the login function from authService.
authService.login sends a POST request to /auth/login with the user’s credentials.
The backend processes the request and responds with an access token and refresh token if the credentials are valid.
The access token is stored in localStorage and the user is redirected to the dashboard.
2. Dashboard Component
Frontend (Dashboard Component):
When the user is redirected to the /dashboard route, the Dashboard.js component is rendered.
The useEffect hook in Dashboard.js triggers the fetchUserInfo function.
fetchUserInfo calls getUserInfo from authService, which sends a GET request to /user with the access token.
The backend verifies the token and returns the user’s information, including their role.
3. Backend (Fetching User Info):
Backend Route:
authRoutes.js has a route for /user that uses the authenticateToken middleware to verify the token and the getAllUsers controller function to handle the request.
getAllUsers returns the list of users if the requester is an admin.
4. Conditional Rendering Based on Role
Frontend (Conditional Rendering):
If the logged-in user is an admin, the Dashboard.js component will fetch the list of users and display it.
The list of users is fetched using the axios.get method with the appropriate authorization header.
The users are displayed in a list with the ability to update user roles.
5. Updating User Role
Frontend (Updating User Role):
The admin can update a user’s role using an interface in the Dashboard.js component.
When the admin selects a new role and submits the change, a PUT request is sent to /api/users/:userId with the new role information.
The backend updates the user’s role in the database.
6. Backend (Updating User Role):
Backend Route:
authRoutes.js has a route for /users/:userId that uses authenticateToken and authorizeRoles('admin') middleware to ensure only admins can access it.
The updateUserRole controller function handles the request to update the user’s role.
The function finds the user by ID, updates their role, and saves the changes to the database.
Flow Summary:
Login:

User logs in → Backend issues tokens → Tokens stored → Redirect to dashboard.
Dashboard:

Dashboard component loads → Fetch user info → Check role.
Role-Specific Actions:

Admin:
Fetch list of users → Display users → Update user roles.
Regular User:
Display user-specific content.
Updating User Roles:

Admin submits role change → PUT request to update user → Backend updates role.
Code Summary
Login.js:

Handles login submission.
Stores tokens and redirects to dashboard.
Dashboard.js:

Fetches user info.
Displays content based on user role.
Allows admins to manage users and update roles.
authRoutes.js:

Defines routes for user operations.
Uses middleware to protect routes.
authController.js:

Handles authentication, including login and role updates.
userController.js:

Contains the logic for updating user roles.
