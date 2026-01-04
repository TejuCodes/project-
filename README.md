# **Coffee Shop Management System** ☕

![Project Banner](https://img.shields.io/badge/BCA-Project-blue) 
![Tech Stack](https://img.shields.io/badge/Stack-MERN-orange) 
![License](https://img.shields.io/badge/License-MIT-green)

A complete **Coffee Shop Management System** with user authentication, table booking, and admin panel. Built for BCA students using modern web technologies.
    
## ✨ **Features**     
        
### 👤 **User Features**
- ✅ User registration & login with JWT authentication
- ✅ Browse coffee shop menu and table availability
- ✅ Book tables with date/time selection
- ✅ View and cancel bookings
- ✅ User dashboard with booking history

### 👨‍💼 **Admin Features**
- ✅ Admin login with elevated privileges
- ✅ View all bookings and user statistics
- ✅ Manage table availability
- ✅ System analytics dashboard

### 🎨 **Technical Features**
- ✅ Responsive UI/UX design
- ✅ Secure authentication with bcrypt password hashing
- ✅ RESTful API architecture
- ✅ MongoDB database integration
- ✅ CORS-enabled for cross-origin requests
- ✅ Real-time form validation

## 🏗️ **Tech Stack**

### **Frontend**
- **HTML5** - Semantic markup
- **CSS3** - Styling with Flexbox/Grid
- **JavaScript (ES6+)** - DOM manipulation & Fetch API

### **Backend**
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** - ODM for MongoDB

### **Authentication & Security**
- **JSON Web Tokens (JWT)** - Stateless authentication
- **Bcrypt.js** - Password hashing
- **CORS** - Cross-origin resource sharing

### **Development Tools**
- **Nodemon** - Auto-restart during development
- **Git** - Version control

## 📁 **Project Structure**

```
coffee-shop-system/
├── public/                 # Static files
│   ├── css/
│   │   └── style.css     # All CSS styles
│   ├── js/
│   │   └── script.js     # Frontend JavaScript
│   └── images/           # Assets
├── views/                 # HTML pages
│   ├── index.html        # Home page
│   ├── login.html        # Login page
│   ├── register.html     # Registration page
│   ├── dashboard.html    # User dashboard
│   ├── admin.html        # Admin panel
│   └── booking.html      # Booking page
├── server.js             # Main server file
├── package.json          # Dependencies
├── .env                  # Environment variables
└── README.md            # This file
```

## 🚀 **Quick Start**

### **Prerequisites**
- [Node.js](https://nodejs.org/) (v14 or higher)
- [MongoDB](https://www.mongodb.com/) (Local or Atlas)
- Git (optional)

### **Installation Steps**

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/coffee-shop-system.git
cd coffee-shop-system
```

2. **Install dependencies**
```bash
npm install
```

3. **Set up MongoDB**
   - **Option A: Local MongoDB**
   ```bash
   # Start MongoDB service
   sudo systemctl start mongod   # Linux/Mac
   # or
   net start MongoDB            # Windows
   ```

   - **Option B: MongoDB Atlas (Cloud)**
     - Create free account at [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
     - Create a cluster
     - Get connection string

4. **Configure environment variables**
```bash
# Create .env file in project root
touch .env
```

Add to `.env`:
```env
PORT=3000
MONGODB_URI=mongodb://localhost:27017/coffeeShopDB
JWT_SECRET=your_super_secret_key_here
```

5. **Run the application**
```bash
# Development mode (with auto-restart)
npm run dev

# Production mode
npm start
```

6. **Access the application**
   - Open browser: `http://localhost:3000`
   - Default admin credentials:
     - Email: `admin@coffee.com`
     - Password: `admin123`

## 📡 **API Endpoints**

### **Authentication**
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/register` | User registration |
| POST | `/api/login` | User login |

### **User Endpoints**
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/tables` | Get available tables |
| POST | `/api/bookings` | Create booking |
| GET | `/api/bookings/user/:userId` | Get user bookings |
| DELETE | `/api/bookings/:id` | Cancel booking |

### **Admin Endpoints**
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/admin/bookings` | Get all bookings |
| GET | `/api/admin/stats` | Get system statistics |

## 🗄️ **Database Schema**

### **User Collection**
```javascript
{
  name: String,
  email: String (unique),
  password: String (hashed),
  phone: String,
  role: String, // 'user' or 'admin'
  createdAt: Date
}
```

### **Booking Collection**
```javascript
{
  userId: ObjectId,
  tableNumber: String,
  bookingDate: Date,
  bookingTime: String,
  guests: Number,
  status: String, // 'confirmed', 'cancelled'
  createdAt: Date
}
```

### **Table Collection**
```javascript
{
  tableNumber: String (unique),
  capacity: Number,
  location: String,
  status: String // 'available', 'booked'
}
```

## 🔐 **Security Features**

1. **Password Security**
   - Bcrypt hashing with salt
   - No plain text passwords stored

2. **Authentication**
   - JWT tokens for stateless authentication
   - Token expiry (24 hours)
   - Protected API endpoints

3. **Data Validation**
   - Input sanitization
   - MongoDB injection prevention
   - CORS policy implementation

## 🎯 **Key Learning Outcomes**

### **For BCA Students:**
1. **Full-stack Development** - Complete MERN-like stack
2. **Authentication Systems** - JWT implementation
3. **Database Design** - MongoDB schema design
4. **RESTful APIs** - Building and consuming APIs
5. **Security Practices** - Password hashing, CORS, input validation
6. **Frontend-Backend Integration** - AJAX with Fetch API

## 🖥️ **Screenshots**

| Home Page | Login Page | Dashboard |
|-----------|------------|-----------|
| ![Home](https://via.placeholder.com/400x250/6f4e37/ffffff?text=Coffee+Shop+Home) | ![Login](https://via.placeholder.com/400x250/2c3e50/ffffff?text=Login+Page) | ![Dashboard](https://via.placeholder.com/400x250/27ae60/ffffff?text=User+Dashboard) |

## 🧪 **Testing the API**

### **Using curl**
```bash
# Register a user
curl -X POST http://localhost:3000/api/register \
  -H "Content-Type: application/json" \
  -d '{"name":"John Doe","email":"john@example.com","password":"test123"}'

# Login
curl -X POST http://localhost:3000/api/login \
  -H "Content-Type: application/json" \
  -d '{"email":"john@example.com","password":"test123","userType":"user"}'

# Get tables (with token)
curl -X GET http://localhost:3000/api/tables \
  -H "Authorization: Bearer YOUR_JWT_TOKEN"
```

### **Using Postman**
1. Import the following collection:
```json
{
  "info": {
    "name": "Coffee Shop API",
    "schema": "https://schema.getpostman.com/json/collection/v2.1.0/collection.json"
  },
  "item": [
    {
      "name": "Register",
      "request": {
        "method": "POST",
        "header": [
          {
            "key": "Content-Type",
            "value": "application/json"
          }
        ],
        "url": "http://localhost:3000/api/register",
        "body": {
          "mode": "raw",
          "raw": "{\n  \"name\": \"Test User\",\n  \"email\": \"test@example.com\",\n  \"password\": \"test123\"\n}"
        }
      }
    }
  ]
}
```

## 🐛 **Troubleshooting**

| Issue | Solution |
|-------|----------|
| **MongoDB Connection Failed** | Check if MongoDB service is running |
| **CORS Errors** | Ensure frontend origin is allowed in CORS config |
| **JWT Token Invalid** | Check token format and expiry |
| **Port Already in Use** | Change PORT in .env or kill process: `killall node` |
| **Module Not Found** | Run `npm install` again |

## 📚 **Learning Resources**

### **For Beginners:**
1. [MDN Web Docs](https://developer.mozilla.org/) - HTML, CSS, JavaScript
2. [Express.js Guide](https://expressjs.com/en/guide/routing.html)
3. [Mongoose Documentation](https://mongoosejs.com/docs/guide.html)
4. [JWT Introduction](https://jwt.io/introduction/)

### **For Advanced Concepts:**
1. [Node.js Best Practices](https://github.com/goldbergyoni/nodebestpractices)
2. [MongoDB University](https://university.mongodb.com/) - Free courses
3. [OWASP Security Guide](https://cheatsheetseries.owasp.org/)

## 🤝 **Contributing**

### **Contributing Guidelines:**
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### **For BCA Students:**
- Add new features like payment integration
- Implement email notifications
- Create a mobile-responsive design
- Add real-time updates with Socket.io

## 📄 **License**

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👥 **Authors**

- **Your Name** - *Initial work* - [YourGitHub](https://github.com/yourusername)

## 🙏 **Acknowledgments**

- Icons by [Font Awesome](https://fontawesome.com/)
- Images from [Unsplash](https://unsplash.com/)
- Inspired by real coffee shop management needs
- Special thanks to BCA curriculum for project guidance

## 📊 **Project Status**

**Completed Features:**
- ✅ User authentication system
- ✅ Table booking functionality
- ✅ Admin dashboard
- ✅ Responsive design
- ✅ Database integration

**Future Enhancements:**
- 🔄 Payment gateway integration
- 🔄 Email/SMS notifications
- 🔄 Real-time table availability
- 🔄 Mobile application
- 🔄 Inventory management

---

## ⭐ **Support**

If you find this project helpful, please give it a star! ⭐

**Made with ❤️ form TEJASHWIN**

---
*This project is created for educational purposes as part of BCA curriculum. Not for commercial use.*
