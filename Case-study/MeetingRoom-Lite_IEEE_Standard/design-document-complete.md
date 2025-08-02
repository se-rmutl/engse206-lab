# Software Design Document (SDD)
## ระบบจองห้องประชุม MeetingRoom Lite

**Document ID:** SDD-MRL-001  
**Version:** 1.0  
**วันที่:** มีนาคม 2567  
**สถานะ:** Final  
**อ้างอิงจาก:** SRS-MRL-001 v1.0  

---

## Revision History

| Version | วันที่ | ผู้แก้ไข | รายละเอียด |
|---------|--------|----------|-------------|
| 0.1 | 11/03/2567 | ทีมพัฒนา | Architecture design |
| 0.5 | 15/03/2567 | ทีมพัฒนา | Database design |
| 0.8 | 18/03/2567 | ทีมพัฒนา | API design |
| 1.0 | 20/03/2567 | ทีมพัฒนา | เอกสารฉบับสมบูรณ์ |

---

## สารบัญ

1. [บทนำ (Introduction)](#1-บทนำ-introduction)
2. [สถาปัตยกรรมระบบ (System Architecture)](#2-สถาปัตยกรรมระบบ-system-architecture)
3. [การออกแบบฐานข้อมูล (Database Design)](#3-การออกแบบฐานข้อมูล-database-design)
4. [การออกแบบ API (API Design)](#4-การออกแบบ-api-api-design)
5. [การออกแบบ User Interface (UI Design)](#5-การออกแบบ-user-interface-ui-design)
6. [การออกแบบความปลอดภัย (Security Design)](#6-การออกแบบความปลอดภัย-security-design)

---

## 1. บทนำ (Introduction)

### 1.1 วัตถุประสงค์
เอกสารนี้อธิบายการออกแบบทางเทคนิคของระบบ MeetingRoom Lite โดยแปลงความต้องการจาก SRS เป็นแบบแผนการพัฒนาที่ชัดเจน

### 1.2 ขอบเขต
เอกสารครอบคลุม:
- System architecture
- Database schema
- API endpoints
- UI layouts
- Security mechanisms

### 1.3 Technology Stack
- **Frontend:** React.js, Bootstrap 5
- **Backend:** Node.js, Express.js
- **Database:** PostgreSQL
- **Authentication:** JWT

---

## 2. สถาปัตยกรรมระบบ (System Architecture)

### 2.1 Overview Architecture

ระบบใช้สถาปัตยกรรมแบบ **3-Tier Architecture**

```
┌─────────────────────────────────────┐
│     Presentation Layer (React)      │
│  - Components                       │
│  - State Management                 │
│  - Routing                         │
└──────────────┬──────────────────────┘
               │ HTTP/JSON
               ▼
┌─────────────────────────────────────┐
│    Business Logic Layer (Node.js)   │
│  - Controllers                      │
│  - Services                         │
│  - Middleware                       │
└──────────────┬──────────────────────┘
               │ SQL
               ▼
┌─────────────────────────────────────┐
│      Data Layer (PostgreSQL)        │
│  - Tables                           │
│  - Indexes                          │
│  - Constraints                      │
└─────────────────────────────────────┘
```

### 2.2 Component Diagram

```
Frontend Components
├── Authentication
│   ├── LoginForm
│   └── RegisterForm
├── Rooms
│   ├── RoomList
│   ├── RoomCard
│   └── RoomFilter
├── Bookings
│   ├── BookingForm
│   ├── BookingList
│   └── BookingCard
└── Common
    ├── Header
    ├── Footer
    └── Loading

Backend Components
├── Routes
│   ├── authRoutes
│   ├── roomRoutes
│   └── bookingRoutes
├── Controllers
│   ├── authController
│   ├── roomController
│   └── bookingController
├── Services
│   ├── authService
│   ├── roomService
│   └── bookingService
└── Middleware
    ├── authMiddleware
    └── errorMiddleware
```

### 2.3 Deployment Architecture

```
┌─────────────────┐
│   Web Browser   │
└────────┬────────┘
         │ HTTPS
         ▼
┌─────────────────┐
│   Web Server    │
│   (Node.js)     │
└────────┬────────┘
         │ SQL
         ▼
┌─────────────────┐
│   PostgreSQL    │
│    Database     │
└─────────────────┘
```

---

## 3. การออกแบบฐานข้อมูล (Database Design)

### 3.1 Entity Relationship Diagram

```
┌──────────────┐        ┌──────────────┐        ┌──────────────┐
│    users     │ 1    * │   bookings   │ *    1 │    rooms     │
├──────────────┤        ├──────────────┤        ├──────────────┤
│ PK: id       ├────────┤ PK: id       ├────────┤ PK: id       │
│ email        │        │ FK: user_id  │        │ name         │
│ password     │        │ FK: room_id  │        │ capacity     │
│ name         │        │ booking_date │        │ floor        │
│ role         │        │ start_time   │        │ is_active    │
│ created_at   │        │ end_time     │        │ created_at   │
└──────────────┘        │ title        │        └──────────────┘
                        │ status       │
                        │ created_at   │
                        └──────────────┘
```

### 3.2 Table Schemas

#### 3.2.1 users table
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

#### 3.2.2 rooms table
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

#### 3.2.3 bookings table
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
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    CONSTRAINT valid_time CHECK (end_time > start_time)
);
```

### 3.3 Indexes
```sql
CREATE INDEX idx_bookings_date ON bookings(booking_date);
CREATE INDEX idx_bookings_room ON bookings(room_id);
CREATE INDEX idx_bookings_user ON bookings(user_id);
CREATE UNIQUE INDEX idx_no_double_booking 
    ON bookings(room_id, booking_date, start_time, end_time)
    WHERE status = 'confirmed';
```

---

## 4. การออกแบบ API (API Design)

### 4.1 API Overview

**Base URL:** `/api/v1`  
**Format:** JSON  
**Authentication:** JWT Bearer Token

### 4.2 Authentication Endpoints

#### POST /api/v1/auth/register
สร้างบัญชีผู้ใช้ใหม่

**Request:**
```json
{
    "email": "user@example.com",
    "password": "password123",
    "name": "ชื่อผู้ใช้"
}
```

**Response (201):**
```json
{
    "success": true,
    "message": "ลงทะเบียนสำเร็จ",
    "data": {
        "id": 1,
        "email": "user@example.com",
        "name": "ชื่อผู้ใช้"
    }
}
```

#### POST /api/v1/auth/login
เข้าสู่ระบบ

**Request:**
```json
{
    "email": "user@example.com",
    "password": "password123"
}
```

**Response (200):**
```json
{
    "success": true,
    "token": "eyJhbGciOiJIUzI1NiIs...",
    "user": {
        "id": 1,
        "email": "user@example.com",
        "name": "ชื่อผู้ใช้",
        "role": "user"
    }
}
```

### 4.3 Room Endpoints

#### GET /api/v1/rooms
ดูรายการห้องทั้งหมด

**Headers:** `Authorization: Bearer {token}`

**Query Parameters:**
- `date` - วันที่ (YYYY-MM-DD)
- `start_time` - เวลาเริ่ม (HH:MM)
- `end_time` - เวลาสิ้นสุด (HH:MM)

**Response (200):**
```json
{
    "success": true,
    "data": [
        {
            "id": 1,
            "name": "ห้องประชุม A",
            "capacity": 20,
            "floor": 3,
            "is_available": true
        }
    ]
}
```

#### POST /api/v1/rooms (Admin only)
เพิ่มห้องใหม่

**Request:**
```json
{
    "name": "ห้องประชุม B",
    "capacity": 15,
    "floor": 4
}
```

### 4.4 Booking Endpoints

#### POST /api/v1/bookings
สร้างการจองใหม่

**Request:**
```json
{
    "room_id": 1,
    "booking_date": "2024-03-25",
    "start_time": "09:00",
    "end_time": "11:00",
    "title": "Team Meeting"
}
```

**Response (201):**
```json
{
    "success": true,
    "message": "จองห้องสำเร็จ",
    "data": {
        "id": 123,
        "room_name": "ห้องประชุม A",
        "booking_date": "2024-03-25",
        "start_time": "09:00:00",
        "end_time": "11:00:00"
    }
}
```

#### GET /api/v1/bookings/my
ดูการจองของตนเอง

**Response (200):**
```json
{
    "success": true,
    "data": {
        "upcoming": [...],
        "past": [...]
    }
}
```

#### DELETE /api/v1/bookings/:id
ยกเลิกการจอง

**Response (200):**
```json
{
    "success": true,
    "message": "ยกเลิกการจองสำเร็จ"
}
```

### 4.5 Error Responses

```json
{
    "success": false,
    "error": {
        "code": "ERROR_CODE",
        "message": "คำอธิบายข้อผิดพลาด"
    }
}
```

Error Codes:
- `VALIDATION_ERROR` - ข้อมูลไม่ถูกต้อง (400)
- `UNAUTHORIZED` - ไม่ได้เข้าสู่ระบบ (401)
- `FORBIDDEN` - ไม่มีสิทธิ์ (403)
- `NOT_FOUND` - ไม่พบข้อมูล (404)
- `CONFLICT` - ข้อมูลซ้ำซ้อน (409)

---

## 5. การออกแบบ User Interface (UI Design)

### 5.1 UI Structure

```
┌────────────────────────────────────┐
│           Navigation Bar           │
│  Logo | Rooms | My Bookings | User│
├────────────────────────────────────┤
│                                    │
│         Main Content Area          │
│                                    │
│  ┌──────────┐  ┌──────────┐      │
│  │Room Card │  │Room Card │      │
│  └──────────┘  └──────────┘      │
│                                    │
└────────────────────────────────────┘
```

### 5.2 Page Layouts

#### 5.2.1 Login Page
```
┌────────────────────────────────────┐
│         MeetingRoom Lite           │
├────────────────────────────────────┤
│                                    │
│      ┌──────────────────┐          │
│      │   Login Form     │          │
│      │ Email:  [______] │          │
│      │ Pass:   [______] │          │
│      │ [Login] [Register]          │
│      └──────────────────┘          │
│                                    │
└────────────────────────────────────┘
```

#### 5.2.2 Room List Page
```
┌────────────────────────────────────┐
│         [Date] [Time Filter]       │
├────────────────────────────────────┤
│ ┌─────────┐ ┌─────────┐ ┌────────┐│
│ │ Room A  │ │ Room B  │ │ Room C ││
│ │ 20 คน   │ │ 15 คน   │ │ 30 คน  ││
│ │ ชั้น 3   │ │ ชั้น 4   │ │ ชั้น 5  ││
│ │ [จอง]   │ │ [จอง]   │ │ [ไม่ว่าง]││
│ └─────────┘ └─────────┘ └────────┘│
└────────────────────────────────────┘
```

#### 5.2.3 Booking Form Modal
```
┌────────────────────────────────────┐
│        จองห้องประชุม A              │
├────────────────────────────────────┤
│ วันที่:     [___________]          │
│ เวลาเริ่ม:   [___________]          │
│ เวลาสิ้นสุด: [___________]          │
│ หัวข้อ:     [___________]          │
│                                    │
│        [ยกเลิก] [ยืนยัน]            │
└────────────────────────────────────┘
```

### 5.3 UI Components

#### Room Card Component
- แสดงชื่อห้อง
- แสดงความจุและชั้น
- ปุ่มจองห้อง
- สถานะห้อง (สีเขียว=ว่าง, สีแดง=ไม่ว่าง)

#### Booking List Component
- แสดงวันที่และเวลา
- แสดงชื่อห้อง
- ปุ่มยกเลิก (สำหรับการจองในอนาคต)
- แยกส่วน upcoming และ past

### 5.4 Color Scheme
- Primary: #0066CC (น้ำเงิน)
- Success: #28A745 (เขียว)
- Danger: #DC3545 (แดง)
- Text: #333333
- Background: #F8F9FA

---

## 6. การออกแบบความปลอดภัย (Security Design)

### 6.1 Authentication
- ใช้ JWT สำหรับ authentication
- Token expire time: 24 ชั่วโมง
- Store token ใน localStorage

### 6.2 Password Security
- Hash password ด้วย bcrypt
- Salt rounds: 10
- Minimum length: 6 characters

### 6.3 API Security
- ใช้ HTTPS สำหรับทุก requests
- Validate input ทุกจุด
- Sanitize data ก่อนเก็บใน database

### 6.4 Authorization
- แยก role: user และ admin
- Check permissions ใน middleware
- Admin routes ต้องตรวจสอบ role

### 6.5 Session Management
- Auto logout หลังไม่มีกิจกรรม 30 นาที
- Clear sensitive data เมื่อ logout
- Regenerate token เมื่อ refresh

---

**หมายเหตุ:** เอกสารนี้เป็นแนวทางการออกแบบที่อาจมีการปรับเปลี่ยนตามความเหมาะสมในระหว่างการพัฒนา