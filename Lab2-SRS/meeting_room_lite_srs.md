# Software Requirements Specification (SRS)
## MeetingRoom Lite - ระบบจองห้องประชุมพื้นฐาน

**Version:** 1.0  
**Date:** March 2024  
**Duration:** 1 Month Project  
**Target:** Software Engineering Students Year 2  

---

## Executive Summary

MeetingRoom Lite เป็นระบบจองห้องประชุมแบบ Web Application พื้นฐาน ออกแบบมาเพื่อให้นักศึกษาชั้นปีที่ 2 สามารถพัฒนาได้จริงภายใน 1 เดือน โดยใช้ **React.js + Node.js + Express + PostgreSQL** 

**Key Features ที่ทำได้จริง:**
- ✅ Login/Register แบบพื้นฐาน
- ✅ ดูห้องว่าง และจองห้อง
- ✅ ดูการจองของตนเอง
- ✅ ยกเลิกการจอง
- ✅ Admin จัดการห้อง (CRUD)

---

## Table of Contents

1. [Introduction](#1-introduction)
2. [System Overview](#2-system-overview)
3. [Functional Requirements (5 Core Features)](#3-functional-requirements)
4. [Technical Requirements](#4-technical-requirements)
5. [Database Design](#5-database-design)
6. [API Endpoints](#6-api-endpoints)
7. [UI/UX Design](#7-uiux-design)
8. [Development Plan (4 Weeks)](#8-development-plan)
9. [Testing Guide](#9-testing-guide)
10. [Learning Resources](#10-learning-resources)

---

## 1. Introduction

### 1.1 Purpose
เอกสารนี้เป็น SRS แบบย่อ (Simplified SRS) ที่ออกแบบมาเพื่อ:
- ให้นักศึกษาเข้าใจ requirement gathering
- ฝึกการวางแผนโปรเจค
- เรียนรู้ full-stack development
- ทำโปรเจคจบได้ใน 1 เดือน

### 1.2 Scope (ขอบเขตที่ทำได้จริง)

**✅ สิ่งที่จะทำ (In Scope):**
1. **User System** - Register, Login, Logout
2. **Room Booking** - ดูห้องว่าง, จองห้อง, ยกเลิก
3. **Admin Panel** - เพิ่ม/แก้ไข/ลบห้อง
4. **Simple Dashboard** - สรุปการจอง
5. **Responsive Design** - ใช้ได้ทั้ง desktop/mobile

**❌ สิ่งที่ไม่ทำ (Out of Scope):**
- Email notifications (ซับซ้อนเกินไป)
- Calendar integration
- Recurring bookings
- Advanced reporting
- Multiple languages

### 1.3 Definitions

| Term | คำอธิบาย |
|------|----------|
| User | ผู้ใช้ทั่วไปที่จองห้อง |
| Admin | ผู้ดูแลระบบที่จัดการห้อง |
| Booking | การจองห้องในช่วงเวลาหนึ่ง |
| Room | ห้องประชุมที่จองได้ |
| Conflict | การจองที่ซ้อนเวลากัน |

---

## 2. System Overview

### 2.1 System Architecture (แบบง่าย)

```
┌─────────────────────────────────────┐
│      Frontend (React.js)            │
│  - Components: Login, Booking, etc. │
│  - State: useState, useEffect       │
│  - Routing: React Router           │
│  - UI: Bootstrap or Material-UI    │
└──────────────┬──────────────────────┘
               │ HTTP/JSON
               ▼
┌─────────────────────────────────────┐
│      Backend (Node.js + Express)    │
│  - Routes: /api/auth, /api/rooms    │
│  - Middleware: Auth, Validation     │
│  - Controllers: Business Logic      │
└──────────────┬──────────────────────┘
               │ SQL
               ▼
┌─────────────────────────────────────┐
│      Database (PostgreSQL)          │
│  - Tables: users, rooms, bookings   │
│  - Simple schema, no complex joins  │
└─────────────────────────────────────┘
```

### 2.2 Technology Stack

**Frontend:**
- React.js 18.x (with hooks)
- React Router 6.x
- Axios for API calls
- Bootstrap 5 หรือ Material-UI
- Day.js for date handling

**Backend:**
- Node.js 18.x
- Express.js 4.x
- JWT for authentication
- bcrypt for passwords
- express-validator

**Database:**
- PostgreSQL 14.x
- pg (node-postgres) driver

**Development Tools:**
- VS Code
- Postman (API testing)
- Git & GitHub
- npm or yarn

---

## 3. Functional Requirements

### FR-01: User Registration ✅

**Description:** ผู้ใช้สามารถสมัครสมาชิกด้วย email

**User Story:**
```
As a new user
I want to register an account
So that I can book meeting rooms
```

**Acceptance Criteria:**
1. หน้า register มี form: email, password, name
2. Validate email format
3. Password ต้องมีอย่างน้อย 6 ตัวอักษร
4. ไม่อนุญาต email ซ้ำ
5. หลัง register สำเร็จ ไปหน้า login

**Technical Details:**
```javascript
// API Endpoint
POST /api/auth/register
Body: {
  email: "student@email.com",
  password: "123456",
  name: "Student Name"
}

// Response
{
  success: true,
  message: "Registration successful"
}
```

---

### FR-02: User Login/Logout ✅

**Description:** ผู้ใช้ login ด้วย email/password

**User Story:**
```
As a registered user
I want to login to the system
So that I can access booking features
```

**Acceptance Criteria:**
1. หน้า login มี email, password fields
2. เก็บ JWT token ใน localStorage
3. Redirect ไป dashboard หลัง login
4. มีปุ่ม logout ที่ navbar
5. Token expire ใน 24 ชั่วโมง

**Technical Details:**
```javascript
// Login API
POST /api/auth/login
Body: {
  email: "student@email.com",
  password: "123456"
}

// Response
{
  success: true,
  token: "jwt-token-here",
  user: {
    id: 1,
    email: "student@email.com",
    name: "Student Name",
    role: "user"
  }
}
```

---

### FR-03: View Available Rooms ✅

**Description:** ดูรายการห้องและสถานะ

**User Story:**
```
As a user
I want to see available rooms
So that I can choose which room to book
```

**Acceptance Criteria:**
1. แสดงรายการห้องทั้งหมด
2. แสดงข้อมูล: ชื่อห้อง, ขนาด, ชั้น
3. กรองตามวันที่และเวลาได้
4. แสดงสถานะ: ว่าง/ไม่ว่าง
5. ใช้สีแยกสถานะ (เขียว/แดง)

**Technical Details:**
```javascript
// API Endpoint
GET /api/rooms?date=2024-03-15&start_time=10:00&end_time=12:00

// Response
{
  success: true,
  rooms: [
    {
      id: 1,
      name: "Meeting Room A",
      capacity: 10,
      floor: 3,
      is_available: true
    }
  ]
}
```

---

### FR-04: Book a Room ✅

**Description:** จองห้องประชุม

**User Story:**
```
As a user
I want to book a meeting room
So that I can reserve it for my meeting
```

**Acceptance Criteria:**
1. เลือกห้อง วันที่ เวลาเริ่ม-สิ้นสุด
2. ใส่หัวข้อการประชุม
3. ตรวจสอบไม่ให้จองซ้ำ
4. จองได้ล่วงหน้าสูงสุด 30 วัน
5. จองขั้นต่ำ 30 นาที สูงสุด 4 ชั่วโมง

**Technical Details:**
```javascript
// API Endpoint
POST /api/bookings
Headers: { Authorization: "Bearer jwt-token" }
Body: {
  room_id: 1,
  date: "2024-03-15",
  start_time: "10:00",
  end_time: "12:00",
  title: "Team Meeting"
}

// Response
{
  success: true,
  booking: {
    id: 123,
    room_name: "Meeting Room A",
    date: "2024-03-15",
    start_time: "10:00",
    end_time: "12:00",
    status: "confirmed"
  }
}
```

---

### FR-05: Manage My Bookings ✅

**Description:** ดูและยกเลิกการจองของตนเอง

**User Story:**
```
As a user
I want to see my bookings
So that I can manage or cancel them
```

**Acceptance Criteria:**
1. แสดงรายการจองของตนเอง
2. แยกเป็น upcoming และ past
3. สามารถยกเลิกการจองในอนาคต
4. ยกเลิกได้ก่อนเวลาเริ่ม 1 ชั่วโมง
5. ยืนยันก่อนยกเลิก

**Technical Details:**
```javascript
// Get My Bookings
GET /api/bookings/my
Headers: { Authorization: "Bearer jwt-token" }

// Cancel Booking
DELETE /api/bookings/:id
Headers: { Authorization: "Bearer jwt-token" }
```

---

### FR-06: Admin Room Management ✅

**Description:** Admin จัดการข้อมูลห้อง

**User Story:**
```
As an admin
I want to manage room information
So that I can add, edit, or remove rooms
```

**Acceptance Criteria:**
1. เฉพาะ admin เข้าถึงได้
2. CRUD operations: Create, Read, Update, Delete
3. ข้อมูลห้อง: ชื่อ, ขนาด, ชั้น, status
4. ไม่ให้ลบห้องที่มีการจอง
5. แสดงรายการห้องแบบ table

---

## 4. Technical Requirements

### 4.1 Performance Requirements
- หน้าเว็บโหลดภายใน 3 วินาที
- API response ภายใน 1 วินาที
- รองรับผู้ใช้พร้อมกัน 50 คน

### 4.2 Security Requirements
- เข้ารหัส password ด้วย bcrypt
- ใช้ JWT สำหรับ authentication
- Validate input ทุกจุด
- ป้องกัน SQL injection

### 4.3 Compatibility
- Chrome, Firefox, Safari ล่าสุด
- Responsive design (mobile-friendly)
- Node.js 16+ 
- PostgreSQL 12+

---

## 5. Database Design

### 5.1 ER Diagram (Simplified)

```
┌─────────────┐      ┌─────────────┐      ┌─────────────┐
│   users     │      │  bookings   │      │   rooms     │
├─────────────┤      ├─────────────┤      ├─────────────┤
│ id (PK)     │ 1──* │ id (PK)     │ *──1 │ id (PK)     │
│ email       │      │ user_id(FK) │      │ name        │
│ password    │      │ room_id(FK) │      │ capacity    │
│ name        │      │ date        │      │ floor       │
│ role        │      │ start_time  │      │ is_active   │
│ created_at  │      │ end_time    │      │ created_at  │
└─────────────┘      │ title       │      └─────────────┘
                     │ status      │
                     │ created_at  │
                     └─────────────┘
```

### 5.2 Table Schemas

**users table:**
```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    email VARCHAR(255) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    name VARCHAR(100) NOT NULL,
    role VARCHAR(20) DEFAULT 'user',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

**rooms table:**
```sql
CREATE TABLE rooms (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    capacity INTEGER NOT NULL,
    floor INTEGER,
    is_active BOOLEAN DEFAULT true,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

**bookings table:**
```sql
CREATE TABLE bookings (
    id SERIAL PRIMARY KEY,
    user_id INTEGER REFERENCES users(id),
    room_id INTEGER REFERENCES rooms(id),
    booking_date DATE NOT NULL,
    start_time TIME NOT NULL,
    end_time TIME NOT NULL,
    title VARCHAR(255) NOT NULL,
    status VARCHAR(20) DEFAULT 'confirmed',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Index for faster queries
CREATE INDEX idx_bookings_date ON bookings(booking_date);
CREATE INDEX idx_bookings_room ON bookings(room_id);
```

---

## 6. API Endpoints

### 6.1 Authentication APIs

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | /api/auth/register | สมัครสมาชิก | No |
| POST | /api/auth/login | เข้าสู่ระบบ | No |
| GET | /api/auth/me | ดูข้อมูลตนเอง | Yes |

### 6.2 Room APIs

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | /api/rooms | ดูรายการห้อง | Yes |
| GET | /api/rooms/:id | ดูรายละเอียดห้อง | Yes |
| POST | /api/rooms | เพิ่มห้อง (Admin) | Admin |
| PUT | /api/rooms/:id | แก้ไขห้อง (Admin) | Admin |
| DELETE | /api/rooms/:id | ลบห้อง (Admin) | Admin |

### 6.3 Booking APIs

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | /api/bookings | ดูการจองทั้งหมด | Admin |
| GET | /api/bookings/my | ดูการจองของตนเอง | Yes |
| POST | /api/bookings | จองห้อง | Yes |
| DELETE | /api/bookings/:id | ยกเลิกการจอง | Yes |

### 6.4 Example API Implementation

**Backend (Express.js):**
```javascript
// routes/auth.js
const express = require('express');
const bcrypt = require('bcrypt');
const jwt = require('jsonwebtoken');
const router = express.Router();

// Register endpoint
router.post('/register', async (req, res) => {
    try {
        const { email, password, name } = req.body;
        
        // Check if user exists
        const existingUser = await db.query(
            'SELECT id FROM users WHERE email = $1',
            [email]
        );
        
        if (existingUser.rows.length > 0) {
            return res.status(400).json({
                success: false,
                message: 'Email already registered'
            });
        }
        
        // Hash password
        const hashedPassword = await bcrypt.hash(password, 10);
        
        // Insert user
        const result = await db.query(
            'INSERT INTO users (email, password, name) VALUES ($1, $2, $3) RETURNING id',
            [email, hashedPassword, name]
        );
        
        res.json({
            success: true,
            message: 'Registration successful'
        });
        
    } catch (error) {
        res.status(500).json({
            success: false,
            message: 'Server error'
        });
    }
});
```

**Frontend (React.js):**
```javascript
// components/Register.jsx
import React, { useState } from 'react';
import axios from 'axios';
import { useNavigate } from 'react-router-dom';

function Register() {
    const [formData, setFormData] = useState({
        email: '',
        password: '',
        name: ''
    });
    const navigate = useNavigate();
    
    const handleSubmit = async (e) => {
        e.preventDefault();
        try {
            const response = await axios.post(
                'http://localhost:5000/api/auth/register',
                formData
            );
            
            if (response.data.success) {
                alert('Registration successful!');
                navigate('/login');
            }
        } catch (error) {
            alert(error.response?.data?.message || 'Registration failed');
        }
    };
    
    return (
        <div className="container mt-5">
            <h2>Register</h2>
            <form onSubmit={handleSubmit}>
                <div className="mb-3">
                    <label>Email</label>
                    <input
                        type="email"
                        className="form-control"
                        value={formData.email}
                        onChange={(e) => setFormData({
                            ...formData,
                            email: e.target.value
                        })}
                        required
                    />
                </div>
                {/* More fields... */}
                <button type="submit" className="btn btn-primary">
                    Register
                </button>
            </form>
        </div>
    );
}
```

---

## 7. UI/UX Design

### 7.1 Page Structure

```
┌─────────────────────────────────────────┐
│            Navigation Bar               │
│  Logo  |  Rooms  |  My Bookings | User │
├─────────────────────────────────────────┤
│                                         │
│            Main Content Area            │
│                                         │
│  ┌─────────────┐  ┌─────────────┐      │
│  │  Room Card  │  │  Room Card  │      │
│  │             │  │             │      │
│  │  [Book Now] │  │  [Book Now] │      │
│  └─────────────┘  └─────────────┘      │
│                                         │
└─────────────────────────────────────────┘
```

### 7.2 Key Pages

1. **Login/Register Page**
   - Simple form with validation
   - Link to switch between login/register

2. **Room List Page**
   - Grid or list view of rooms
   - Filter by date/time
   - Status indicator (green/red)

3. **Booking Form Modal**
   - Date picker
   - Time selection (dropdown)
   - Title input
   - Confirm/Cancel buttons

4. **My Bookings Page**
   - Table view of bookings
   - Upcoming and past tabs
   - Cancel button for future bookings

5. **Admin Dashboard**
   - Room management table
   - Add/Edit/Delete buttons
   - Simple statistics

### 7.3 Design Guidelines

- ใช้ Bootstrap 5 หรือ Material-UI
- สีหลัก: Blue (#0066CC)
- สีรอง: Gray (#6C757D)
- Font: Prompt (Thai), Roboto (English)
- Mobile-first approach

---

## 8. Development Plan (4 Weeks)

### Week 1: Setup & Backend Basics
**Day 1-2: Project Setup**
- Setup Git repository
- Initialize Node.js project
- Setup PostgreSQL database
- Create folder structure

**Day 3-5: Backend Foundation**
- Setup Express server
- Create database schema
- Implement authentication (register/login)
- Test with Postman

**Day 6-7: Room & Booking APIs**
- CRUD APIs for rooms
- Booking creation API
- Conflict checking logic

### Week 2: Frontend Basics
**Day 8-10: React Setup & Auth**
- Create React app
- Setup routing
- Build login/register pages
- Implement JWT storage

**Day 11-14: Core Pages**
- Room listing page
- Booking form component
- My bookings page
- Basic styling with Bootstrap

### Week 3: Integration & Features
**Day 15-17: Connect Frontend & Backend**
- Integrate all APIs
- Handle errors properly
- Add loading states

**Day 18-21: Admin Features**
- Admin authentication
- Room management page
- Protected routes

### Week 4: Polish & Deploy
**Day 22-24: Testing & Bug Fixes**
- Test all features
- Fix bugs
- Improve UI/UX

**Day 25-27: Documentation & Deployment**
- Write user manual
- Deploy to Heroku/Render
- Prepare presentation

**Day 28-30: Buffer & Presentation**
- Final testing
- Prepare demo
- Project submission

---

## 9. Testing Guide

### 9.1 Manual Testing Checklist

**Authentication:**
- [ ] Register with new email
- [ ] Register with existing email (should fail)
- [ ] Login with correct credentials
- [ ] Login with wrong password
- [ ] Access protected route without login

**Room Booking:**
- [ ] View all rooms
- [ ] Filter rooms by date/time
- [ ] Book available room
- [ ] Try double booking (should fail)
- [ ] Book for invalid time (past, too long)

**Booking Management:**
- [ ] View my bookings
- [ ] Cancel future booking
- [ ] Cannot cancel past booking
- [ ] Cannot cancel within 1 hour

**Admin Features:**
- [ ] Login as admin
- [ ] Add new room
- [ ] Edit room details
- [ ] Delete room without bookings
- [ ] Cannot delete room with bookings

### 9.2 Sample Test Data

```sql
-- Insert test users
INSERT INTO users (email, password, name, role) VALUES
('user@test.com', '$2b$10$...', 'Test User', 'user'),
('admin@test.com', '$2b$10$...', 'Test Admin', 'admin');

-- Insert test rooms
INSERT INTO rooms (name, capacity, floor) VALUES
('Meeting Room A', 10, 3),
('Meeting Room B', 20, 3),
('Conference Room', 50, 5);

-- Insert test bookings
INSERT INTO bookings (user_id, room_id, booking_date, start_time, end_time, title) VALUES
(1, 1, '2024-03-15', '10:00', '12:00', 'Team Meeting'),
(1, 2, '2024-03-16', '14:00', '16:00', 'Client Presentation');
```

---

## 10. Learning Resources

### 10.1 Recommended Tutorials

**React.js:**
- [React Official Tutorial](https://react.dev/learn)
- [React Hooks Explained](https://www.youtube.com/watch?v=dpw9EHDh2bM)
- [React Router v6](https://reactrouter.com/en/main/start/tutorial)

**Node.js & Express:**
- [Express.js Guide](https://expressjs.com/en/guide/routing.html)
- [JWT Authentication Tutorial](https://www.youtube.com/watch?v=mbsmsi7l3r4)
- [REST API Best Practices](https://stackoverflow.blog/2020/03/02/best-practices-for-rest-api-design/)

**PostgreSQL:**
- [PostgreSQL Tutorial](https://www.postgresqltutorial.com/)
- [Node-Postgres Documentation](https://node-postgres.com/)

### 10.2 Common Issues & Solutions

**Issue 1: CORS Error**
```javascript
// Add to Express server
const cors = require('cors');
app.use(cors());
```

**Issue 2: JWT Token Expiry**
```javascript
// Check token before API calls
const token = localStorage.getItem('token');
if (!token) {
    // Redirect to login
}
```

**Issue 3: Date/Time Handling**
```javascript
// Use consistent format
const bookingDateTime = `${date}T${startTime}:00`;
const booking = new Date(bookingDateTime);
```

### 10.3 Code Structure

**Backend Structure:**
```
backend/
├── config/
│   └── db.js
├── middleware/
│   └── auth.js
├── routes/
│   ├── auth.js
│   ├── rooms.js
│   └── bookings.js
├── .env
├── server.js
└── package.json
```

**Frontend Structure:**
```
frontend/
├── public/
├── src/
│   ├── components/
│   │   ├── Login.jsx
│   │   ├── RoomList.jsx
│   │   └── BookingForm.jsx
│   ├── services/
│   │   └── api.js
│   ├── App.js
│   └── index.js
└── package.json
```

---

## Project Evaluation Criteria

### สำหรับอาจารย์ผู้สอน - เกณฑ์การให้คะแนน (100 คะแนน)

**1. Functionality (40%)**
- Authentication works correctly (10%)
- Room booking without conflicts (15%)
- Booking management features (10%)
- Admin features (5%)

**2. Code Quality (30%)**
- Clean, readable code (10%)
- Proper error handling (10%)
- Security implementation (10%)

**3. User Interface (20%)**
- Responsive design (10%)
- User-friendly interface (10%)

**4. Documentation (10%)**
- Code comments (5%)
- User manual (5%)

---

## Conclusion

MeetingRoom Lite เป็นโปรเจคที่เหมาะสมสำหรับนักศึกษาปี 2 ด้วยขอบเขตที่ชัดเจน สามารถทำเสร็จได้ใน 1 เดือน และครอบคลุมทักษะ Full-Stack Development ที่สำคัญ

**Key Success Factors:**
1. เริ่มจาก features พื้นฐานก่อน
2. ทดสอบ API ด้วย Postman ก่อน integrate
3. ใช้ Bootstrap/Material-UI ช่วยด้าน UI
4. Focus on functionality มากกว่า design
5. ขอความช่วยเหลือเมื่อติดปัญหา

**Good luck with your project! 🚀**ทำำ