# Smartworld Developers Attendance Management System

## Features
- 🕐 **1-Hour Auto Logout Timer** - Automatically logs users out after 1 hour of inactivity
- 🏢 **Multi-Site Management** - Support for 9 sites with 10 teams each
- 📊 **Real-time Dashboard** - Beautiful charts and statistics
- 👥 **Employee Management** - Add, edit, and manage employees
- 📅 **Attendance Tracking** - Biometric attendance simulation
- 🌙 **Dark/Light Theme** - Toggle between themes
- 🔒 **Role-based Access** - Admin, President, Head, User roles
- 🎨 **Professional UI** - Corporate background images and modern design

## Quick Start

### Local Development
```bash
# Backend
cd backend
pip install -r requirements.txt
uvicorn server:app --reload

# Frontend  
cd frontend
yarn install
yarn start
```

### Production Deployment

#### Option 1: Deploy to Render.com

1. **Fork this repository** to your GitHub account

2. **Set up MongoDB Atlas** (Required for production):
   - Create account at https://cloud.mongodb.com/
   - Create a new cluster
   - Get connection string: `mongodb+srv://username:password@cluster.mongodb.net/attendance_db`

3. **Deploy on Render**:
   - Go to https://render.com/
   - Create new "Web Service"
   - Connect your GitHub repository
   - Use these settings:
     - **Build Command**: `pip install -r requirements.txt`
     - **Start Command**: `uvicorn server:app --host 0.0.0.0 --port $PORT`
     - **Environment**: `Python 3`

4. **Set Environment Variables** in Render Dashboard:
   ```
   ENVIRONMENT=production
   MONGO_URL=mongodb+srv://username:password@cluster.mongodb.net/attendance_db?retryWrites=true&w=majority
   DB_NAME=attendance_db
   JWT_SECRET_KEY=your-super-secret-jwt-key-here
   ```

#### Option 2: Deploy to Railway

1. **Install Railway CLI**:
   ```bash
   npm install -g @railway/cli
   ```

2. **Deploy**:
   ```bash
   railway login
   railway link
   railway up
   ```

3. **Set Environment Variables**:
   ```bash
   railway variables set MONGO_URL=your-mongodb-url
   railway variables set JWT_SECRET_KEY=your-secret-key
   ```

#### Option 3: Deploy to Heroku

1. **Create Heroku App**:
   ```bash
   heroku create your-app-name
   ```

2. **Set Environment Variables**:
   ```bash
   heroku config:set MONGO_URL=your-mongodb-url
   heroku config:set JWT_SECRET_KEY=your-secret-key
   ```

3. **Deploy**:
   ```bash
   git push heroku main
   ```

## Default Login Credentials

- **Username**: `admin`
- **Password**: `admin123`

## API Endpoints

### Authentication
- `POST /api/login` - User login
- `GET /api/me` - Get current user info

### Employees
- `GET /api/employees` - List all employees
- `POST /api/employees` - Create new employee
- `PUT /api/employees/{id}` - Update employee
- `DELETE /api/employees/{id}` - Delete employee

### Attendance
- `GET /api/attendance/stats` - Overall attendance statistics
- `GET /api/attendance/team-stats` - Team-wise statistics
- `GET /api/attendance/site-stats` - Site-wise statistics

### Sites & Teams
- `GET /api/sites` - List all sites
- `GET /api/teams` - List all teams

### Leave Management
- `GET /api/leaves` - List leave requests
- `POST /api/leaves` - Create leave request

## Auto-Logout Timer

The application includes a 1-hour auto-logout timer that:
- Starts when user logs in
- Resets on user activity (mouse, keyboard, scroll)
- Shows alert when session expires
- Automatically logs out inactive users

## Security Features

- JWT token authentication
- Role-based access control
- Password hashing with bcrypt
- CORS protection
- Input validation

## Tech Stack

- **Backend**: FastAPI, MongoDB, JWT
- **Frontend**: React, Tailwind CSS, Chart.js
- **Database**: MongoDB Atlas (production)
- **Deployment**: Render, Railway, Heroku compatible

## Support

For issues or questions, please create an issue in the GitHub repository.