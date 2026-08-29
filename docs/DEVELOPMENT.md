# Development Guide

## Environment Setup

### Backend Environment Variables

Create `.env` file in the `backend/` directory:

```env
# Server
NODE_ENV=development
PORT=3000
LOG_LEVEL=debug

# Database
DB_HOST=localhost
DB_PORT=5432
DB_NAME=bank_app
DB_USER=postgres
DB_PASSWORD=your_password

# JWT
JWT_SECRET=your_super_secret_key
JWT_EXPIRE_IN=15m
JWT_REFRESH_SECRET=your_refresh_secret
JWT_REFRESH_EXPIRE_IN=7d

# API
API_URL=http://localhost:3000
CLIENT_URL=http://localhost:8081
```

### Mobile Environment Variables

Create `.env` file in the `mobile/` directory:

```env
API_URL=http://localhost:3000/api/v1
ENABLE_LOGGING=true
```

## Running the Application

### Backend

```bash
cd backend

# Install dependencies
npm install

# Run migrations
npm run migrate

# Seed database (optional)
npm run seed

# Start development server
npm run dev

# Run tests
npm test
```

### Mobile

```bash
cd mobile

# Install dependencies
npm install

# Start Metro bundler
npm start

# Run on iOS
npm run ios

# Run on Android
npm run android

# Run tests
npm test
```

## Code Structure

### Backend

```
backend/
├── src/
│   ├── controllers/      # Route handlers
│   ├── services/         # Business logic
│   ├── models/           # Database models
│   ├── middleware/       # Auth, validation, error handling
│   ├── routes/           # API routes
│   ├── utils/            # Utility functions
│   ├── config/           # Configuration files
│   └── app.js            # Express app setup
├── migrations/           # Database migrations
├── seeders/              # Database seeders
├── tests/                # Test files
└── server.js             # Entry point
```

### Mobile

```
mobile/
├── src/
│   ├── screens/          # Screen components
│   ├── components/       # Reusable components
│   ├── navigation/       # Navigation configuration
│   ├── redux/
│   │   ├── slices/       # Redux slices (reducers)
│   │   └── store.js      # Redux store configuration
│   ├── services/         # API services
│   ├── hooks/            # Custom hooks
│   ├── utils/            # Utility functions
│   ├── constants/        # Constants & enums
│   └── styles/           # Global styles
├── assets/               # Images, fonts, etc.
└── App.js                # Entry point
```

## Git Workflow

1. Create feature branch from `develop`:
   ```bash
   git checkout develop
   git pull origin develop
   git checkout -b feature/your-feature-name
   ```

2. Make your changes and commit:
   ```bash
   git add .
   git commit -m "feat: describe your changes"
   ```

3. Push and create a pull request:
   ```bash
   git push origin feature/your-feature-name
   ```

## Testing

### Backend Tests

```bash
cd backend
npm test                    # Run all tests
npm run test:watch         # Run tests in watch mode
npm run test:coverage      # Generate coverage report
```

### Mobile Tests

```bash
cd mobile
npm test                    # Run all tests
npm run test:watch         # Run tests in watch mode
```

## Debugging

### Backend

Use VS Code debugger or Node Inspector:

```bash
node --inspect=9229 server.js
```

### Mobile

Use React Native debugger or Chrome DevTools:

```bash
npm start
# Shake device or press Ctrl+D (Android) / Cmd+D (iOS)
# Select "Debug JS Remotely"
```

## Linting & Formatting

```bash
# Backend
cd backend
npm run lint               # Run ESLint
npm run lint:fix          # Fix linting issues
npm run format            # Format with Prettier

# Mobile
cd mobile
npm run lint               # Run ESLint
npm run lint:fix          # Fix linting issues
npm run format            # Format with Prettier
```
