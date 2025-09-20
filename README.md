# School Payment & Dashboard Application

A full-stack microservice for managing school payments and transactions, featuring a secure backend (Node.js, Express, MongoDB) and a modern, responsive frontend (React + Vite + Tailwind CSS).

---

## Table of Contents

- [Features](#features)
- [Project Structure](#project-structure)
- [Backend Setup](#backend-setup)
- [Frontend Setup](#frontend-setup)
- [API Endpoints](#api-endpoints)
- [Environment Variables](#environment-variables)
- [Usage Examples](#usage-examples)
- [Deployment](#deployment)
- [Screenshots](#screenshots)

---

## Features

- User registration and login with JWT authentication
- Secure payment creation and integration with external payment gateway
- Webhook support for payment status updates
- Transactions dashboard with filtering, sorting, and pagination
- Responsive, modern UI with Tailwind CSS
- Role-based access and protected routes
- Robust error handling and logging

---

## Project Structure

payment/
│
├── school-payment-backend/
│   ├── config/
│   ├── middleware/
│   ├── models/
│   ├── routes/
│   ├── node_modules/
│   ├── index.js
│   ├── package.json
│   ├── package-lock.json
│   ├── .env
│   └── .gitignore
│
├── school-payments-frontend/
│   ├── src/
│   ├── public/
│   ├── dist/
│   ├── node_modules/
│   ├── index.html
│   ├── vite.config.js
│   ├── tailwind.config.js
│   ├── postcss.config.js
│   ├── eslint.config.js
│   ├── vercel.json
│   ├── package.json
│   ├── package-lock.json
│   ├── .env
│   ├── .gitignore
│   └── README.md
│
└── README.md

---

## Backend Setup

1. **Install dependencies:**
   ```bash
   cd backend
   npm install
   ```

2. **Configure environment variables:**
   - Copy `.env.example` to `.env` and fill in your MongoDB URI, JWT secret, payment API keys, etc.

3. **Run the server:**
   ```bash
   npm run dev
   ```
   The backend will start on the port specified in your `.env`.

---

## Frontend Setup

1. **Install dependencies:**
   ```bash
   cd frontend
   npm install
   ```

2. **Configure environment variables:**
   - Copy `.env.example` to `.env` and set `VITE_API_URL` to your backend server URL.

3. **Run the frontend:**
   ```bash
   npm run dev
   ```
   The app will be available at `http://localhost:5173` (or your configured port).

---

## API Endpoints

### Authentication

- `POST /api/auth/register` — Register a new user (`username`, `email`, `password`)
- `POST /api/auth/login` — Login and receive JWT token

### Payments

- `POST /api/payments/create-payment` — Create a payment (protected)
- `POST /api/payments/payment-callback` — Payment callback endpoint

### Transactions

- `GET /api/transactions` — List all transactions (with filters, pagination)
- `GET /api/transactions/school/:schoolId` — Transactions for a specific school
- `GET /api/transactions/status/:custom_order_id` — Check transaction status

### Webhook

- `POST /api/webhook` — Receive and log payment status updates

---

## Environment Variables

### Backend (`backend/.env.example`)
```
PORT=5000
MONGO_URI=your_mongodb_atlas_uri
JWT_SECRET=your_jwt_secret
SCHOOL_ID=your_school_id
PG_SECRET=your_payment_gateway_secret
PAYMENT_BASE_URL=https://payment.api.url
API_KEY=your_payment_api_key
```

### Frontend (`frontend/.env.example`)
```
VITE_API_URL=http://localhost:5000
```

---

## Usage Examples

- **Register:**  
  Send `{ "username": "john", "email": "john@example.com", "password": "yourpassword" }` to `/api/auth/register`
- **Login:**  
  Send `{ "email": "john@example.com", "password": "yourpassword" }` to `/api/auth/login`
- **Create Payment:**  
  Authenticated users can submit payment details via the frontend form.

---

## Deployment

- Deploy the backend (e.g., Heroku, AWS, Render) and set environment variables.
- Deploy the frontend (e.g., Netlify, Vercel) and set `VITE_API_URL` to your backend’s public URL.

---

