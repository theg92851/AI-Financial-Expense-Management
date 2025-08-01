# Installation Requirements for AI Financial Expense Management System

## System Requirements

### Operating System
- **Windows**: Windows 10 or later (64-bit)
- **macOS**: macOS 10.15 (Catalina) or later
- **Linux**: Ubuntu 18.04 LTS or later, CentOS 7+, or equivalent

### Hardware Requirements
- **RAM**: Minimum 4GB, Recommended 8GB+
- **Storage**: Minimum 2GB free space
- **Processor**: Intel i3 or AMD equivalent (64-bit)
- **Network**: Internet connection for package installation and OAuth

## Software Dependencies

### 1. Node.js (Required)
**Version**: 18.0.0 or higher (LTS recommended)

#### Installation:

**Windows:**
1. Download from https://nodejs.org/
2. Run the installer (.msi file)
3. Follow installation wizard
4. Verify installation:
   ```cmd
   node --version
   npm --version
   ```

**macOS:**
```bash
# Using Homebrew (recommended)
brew install node

# Or download from https://nodejs.org/
```

**Linux (Ubuntu/Debian):**
```bash
# Using NodeSource repository
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt-get install -y nodejs

# Verify installation
node --version
npm --version
```

**Linux (CentOS/RHEL):**
```bash
# Using NodeSource repository
curl -fsSL https://rpm.nodesource.com/setup_lts.x | sudo bash -
sudo yum install -y nodejs npm

# Verify installation
node --version
npm --version
```

### 2. MongoDB (Required)
**Version**: 6.0 or higher

#### Installation:

**Windows:**
1. Download MongoDB Community Server from https://www.mongodb.com/try/download/community
2. Run the installer (.msi file)
3. Choose "Complete" installation
4. Install as a Windows Service
5. Start MongoDB service:
   ```cmd
   net start MongoDB
   ```

**macOS:**
```bash
# Using Homebrew
brew tap mongodb/brew
brew install mongodb-community

# Start MongoDB service
brew services start mongodb-community
```

**Linux (Ubuntu):**
```bash
# Import MongoDB public GPG key
wget -qO - https://www.mongodb.org/static/pgp/server-6.0.asc | sudo apt-key add -

# Create list file for MongoDB
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu $(lsb_release -cs)/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list

# Update package database
sudo apt-get update

# Install MongoDB
sudo apt-get install -y mongodb-org

# Start MongoDB service
sudo systemctl start mongod
sudo systemctl enable mongod
```

**Linux (CentOS/RHEL):**
```bash
# Create repository file
sudo tee /etc/yum.repos.d/mongodb-org-6.0.repo << EOF
[mongodb-org-6.0]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/8/mongodb-org/6.0/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://www.mongodb.org/static/pgp/server-6.0.asc
EOF

# Install MongoDB
sudo yum install -y mongodb-org

# Start MongoDB service
sudo systemctl start mongod
sudo systemctl enable mongod
```

#### Alternative: MongoDB Atlas (Cloud)
If you prefer a cloud solution:
1. Create account at https://www.mongodb.com/atlas
2. Create a new cluster (free tier available)
3. Get connection string
4. Use in `.env` file as `MONGODB_URI`

### 3. Git (Recommended)
**Version**: 2.0 or higher

#### Installation:

**Windows:**
1. Download from https://git-scm.com/download/win
2. Run installer and follow wizard
3. Choose default options

**macOS:**
```bash
# Using Homebrew
brew install git

# Or install Xcode Command Line Tools
xcode-select --install
```

**Linux:**
```bash
# Ubuntu/Debian
sudo apt-get install git

# CentOS/RHEL
sudo yum install git
```

### 4. VS Code (Recommended)
**Version**: Latest stable version

#### Installation:
1. Download from https://code.visualstudio.com/
2. Install for your operating system
3. Install recommended extensions (see VS Code Setup Guide)

## Package Dependencies

The following npm packages will be automatically installed when you run `npm install`:

### Production Dependencies
```json
{
  "express": "^5.1.0",
  "mongoose": "^8.8.4",
  "bcryptjs": "^2.4.3",
  "jsonwebtoken": "^9.0.2",
  "passport": "^0.7.0",
  "passport-jwt": "^4.0.1",
  "passport-google-oauth20": "^2.0.0",
  "express-session": "^1.18.1",
  "connect-mongo": "^5.1.0",
  "cookie-parser": "^1.4.7",
  "cors": "^2.8.5",
  "dotenv": "^17.2.1",
  "express-validator": "^7.2.0",
  "helmet": "^8.0.0",
  "express-rate-limit": "^8.0.1",
  "morgan": "^1.10.0",
  "ejs": "^3.1.10"
}
```

### Development Dependencies
```json
{
  "nodemon": "^3.1.9"
}
```

## Environment Setup

### Environment Variables
Create a `.env` file with the following variables:

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

### Security Considerations
- **Never commit `.env` file to version control**
- **Use strong, randomly generated secrets in production**
- **Change default secrets before deployment**
- **Use environment-specific configurations**

## Installation Steps

### 1. Download/Clone Project
```bash
# If using Git
git clone <repository-url>
cd ai-expense-manager

# Or extract downloaded ZIP file
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Configure Environment
```bash
# Copy example environment file
cp .env.example .env

# Edit .env file with your configuration
```

### 4. Start Database
```bash
# Windows
net start MongoDB

# macOS
brew services start mongodb-community

# Linux
sudo systemctl start mongod
```

### 5. Run Application
```bash
# Development mode
npm run dev

# Production mode
npm start
```

## Verification

### Check Installation
1. **Node.js**: `node --version` should show v18.0.0+
2. **npm**: `npm --version` should show compatible version
3. **MongoDB**: `mongod --version` should show v6.0+
4. **Git**: `git --version` should show v2.0+

### Test Application
1. Start the application: `npm start`
2. Open browser: http://localhost:3000
3. Check health endpoint: http://localhost:3000/health
4. Test registration and login

### Common Issues and Solutions

#### Node.js Issues
**Problem**: `node: command not found`
**Solution**: 
- Restart terminal/command prompt
- Check PATH environment variable
- Reinstall Node.js

#### MongoDB Issues
**Problem**: `MongoNetworkError: failed to connect`
**Solution**:
- Ensure MongoDB service is running
- Check MongoDB logs
- Verify connection string in `.env`

#### Permission Issues (Linux/macOS)
**Problem**: `EACCES: permission denied`
**Solution**:
```bash
# Fix npm permissions
sudo chown -R $(whoami) ~/.npm
sudo chown -R $(whoami) /usr/local/lib/node_modules
```

#### Port Already in Use
**Problem**: `EADDRINUSE: address already in use`
**Solution**:
```bash
# Find and kill process using port 3000
# Windows
netstat -ano | findstr :3000
taskkill /PID <PID> /F

# macOS/Linux
lsof -ti:3000 | xargs kill
```

## Performance Optimization

### System Optimization
- **RAM**: Allocate sufficient memory for MongoDB
- **Storage**: Use SSD for better database performance
- **Network**: Stable internet for package downloads

### Application Optimization
- **Environment**: Use `NODE_ENV=production` for production
- **Database**: Create indexes for frequently queried fields
- **Caching**: Enable MongoDB caching
- **Monitoring**: Use process managers like PM2

## Security Checklist

### Development Environment
- [ ] Use strong passwords for database
- [ ] Keep dependencies updated
- [ ] Use HTTPS in production
- [ ] Configure firewall rules
- [ ] Regular security updates

### Production Environment
- [ ] Change all default secrets
- [ ] Enable database authentication
- [ ] Configure SSL/TLS
- [ ] Set up monitoring
- [ ] Regular backups
- [ ] Security audits

This comprehensive installation guide ensures a smooth setup process for the AI Financial Expense Management System across different operating systems and environments.

