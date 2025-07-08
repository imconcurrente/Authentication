# Authentication-Security (OAuth)
The "Authentication-Security" focuses on implementing and demonstrating various authentication and security techniques using Node.js, Express, and EJS. It provides a clean, modular structure to build, test, and understand different levels of security in modern web applications, including local authentication and OAuth2 integration.

### Files and Directories

1. **`index.js`** : Main server file that initializes the Express app, configures middleware, sets up authentication (local and Google OAuth), and defines all routes.

2. **`package.json`** : Contains project metadata, scripts, and a list of dependencies required to run the application.

3. **`public/`** : Static assets directory for client-side files such as CSS, images, and JavaScript.

4. **`views/`** : EJS template directory used to render dynamic HTML pages like login, register, and secrets.

###  Environment Configuration
```js
const db = new pg.Client({
  user: process.env.PG_USER,
  host: process.env.PG_HOST,
  database: process.env.PG_DATABASE,
  password: process.env.PG_PASSWORD,
  port: process.env.PG_PORT,
});
db.connect();

```
#### `app.js`

1. **Routes**:
  - **GET `/`**: Renders the home page.
  - **GET `/register`**: Renders the registration page.
  - **GET `/login`**: Renders the login page.

2. **Database Connection**:
  - Uses PostgreSQL for storing user credentials and submitted secrets.
  - Connection is established using the `pg` library.
  - Environment variables (`.env`) are used to manage database credentials securely.
  - Queries are parameterized to protect against SQL injection.

3. **POST /register**:
  - Handles user registration via form submission.
  - Checks if the user already exists in the database.
  - Hashes the password using `bcrypt` before storing.
  - Creates a new user entry in the `users` table.
  - Automatically logs the user in after successful registration.
  - Redirects to the protected `/secrets` page.

4. **POST /login**:
  - Authenticates users using `passport-local` strategy.
  - Matches the submitted email with a user record in the database.
  - Compares submitted password with hashed password using `bcrypt`.
  - If valid, logs the user in and creates a session.
  - Redirects to the `/secrets` page on success, or back to `/login` on failure.







