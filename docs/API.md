# API Documentation

## Base URL
```
http://localhost:3000/api/v1
```

## Authentication

All protected endpoints require a Bearer token in the Authorization header:

```
Authorization: Bearer <access_token>
```

## Endpoints

### Auth

#### Sign Up
```
POST /auth/signup

Request Body:
{
  "email": "user@example.com",
  "password": "securepassword",
  "first_name": "John",
  "last_name": "Doe"
}

Response:
{
  "status": "success",
  "data": {
    "id": 1,
    "email": "user@example.com",
    "accessToken": "jwt_token",
    "refreshToken": "refresh_token"
  }
}
```

#### Login
```
POST /auth/login

Request Body:
{
  "email": "user@example.com",
  "password": "securepassword"
}

Response:
{
  "status": "success",
  "data": {
    "id": 1,
    "email": "user@example.com",
    "accessToken": "jwt_token",
    "refreshToken": "refresh_token"
  }
}
```

#### Refresh Token
```
POST /auth/refresh

Request Body:
{
  "refreshToken": "refresh_token"
}

Response:
{
  "status": "success",
  "data": {
    "accessToken": "new_jwt_token"
  }
}
```

### Accounts

#### Get All Accounts (Protected)
```
GET /accounts

Response:
{
  "status": "success",
  "data": [
    {
      "id": 1,
      "account_type": "checking",
      "account_number": "1234567890",
      "balance": 5000.00,
      "created_at": "2026-08-20T10:00:00Z"
    },
    {
      "id": 2,
      "account_type": "savings",
      "account_number": "0987654321",
      "balance": 10000.00,
      "created_at": "2026-08-20T10:00:00Z"
    }
  ]
}
```

#### Get Account Details (Protected)
```
GET /accounts/:id

Response:
{
  "status": "success",
  "data": {
    "id": 1,
    "account_type": "checking",
    "account_number": "1234567890",
    "balance": 5000.00,
    "created_at": "2026-08-20T10:00:00Z"
  }
}
```

### Transactions

#### Deposit (Protected)
```
POST /transactions/deposit

Request Body:
{
  "account_id": 1,
  "amount": 500.00,
  "description": "Salary deposit"
}

Response:
{
  "status": "success",
  "data": {
    "id": 1,
    "transaction_type": "deposit",
    "amount": 500.00,
    "status": "completed",
    "created_at": "2026-08-29T10:00:00Z"
  }
}
```

#### Withdrawal (Protected)
```
POST /transactions/withdraw

Request Body:
{
  "account_id": 1,
  "amount": 200.00,
  "description": "ATM withdrawal"
}

Response:
{
  "status": "success",
  "data": {
    "id": 2,
    "transaction_type": "withdrawal",
    "amount": 200.00,
    "status": "completed",
    "created_at": "2026-08-29T10:00:00Z"
  }
}
```

#### Transfer (Protected)
```
POST /transactions/transfer

Request Body:
{
  "from_account_id": 1,
  "to_account_id": 2,
  "amount": 1000.00,
  "description": "Transfer to savings"
}

Response:
{
  "status": "success",
  "data": {
    "id": 3,
    "transaction_type": "transfer",
    "amount": 1000.00,
    "status": "completed",
    "created_at": "2026-08-29T10:00:00Z"
  }
}
```

#### Get Transaction History (Protected)
```
GET /transactions?account_id=1&limit=10&offset=0

Response:
{
  "status": "success",
  "data": [
    {
      "id": 1,
      "transaction_type": "deposit",
      "amount": 500.00,
      "status": "completed",
      "created_at": "2026-08-29T10:00:00Z"
    }
  ],
  "pagination": {
    "total": 1,
    "limit": 10,
    "offset": 0
  }
}
```

### Dashboard

#### Get Dashboard Summary (Protected)
```
GET /dashboard/summary

Response:
{
  "status": "success",
  "data": {
    "total_balance": 15000.00,
    "checking_balance": 5000.00,
    "savings_balance": 10000.00,
    "total_transactions": 25,
    "recent_transactions": [
      {
        "id": 1,
        "account_type": "checking",
        "amount": 500.00,
        "type": "deposit",
        "created_at": "2026-08-29T10:00:00Z"
      }
    ]
  }
}
```
