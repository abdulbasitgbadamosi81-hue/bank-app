# BankApp Architecture

## System Overview

```
┌─────────────────┐
│  React Native   │
│   Mobile App    │
└────────┬────────┘
         │
         │ HTTP/REST
         │
┌────────▼─────────┐
│   Express API    │
│   (Node.js)      │
└────────┬─────────┘
         │
         │ SQL
         │
┌────────▼──────────┐
│   PostgreSQL DB   │
└───────────────────┘
```

## Backend Architecture

### Layers

1. **Controller Layer** - HTTP request handlers
2. **Service Layer** - Business logic
3. **Model Layer** - Database models (Sequelize)
4. **Middleware** - Authentication, validation, error handling

### Key Components

- **Authentication Service**: JWT-based auth
- **Account Service**: Checking & Savings account management
- **Transaction Service**: Deposit, withdrawal, transfer operations
- **User Service**: User profile management

## Mobile Architecture

### Navigation Flow

```
Auth Stack
├── Login Screen
├── Sign Up Screen
└── Forgot Password

App Stack (After Auth)
├── Dashboard
│   ├── Account Overview
│   ├── Recent Transactions
│   └── Quick Actions
├── Accounts
│   ├── Checking Details
│   └── Savings Details
├── Transactions
│   ├── Transfer
│   ├── Deposit
│   └── Withdraw
└── Profile
    ├── Account Settings
    ├── Security
    └── Logout
```

### State Management

- Redux stores:
  - `auth` - User authentication state
  - `accounts` - Account data
  - `transactions` - Transaction history
  - `user` - User profile data

## Data Flow

1. **User initiates action** (e.g., transfer money)
2. **Mobile app dispatches Redux action**
3. **API middleware intercepts** and sends HTTP request
4. **Backend validates request** and checks authorization
5. **Service processes business logic**
6. **Database updates** (atomic transactions)
7. **Response sent back** to mobile app
8. **Redux store updates** with new state
9. **UI re-renders** with updated data

## Security

- **JWT Tokens**: Short-lived access tokens + refresh tokens
- **Password Hashing**: bcrypt for secure password storage
- **HTTPS/TLS**: All API communication encrypted
- **Input Validation**: Server-side validation on all endpoints
- **Authorization**: Role-based access control (RBAC)
