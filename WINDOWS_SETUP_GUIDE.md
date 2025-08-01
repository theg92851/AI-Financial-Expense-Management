# AI Financial Expense Management System - Complete Windows Setup Guide

## Table of Contents
1. [Prerequisites Installation](#prerequisites-installation)
2. [Environment Setup](#environment-setup)
3. [Project Installation](#project-installation)
4. [Database Configuration](#database-configuration)
5. [VS Code Setup](#vs-code-setup)
6. [Running the Application](#running-the-application)
7. [Troubleshooting](#troubleshooting)
8. [Command Reference](#command-reference)

---

## Prerequisites Installation

### 1. Install Node.js (Required)

**Step 1: Download Node.js**
1. Open your web browser
2. Go to https://nodejs.org/
3. Click "Download for Windows" (LTS version recommended)
4. Download the `.msi` installer file

**Step 2: Install Node.js**
1. Double-click the downloaded `.msi` file
2. Click "Next" through the installation wizard
3. Accept the license agreement
4. Choose installation directory (default is fine)
5. Make sure "Add to PATH" is checked
6. Click "Install"
7. Wait for installation to complete

**Step 3: Verify Installation**
1. Press `Win + R` to open Run dialog
2. Type `cmd` and press Enter
3. In Command Prompt, type:
   ```cmd
   node --version
   ```
   Expected output: `v18.x.x` or higher
4. Type:
   ```cmd
   npm --version
   ```
   Expected output: `9.x.x` or higher

### 2. Install MongoDB (Required)

**Step 1: Download MongoDB**
1. Go to https://www.mongodb.com/try/download/community
2. Select:
   - Version: Latest (6.0 or higher)
   - Platform: Windows
   - Package: msi
3. Click "Download"

**Step 2: Install MongoDB**
1. Run the downloaded `.msi` file as Administrator
2. Choose "Complete" installation type
3. **Important**: Check "Install MongoDB as a Service"
4. **Important**: Check "Run service as Network Service user"
5. **Important**: Check "Install MongoDB Compass" (GUI tool)
6. Click "Install"
7. Wait for installation to complete

**Step 3: Verify MongoDB Installation**
1. Open Command Prompt as Administrator
2. Type:
   ```cmd
   mongod --version
   ```
   Expected output: MongoDB version information

**Step 4: Start MongoDB Service**
1. Press `Win + R`, type `services.msc`, press Enter
2. Find "MongoDB" in the services list
3. Right-click and select "Start" (if not already running)
4. Right-click and select "Properties"
5. Set "Startup type" to "Automatic"

### 3. Install Git (Recommended)

**Step 1: Download Git**
1. Go to https://git-scm.com/download/win
2. Download the latest version

**Step 2: Install Git**
1. Run the installer
2. Use default settings (recommended)
3. Make sure "Git Bash Here" is selected
4. Choose "Use Git from the Windows Command Prompt"

**Step 3: Verify Git Installation**
```cmd
git --version
```
Expected output: `git version 2.x.x`

### 4. Install VS Code (Recommended)

**Step 1: Download VS Code**
1. Go to https://code.visualstudio.com/
2. Click "Download for Windows"

**Step 2: Install VS Code**
1. Run the installer
2. Accept license agreement
3. **Important**: Check "Add to PATH"
4. **Important**: Check "Register Code as an editor for supported file types"
5. Install

---

## Environment Setup

### 1. Create Project Directory

**Option A: Using File Explorer**
1. Open File Explorer
2. Navigate to `C:\Users\YourUsername\`
3. Create new folder called `ai-expense-manager`

**Option B: Using Command Prompt**
```cmd
cd C:\Users\%USERNAME%
mkdir ai-expense-manager
cd ai-expense-manager
```

### 2. Download Project Files

**If you have the project as a ZIP file:**
1. Extract the ZIP file to `C:\Users\YourUsername\ai-expense-manager`
2. Make sure all files are in the root directory

**If using Git:**
```cmd
cd C:\Users\%USERNAME%
git clone <repository-url> ai-expense-manager
cd ai-expense-manager
```

---

## Project Installation

### 1. Open Command Prompt in Project Directory

**Method 1: Using File Explorer**
1. Navigate to your project folder
2. Hold `Shift` and right-click in empty space
3. Select "Open PowerShell window here" or "Open command window here"

**Method 2: Using Command Prompt**
```cmd
cd C:\Users\%USERNAME%\ai-expense-manager
```

### 2. Install Project Dependencies

**Run the following command:**
```cmd
npm install
```

**Expected output:**
```
npm WARN deprecated ...
added 234 packages from 456 contributors and audited 567 packages in 45.123s
```

**If you see any errors, try:**
```cmd
npm cache clean --force
npm install
```

### 3. Create Environment Configuration

**Step 1: Create .env file**
1. In your project folder, create a new file called `.env`
2. Open it with Notepad or VS Code
3. Add the following content:

```env
# Server Configuration
PORT=3000
NODE_ENV=development

# Database Configuration
MONGODB_URI=mongodb://localhost:27017/ai-expense-manager

# JWT Configuration
JWT_SECRET=your_super_secret_jwt_key_change_in_production_12345
JWT_EXPIRE=7d

# Session Configuration
SESSION_SECRET=your_super_secret_session_key_change_in_production_67890

# Google OAuth Configuration (Optional)
GOOGLE_CLIENT_ID=your_google_client_id_here
GOOGLE_CLIENT_SECRET=your_google_client_secret_here
```

**Important Notes:**
- Replace the secret keys with your own random strings
- Keep the `.env` file secure and never share it
- For Google OAuth, you'll need to set up Google Cloud Console (optional)

---

## Database Configuration

### 1. Start MongoDB Service

**Method 1: Using Services**
1. Press `Win + R`, type `services.msc`
2. Find "MongoDB" service
3. Right-click and select "Start"

**Method 2: Using Command Prompt (as Administrator)**
```cmd
net start MongoDB
```

### 2. Verify MongoDB is Running

**Open Command Prompt and type:**
```cmd
mongosh
```

**Expected output:**
```
Current Mongosh Log ID: ...
Connecting to: mongodb://127.0.0.1:27017/?directConnection=true
Using MongoDB: 6.0.x
```

**To exit MongoDB shell:**
```
exit
```

### 3. Test Database Connection

**In your project directory, run:**
```cmd
node -e "const mongoose = require('mongoose'); mongoose.connect('mongodb://localhost:27017/ai-expense-manager').then(() => console.log('Database connected successfully')).catch(err => console.log('Database connection failed:', err));"
```

**Expected output:**
```
Database connected successfully
```

---

## VS Code Setup

### 1. Open Project in VS Code

**Method 1: Using Command Prompt**
```cmd
cd C:\Users\%USERNAME%\ai-expense-manager
code .
```

**Method 2: Using VS Code**
1. Open VS Code
2. File → Open Folder
3. Navigate to your project folder
4. Click "Select Folder"

### 2. Install Recommended Extensions

**When VS Code opens, you'll see a notification about recommended extensions. Click "Install All"**

**Or manually install these extensions:**
1. Press `Ctrl + Shift + X` to open Extensions
2. Search and install:
   - **Node.js Extension Pack**
   - **MongoDB for VS Code**
   - **REST Client**
   - **Prettier - Code formatter**
   - **ESLint**
   - **Auto Rename Tag**
   - **GitLens**
   - **Thunder Client**

### 3. Configure VS Code Settings

**Create .vscode/settings.json:**
1. In VS Code, create folder `.vscode` in project root
2. Create file `settings.json` inside `.vscode`
3. Add this content:

```json
{
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "emmet.includeLanguages": {
    "javascript": "javascriptreact"
  },
  "files.exclude": {
    "**/node_modules": true,
    "**/.env": false
  }
}
```

---

## Running the Application

### 1. Start the Application

**In Command Prompt/PowerShell (in project directory):**

**For Development (with auto-restart):**
```cmd
npm run dev
```

**For Production:**
```cmd
npm start
```

**Expected output:**
```
> ai-expense-manager@1.0.0 start
> node app.js

Server running on port 3000 in development mode
MongoDB Connected: localhost
```

### 2. Access the Application

**Open your web browser and go to:**
- **Main Application**: http://localhost:3000
- **Health Check**: http://localhost:3000/health
- **Login Page**: http://localhost:3000/login
- **Registration**: http://localhost:3000/register

### 3. Test the Application

**1. Health Check Test:**
```cmd
curl http://localhost:3000/health
```

**2. Registration Test:**
- Go to http://localhost:3000/register
- Fill out the form
- Click "Create Account"

**3. Login Test:**
- Go to http://localhost:3000/login
- Use your registered credentials
- Click "Sign In"

---

## Troubleshooting

### Common Issues and Solutions

#### 1. "node is not recognized as an internal or external command"

**Solution:**
1. Reinstall Node.js
2. Make sure "Add to PATH" is checked during installation
3. Restart Command Prompt
4. If still not working, manually add to PATH:
   - Press `Win + R`, type `sysdm.cpl`
   - Click "Environment Variables"
   - Add `C:\Program Files\nodejs` to PATH

#### 2. "npm install" fails with permission errors

**Solution:**
```cmd
npm cache clean --force
npm config set registry https://registry.npmjs.org/
npm install
```

#### 3. MongoDB connection failed

**Solutions:**
1. **Check if MongoDB service is running:**
   ```cmd
   net start MongoDB
   ```

2. **Check MongoDB status:**
   ```cmd
   sc query MongoDB
   ```

3. **Restart MongoDB service:**
   ```cmd
   net stop MongoDB
   net start MongoDB
   ```

4. **Check if port 27017 is available:**
   ```cmd
   netstat -an | findstr 27017
   ```

#### 4. Port 3000 already in use

**Solution:**
1. **Find process using port 3000:**
   ```cmd
   netstat -ano | findstr :3000
   ```

2. **Kill the process:**
   ```cmd
   taskkill /PID <PID_NUMBER> /F
   ```

3. **Or change port in .env file:**
   ```env
   PORT=3001
   ```

#### 5. "Cannot find module" errors

**Solution:**
```cmd
rm -rf node_modules
rm package-lock.json
npm install
```

#### 6. VS Code not opening

**Solution:**
1. **Add VS Code to PATH manually:**
   - Add `C:\Users\%USERNAME%\AppData\Local\Programs\Microsoft VS Code\bin` to PATH
2. **Or use full path:**
   ```cmd
   "C:\Users\%USERNAME%\AppData\Local\Programs\Microsoft VS Code\Code.exe" .
   ```

### Performance Issues

#### 1. Slow npm install

**Solutions:**
```cmd
npm config set registry https://registry.npmjs.org/
npm cache clean --force
npm install --verbose
```

#### 2. MongoDB slow startup

**Solutions:**
1. **Increase MongoDB memory:**
   - Edit `C:\Program Files\MongoDB\Server\6.0\bin\mongod.cfg`
   - Add: `storage.wiredTiger.engineConfig.cacheSizeGB: 1`

2. **Disable Windows Defender real-time scanning for project folder**

---

## Command Reference

### Essential Commands

#### Node.js Commands
```cmd
# Check Node.js version
node --version

# Check npm version
npm --version

# Install dependencies
npm install

# Start application (development)
npm run dev

# Start application (production)
npm start

# Install specific package
npm install package-name

# Update packages
npm update
```

#### MongoDB Commands
```cmd
# Start MongoDB service
net start MongoDB

# Stop MongoDB service
net stop MongoDB

# Check MongoDB service status
sc query MongoDB

# Connect to MongoDB shell
mongosh

# Show databases (in MongoDB shell)
show dbs

# Use specific database (in MongoDB shell)
use ai-expense-manager

# Show collections (in MongoDB shell)
show collections
```

#### Git Commands
```cmd
# Clone repository
git clone <repository-url>

# Check status
git status

# Add files
git add .

# Commit changes
git commit -m "Your message"

# Push changes
git push origin main

# Pull latest changes
git pull origin main
```

#### VS Code Commands
```cmd
# Open current directory in VS Code
code .

# Open specific file
code filename.js

# Open VS Code with specific folder
code "C:\path\to\folder"
```

### Development Commands

#### Testing API Endpoints
```cmd
# Test health endpoint
curl http://localhost:3000/health

# Test with PowerShell
Invoke-RestMethod -Uri "http://localhost:3000/health" -Method GET

# Test registration (PowerShell)
$body = @{
    username = "testuser"
    email = "test@example.com"
    password = "Test123!"
    confirmPassword = "Test123!"
} | ConvertTo-Json

Invoke-RestMethod -Uri "http://localhost:3000/api/auth/register" -Method POST -Body $body -ContentType "application/json"
```

#### Package Management
```cmd
# List installed packages
npm list

# Check for outdated packages
npm outdated

# Update specific package
npm update package-name

# Uninstall package
npm uninstall package-name

# Install package globally
npm install -g package-name
```

#### Environment Management
```cmd
# Set environment variable (current session)
set NODE_ENV=production

# Set environment variable (permanent)
setx NODE_ENV production

# View environment variables
echo %NODE_ENV%
echo %PATH%
```

### Debugging Commands

#### Process Management
```cmd
# List running Node.js processes
tasklist | findstr node

# Kill specific process
taskkill /PID <process-id> /F

# Kill all Node.js processes
taskkill /IM node.exe /F
```

#### Network Debugging
```cmd
# Check which process is using a port
netstat -ano | findstr :3000

# Check all listening ports
netstat -an | findstr LISTENING

# Test network connectivity
ping localhost
telnet localhost 3000
```

#### File System
```cmd
# Navigate to project directory
cd C:\Users\%USERNAME%\ai-expense-manager

# List files
dir

# Show hidden files
dir /a

# Create directory
mkdir folder-name

# Remove directory
rmdir /s folder-name

# Copy files
copy source destination

# Move files
move source destination
```

---

## Quick Start Checklist

### Pre-Installation Checklist
- [ ] Windows 10 or later (64-bit)
- [ ] Administrator access
- [ ] Stable internet connection
- [ ] At least 4GB RAM available
- [ ] At least 2GB free disk space

### Installation Checklist
- [ ] Node.js installed and verified (`node --version`)
- [ ] npm working (`npm --version`)
- [ ] MongoDB installed and service running
- [ ] Git installed (optional but recommended)
- [ ] VS Code installed with extensions

### Project Setup Checklist
- [ ] Project files downloaded/cloned
- [ ] Dependencies installed (`npm install`)
- [ ] `.env` file created with proper configuration
- [ ] MongoDB service started and accessible
- [ ] Application starts without errors (`npm start`)
- [ ] Can access http://localhost:3000

### Testing Checklist
- [ ] Health endpoint responds (http://localhost:3000/health)
- [ ] Registration page loads (http://localhost:3000/register)
- [ ] Login page loads (http://localhost:3000/login)
- [ ] Can create new user account
- [ ] Can login with created account
- [ ] Dashboard loads after login

---

## Additional Resources

### Official Documentation
- **Node.js**: https://nodejs.org/en/docs/
- **MongoDB**: https://docs.mongodb.com/
- **Express.js**: https://expressjs.com/
- **VS Code**: https://code.visualstudio.com/docs

### Useful Tools
- **MongoDB Compass**: GUI for MongoDB (installed with MongoDB)
- **Postman**: API testing tool
- **Git Bash**: Better terminal for Windows
- **Windows Terminal**: Modern terminal application

### Learning Resources
- **Node.js Tutorial**: https://www.w3schools.com/nodejs/
- **MongoDB Tutorial**: https://www.w3schools.com/mongodb/
- **JavaScript Tutorial**: https://www.w3schools.com/js/

---

This comprehensive Windows setup guide provides step-by-step instructions for installing and running the AI Financial Expense Management System on Windows. Follow each section carefully, and refer to the troubleshooting section if you encounter any issues.

