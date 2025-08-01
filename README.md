# AI Financial Expense Management System

A comprehensive, professional financial management application with AI-powered budget suggestions, built with modern web technologies and robust security features.

## 🚀 Features

### 🔐 Authentication & Security
- **JWT Token Authentication** - Secure, stateless authentication
- **OAuth 2.0 Integration** - Google login support
- **Session Management** - Express sessions with MongoDB store
- **Password Security** - bcrypt hashing with salt rounds
- **Input Validation** - Comprehensive validation and sanitization
- **Rate Limiting** - Protection against brute force attacks
- **Security Headers** - Helmet.js for enhanced security

### 💰 Expense Management
- **Expense Tracking** - Add, edit, delete, and categorize expenses
- **Income Tracking** - Monitor income sources and amounts
- **Category Management** - Predefined and custom expense categories
- **Date-based Filtering** - Filter expenses by date ranges
- **Search Functionality** - Find specific transactions quickly
- **Pagination** - Efficient handling of large datasets

### 📊 Budget Management
- **Budget Setting** - Set monthly and category-specific budgets
- **Budget Analysis** - Real-time budget vs. actual spending analysis
- **Progress Tracking** - Visual progress indicators
- **Overspending Alerts** - Warnings when approaching budget limits

### 🤖 AI-Powered Insights
- **Spending Pattern Analysis** - Identify trends and patterns
- **Smart Budget Suggestions** - AI-generated budget recommendations
- **Financial Health Score** - Comprehensive financial wellness assessment
- **Seasonal Adjustments** - Budget recommendations based on seasonal trends
- **Anomaly Detection** - Identify unusual spending patterns
- **50/30/20 Rule Implementation** - Automated budget allocation suggestions

### 📱 User Experience
- **Responsive Design** - Works on desktop, tablet, and mobile
- **Interactive Dashboard** - Real-time charts and statistics
- **Modern UI/UX** - Clean, intuitive interface
- **Dark/Light Theme Support** - User preference-based theming
- **Progressive Web App** - App-like experience on mobile devices

## 🛠 Technology Stack

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web application framework
- **MongoDB** - NoSQL database
- **Mongoose** - MongoDB object modeling

### Authentication
- **Passport.js** - Authentication middleware
- **JWT** - JSON Web Tokens
- **bcryptjs** - Password hashing
- **express-session** - Session management

### Frontend
- **HTML5** - Semantic markup
- **CSS3** - Modern styling with Flexbox/Grid
- **JavaScript (ES6+)** - Interactive functionality
- **Chart.js** - Data visualization

### Security & Validation
- **Helmet.js** - Security headers
- **express-validator** - Input validation
- **express-rate-limit** - Rate limiting
- **CORS** - Cross-origin resource sharing

## 📋 Prerequisites

- Node.js (v18 or higher)
- MongoDB (v6.0 or higher)
- npm or yarn package manager

## 🚀 Quick Start

### 2. Install Dependencies
```bash
npm install
```

### 3. Environment Setup
Create a `.env` file in the root directory:
```env
PORT=3000
MONGODB_URI=mongodb://localhost:27017/ai-expense-manager
JWT_SECRET=your_jwt_secret_key_here
JWT_EXPIRE=7d
SESSION_SECRET=your_session_secret_key_here
GOOGLE_CLIENT_ID=your_google_client_id_here
GOOGLE_CLIENT_SECRET=your_google_client_secret_here
NODE_ENV=development
```

### 4. Start MongoDB
```bash
# Windows
net start MongoDB

# macOS (with Homebrew)
brew services start mongodb-community

# Linux
sudo systemctl start mongod
```

### 5. Run the Application
```bash
# Development mode (with auto-restart)
npm run dev

# Production mode
npm start
```

### 6. Access the Application
- **Frontend**: http://localhost:3000
- **API**: http://localhost:3000/api
- **Health Check**: http://localhost:3000/health

### Authentication
```
POST   /api/auth/register     # User registration
POST   /api/auth/login        # User login
POST   /api/auth/logout       # User logout
GET    /api/auth/me           # Get current user info
GET    /auth/google           # Google OAuth login
GET    /auth/google/callback  # Google OAuth callback
```

### Expenses
```
GET    /api/expenses          # Get user expenses (paginated)
POST   /api/expenses          # Create new expense
GET    /api/expenses/:id      # Get specific expense
PUT    /api/expenses/:id      # Update expense
DELETE /api/expenses/:id      # Delete expense
GET    /api/expenses/stats    # Get expense statistics
```

### Budget
```
GET    /api/budget            # Get user budget
PUT    /api/budget            # Update budget
GET    /api/budget/analysis   # Get budget analysis
POST   /api/budget/ai-suggestions  # Generate AI suggestions
GET    /api/budget/ai-suggestions  # Get AI suggestion history
```


## 🧠 AI Features Explained

### Spending Pattern Analysis
The AI system analyzes your financial data to identify:
- **Monthly Trends**: Income and expense patterns over time
- **Category Distribution**: How you allocate spending across categories
- **Weekly Patterns**: Day-of-week spending habits
- **Seasonal Trends**: Seasonal variations in spending
- **Anomaly Detection**: Unusual transactions that deviate from normal patterns

### Budget Recommendations
The AI provides intelligent budget suggestions based on:
- **50/30/20 Rule**: 50% needs, 30% wants, 20% savings
- **Historical Data**: Your past spending patterns
- **Seasonal Adjustments**: Time-of-year considerations
- **Growth Rate Analysis**: Trends in spending increases/decreases

### Financial Health Score
A comprehensive score (0-100) based on:
- **Savings Rate**: Percentage of income saved
- **Expense Growth**: Rate of spending increase
- **Budget Adherence**: How well you stick to budgets
- **Spending Consistency**: Regularity of spending patterns

## 🔒 Security Features

### Authentication Security
- JWT tokens with configurable expiration
- Secure password hashing with bcrypt
- Session management with secure cookies
- OAuth 2.0 integration for third-party authentication

### Input Security
- Comprehensive input validation and sanitization
- XSS protection through input filtering
- SQL injection prevention with parameterized queries
- Rate limiting to prevent abuse

### Application Security
- Security headers with Helmet.js
- CORS configuration for cross-origin requests
- Environment variable protection
- Error handling without information disclosure

## 🧪 Testing

### Manual Testing
1. **Authentication Flow**
   - Register new user
   - Login with credentials
   - Test Google OAuth
   - Verify JWT token handling

2. **Expense Management**
   - Add various expense types
   - Edit existing expenses
   - Delete expenses
   - Test filtering and search

3. **Budget Features**
   - Set monthly budget
   - Create category budgets
   - View budget analysis
   - Generate AI suggestions

### API Testing
Use tools like Postman or Thunder Client to test API endpoints:

## 🚀 Deployment

### Environment Variables for Production
```env
NODE_ENV=production
PORT=80
MONGODB_URI=mongodb://your-production-db-url
JWT_SECRET=your-secure-production-jwt-secret
SESSION_SECRET=your-secure-production-session-secret
GOOGLE_CLIENT_ID=your-production-google-client-id
GOOGLE_CLIENT_SECRET=your-production-google-client-secret
```

### Production Checklist
- [ ] Update all environment variables
- [ ] Enable HTTPS
- [ ] Configure proper CORS origins
- [ ] Set up database authentication
- [ ] Configure firewall rules
- [ ] Set up monitoring and logging
- [ ] Regular security updates

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request


## 🆘 Support

If you encounter any issues:

1. Check the [VS Code Setup Guide](VS_CODE_SETUP_GUIDE.md) for detailed setup instructions
2. Review the error logs in the terminal
3. Verify your environment configuration
4. Test API endpoints individually
5. Check database connectivity

## 🙏 Acknowledgments

- Express.js team for the excellent web framework
- MongoDB team for the robust database solution
- Passport.js for authentication middleware
- Chart.js for data visualization capabilities


