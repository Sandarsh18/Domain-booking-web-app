# 🌐 Domain Booking Web Application

<div align="center">

![Domain Booking](https://img.shields.io/badge/Domain-Booking-blue?style=for-the-badge&logo=internet-archive&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Bootstrap](https://img.shields.io/badge/Bootstrap-7952B3?style=for-the-badge&logo=bootstrap&logoColor=white)

**A modern, full-stack domain booking system built with Node.js and Express.js** 🚀

</div>

## 📋 Table of Contents

- [🌟 Features](#-features)
- [🛠️ Tech Stack](#️-tech-stack)
- [📁 Project Structure](#-project-structure)
- [⚡ Quick Start](#-quick-start)
- [🔧 Installation](#-installation)
- [🗄️ Database Setup](#️-database-setup)
- [🚀 Running the Application](#-running-the-application)
- [📱 Usage Guide](#-usage-guide)
- [🔗 API Endpoints](#-api-endpoints)
- [📸 Screenshots](#-screenshots)
- [🤝 Contributing](#-contributing)
- [📄 License](#-license)

## 🌟 Features

### 👥 User Features
- **🔐 User Registration & Authentication** - Secure user registration with password hashing
- **📝 Domain Booking** - Easy domain booking through intuitive web interface
- **📊 Personal Dashboard** - View personal booking history and status
- **🔍 Real-time Status Updates** - Track booking status (Pending/Approved/Rejected)

### 👨‍💼 Admin Features
- **🎛️ Admin Dashboard** - Comprehensive booking management interface
- **✅ Booking Approval System** - Approve or reject domain booking requests
- **📈 Booking Overview** - View all user bookings with detailed information
- **👤 User Management** - Monitor user activities and bookings

### 🔒 Security Features
- **🔐 Password Encryption** - bcrypt hashing for secure password storage
- **🛡️ Session Management** - Express sessions for user authentication
- **🚪 Role-based Access** - Separate user and admin access levels

## 🛠️ Tech Stack

### Backend
- **Node.js** 🟢 - JavaScript runtime environment
- **Express.js** ⚡ - Fast, unopinionated web framework
- **MySQL** 🐬 - Relational database management system
- **bcrypt** 🔐 - Password hashing library
- **express-session** 🛡️ - Session middleware

### Frontend
- **HTML5** 📝 - Markup language for web pages
- **CSS3** 🎨 - Styling and responsive design
- **JavaScript (ES6+)** ⚡ - Dynamic frontend functionality
- **Bootstrap 5** 🎯 - CSS framework for responsive UI

## 📁 Project Structure

```
domain-booking-app/
├── 📄 server.js              # Main application server
├── 🗄️ db.js                 # Database connection configuration
├── 📋 package.json          # Project dependencies and scripts
├── 🗃️ schema.sql            # Database schema definition
├── 📖 README.md             # Project documentation
│
├── 📁 routes/               # Express.js route handlers
│   ├── 🔐 auth.js          # Authentication routes (login/register)
│   ├── 📝 booking.js       # Domain booking functionality
│   └── 👨‍💼 admin.js        # Admin management routes
│
├── 📁 public/              # Static frontend files
│   ├── 🏠 index.html       # Login page
│   ├── 📝 register.html    # User registration page
│   ├── 👤 user-dashboard.html    # User dashboard
│   ├── 👨‍💼 dashboard.html  # Admin dashboard
│   ├── ⚡ script.js        # Client-side JavaScript
│   ├── 🎨 style.css        # Custom styles
│   └── 🗃️ schema.sql       # Database schema backup
│
└── 📁 images/              # Application screenshots
    └── 📸 Screenshot from 2025-03-27 19-39-44.png
```

## ⚡ Quick Start

### Prerequisites
- **Node.js** (v14 or higher) 📦
- **MySQL** (v8.0 or higher) 🗄️
- **npm** (Node Package Manager) 📥

### 🚀 One-Command Setup
```bash
# Clone, install, and setup in one go
git clone <repository-url> && cd domain-booking-app && npm install
```

## 🔧 Installation

### Step 1: Clone the Repository
```bash
git clone <repository-url>
cd domain-booking-app
```

### Step 2: Install Dependencies
```bash
npm install
```

**Dependencies installed:**
- `express` - Web application framework
- `mysql` - MySQL database driver
- `bcrypt` - Password hashing
- `body-parser` - Parse incoming request bodies
- `express-session` - Session middleware

## 🗄️ Database Setup

### Step 1: Create MySQL Database
```sql
CREATE DATABASE domain_booking;
USE domain_booking;
```

### Step 2: Create Tables
```sql
-- Users table for authentication
CREATE TABLE user (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL,
    role ENUM('user', 'admin') NOT NULL DEFAULT 'user'
);

-- Bookings table for domain requests
CREATE TABLE bookings (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    domain_name VARCHAR(255) NOT NULL,
    booking_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    status ENUM('pending', 'approved', 'rejected') DEFAULT 'pending',
    FOREIGN KEY (user_id) REFERENCES user(id) ON DELETE CASCADE
);
```

### Step 3: Configure Database Connection
Update `db.js` with your MySQL credentials:
```javascript
const mysql = require('mysql');
const connection = mysql.createConnection({
    host: 'localhost',        // Your MySQL host
    user: 'root',            // Your MySQL username
    password: 'your_password', // Your MySQL password
    database: 'domain_booking'
});
```

## 🚀 Running the Application

### Development Mode
```bash
npm start
```

### Production Mode
```bash
NODE_ENV=production node server.js
```

**Application will be available at:** `http://localhost:3000` 🌐

### Default Admin Account
- **Username:** `admin`
- **Password:** `admin123`
- **Role:** `admin`

## 📱 Usage Guide

### 👤 For Regular Users

#### 1. **Registration Process** 📝
1. Navigate to `/register.html`
2. Fill in username and password
3. Confirm password
4. Click "Register" button
5. Redirected to login page upon success

#### 2. **Login Process** 🔐
1. Go to main page (`/`)
2. Enter credentials
3. Click "Login"
4. Redirected to user dashboard

#### 3. **Booking a Domain** 🌐
1. Access user dashboard
2. Enter desired domain name
3. Click "Book Domain"
4. View booking in "Your Bookings" section
5. Monitor status changes

### 👨‍💼 For Administrators

#### 1. **Admin Login** 🔑
1. Use admin credentials at login page
2. Automatically redirected to admin dashboard

#### 2. **Managing Bookings** ⚖️
1. View all pending bookings
2. See user details and domain requests
3. Approve or reject bookings
4. Monitor booking statistics

## 🔗 API Endpoints

### 🔐 Authentication Routes (`/auth`)
| Method | Endpoint | Description | Body Parameters |
|--------|----------|-------------|----------------|
| `POST` | `/auth/register` | Register new user | `username`, `password` |
| `POST` | `/auth/login` | User login | `username`, `password` |

### 📝 Booking Routes (`/booking`)
| Method | Endpoint | Description | Body Parameters |
|--------|----------|-------------|----------------|
| `POST` | `/booking/book` | Create domain booking | `domain_name` |
| `GET` | `/booking/user-bookings` | Get user's bookings | None |

### 👨‍💼 Admin Routes (`/admin`)
| Method | Endpoint | Description | Parameters |
|--------|----------|-------------|-----------|
| `GET` | `/admin/bookings` | Get all bookings | None |
| `PUT` | `/admin/approve/:id` | Approve booking | `id` (URL param) |
| `DELETE` | `/admin/reject/:id` | Reject booking | `id` (URL param) |

## 📸 Screenshots

### 🏠 Login Page
- Clean, modern interface with gradient background
- Form validation and error handling
- Responsive design for all devices

### 👤 User Dashboard
- Personal booking history
- Real-time status updates
- Easy domain booking form

### 👨‍💼 Admin Dashboard
- Comprehensive booking management
- User information display
- One-click approve/reject functionality

## 🎨 Styling Features

- **🌈 Gradient Backgrounds** - Beautiful color transitions
- **📱 Responsive Design** - Works on all screen sizes
- **✨ Animations** - Smooth fade-in effects
- **🎯 Bootstrap Integration** - Professional UI components
- **🎨 Custom CSS** - Tailored styling for enhanced UX

## 🔒 Security Measures

- **Password Hashing** - bcrypt with salt rounds
- **Session Management** - Secure session handling
- **SQL Injection Prevention** - Parameterized queries
- **Role-based Authorization** - Admin/User separation
- **Input Validation** - Frontend and backend validation

## 🚨 Troubleshooting

### Common Issues

1. **Database Connection Error**
   ```bash
   # Check MySQL service status
   sudo systemctl status mysql
   
   # Start MySQL if not running
   sudo systemctl start mysql
   ```

2. **Port 3000 Already in Use**
   ```bash
   # Find and kill process using port 3000
   lsof -ti:3000 | xargs kill -9
   ```

3. **bcrypt Installation Issues**
   ```bash
   # Rebuild bcrypt
   npm rebuild bcrypt
   ```

## 🔮 Future Enhancements

- [ ] **Email Notifications** 📧 - Notify users about booking status
- [ ] **Payment Integration** 💳 - Process domain payments
- [ ] **Domain Availability Check** 🔍 - Real-time domain availability
- [ ] **Multi-year Bookings** 📅 - Support for extended periods
- [ ] **Advanced Analytics** 📊 - Booking trends and statistics
- [ ] **API Rate Limiting** ⚡ - Prevent abuse and spam
- [ ] **Docker Support** 🐳 - Containerized deployment
- [ ] **Unit Testing** 🧪 - Comprehensive test coverage

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

### Development Setup
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## 📞 Support

If you encounter any issues or have questions:
- Create an issue in the repository
- Contact the development team
- Check the troubleshooting section

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

<div align="center">

**Made with ❤️ by the Development Team**

⭐ **Star this repository if you find it helpful!** ⭐

</div>
