# Aadhaar Request Portal

A simple full-stack web application built with Node.js, Express, MongoDB, EJS, Bootstrap, bcrypt, and JWT cookies.

## Features

- User registration and login
- Password hashing with `bcrypt`
- JWT cookie authentication
- Wallet balance display on dashboard
- Aadhaar request form that deducts a fixed wallet charge
- Admin login with separate panel
- Admin wallet top-up for users
- Admin request approval with ID and password entry
- User dashboard showing request history and approved credentials
- MongoDB Atlas friendly setup
- Vercel-ready Express structure

## Folder Structure

```text
.
|-- api
|   `-- index.js
|-- config
|   `-- db.js
|-- controllers
|   |-- adminController.js
|   |-- authController.js
|   `-- userController.js
|-- middleware
|   `-- authMiddleware.js
|-- models
|   |-- Request.js
|   `-- User.js
|-- public
|   |-- css
|   |   `-- style.css
|   `-- js
|       `-- main.js
|-- routes
|   |-- adminRoutes.js
|   |-- authRoutes.js
|   `-- userRoutes.js
|-- utils
|   `-- appConfig.js
|-- views
|   |-- partials
|   |   |-- footer.ejs
|   |   `-- header.ejs
|   |-- admin-login.ejs
|   |-- admin-panel.ejs
|   |-- dashboard.ejs
|   |-- error.ejs
|   |-- login.ejs
|   |-- register.ejs
|   `-- request-form.ejs
|-- .env.example
|-- package.json
|-- README.md
`-- vercel.json
```

## Local Setup

1. Install Node.js 18 or newer.
2. Install dependencies:

   ```bash
   npm install
   ```

3. Copy `.env.example` to `.env`.
4. Update these values in `.env`:
   - `MONGODB_URI`
   - `MONGODB_DB_NAME`
   - `JWT_SECRET`
   - `ADMIN_USERNAME`
   - `ADMIN_PASSWORD` or `ADMIN_PASSWORD_HASH`
   - `ADMIN_TELEGRAM`
5. Start the app:

   ```bash
   npm run dev
   ```

6. Open [http://localhost:3000](http://localhost:3000)

## MongoDB Atlas

- Create a MongoDB Atlas cluster
- Add your database user and password
- Allow your IP or allow access from anywhere for testing
- Paste the connection string into `MONGODB_URI`
- Set `MONGODB_DB_NAME` to your preferred database name

## Admin Login

- Go to `/admin/login`
- Use the credentials from your `.env` file

If you want to store a hashed admin password, generate a bcrypt hash and put it in `ADMIN_PASSWORD_HASH`. When a hash is present, the app will use it instead of `ADMIN_PASSWORD`.

## Vercel Deployment

This project follows Vercel's current Express guidance by exporting the app from `api/index.js` and routing all traffic to `/api` through `vercel.json`.

1. Push the project to GitHub
2. Import the repository into Vercel
3. Add the environment variables from `.env.example` in the Vercel project settings
4. Deploy

Static files are kept in `public/`, which is the recommended location for Vercel deployments.

## Notes

- This is a beginner-friendly demo project
- Approved ID/password pairs are stored in plain text so users can view them later
- For a production-grade system, consider encrypting sensitive values at rest and adding audit logs
