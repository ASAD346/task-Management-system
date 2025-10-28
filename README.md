# task-Management-system

# 🚀 Quick Start Guide

## Prerequisites
- ✅ MongoDB is installed and running (Already confirmed!)
- ✅ Node.js is installed
- ✅ npm is installed

## Step-by-Step Setup

# 1. Backend Configuration

 All backend environment variables are stored in the .env file.

  Example:
- {
- PORT=5000
- MONGODB_URI=mongodb://localhost:27017/task-management
- JWT_SECRET=your_jwt_secret_key_here_change_in_production
- JWT_EXPIRE=7d
- NODE_ENV=development
- }
- Change the PORT and MONGODB_URI values according to your local MongoDB setup.
- In the backend/createAdmin.js file, update your API URL according to your backend port number:
- const API_URL = 'http://localhost:5000/api';
- If your backend runs on a different port (for example 4000), update it accordingly:
- const API_URL = 'http://localhost:4000/api';

# 2. FrontEnd Configuration

- In the frontend/api.js file, update the frontend base API URL to match your backend URL:
- const API_URL = 'http://localhost:5000/api';
- Both backend and frontend URLs must match for proper communication.

# 3. Backend Setup

- open powershell
- Navigate to backend directory
- ForExample:
- ```
  cd E:\D_Software\task-management-app\backend
  ```
- Install dependencies
  ```
   npm install
  ```
- After Installation navigate to same directory
- And Run the command Below
  ```
  npm run dev
  ```
- The backend should now be running on `http://localhost:5000`
- Keep this terminal window open!


# 4. Create Initial Admin User

- Open a **NEW** PowerShell window and run:
- Navigate to Your Directory
  ```
  cd E:\D_Software\task-management-app\backend
  ```
- And Run the command Below
  ```
  node createAdmin.js
  ```
- You should see:
- Admin user created successfully!
  Login credentials:
- Email: admin@example.com
- Password: password123
- 
# 5. Frontend Setup

- Open **ANOTHER NEW** PowerShell window
- Navigate to frontend directory
  ```
  cd E:\D_Software\task-management-app\frontend
  ```
- And Run the command Below
  ```
  npm start
  ```
- The frontend will open automatically at `http://localhost:3000`

# 6. Login and Test

1. **Login as Admin:**
   - Email: `admin@example.com`
   - Password: `password123`

2. **You can now:**
   - ✅ Create managers
   - ✅ Create regular users
   - ✅ Assign users to managers
   - ✅ Create tasks
   - ✅ Filter and search tasks
   - ✅ View statistics

## 📊 Testing Different Roles

### Create a Manager:
1. Login as admin
2. Click "+ Add Manager" button
3. Fill in the form:
   - Name: Manager User
   - Email: manager@example.com
   - Password: password123
4. Click "Create Manager"

### Create a Regular User:
1. Click "+ Add User" button
2. Fill in the form:
   - Name: Regular User
   - Email: user@example.com
   - Password: password123
   - Select a manager (optional)
3. Click "Create User"

### Login as Different Users:
- Logout from admin account
- Login with manager or user credentials to see their respective dashboards

## 🎯 Features to Test

### Admin Dashboard:
- ✅ View all tasks from all users
- ✅ Create and manage managers
- ✅ Create and manage users
- ✅ Assign users to managers
- ✅ View task statistics
- ✅ Filter tasks by status
- ✅ Search tasks

### Manager Dashboard:
- ✅ View own tasks
- ✅ View tasks of assigned users
- ✅ Create new users (auto-assigned to self)
- ✅ Create and manage tasks
- ✅ View statistics for team

### User Dashboard:
- ✅ View only own tasks
- ✅ Create new tasks
- ✅ Edit and delete own tasks
- ✅ Change task status
- ✅ Filter and search tasks

## 🐛 Troubleshooting

### Backend won't start:
```powershell
# Check if MongoDB service is running
Get-Service -Name MongoDB

# If not running, start it
Start-Service -Name MongoDB
```

### Frontend errors:
```powershell
# Clear node_modules and reinstall
cd E:\D_Software\task-management-app\frontend
Remove-Item -Recurse -Force node_modules
npm install
npm start
```

### Can't create admin:
- Make sure backend is running
- Check if admin already exists (run createAdmin.js again to see the error)

## 📱 API Testing (Optional)

You can also test the API directly using PowerShell:

```powershell
# Test login
$body = @{
    email = "admin@example.com"
    password = "password123"
} | ConvertTo-Json

Invoke-RestMethod -Uri "http://localhost:5000/api/auth/login" `
    -Method POST `
    -Body $body `
    -ContentType "application/json"
