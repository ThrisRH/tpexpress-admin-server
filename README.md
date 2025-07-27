# TPAdmin-Server

TPExpress Delivery Management System - Backend API Server

## 📋 Description

TPAdmin-Server is a backend API system built with Node.js and Express.js to manage TPExpress delivery operations. The system supports user management, customer management, driver management, order management, and delivery services.

## 🚀 Core Features

### 👥 User Management

- Register new accounts (Admin, Saleperson, Supporter, Driver)
- Login with JWT authentication
- User information management
- Role-based access control

### 🚗 Driver Management

- Register new drivers
- Manage driver personal information
- Track driver activity status
- Manage delivery vehicles
- Statistics of active orders

### 👤 Customer Management

- Register new customers
- Manage customer personal information
- Track order history

### 📦 Order Management

- Create new orders
- Track delivery status
- Manage sender/receiver information
- Calculate delivery fees
- Support COD (Cash on Delivery)

### 🚚 Vehicle Management

- Register delivery vehicles
- Manage vehicle information (license plate, vehicle type, manufacturer)
- Link with drivers

### 📋 Request Management

- Handle complaint requests
- Categorize requests (HBV: Damaged goods, HBL: Lost goods, HCG: Undelivered goods, CNT: Unpaid delivery)

## 🛠 Technologies Used

- **Backend Framework**: Node.js, Express.js
- **Database**: MongoDB with Mongoose ODM
- **Authentication**: JWT (JSON Web Token)
- **Password Hashing**: bcrypt
- **Database ORM**: Prisma (for session management)
- **CORS**: Cross-Origin Resource Sharing
- **Logging**: Morgan
- **Development**: Nodemon

## 📁 Project Structure

```
TPAdmin-Server/
├── prisma/
│   └── schema.prisma          # Prisma schema for session management
├── src/
│   ├── config/
│   │   └── db.mongo.config.js # MongoDB connection configuration
│   ├── controllers/           # Business logic handlers
│   │   ├── CustomerInfo/
│   │   ├── DriverInfo/
│   │   ├── OrderInfo/
│   │   ├── RequestInfo/
│   │   └── UserInfo/
│   ├── models/               # Mongoose schemas
│   │   ├── CustomerInfo/
│   │   ├── DriverInfo/
│   │   ├── OrderInfo/
│   │   ├── RequestInfo/
│   │   └── UserInfo/
│   └── routes/              # API routes
│       ├── CustomerInfo/
│       ├── DriverInfo/
│       ├── OrderInfo/
│       ├── RequestInfo/
│       └── UserInfo/
├── server.js                # Entry point
├── package.json
└── README.md
```

## 🗄️ Database Structure

### Main Collections:

1. **User**: User account management
2. **Employee**: Employee information
3. **Driver**: Driver information
4. **Customer**: Customer information
5. **Order**: Delivery orders
6. **Vehicle**: Delivery vehicles
7. **DeliveryServices**: Delivery services
8. **Request**: Complaint requests
9. **Session**: Login session management (Prisma)

## 🔌 API Endpoints

### Authentication & User Management

```
POST   /api/user/login          # Login
POST   /api/user/addUser        # Register new account
GET    /api/user/me             # Get current user info
GET    /api/user/               # Get all users
GET    /api/user/:id            # Get user by ID
```

### Customer Management

```
GET    /api/customer/           # Get all customers
GET    /api/customer/:id        # Get customer by ID
POST   /api/customer/create     # Create new customer
```

### Driver Management

```
GET    /api/driver/             # Get all drivers
GET    /api/driver/:id          # Get driver by ID
POST   /api/driver/create       # Register new driver
DELETE /api/driver/delete/:id   # Delete driver
POST   /api/driver/update/:id   # Update driver information
GET    /api/driver/checkuser/:userId # Check driver account
```

### Vehicle Management

```
GET    /api/vehicle/            # Get all vehicles
POST   /api/vehicle/create      # Register new vehicle
```

### Order Management

```
GET    /api/order/              # Get all orders
GET    /api/order/:id           # Get orders by customer ID
POST   /api/order/create        # Create new order
GET    /api/order/services/dservices # Get delivery services
```

### Request Management

```
GET    /api/request/            # Get all requests
POST   /api/request/create      # Create new request
```

## 🚀 Installation and Setup

### System Requirements

- Node.js (v14 or higher)
- MongoDB
- npm or yarn

### Installation

1. **Clone repository**

```bash
git clone <repository-url>
cd TPAdmin-Server
```

2. **Install dependencies**

```bash
npm install
```

3. **Configure environment**
   Create a `.env` file with environment variables:

```env
PORT=3000
MONGO_URI=mongodb://localhost:27017/tpexpress
JWT_SECRET=your_jwt_secret_key
```

4. **Initialize database**

```bash
npx prisma generate
npx prisma db push
```

5. **Run server**

```bash
# Development mode
npm run dev

# Production mode
npm start
```

Server will run at `http://localhost:3000`

## 🔐 Authentication

The system uses JWT (JSON Web Token) for authentication:

1. **Login**: Send POST request to `/api/user/login` with `userPhone` and `userPassword`
2. **Use token**: Add header `Authorization: Bearer <token>` for authenticated requests

## 📊 User Roles

- **Admin**: System administrator
- **Saleperson**: Sales staff
- **Supporter**: Support staff
- **Driver**: Delivery driver

## 🔧 Development

### Available Scripts

```bash
npm run dev      # Run server with nodemon (development)
npm start        # Run production server
npm test         # Run tests (not configured yet)
```

### Auto-generated ID Structure

- **User ID**: `ND` + 8 random digits
- **Driver ID**: `TX` + 8 random digits
- **Customer ID**: `KH` + 8 random digits
- **Order ID**: 10 random characters (A-Z, 0-9)

## 🤝 Contributing

1. Fork the project
2. Create feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open Pull Request

## 📝 License

This project is released under ISC license.

## 📞 Contact

For any questions, please contact the development team:

- **LinkedIn**: [Trần Hữu Minh Trí](https://www.linkedin.com/in/tr%E1%BA%A7n-h%E1%BB%AFu-minh-tr%C3%AD-935754375/)
- **Email**: thrisx03@gmail.com

---

**Note**: This is the backend API version for the TPExpress delivery management system. For a complete experience, you need to combine it with the corresponding frontend application.
