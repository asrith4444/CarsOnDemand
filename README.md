# CarsOnDemand 🚗

A full-stack car rental platform that connects car owners with customers, enabling seamless vehicle rentals with secure payments and comprehensive management features.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Configuration](#configuration)
- [Running the Application](#running-the-application)
- [API Endpoints](#api-endpoints)
- [User Roles](#user-roles)
- [License](#license)

## Overview

CarsOnDemand is a peer-to-peer car rental marketplace where car owners can list their vehicles for rent and customers can search, book, and rent cars based on location and availability. The platform includes an admin dashboard for managing users, handling disputes, and overseeing transactions.

## Features

### For Customers
- User registration and authentication
- Search cars by location and availability
- View car details, images, and pricing
- Book vehicles with flexible date/time selection
- Secure payment processing via Stripe
- View and manage bookings
- Rate and review rentals

### For Car Owners
- Register and list multiple vehicles
- Set pricing (hourly, daily rates, insurance)
- Manage car availability with date ranges
- View and manage rental requests
- Track rental history and earnings
- Upload car images
- End trip and settlement management

### For Admins
- Admin dashboard for platform oversight
- Manage car owners and customers
- Handle dispute resolution
- Commission tracking
- User verification management

## Tech Stack

### Backend
- **Runtime:** Node.js
- **Framework:** Express.js
- **Database:** MongoDB with Mongoose ODM
- **Authentication:** JWT (JSON Web Tokens)
- **Password Hashing:** bcryptjs
- **Payment Processing:** Stripe
- **File Upload:** Multer with Sharp for image processing
- **Email Service:** Nodemailer

### Frontend
- **Framework:** React 18
- **Routing:** React Router v7
- **HTTP Client:** Axios
- **Payment UI:** Stripe React components
- **Icons:** Lucide React
- **Image Compression:** browser-image-compression

## Project Structure

```
CarsOnDemand/
├── backend/
│   ├── controllers/          # Request handlers
│   │   ├── adminController.js
│   │   ├── authController.js
│   │   ├── carController.js
│   │   ├── carOwnerController.js
│   │   ├── imageController.js
│   │   ├── paymentController.js
│   │   └── userController.js
│   ├── middlewares/          # Custom middleware
│   │   └── uploadMiddleware.js
│   ├── models/               # Mongoose schemas
│   │   ├── Admin.js
│   │   ├── Car.js
│   │   ├── CarOwner.js
│   │   ├── Customer.js
│   │   ├── Payment.js
│   │   └── Rental.js
│   ├── routes/               # API route definitions
│   │   ├── adminRoutes.js
│   │   ├── authRoutes.js
│   │   ├── carOwnerRoutes.js
│   │   ├── carRoutes.js
│   │   ├── imageRoutes.js
│   │   ├── paymentRoutes.js
│   │   └── userRoutes.js
│   ├── uploads/              # Uploaded images storage
│   ├── utils/                # Utility functions
│   │   ├── Functions.js
│   │   ├── imageProcessor.js
│   │   ├── mailer.js
│   │   └── StripeOperations.js
│   ├── package.json
│   └── server.js             # Application entry point
│
├── frontend/
│   ├── public/               # Static assets
│   ├── src/
│   │   ├── components/       # React components
│   │   │   ├── AccessWrapper.js
│   │   │   ├── AddCar.js
│   │   │   ├── AdminDashboard.js
│   │   │   ├── AdminSignup.js
│   │   │   ├── AlertModal.js
│   │   │   ├── Booking.js
│   │   │   ├── Bookings.js
│   │   │   ├── CarDetails.js
│   │   │   ├── CarInfo.js
│   │   │   ├── CarOwnerSignup.js
│   │   │   ├── CarsList.js
│   │   │   ├── ChangeAvailabilityModal.js
│   │   │   ├── Dashboard.js
│   │   │   ├── DateTimeModal.js
│   │   │   ├── Dispute.js
│   │   │   ├── EditCarOwner.js
│   │   │   ├── EditCustomer.js
│   │   │   ├── EndTripModal.js
│   │   │   ├── ImageUpload.js
│   │   │   ├── Index.js
│   │   │   ├── Login.js
│   │   │   ├── PrivateRoute.js
│   │   │   ├── Rental.js
│   │   │   ├── Rentals.js
│   │   │   ├── Search.js
│   │   │   ├── Settlement.js
│   │   │   ├── Signup.js
│   │   │   ├── Success.js
│   │   │   ├── VerificationModal.js
│   │   │   ├── ViewCarOwner.js
│   │   │   └── ViewCustomers.js
│   │   ├── modules/          # Utility modules
│   │   │   └── CustomFunctions.js
│   │   ├── styles/           # CSS stylesheets
│   │   ├── App.js            # Main application component
│   │   └── index.js          # React entry point
│   └── package.json
│
├── .gitignore
├── LICENSE
└── README.md
```

## Installation

### Prerequisites
- Node.js (v16 or higher)
- MongoDB (local installation or MongoDB Atlas)
- Stripe account for payment processing
- SMTP service for email notifications

### Backend Setup

1. Navigate to the backend directory:
   ```bash
   cd backend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create a `.env` file in the backend directory with the following variables:
   ```env
   PORT=5050
   MONGO_URI=your_mongodb_connection_string
   JWT_SECRET=your_jwt_secret_key
   STRIPE_SECRET_KEY=your_stripe_secret_key
   SMTP_HOST=your_smtp_host
   SMTP_PORT=your_smtp_port
   SMTP_USER=your_smtp_username
   SMTP_PASS=your_smtp_password
   ```

### Frontend Setup

1. Navigate to the frontend directory:
   ```bash
   cd frontend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. The frontend is configured to connect to the backend at `http://localhost:5050`. If you need to change this, update the API URLs in the component files under `src/components/`.

## Configuration

### Environment Variables

| Variable | Description |
|----------|-------------|
| `PORT` | Backend server port (default: 5050) |
| `MONGO_URI` | MongoDB connection string |
| `JWT_SECRET` | Secret key for JWT token generation |
| `STRIPE_SECRET_KEY` | Stripe API secret key |
| `SMTP_HOST` | SMTP server host for emails |
| `SMTP_PORT` | SMTP server port |
| `SMTP_USER` | SMTP authentication username |
| `SMTP_PASS` | SMTP authentication password |

## Running the Application

### Development Mode

**Backend:**
```bash
cd backend
npx nodemon server.js   # Uses nodemon for hot reloading
# Or run directly with Node.js:
node server.js
```

**Frontend:**
```bash
cd frontend
npm start     # Starts React development server on port 3000
```

### Production Mode

**Backend:**
```bash
cd backend
node server.js
```

**Frontend:**
```bash
cd frontend
npm run build   # Creates optimized production build
```

## API Endpoints

### Authentication (`/api`)
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/signup` | Customer registration |
| POST | `/login` | User login (all roles) |
| POST | `/carOwnerSignup` | Car owner registration |
| POST | `/adminSignup` | Admin registration |

### Cars (`/api`)
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/addCar` | Add a new car (Car Owner) |
| POST | `/getAllCars` | Get all cars by owner |
| POST | `/searchCars` | Search available cars |
| GET | `/car/:id` | Get car by ID |
| PUT | `/changeAvailability/:id` | Update car availability |
| DELETE | `/deleteCar/:id` | Delete a car |

### Car Owner (`/api/carOwner`)
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | Get car owner details |
| PUT | `/` | Update car owner profile |

### Payments (`/api/payment`)
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/create-checkout-session` | Create Stripe checkout session |
| POST | `/webhook` | Handle Stripe webhooks |

### Users (`/api/user`)
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | Get user profile |
| PUT | `/` | Update user profile |

### Admin (`/api/admin`)
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/carowners` | List all car owners |
| GET | `/customers` | List all customers |
| PUT | `/carowner/:id` | Update car owner |
| PUT | `/customer/:id` | Update customer |

### Images (`/api/images`)
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/upload` | Upload car images |

## User Roles

### Customer
- Can search and book available cars
- View booking history
- Make payments via Stripe
- Rate completed rentals

### Car Owner
- Can list and manage vehicles
- Set availability and pricing
- View rental requests and history
- End trips and request settlements
- Requires admin verification

### Admin
- Full platform management access
- User verification and management
- Dispute resolution
- Commission tracking

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

**Copyright © 2025 Asrith Krishna**
