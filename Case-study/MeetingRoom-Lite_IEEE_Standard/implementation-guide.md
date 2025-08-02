# Implementation Guide
## ระบบจองห้องประชุม MeetingRoom Lite

**Document ID:** IMG-MRL-001  
**Version:** 1.0  
**วันที่:** มีนาคม 2567  
**สถานะ:** Final  

---

## สารบัญ

1. [การเตรียมสภาพแวดล้อม (Environment Setup)](#1-การเตรียมสภาพแวดล้อม-environment-setup)
2. [โครงสร้างโปรเจค (Project Structure)](#2-โครงสร้างโปรเจค-project-structure)
3. [การพัฒนา Backend (Backend Development)](#3-การพัฒนา-backend-backend-development)
4. [การพัฒนา Frontend (Frontend Development)](#4-การพัฒนา-frontend-frontend-development)
5. [การจัดการฐานข้อมูล (Database Management)](#5-การจัดการฐานข้อมูล-database-management)
6. [Best Practices](#6-best-practices)
7. [การ Deploy (Deployment)](#7-การ-deploy-deployment)

---

## 1. การเตรียมสภาพแวดล้อม (Environment Setup)

### 1.1 Software Requirements

- **Node.js** version 18.x หรือใหม่กว่า
- **PostgreSQL** version 14.x หรือใหม่กว่า
- **Git** สำหรับ version control
- **VS Code** หรือ code editor อื่นๆ
- **Postman** สำหรับทดสอบ API

### 1.2 การติดตั้ง Dependencies

#### สร้างโครงสร้างโปรเจค
```bash
mkdir meetingroom-lite
cd meetingroom-lite
mkdir backend frontend
```

#### Backend Setup
```bash
cd backend
npm init -y
npm install express cors dotenv bcrypt jsonwebtoken pg
npm install -D nodemon

# สร้างไฟล์ package.json scripts
```

**package.json:**
```json
{
  "name": "meetingroom-backend",
  "version": "1.0.0",
  "main": "server.js",
  "scripts": {
    "start": "node server.js",
    "dev": "nodemon server.js"
  },
  "dependencies": {
    "express": "^4.18.2",
    "cors": "^2.8.5",
    "dotenv": "^16.3.1",
    "bcrypt": "^5.1.1",
    "jsonwebtoken": "^9.0.2",
    "pg": "^8.11.3"
  },
  "devDependencies": {
    "nodemon": "^3.0.1"
  }
}
```

#### Frontend Setup
```bash
cd ../frontend
npx create-react-app .
npm install axios react-router-dom bootstrap
```

### 1.3 Environment Variables

**backend/.env:**
```env
PORT=5000
DATABASE_URL=postgresql://username:password@localhost:5432/meetingroom_db
JWT_SECRET=your-secret-key-here
NODE_ENV=development
```

**frontend/.env:**
```env
REACT_APP_API_URL=http://localhost:5000/api/v1
```

---

## 2. โครงสร้างโปรเจค (Project Structure)

### 2.1 Backend Structure
```
backend/
├── config/
│   └── database.js
├── controllers/
│   ├── authController.js
│   ├── roomController.js
│   └── bookingController.js
├── middleware/
│   ├── authMiddleware.js
│   └── errorMiddleware.js
├── routes/
│   ├── authRoutes.js
│   ├── roomRoutes.js
│   └── bookingRoutes.js
├── services/
│   ├── authService.js
│   ├── roomService.js
│   └── bookingService.js
├── utils/
│   └── validators.js
├── .env
├── .gitignore
├── package.json
└── server.js
```

### 2.2 Frontend Structure
```
frontend/
├── public/
├── src/
│   ├── components/
│   │   ├── auth/
│   │   │   ├── Login.jsx
│   │   │   └── Register.jsx
│   │   ├── rooms/
│   │   │   ├── RoomList.jsx
│   │   │   └── RoomCard.jsx
│   │   ├── bookings/
│   │   │   ├── BookingForm.jsx
│   │   │   └── BookingList.jsx
│   │   └── common/
│   │       ├── Header.jsx
│   │       └── Footer.jsx
│   ├── services/
│   │   └── api.js
│   ├── App.js
│   ├── App.css
│   └── index.js
├── .env
├── .gitignore
└── package.json
```

---

## 3. การพัฒนา Backend (Backend Development)

### 3.1 Basic Server Setup

**server.js:**
```javascript
const express = require('express');
const cors = require('cors');
const dotenv = require('dotenv');

// Load environment variables
dotenv.config();

// Create Express app
const app = express();

// Middleware
app.use(cors());
app.use(express.json());
app.use(express.urlencoded({ extended: true }));

// Routes
app.use('/api/v1/auth', require('./routes/authRoutes'));
app.use('/api/v1/rooms', require('./routes/roomRoutes'));
app.use('/api/v1/bookings', require('./routes/bookingRoutes'));

// Error handling middleware
app.use(require('./middleware/errorMiddleware'));

// Start server
const PORT = process.env.PORT || 5000;
app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
```

### 3.2 Database Configuration

**config/database.js:**
```javascript
const { Pool } = require('pg');

const pool = new Pool({
  connectionString: process.env.DATABASE_URL,
  ssl: process.env.NODE_ENV === 'production' ? { rejectUnauthorized: false } : false
});

// Test connection
pool.connect((err, client, release) => {
  if (err) {
    console.error('Error connecting to database:', err.stack);
  } else {
    console.log('Connected to PostgreSQL database');
    release();
  }
});

module.exports = {
  query: (text, params) => pool.query(text, params),
  pool
};
```

### 3.3 Authentication Implementation

**controllers/authController.js:**
```javascript
const bcrypt = require('bcrypt');
const jwt = require('jsonwebtoken');
const db = require('../config/database');

// Register new user
const register = async (req, res) => {
  try {
    const { email, password, name } = req.body;
    
    // Check if user exists
    const userExists = await db.query(
      'SELECT id FROM users WHERE email = $1',
      [email]
    );
    
    if (userExists.rows.length > 0) {
      return res.status(400).json({
        success: false,
        error: {
          code: 'EMAIL_EXISTS',
          message: 'Email นี้ถูกใช้งานแล้ว'
        }
      });
    }
    
    // Hash password
    const hashedPassword = await bcrypt.hash(password, 10);
    
    // Insert user
    const result = await db.query(
      'INSERT INTO users (email, password, name) VALUES ($1, $2, $3) RETURNING id, email, name, role',
      [email, hashedPassword, name]
    );
    
    res.status(201).json({
      success: true,
      message: 'ลงทะเบียนสำเร็จ',
      data: result.rows[0]
    });
    
  } catch (error) {
    console.error('Register error:', error);
    res.status(500).json({
      success: false,
      error: {
        code: 'SERVER_ERROR',
        message: 'เกิดข้อผิดพลาดในระบบ'
      }
    });
  }
};

// Login user
const login = async (req, res) => {
  try {
    const { email, password } = req.body;
    
    // Get user
    const result = await db.query(
      'SELECT * FROM users WHERE email = $1',
      [email]
    );
    
    if (result.rows.length === 0) {
      return res.status(401).json({
        success: false,
        error: {
          code: 'INVALID_CREDENTIALS',
          message: 'Email หรือ password ไม่ถูกต้อง'
        }
      });
    }
    
    const user = result.rows[0];
    
    // Verify password
    const validPassword = await bcrypt.compare(password, user.password);
    
    if (!validPassword) {
      return res.status(401).json({
        success: false,
        error: {
          code: 'INVALID_CREDENTIALS',
          message: 'Email หรือ password ไม่ถูกต้อง'
        }
      });
    }
    
    // Generate token
    const token = jwt.sign(
      { id: user.id, email: user.email, role: user.role },
      process.env.JWT_SECRET,
      { expiresIn: '24h' }
    );
    
    res.json({
      success: true,
      token,
      user: {
        id: user.id,
        email: user.email,
        name: user.name,
        role: user.role
      }
    });
    
  } catch (error) {
    console.error('Login error:', error);
    res.status(500).json({
      success: false,
      error: {
        code: 'SERVER_ERROR',
        message: 'เกิดข้อผิดพลาดในระบบ'
      }
    });
  }
};

module.exports = {
  register,
  login
};
```

### 3.4 Authentication Middleware

**middleware/authMiddleware.js:**
```javascript
const jwt = require('jsonwebtoken');

const authMiddleware = (req, res, next) => {
  try {
    // Get token from header
    const authHeader = req.headers.authorization;
    
    if (!authHeader || !authHeader.startsWith('Bearer ')) {
      return res.status(401).json({
        success: false,
        error: {
          code: 'UNAUTHORIZED',
          message: 'กรุณาเข้าสู่ระบบ'
        }
      });
    }
    
    const token = authHeader.split(' ')[1];
    
    // Verify token
    const decoded = jwt.verify(token, process.env.JWT_SECRET);
    req.user = decoded;
    
    next();
  } catch (error) {
    return res.status(401).json({
      success: false,
      error: {
        code: 'INVALID_TOKEN',
        message: 'Token ไม่ถูกต้องหรือหมดอายุ'
      }
    });
  }
};

const adminMiddleware = (req, res, next) => {
  if (req.user.role !== 'admin') {
    return res.status(403).json({
      success: false,
      error: {
        code: 'FORBIDDEN',
        message: 'ไม่มีสิทธิ์เข้าถึง'
      }
    });
  }
  next();
};

module.exports = {
  authMiddleware,
  adminMiddleware
};
```

### 3.5 Room Management

**controllers/roomController.js:**
```javascript
const db = require('../config/database');

// Get all rooms
const getAllRooms = async (req, res) => {
  try {
    const { date, start_time, end_time } = req.query;
    
    let query = 'SELECT * FROM rooms WHERE is_active = true ORDER BY name';
    const result = await db.query(query);
    
    // If date and time provided, check availability
    if (date && start_time && end_time) {
      const rooms = await Promise.all(
        result.rows.map(async (room) => {
          const bookingCheck = await db.query(
            `SELECT COUNT(*) as count FROM bookings 
             WHERE room_id = $1 
             AND booking_date = $2 
             AND status = 'confirmed'
             AND ((start_time < $4 AND end_time > $3) 
                  OR (start_time >= $3 AND start_time < $4))`,
            [room.id, date, start_time, end_time]
          );
          
          return {
            ...room,
            is_available: bookingCheck.rows[0].count == 0
          };
        })
      );
      
      return res.json({
        success: true,
        data: rooms
      });
    }
    
    res.json({
      success: true,
      data: result.rows
    });
    
  } catch (error) {
    console.error('Get rooms error:', error);
    res.status(500).json({
      success: false,
      error: {
        code: 'SERVER_ERROR',
        message: 'เกิดข้อผิดพลาดในระบบ'
      }
    });
  }
};

// Create new room (Admin only)
const createRoom = async (req, res) => {
  try {
    const { name, capacity, floor } = req.body;
    
    const result = await db.query(
      'INSERT INTO rooms (name, capacity, floor) VALUES ($1, $2, $3) RETURNING *',
      [name, capacity, floor]
    );
    
    res.status(201).json({
      success: true,
      message: 'เพิ่มห้องสำเร็จ',
      data: result.rows[0]
    });
    
  } catch (error) {
    console.error('Create room error:', error);
    res.status(500).json({
      success: false,
      error: {
        code: 'SERVER_ERROR',
        message: 'เกิดข้อผิดพลาดในระบบ'
      }
    });
  }
};

module.exports = {
  getAllRooms,
  createRoom
};
```

### 3.6 Booking Management

**controllers/bookingController.js:**
```javascript
const db = require('../config/database');

// Create new booking
const createBooking = async (req, res) => {
  try {
    const { room_id, booking_date, start_time, end_time, title } = req.body;
    const user_id = req.user.id;
    
    // Check for conflicts
    const conflictCheck = await db.query(
      `SELECT COUNT(*) as count FROM bookings 
       WHERE room_id = $1 
       AND booking_date = $2 
       AND status = 'confirmed'
       AND ((start_time < $4 AND end_time > $3) 
            OR (start_time >= $3 AND start_time < $4))`,
      [room_id, booking_date, start_time, end_time]
    );
    
    if (conflictCheck.rows[0].count > 0) {
      return res.status(409).json({
        success: false,
        error: {
          code: 'CONFLICT',
          message: 'ห้องไม่ว่างในช่วงเวลานี้'
        }
      });
    }
    
    // Create booking
    const result = await db.query(
      `INSERT INTO bookings (user_id, room_id, booking_date, start_time, end_time, title) 
       VALUES ($1, $2, $3, $4, $5, $6) 
       RETURNING id, booking_date, start_time, end_time, title`,
      [user_id, room_id, booking_date, start_time, end_time, title]
    );
    
    // Get room name
    const room = await db.query('SELECT name FROM rooms WHERE id = $1', [room_id]);
    
    res.status(201).json({
      success: true,
      message: 'จองห้องสำเร็จ',
      data: {
        ...result.rows[0],
        room_name: room.rows[0].name
      }
    });
    
  } catch (error) {
    console.error('Create booking error:', error);
    res.status(500).json({
      success: false,
      error: {
        code: 'SERVER_ERROR',
        message: 'เกิดข้อผิดพลาดในระบบ'
      }
    });
  }
};

// Get user's bookings
const getMyBookings = async (req, res) => {
  try {
    const user_id = req.user.id;
    const today = new Date().toISOString().split('T')[0];
    
    // Get upcoming bookings
    const upcoming = await db.query(
      `SELECT b.*, r.name as room_name 
       FROM bookings b 
       JOIN rooms r ON b.room_id = r.id 
       WHERE b.user_id = $1 
       AND b.status = 'confirmed'
       AND b.booking_date >= $2 
       ORDER BY b.booking_date, b.start_time`,
      [user_id, today]
    );
    
    // Get past bookings
    const past = await db.query(
      `SELECT b.*, r.name as room_name 
       FROM bookings b 
       JOIN rooms r ON b.room_id = r.id 
       WHERE b.user_id = $1 
       AND b.booking_date < $2 
       ORDER BY b.booking_date DESC, b.start_time DESC 
       LIMIT 20`,
      [user_id, today]
    );
    
    res.json({
      success: true,
      data: {
        upcoming: upcoming.rows,
        past: past.rows
      }
    });
    
  } catch (error) {
    console.error('Get bookings error:', error);
    res.status(500).json({
      success: false,
      error: {
        code: 'SERVER_ERROR',
        message: 'เกิดข้อผิดพลาดในระบบ'
      }
    });
  }
};

// Cancel booking
const cancelBooking = async (req, res) => {
  try {
    const { id } = req.params;
    const user_id = req.user.id;
    
    // Check ownership
    const booking = await db.query(
      'SELECT * FROM bookings WHERE id = $1 AND user_id = $2',
      [id, user_id]
    );
    
    if (booking.rows.length === 0) {
      return res.status(404).json({
        success: false,
        error: {
          code: 'NOT_FOUND',
          message: 'ไม่พบการจอง'
        }
      });
    }
    
    // Update status
    await db.query(
      'UPDATE bookings SET status = $1 WHERE id = $2',
      ['cancelled', id]
    );
    
    res.json({
      success: true,
      message: 'ยกเลิกการจองสำเร็จ'
    });
    
  } catch (error) {
    console.error('Cancel booking error:', error);
    res.status(500).json({
      success: false,
      error: {
        code: 'SERVER_ERROR',
        message: 'เกิดข้อผิดพลาดในระบบ'
      }
    });
  }
};

module.exports = {
  createBooking,
  getMyBookings,
  cancelBooking
};
```

---

## 4. การพัฒนา Frontend (Frontend Development)

### 4.1 API Service Setup

**src/services/api.js:**
```javascript
import axios from 'axios';

const API_URL = process.env.REACT_APP_API_URL || 'http://localhost:5000/api/v1';

// Create axios instance
const api = axios.create({
  baseURL: API_URL,
  headers: {
    'Content-Type': 'application/json'
  }
});

// Request interceptor
api.interceptors.request.use(
  (config) => {
    const token = localStorage.getItem('token');
    if (token) {
      config.headers.Authorization = `Bearer ${token}`;
    }
    return config;
  },
  (error) => Promise.reject(error)
);

// Response interceptor
api.interceptors.response.use(
  (response) => response,
  (error) => {
    if (error.response?.status === 401) {
      localStorage.removeItem('token');
      window.location.href = '/login';
    }
    return Promise.reject(error);
  }
);

// Auth API
export const authAPI = {
  register: (data) => api.post('/auth/register', data),
  login: (data) => api.post('/auth/login', data)
};

// Room API
export const roomAPI = {
  getAll: (params) => api.get('/rooms', { params }),
  create: (data) => api.post('/rooms', data),
  update: (id, data) => api.put(`/rooms/${id}`, data),
  delete: (id) => api.delete(`/rooms/${id}`)
};

// Booking API
export const bookingAPI = {
  create: (data) => api.post('/bookings', data),
  getMy: () => api.get('/bookings/my'),
  cancel: (id) => api.delete(`/bookings/${id}`)
};

export default api;
```

### 4.2 Login Component

**src/components/auth/Login.jsx:**
```javascript
import React, { useState } from 'react';
import { useNavigate, Link } from 'react-router-dom';
import { authAPI } from '../../services/api';

function Login() {
  const navigate = useNavigate();
  const [formData, setFormData] = useState({
    email: '',
    password: ''
  });
  const [error, setError] = useState('');
  const [loading, setLoading] = useState(false);

  const handleChange = (e) => {
    setFormData({
      ...formData,
      [e.target.name]: e.target.value
    });
  };

  const handleSubmit = async (e) => {
    e.preventDefault();
    setError('');
    setLoading(true);

    try {
      const response = await authAPI.login(formData);
      
      // Save token and user info
      localStorage.setItem('token', response.data.token);
      localStorage.setItem('user', JSON.stringify(response.data.user));
      
      // Redirect
      navigate('/rooms');
    } catch (err) {
      setError(err.response?.data?.error?.message || 'เกิดข้อผิดพลาด');
    } finally {
      setLoading(false);
    }
  };

  return (
    <div className="container mt-5">
      <div className="row justify-content-center">
        <div className="col-md-6">
          <div className="card">
            <div className="card-body">
              <h3 className="text-center mb-4">เข้าสู่ระบบ</h3>
              
              {error && (
                <div className="alert alert-danger" role="alert">
                  {error}
                </div>
              )}
              
              <form onSubmit={handleSubmit}>
                <div className="mb-3">
                  <label htmlFor="email" className="form-label">Email</label>
                  <input
                    type="email"
                    className="form-control"
                    id="email"
                    name="email"
                    value={formData.email}
                    onChange={handleChange}
                    required
                  />
                </div>
                
                <div className="mb-3">
                  <label htmlFor="password" className="form-label">Password</label>
                  <input
                    type="password"
                    className="form-control"
                    id="password"
                    name="password"
                    value={formData.password}
                    onChange={handleChange}
                    required
                  />
                </div>
                
                <button 
                  type="submit" 
                  className="btn btn-primary w-100"
                  disabled={loading}
                >
                  {loading ? 'กำลังเข้าสู่ระบบ...' : 'เข้าสู่ระบบ'}
                </button>
              </form>
              
              <div className="text-center mt-3">
                <Link to="/register">ยังไม่มีบัญชี? สมัครสมาชิก</Link>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  );
}

export default Login;
```

### 4.3 Room List Component

**src/components/rooms/RoomList.jsx:**
```javascript
import React, { useState, useEffect } from 'react';
import { roomAPI } from '../../services/api';
import RoomCard from './RoomCard';

function RoomList() {
  const [rooms, setRooms] = useState([]);
  const [loading, setLoading] = useState(true);
  const [filters, setFilters] = useState({
    date: new Date().toISOString().split('T')[0],
    start_time: '09:00',
    end_time: '10:00'
  });

  useEffect(() => {
    fetchRooms();
  }, [filters]);

  const fetchRooms = async () => {
    try {
      const response = await roomAPI.getAll(filters);
      setRooms(response.data.data);
    } catch (error) {
      console.error('Error fetching rooms:', error);
    } finally {
      setLoading(false);
    }
  };

  const handleFilterChange = (e) => {
    setFilters({
      ...filters,
      [e.target.name]: e.target.value
    });
  };

  if (loading) {
    return (
      <div className="text-center mt-5">
        <div className="spinner-border" role="status">
          <span className="visually-hidden">Loading...</span>
        </div>
      </div>
    );
  }

  return (
    <div className="container mt-4">
      <h2>ห้องประชุม</h2>
      
      {/* Filters */}
      <div className="row mb-4">
        <div className="col-md-4">
          <label>วันที่</label>
          <input
            type="date"
            className="form-control"
            name="date"
            value={filters.date}
            onChange={handleFilterChange}
            min={new Date().toISOString().split('T')[0]}
          />
        </div>
        <div className="col-md-4">
          <label>เวลาเริ่ม</label>
          <input
            type="time"
            className="form-control"
            name="start_time"
            value={filters.start_time}
            onChange={handleFilterChange}
          />
        </div>
        <div className="col-md-4">
          <label>เวลาสิ้นสุด</label>
          <input
            type="time"
            className="form-control"
            name="end_time"
            value={filters.end_time}
            onChange={handleFilterChange}
          />
        </div>
      </div>
      
      {/* Room Grid */}
      <div className="row">
        {rooms.map(room => (
          <div key={room.id} className="col-md-4 mb-4">
            <RoomCard 
              room={room} 
              bookingData={filters}
              onBooked={fetchRooms}
            />
          </div>
        ))}
      </div>
    </div>
  );
}

export default RoomList;
```

### 4.4 Booking Form Component

**src/components/bookings/BookingForm.jsx:**
```javascript
import React, { useState } from 'react';
import { bookingAPI } from '../../services/api';

function BookingForm({ room, bookingData, onClose, onSuccess }) {
  const [title, setTitle] = useState('');
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState('');

  const handleSubmit = async (e) => {
    e.preventDefault();
    setLoading(true);
    setError('');

    try {
      await bookingAPI.create({
        room_id: room.id,
        booking_date: bookingData.date,
        start_time: bookingData.start_time,
        end_time: bookingData.end_time,
        title
      });
      
      alert('จองห้องสำเร็จ!');
      onSuccess();
      onClose();
    } catch (err) {
      setError(err.response?.data?.error?.message || 'เกิดข้อผิดพลาด');
    } finally {
      setLoading(false);
    }
  };

  return (
    <div className="modal show d-block" tabIndex="-1">
      <div className="modal-dialog">
        <div className="modal-content">
          <div className="modal-header">
            <h5 className="modal-title">จองห้อง {room.name}</h5>
            <button 
              type="button" 
              className="btn-close" 
              onClick={onClose}
            ></button>
          </div>
          <div className="modal-body">
            {error && (
              <div className="alert alert-danger">{error}</div>
            )}
            
            <form onSubmit={handleSubmit}>
              <div className="mb-3">
                <label>วันที่</label>
                <input 
                  type="date" 
                  className="form-control" 
                  value={bookingData.date}
                  readOnly
                />
              </div>
              
              <div className="row">
                <div className="col">
                  <label>เวลาเริ่ม</label>
                  <input 
                    type="time" 
                    className="form-control" 
                    value={bookingData.start_time}
                    readOnly
                  />
                </div>
                <div className="col">
                  <label>เวลาสิ้นสุด</label>
                  <input 
                    type="time" 
                    className="form-control" 
                    value={bookingData.end_time}
                    readOnly
                  />
                </div>
              </div>
              
              <div className="mb-3 mt-3">
                <label>หัวข้อการประชุม</label>
                <input
                  type="text"
                  className="form-control"
                  value={title}
                  onChange={(e) => setTitle(e.target.value)}
                  required
                  placeholder="เช่น Team Meeting"
                />
              </div>
              
              <div className="d-grid gap-2">
                <button 
                  type="submit" 
                  className="btn btn-primary"
                  disabled={loading}
                >
                  {loading ? 'กำลังจอง...' : 'ยืนยันการจอง'}
                </button>
                <button 
                  type="button" 
                  className="btn btn-secondary"
                  onClick={onClose}
                >
                  ยกเลิก
                </button>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
  );
}

export default BookingForm;
```

---

## 5. การจัดการฐานข้อมูล (Database Management)

### 5.1 Database Setup

**database/schema.sql:**
```sql
-- Create database
CREATE DATABASE meetingroom_db;

-- Connect to database
\c meetingroom_db;

-- Create users table
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    email VARCHAR(255) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    name VARCHAR(100) NOT NULL,
    role VARCHAR(20) DEFAULT 'user' CHECK (role IN ('user', 'admin')),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Create rooms table
CREATE TABLE rooms (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    capacity INTEGER NOT NULL CHECK (capacity > 0),
    floor INTEGER,
    is_active BOOLEAN DEFAULT true,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Create bookings table
CREATE TABLE bookings (
    id SERIAL PRIMARY KEY,
    user_id INTEGER NOT NULL REFERENCES users(id) ON DELETE CASCADE,
    room_id INTEGER NOT NULL REFERENCES rooms(id) ON DELETE CASCADE,
    booking_date DATE NOT NULL,
    start_time TIME NOT NULL,
    end_time TIME NOT NULL,
    title VARCHAR(255) NOT NULL,
    status VARCHAR(20) DEFAULT 'confirmed' 
        CHECK (status IN ('confirmed', 'cancelled', 'completed', 'no-show')),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    CONSTRAINT valid_time_range CHECK (end_time > start_time)
);

-- Create indexes
CREATE INDEX idx_users_email ON users(email);
CREATE INDEX idx_bookings_date ON bookings(booking_date);
CREATE INDEX idx_bookings_room ON bookings(room_id);
CREATE INDEX idx_bookings_user ON bookings(user_id);
CREATE INDEX idx_bookings_status ON bookings(status);

-- Prevent double booking
CREATE UNIQUE INDEX idx_no_double_booking 
ON bookings(room_id, booking_date, start_time, end_time)
WHERE status = 'confirmed';

-- Update timestamp function
CREATE OR REPLACE FUNCTION update_updated_at_column()
RETURNS TRIGGER AS $
BEGIN
    NEW.updated_at = CURRENT_TIMESTAMP;
    RETURN NEW;
END;
$ language 'plpgsql';

-- Create triggers
CREATE TRIGGER update_users_updated_at BEFORE UPDATE ON users
    FOR EACH ROW EXECUTE FUNCTION update_updated_at_column();

CREATE TRIGGER update_rooms_updated_at BEFORE UPDATE ON rooms
    FOR EACH ROW EXECUTE FUNCTION update_updated_at_column();

CREATE TRIGGER update_bookings_updated_at BEFORE UPDATE ON bookings
    FOR EACH ROW EXECUTE FUNCTION update_updated_at_column();
```

### 5.2 Seed Data

**database/seed.sql:**
```sql
-- Insert admin user (password: admin123)
INSERT INTO users (email, password, name, role) VALUES
('admin@meetingroom.com', '$2b$10$YourHashedPasswordHere', 'System Admin', 'admin');

-- Insert test users
INSERT INTO users (email, password, name) VALUES
('user1@example.com', '$2b$10$YourHashedPasswordHere', 'สมชาย ใจดี'),
('user2@example.com', '$2b$10$YourHashedPasswordHere', 'สมหญิง รักเรียน');

-- Insert rooms
INSERT INTO rooms (name, capacity, floor) VALUES
('ห้องประชุม A', 20, 3),
('ห้องประชุม B', 15, 3),
('ห้องประชุม C', 30, 4),
('ห้องประชุมใหญ่', 50, 5),
('ห้องประชุมเล็ก', 8, 2);

-- Insert sample bookings
INSERT INTO bookings (user_id, room_id, booking_date, start_time, end_time, title) VALUES
(2, 1, CURRENT_DATE + INTERVAL '1 day', '09:00', '10:00', 'Team Meeting'),
(2, 2, CURRENT_DATE + INTERVAL '2 days', '14:00', '16:00', 'Project Review'),
(3, 3, CURRENT_DATE + INTERVAL '1 day', '10:00', '12:00', 'Client Presentation');
```

---

## 6. Best Practices

### 6.1 Code Organization
- แยก business logic ออกจาก controllers
- ใช้ services layer สำหรับ reusable logic
- ตั้งชื่อ files และ functions ให้ชัดเจน

### 6.2 Error Handling
- จัดการ errors ทุกระดับ
- ส่ง error messages ที่เข้าใจง่าย
- Log errors สำหรับ debugging

### 6.3 Security
- Validate input ทุกจุด
- ใช้ parameterized queries
- ไม่เก็บ sensitive data ใน logs
- ใช้ HTTPS ใน production

### 6.4 Performance
- ใช้ indexes สำหรับ queries ที่ใช้บ่อย
- Implement caching ถ้าจำเป็น
- Optimize database queries

### 6.5 Testing
- ทดสอบ edge cases
- ทดสอบ error scenarios
- ทดสอบ security vulnerabilities

---

## 7. การ Deploy (Deployment)

### 7.1 Prepare for Production

**Backend:**
1. Set production environment variables
2. Enable CORS for production domain
3. Set up database migrations
4. Configure logging

**Frontend:**
1. Build production bundle
2. Optimize images and assets
3. Configure environment variables
4. Set up error tracking

### 7.2 Deployment Options

**Free Hosting:**
- Backend: Render, Railway, Cyclic
- Database: ElephantSQL, Supabase
- Frontend: Netlify, Vercel

**Example Deploy Commands:**
```bash
# Backend (Render)
# Create render.yaml file
# Push to GitHub
# Connect to Render

# Frontend (Netlify)
cd frontend
npm run build
# Drag build folder to Netlify

# Database (ElephantSQL)
# Create free instance
# Run schema.sql
# Update DATABASE_URL
```

### 7.3 Post-Deployment
1. Test all features
2. Monitor error logs
3. Set up backups
4. Create user documentation

---

**หมายเหตุ:** เอกสารนี้เป็นคู่มือการพัฒนาที่สามารถปรับเปลี่ยนได้ตามความเหมาะสม ควรศึกษาเพิ่มเติมจาก official documentation ของแต่ละ technology