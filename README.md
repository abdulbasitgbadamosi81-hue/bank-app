# BankApp - Full Stack Mobile Banking Application

A comprehensive banking application with mobile frontend, backend API, and user authentication. Manage checking accounts, savings accounts, and view financial dashboards.

## Features

- 🔐 User Authentication (Sign Up, Login, Logout)
- 💳 Account Management (Checking & Savings)
- 💸 Transaction Management (Deposits, Withdrawals, Transfers)
- 📊 Financial Dashboard & Analytics
- 📱 React Native Mobile App
- 🔄 RESTful API Backend
- 🗄️ PostgreSQL Database

## Project Structure

```
bank-app/
├── backend/           # Node.js/Express API
├── mobile/            # React Native App
├── docs/              # Documentation & Architecture
└── README.md
```

## Tech Stack

### Backend
- **Runtime**: Node.js
- **Framework**: Express.js
- **Database**: PostgreSQL
- **Authentication**: JWT (JSON Web Tokens)
- **ORM**: Sequelize

### Mobile
- **Framework**: React Native
- **Navigation**: React Navigation
- **State Management**: Redux
- **HTTP Client**: Axios
- **UI Kit**: React Native Paper

## Getting Started

### Prerequisites
- Node.js (v16+)
- PostgreSQL (v12+)
- React Native CLI
- Xcode (iOS) or Android Studio (Android)

### Backend Setup

```bash
cd backend
npm install
cp .env.example .env
npm run migrate
npm start
```

### Mobile Setup

```bash
cd mobile
npm install
npm start
```

## Documentation

- [Architecture](./docs/ARCHITECTURE.md)
- [API Documentation](./docs/API.md)
- [Database Schema](./docs/DATABASE.md)
- [Development Guide](./docs/DEVELOPMENT.md)

## Contributing

Fork the repository, create a feature branch, and submit a pull request.

## License

MIT License
