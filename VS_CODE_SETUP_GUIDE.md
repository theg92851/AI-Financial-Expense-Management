# AI Financial Expense Management System - VS Code Setup Guide

## Overview
This is a complete AI-powered financial expense management system built with Node.js, Express, MongoDB, and vanilla JavaScript. The system includes JWT authentication, OAuth 2.0 integration, session handling, cookies, bcrypt password hashing, input validation, and comprehensive error handling.

## Prerequisites

### Required Software
1. **Node.js** (v18 or higher)
   - Download from: https://nodejs.org/
   - Verify installation: `node --version`

2. **MongoDB** (v6.0 or higher)
   - Download from: https://www.mongodb.com/try/download/community
   - Or use MongoDB Atlas (cloud): https://www.mongodb.com/atlas

3. **Git**
   - Download from: https://git-scm.com/
   - Verify installation: `git --version`

4. **VS Code**
   - Download from: https://code.visualstudio.com/

### Recommended VS Code Extensions
Install these extensions for the best development experience:

1. **Node.js Extension Pack** - Comprehensive Node.js development tools
2. **MongoDB for VS Code** - MongoDB integration and management
3. **REST Client** - Test API endpoints directly in VS Code
4. **Prettier - Code formatter** - Automatic code formatting
5. **ESLint** - JavaScript linting and error detection
6. **Auto Rename Tag** - Automatically rename paired HTML tags
7. **Bracket Pair Colorizer** - Color matching brackets
8. **GitLens** - Enhanced Git capabilities
9. **Thunder Client** - API testing tool
10. **Live Server** - Local development server for frontend testing

## Project Setup Instructions

### 1. Clone or Download the Project
```bash
# If using Git
git clone <repository-url>
cd ai-expense-manager

# Or extract the downloaded ZIP file and navigate to the folder
```

### 2. Install Dependencies
```bash
# Install all required Node.js packages
npm install

# This will install:
# - express (web framework)
# - mongoose (MongoDB ODM)
# - bcryptjs (password hashing)
# - jsonwebtoken (JWT authentication)
# - passport & passport-google-oauth20 (OAuth 2.0)
# - passport-jwt (JWT strategy)
# - express-session (session management)
# - cookie-parser (cookie handling)
# - cors (cross-origin requests)
# - dotenv (environment variables)
# - express-validator (input validation)
# - helmet (security headers)
# - express-rate-limit (rate limiting)
# - morgan (logging)
# - connect-mongo (session store)
# - ejs (view engine)
# - nodemon (development server)
```

### 3. Environment Configuration
Create a `.env` file in the project root with the following variables:

```env
# Server Configuration
PORT=3000
NODE_ENV=development

# Database Configuration
MONGODB_URI=mongodb://localhost:27017/ai-expense-manager

# JWT Configuration
JWT_SECRET=your_super_secret_jwt_key_change_in_production
JWT_EXPIRE=7d

# Session Configuration
SESSION_SECRET=your_super_secret_session_key_change_in_production

# Google OAuth Configuration (Optional)
GOOGLE_CLIENT_ID=your_google_client_id_here
GOOGLE_CLIENT_SECRET=your_google_client_secret_here
```

**Important Security Notes:**
- Change all secret keys in production
- Use strong, randomly generated secrets
- Never commit the `.env` file to version control

### 4. Database Setup

#### Option A: Local MongoDB Installation
1. Install MongoDB Community Edition
2. Start MongoDB service:
   ```bash
   # Windows
   net start MongoDB
   
   # macOS (with Homebrew)
   brew services start mongodb-community
   
   # Linux (Ubuntu/Debian)
   sudo systemctl start mongod
   sudo systemctl enable mongod
   ```

#### Option B: MongoDB Atlas (Cloud)
1. Create account at https://www.mongodb.com/atlas
2. Create a new cluster
3. Get connection string and update `MONGODB_URI` in `.env`
4. Example: `mongodb+srv://username:password@cluster.mongodb.net/ai-expense-manager`

### 5. Google OAuth Setup (Optional)
1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select existing one
3. Enable Google+ API
4. Create OAuth 2.0 credentials
5. Add authorized redirect URIs:
   - `http://localhost:3000/auth/google/callback` (development)
   - `https://yourdomain.com/auth/google/callback` (production)
6. Copy Client ID and Client Secret to `.env` file

## Running the Application

### Development Mode
```bash
# Start with automatic restart on file changes
npm run dev

# Or start normally
npm start
```

### Production Mode
```bash
# Set environment to production
NODE_ENV=production npm start
```

The application will be available at:
- **Frontend**: http://localhost:3000
- **API**: http://localhost:3000/api
- **Health Check**: http://localhost:3000/health

## Project Structure

```
ai-expense-manager/
├── config/
│   ├── database.js          # MongoDB connection
│   └── passport.js          # Passport authentication strategies
├── controllers/
│   ├── authController.js    # Authentication logic
│   ├── budgetController.js  # Budget management
│   ├── expenseController.js # Expense management
│   └── aiController.js      # AI analysis and suggestions
├── middleware/
│   ├── auth.js             # Authentication middleware
│   └── validation.js       # Input validation middleware
├── models/
│   ├── User.js             # User data model
│   ├── Expense.js          # Expense data model
│   └── Budget.js           # Budget data model
├── routes/
│   ├── auth.js             # Authentication routes
│   ├── expenses.js         # Expense routes
│   ├── budget.js           # Budget routes
│   └── ai.js               # AI analysis routes
├── public/
│   ├── css/
│   │   └── style.css       # Main stylesheet
│   ├── js/
│   │   ├── main.js         # Landing page scripts
│   │   ├── auth.js         # Authentication scripts
│   │   └── dashboard.js    # Dashboard functionality
│   ├── images/             # Static images
│   ├── index.html          # Landing page
│   ├── login.html          # Login page
│   ├── register.html       # Registration page
│   └── dashboard.html      # Main application dashboard
├── views/                  # EJS templates (if needed)
├── .env                    # Environment variables
├── .gitignore             # Git ignore rules
├── app.js                 # Main application file
└── package.json           # Project dependencies
```

## API Endpoints

### Authentication
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `POST /api/auth/logout` - User logout
- `GET /api/auth/me` - Get current user
- `GET /auth/google` - Google OAuth login
- `GET /auth/google/callback` - Google OAuth callback

### Expenses
- `GET /api/expenses` - Get user expenses (with pagination and filters)
- `POST /api/expenses` - Create new expense
- `GET /api/expenses/:id` - Get specific expense
- `PUT /api/expenses/:id` - Update expense
- `DELETE /api/expenses/:id` - Delete expense
- `GET /api/expenses/stats` - Get expense statistics

### Budget
- `GET /api/budget` - Get user budget
- `PUT /api/budget` - Update budget
- `GET /api/budget/analysis` - Get budget analysis
- `POST /api/budget/ai-suggestions` - Generate AI suggestions
- `GET /api/budget/ai-suggestions` - Get AI suggestion history

### AI Analysis
- `POST /api/ai/advanced-suggestions` - Generate advanced AI suggestions
- `GET /api/ai/financial-health` - Get financial health score

## Development Workflow

### 1. VS Code Workspace Setup
1. Open the project folder in VS Code
2. Install recommended extensions when prompted
3. Configure VS Code settings (optional):
   ```json
   {
     "editor.formatOnSave": true,
     "editor.codeActionsOnSave": {
       "source.fixAll.eslint": true
     },
     "emmet.includeLanguages": {
       "javascript": "javascriptreact"
     }
   }
   ```

### 2. Testing API Endpoints
Use the REST Client extension or Thunder Client to test API endpoints:

```http
### Health Check
GET http://localhost:3000/health

### Register User
POST http://localhost:3000/api/auth/register
Content-Type: application/json

{
  "username": "testuser",
  "email": "test@example.com",
  "password": "Test123!",
  "confirmPassword": "Test123!"
}

### Login User
POST http://localhost:3000/api/auth/login
Content-Type: application/json

{
  "email": "test@example.com",
  "password": "Test123!"
}

### Get Expenses (requires authentication)
GET http://localhost:3000/api/expenses
Authorization: Bearer YOUR_JWT_TOKEN_HERE
```

### 3. Database Management
Use MongoDB for VS Code extension to:
- Connect to your MongoDB instance
- View and edit collections
- Run queries
- Monitor database performance

### 4. Debugging
1. Set breakpoints in VS Code
2. Use the built-in debugger
3. Configure launch.json for Node.js debugging:
   ```json
   {
     "version": "0.2.0",
     "configurations": [
       {
         "type": "node",
         "request": "launch",
         "name": "Launch Program",
         "program": "${workspaceFolder}/app.js",
         "env": {
           "NODE_ENV": "development"
         }
       }
     ]
   }
   ```

## Security Features Implemented

### 1. Authentication & Authorization
- **JWT Tokens**: Stateless authentication with configurable expiration
- **OAuth 2.0**: Google login integration
- **Session Management**: Express sessions with MongoDB store
- **Password Hashing**: bcrypt with salt rounds for secure password storage

### 2. Input Validation & Sanitization
- **express-validator**: Comprehensive input validation
- **XSS Protection**: Input sanitization to prevent cross-site scripting
- **SQL Injection Prevention**: MongoDB ODM with parameterized queries

### 3. Security Headers & Rate Limiting
- **Helmet**: Security headers (CSP, HSTS, etc.)
- **Rate Limiting**: Prevent brute force attacks
- **CORS**: Configurable cross-origin request handling

### 4. Error Handling
- **Global Error Handler**: Centralized error processing
- **Validation Errors**: Detailed validation feedback
- **Security Error Handling**: No sensitive information exposure

## AI Features

### 1. Spending Pattern Analysis
- Monthly trend analysis
- Category distribution analysis
- Weekly spending patterns
- Seasonal trend detection
- Anomaly detection

### 2. Budget Recommendations
- 50/30/20 rule implementation
- Category-specific suggestions
- Seasonal adjustments
- Growth rate analysis

### 3. Financial Health Score
- Comprehensive scoring algorithm
- Savings rate evaluation
- Expense growth monitoring
- Personalized recommendations

## Troubleshooting

### Common Issues

1. **MongoDB Connection Error**
   - Ensure MongoDB is running
   - Check connection string in `.env`
   - Verify network connectivity

2. **Port Already in Use**
   - Change PORT in `.env` file
   - Kill existing process: `lsof -ti:3000 | xargs kill`

3. **JWT Token Issues**
   - Check JWT_SECRET in `.env`
   - Verify token expiration settings
   - Clear browser localStorage/cookies

4. **Google OAuth Not Working**
   - Verify Google Client ID and Secret
   - Check redirect URIs in Google Console
   - Ensure Google+ API is enabled

5. **Dependencies Issues**
   - Delete `node_modules` and `package-lock.json`
   - Run `npm install` again
   - Check Node.js version compatibility

### Debugging Tips
1. Check server logs in terminal
2. Use browser developer tools for frontend issues
3. Test API endpoints with REST client
4. Monitor MongoDB logs
5. Use VS Code debugger for step-by-step debugging

## Deployment Considerations

### Environment Variables for Production
```env
NODE_ENV=production
PORT=80
MONGODB_URI=mongodb://your-production-db
JWT_SECRET=your-production-jwt-secret
SESSION_SECRET=your-production-session-secret
GOOGLE_CLIENT_ID=your-production-google-client-id
GOOGLE_CLIENT_SECRET=your-production-google-client-secret
```

### Security Checklist for Production
- [ ] Change all default secrets
- [ ] Enable HTTPS
- [ ] Configure proper CORS origins
- [ ] Set up database authentication
- [ ] Enable MongoDB authentication
- [ ] Configure firewall rules
- [ ] Set up monitoring and logging
- [ ] Regular security updates

## Additional Resources

### Documentation
- [Express.js Documentation](https://expressjs.com/)
- [MongoDB Documentation](https://docs.mongodb.com/)
- [Mongoose Documentation](https://mongoosejs.com/)
- [Passport.js Documentation](http://www.passportjs.org/)

### Learning Resources
- [Node.js Best Practices](https://github.com/goldbergyoni/nodebestpractices)
- [Express Security Best Practices](https://expressjs.com/en/advanced/best-practice-security.html)
- [MongoDB Security Checklist](https://docs.mongodb.com/manual/administration/security-checklist/)

## Support
For issues and questions:
1. Check this documentation
2. Review error logs
3. Test API endpoints
4. Check database connectivity
5. Verify environment configuration

This comprehensive setup guide should help you get the AI Financial Expense Management System running in VS Code with all features working correctly.

