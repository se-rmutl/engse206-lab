# Software Design Document (SDD)
## ระบบติดตาม Carbon Footprint - EcoTrack

**Document ID:** SDD-ECO-001  
**Version:** 1.0  
**วันที่:** มีนาคม 2567  
**สถานะ:** Final  
**อ้างอิงจาก:** SRS-ECO-001 v1.0  

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
เอกสารนี้อธิบายการออกแบบทางเทคนิคของระบบ EcoTrack โดยแปลงความต้องการจาก SRS เป็นแบบแผนการพัฒนาที่ชัดเจน รองรับการทำงานของ mobile app และ web application

### 1.2 ขอบเขต
เอกสารครอบคลุม:
- System architecture และ deployment
- Database schema และ relationships
- API endpoints และ protocols
- UI/UX design patterns
- Security mechanisms และ data protection

### 1.3 Technology Stack
- **Frontend Web:** React.js, TypeScript, Material-UI
- **Frontend Mobile:** React Native, Expo
- **Backend:** Node.js, Express.js, TypeScript
- **Database:** PostgreSQL, Redis (cache)
- **Authentication:** JWT, OAuth 2.0
- **Cloud:** AWS (EC2, S3, RDS)
- **Monitoring:** New Relic, CloudWatch

---

## 2. สถาปัตยกรรมระบบ (System Architecture)

### 2.1 Overview Architecture

ระบบใช้สถาปัตยกรรมแบบ **Microservices Architecture** with **API Gateway**

```
┌─────────────────────────────────────────────────────┐
│            Presentation Layer                        │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐ │
│  │  Mobile App │  │   Web App   │  │ Admin Panel │ │
│  │(React Native)│ │  (React.js) │  │  (React.js) │ │
│  └──────┬──────┘  └──────┬──────┘  └──────┬──────┘ │
└─────────┼─────────────────┼────────────────┼────────┘
          │                 │                 │
          └─────────────────┼─────────────────┘
                           │ HTTPS/REST
                           ▼
        ┌──────────────────────────────────────┐
        │          API Gateway (Kong)          │
        │  - Authentication                    │
        │  - Rate Limiting                     │
        │  - Load Balancing                   │
        └───────────┬──────────────────────────┘
                    │
    ┌───────────────┼───────────────────────────┐
    │               │                           │
    ▼               ▼                           ▼
┌─────────┐  ┌─────────────┐  ┌──────────────────┐
│  Auth   │  │   Carbon    │  │   Gamification   │
│ Service │  │   Service   │  │     Service      │
└────┬────┘  └──────┬──────┘  └────────┬─────────┘
     │              │                   │
     └──────────────┼───────────────────┘
                    │
                    ▼
        ┌──────────────────────────────┐
        │      Data Layer              │
        │  ┌──────────┐  ┌──────────┐ │
        │  │PostgreSQL│  │  Redis   │ │
        │  └──────────┘  └──────────┘ │
        └──────────────────────────────┘
```

### 2.2 Component Diagram

```
Frontend Components
├── Mobile App (React Native)
│   ├── Authentication Module
│   │   ├── LoginScreen
│   │   └── OnboardingFlow
│   ├── Activity Recording
│   │   ├── TravelTracker
│   │   ├── EnergyInput
│   │   └── WasteManager
│   ├── Dashboard Module
│   │   ├── CarbonSummary
│   │   ├── Charts
│   │   └── QuickStats
│   └── Gamification Module
│       ├── PointsDisplay
│       ├── BadgeGallery
│       └── Leaderboard
│
├── Web Application (React)
│   ├── Same structure as Mobile
│   └── Additional Admin Features
│
Backend Services
├── Auth Service (Port 3001)
│   ├── SSO Integration
│   ├── JWT Management
│   └── User Profile
│
├── Carbon Service (Port 3002)
│   ├── Activity Recording
│   ├── Carbon Calculator
│   ├── Report Generator
│   └── Data Analytics
│
├── Gamification Service (Port 3003)
│   ├── Points Engine
│   ├── Badge Manager
│   ├── Leaderboard
│   └── Achievements
│
└── Notification Service (Port 3004)
    ├── Push Notifications
    ├── Email Service
    └── In-app Messages
```

### 2.3 Deployment Architecture

```
┌──────────────────────────────────────────────┐
│                   AWS Cloud                   │
│                                               │
│  ┌─────────────────────────────────────────┐ │
│  │          CloudFront (CDN)               │ │
│  └─────────────────────────────────────────┘ │
│                      │                        │
│  ┌─────────────────────────────────────────┐ │
│  │    Application Load Balancer (ALB)      │ │
│  └─────────────────────────────────────────┘ │
│                      │                        │
│  ┌──────────────────┼──────────────────────┐ │
│  │     ECS Cluster (Auto-scaling)          │ │
│  │  ┌────────┐  ┌────────┐  ┌────────┐   │ │
│  │  │Service │  │Service │  │Service │   │ │
│  │  │Task 1  │  │Task 2  │  │Task 3  │   │ │
│  │  └────────┘  └────────┘  └────────┘   │ │
│  └──────────────────────────────────────────┘ │
│                      │                        │
│  ┌──────────────────┼──────────────────────┐ │
│  │  RDS PostgreSQL  │  ElastiCache Redis   │ │
│  │  (Multi-AZ)      │                      │ │
│  └──────────────────────────────────────────┘ │
│                                               │
│  ┌─────────────────────────────────────────┐ │
│  │         S3 Bucket (Static Assets)       │ │
│  └─────────────────────────────────────────┘ │
└──────────────────────────────────────────────┘
```

---

## 3. การออกแบบฐานข้อมูล (Database Design)

### 3.1 Entity Relationship Diagram

```
┌─────────────┐      ┌─────────────┐      ┌─────────────┐
│    users    │ 1  * │  activities │ *  1 │ activity    │
├─────────────┤      ├─────────────┤      │    types    │
│ PK: id      ├──────┤ PK: id      ├──────┤ PK: id      │
│ email       │      │ FK: user_id │      │ name        │
│ name        │      │ FK: type_id │      │ category    │
│ faculty     │      │ value       │      │ unit        │
│ role        │      │ co2e        │      │ factor      │
│ points      │      │ date        │      └─────────────┘
│ level       │      │ created_at  │
│ created_at  │      └─────────────┘
└─────────────┘             │
       │                    │
       │ 1                  │ *
       │                    ▼
       │             ┌─────────────┐
       │      *      │   rewards   │
       ├─────────────┤ PK: id      │
       │             │ FK: user_id │
       │             │ FK: badge_id│
       │             │ earned_at   │
       │             └─────────────┘
       │                    │ 1
       │ 1                  ▼
       │             ┌─────────────┐
       │      *      │   badges    │
       └─────────────┤ PK: id      │
                     │ name        │
                     │ description │
                     │ points      │
                     │ icon_url    │
                     └─────────────┘
                     
┌─────────────┐      ┌─────────────┐
│    goals    │ 1  * │ goal_progress│
├─────────────┤      ├─────────────┤
│ PK: id      ├──────┤ PK: id      │
│ FK: user_id │      │ FK: goal_id │
│ target      │      │ current     │
│ period      │      │ date        │
│ status      │      └─────────────┘
│ created_at  │
└─────────────┘
```

### 3.2 Table Schemas

#### 3.2.1 users table
```sql
CREATE TABLE users (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    email VARCHAR(255) UNIQUE NOT NULL,
    name VARCHAR(100) NOT NULL,
    student_id VARCHAR(20),
    faculty VARCHAR(100),
    department VARCHAR(100),
    role VARCHAR(20) DEFAULT 'student',
    points INTEGER DEFAULT 0,
    level INTEGER DEFAULT 1,
    streak_days INTEGER DEFAULT 0,
    last_activity_date DATE,
    preferences JSONB,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE INDEX idx_users_email ON users(email);
CREATE INDEX idx_users_faculty ON users(faculty);
CREATE INDEX idx_users_points ON users(points DESC);
```

#### 3.2.2 activity_types table
```sql
CREATE TABLE activity_types (
    id SERIAL PRIMARY KEY,
    category VARCHAR(50) NOT NULL, -- travel, energy, waste
    name VARCHAR(100) NOT NULL,
    unit VARCHAR(20) NOT NULL, -- km, kwh, kg
    emission_factor DECIMAL(10,4) NOT NULL,
    points_per_unit INTEGER DEFAULT 1,
    icon VARCHAR(50),
    is_eco_friendly BOOLEAN DEFAULT false,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Seed data
INSERT INTO activity_types (category, name, unit, emission_factor, points_per_unit, is_eco_friendly) VALUES
('travel', 'การเดิน', 'km', 0.0000, 10, true),
('travel', 'จักรยาน', 'km', 0.0000, 8, true),
('travel', 'รถไฟฟ้า', 'km', 0.0200, 5, true),
('travel', 'รถเมล์', 'km', 0.0400, 4, true),
('travel', 'มอเตอร์ไซค์', 'km', 0.1100, 2, false),
('travel', 'รถยนต์', 'km', 0.2100, 1, false),
('energy', 'ไฟฟ้า', 'kwh', 0.5610, 3, false),
('energy', 'น้ำประปา', 'unit', 0.2720, 2, false),
('waste', 'ขยะทั่วไป', 'kg', 2.8600, -2, false),
('waste', 'รีไซเคิล', 'kg', -1.0200, 5, true),
('waste', 'ขยะอินทรีย์', 'kg', 0.4700, 3, true);
```

#### 3.2.3 activities table
```sql
CREATE TABLE activities (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    user_id UUID REFERENCES users(id) ON DELETE CASCADE,
    type_id INTEGER REFERENCES activity_types(id),
    activity_date DATE NOT NULL,
    value DECIMAL(10,2) NOT NULL,
    co2e_calculated DECIMAL(10,4),
    points_earned INTEGER,
    purpose VARCHAR(50), -- work, study, personal
    notes TEXT,
    image_url VARCHAR(500),
    location JSONB, -- {lat, lng, address}
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE INDEX idx_activities_user ON activities(user_id);
CREATE INDEX idx_activities_date ON activities(activity_date DESC);
CREATE INDEX idx_activities_type ON activities(type_id);
```

#### 3.2.4 badges table
```sql
CREATE TABLE badges (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    description TEXT,
    category VARCHAR(50), -- starter, travel, energy, waste, achievement
    criteria JSONB NOT NULL, -- conditions to earn
    points INTEGER DEFAULT 0,
    icon_url VARCHAR(500),
    tier INTEGER DEFAULT 1, -- 1=bronze, 2=silver, 3=gold
    is_active BOOLEAN DEFAULT true,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Sample badges
INSERT INTO badges (name, description, category, criteria, points, tier) VALUES
('Eco Starter', 'บันทึกกิจกรรม 7 วันติดต่อกัน', 'starter', 
 '{"type": "streak", "days": 7}', 50, 1),
('Green Commuter', 'ใช้ขนส่งสาธารณะ 20 ครั้ง', 'travel',
 '{"type": "count", "activity": "public_transport", "count": 20}', 100, 1),
('Energy Saver', 'ลดการใช้ไฟ 10%', 'energy',
 '{"type": "reduction", "category": "energy", "percent": 10}', 150, 2),
('Zero Hero', 'Zero carbon day 5 วัน', 'achievement',
 '{"type": "zero_carbon", "days": 5}', 200, 2),
('Carbon Champion', 'Top 10 ของคณะ', 'achievement',
 '{"type": "ranking", "position": 10}', 1000, 3);
```

#### 3.2.5 rewards table
```sql
CREATE TABLE rewards (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    user_id UUID REFERENCES users(id) ON DELETE CASCADE,
    badge_id INTEGER REFERENCES badges(id),
    earned_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    notified BOOLEAN DEFAULT false,
    UNIQUE(user_id, badge_id)
);

CREATE INDEX idx_rewards_user ON rewards(user_id);
```

#### 3.2.6 goals table
```sql
CREATE TABLE goals (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    user_id UUID REFERENCES users(id) ON DELETE CASCADE,
    title VARCHAR(200) NOT NULL,
    target_type VARCHAR(50), -- reduction_percent, total_co2e, activity_count
    target_value DECIMAL(10,2) NOT NULL,
    current_value DECIMAL(10,2) DEFAULT 0,
    period VARCHAR(20), -- daily, weekly, monthly
    start_date DATE NOT NULL,
    end_date DATE NOT NULL,
    status VARCHAR(20) DEFAULT 'active', -- active, completed, failed
    reminders BOOLEAN DEFAULT true,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE INDEX idx_goals_user ON goals(user_id);
CREATE INDEX idx_goals_status ON goals(status);
```

#### 3.2.7 notifications table
```sql
CREATE TABLE notifications (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    user_id UUID REFERENCES users(id) ON DELETE CASCADE,
    type VARCHAR(50), -- badge_earned, goal_reminder, tip, announcement
    title VARCHAR(200) NOT NULL,
    message TEXT,
    data JSONB,
    is_read BOOLEAN DEFAULT false,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE INDEX idx_notifications_user ON notifications(user_id, is_read);
```

### 3.3 Database Optimization

#### Indexes
```sql
-- Performance indexes
CREATE INDEX idx_activities_monthly ON activities(user_id, date_trunc('month', activity_date));
CREATE INDEX idx_leaderboard ON users(faculty, points DESC);
CREATE INDEX idx_user_streak ON users(last_activity_date, streak_days);

-- Materialized view for dashboard
CREATE MATERIALIZED VIEW user_monthly_summary AS
SELECT 
    user_id,
    date_trunc('month', activity_date) as month,
    SUM(co2e_calculated) as total_co2e,
    SUM(points_earned) as total_points,
    COUNT(*) as activity_count,
    AVG(co2e_calculated) as avg_co2e
FROM activities
GROUP BY user_id, date_trunc('month', activity_date);

CREATE INDEX idx_summary_user_month ON user_monthly_summary(user_id, month);
```

---

## 4. การออกแบบ API (API Design)

### 4.1 API Overview

**Base URL:** `https://api.ecotrack.university.ac.th/v1`  
**Format:** JSON  
**Authentication:** JWT Bearer Token  
**Rate Limiting:** 100 requests/minute per user

### 4.2 Authentication Endpoints

#### POST /auth/sso
SSO login through university system

**Request:**
```json
{
    "redirectUri": "https://ecotrack.university.ac.th/callback"
}
```

**Response (200):**
```json
{
    "success": true,
    "authUrl": "https://sso.university.ac.th/oauth/authorize?...",
    "state": "random_state_string"
}
```

#### POST /auth/callback
Handle SSO callback

**Request:**
```json
{
    "code": "auth_code_from_sso",
    "state": "random_state_string"
}
```

**Response (200):**
```json
{
    "success": true,
    "token": "eyJhbGciOiJIUzI1NiIs...",
    "refreshToken": "refresh_token_string",
    "user": {
        "id": "uuid",
        "email": "student@university.ac.th",
        "name": "นักศึกษา ตัวอย่าง",
        "faculty": "วิศวกรรมศาสตร์",
        "role": "student",
        "points": 150,
        "level": 2
    }
}
```

### 4.3 Activity Endpoints

#### GET /activities/types
Get all activity types

**Response (200):**
```json
{
    "success": true,
    "data": {
        "travel": [
            {
                "id": 1,
                "name": "การเดิน",
                "unit": "km",
                "emissionFactor": 0,
                "pointsPerUnit": 10,
                "isEcoFriendly": true
            }
        ],
        "energy": [...],
        "waste": [...]
    }
}
```

#### POST /activities
Record new activity

**Request:**
```json
{
    "typeId": 1,
    "value": 5.2,
    "date": "2024-03-25",
    "purpose": "study",
    "notes": "เดินไปเรียนที่คณะ",
    "location": {
        "lat": 18.7883,
        "lng": 98.9853
    }
}
```

**Response (201):**
```json
{
    "success": true,
    "data": {
        "id": "activity_uuid",
        "co2eCalculated": 0,
        "pointsEarned": 52,
        "message": "Great job! You saved 1.092 kg CO2e by walking",
        "newBadges": []
    }
}
```

#### GET /activities/my
Get user's activities

**Query Parameters:**
- `startDate` - YYYY-MM-DD
- `endDate` - YYYY-MM-DD
- `category` - travel|energy|waste
- `page` - page number
- `limit` - items per page (max 100)

**Response (200):**
```json
{
    "success": true,
    "data": {
        "activities": [...],
        "pagination": {
            "page": 1,
            "limit": 20,
            "total": 150,
            "pages": 8
        },
        "summary": {
            "totalCo2e": 45.67,
            "totalPoints": 234,
            "activityCount": 150
        }
    }
}
```

### 4.4 Dashboard Endpoints

#### GET /dashboard
Get dashboard data

**Response (200):**
```json
{
    "success": true,
    "data": {
        "today": {
            "co2e": 2.45,
            "points": 23,
            "activities": 3
        },
        "thisWeek": {
            "co2e": 15.67,
            "points": 156,
            "trend": -12.5
        },
        "thisMonth": {
            "co2e": 67.89,
            "points": 678,
            "breakdown": {
                "travel": 45.2,
                "energy": 18.4,
                "waste": 4.29
            }
        },
        "streak": 7,
        "rank": {
            "faculty": 15,
            "university": 234
        },
        "recentBadges": [
            {
                "id": 1,
                "name": "Eco Starter",
                "iconUrl": "/badges/eco-starter.png"
            }
        ]
    }
}
```

### 4.5 Gamification Endpoints

#### GET /gamification/leaderboard
Get leaderboard

**Query Parameters:**
- `scope` - faculty|university
- `period` - week|month|all

**Response (200):**
```json
{
    "success": true,
    "data": {
        "leaderboard": [
            {
                "rank": 1,
                "userId": "uuid",
                "name": "นักศึกษา A",
                "faculty": "วิศวกรรมศาสตร์",
                "points": 2345,
                "co2eSaved": 123.45
            }
        ],
        "userPosition": {
            "rank": 15,
            "points": 678,
            "percentile": 85
        }
    }
}
```

#### GET /gamification/badges
Get all badges and user progress

**Response (200):**
```json
{
    "success": true,
    "data": {
        "earned": [
            {
                "id": 1,
                "name": "Eco Starter",
                "description": "บันทึกกิจกรรม 7 วันติดต่อกัน",
                "earnedAt": "2024-03-20T10:00:00Z",
                "points": 50
            }
        ],
        "available": [
            {
                "id": 2,
                "name": "Green Commuter",
                "description": "ใช้ขนส่งสาธารณะ 20 ครั้ง",
                "progress": {
                    "current": 15,
                    "target": 20,
                    "percentage": 75
                }
            }
        ]
    }
}
```

### 4.6 Goals Endpoints

#### POST /goals
Create personal goal

**Request:**
```json
{
    "title": "ลด Carbon 20% ในเดือนนี้",
    "targetType": "reduction_percent",
    "targetValue": 20,
    "period": "monthly",
    "reminders": true
}
```

**Response (201):**
```json
{
    "success": true,
    "data": {
        "id": "goal_uuid",
        "title": "ลด Carbon 20% ในเดือนนี้",
        "startDate": "2024-03-01",
        "endDate": "2024-03-31",
        "currentValue": 0,
        "targetValue": 20,
        "status": "active"
    }
}
```

### 4.7 Reports Endpoints

#### GET /reports/monthly
Get monthly report

**Query Parameters:**
- `month` - YYYY-MM

**Response (200):**
```json
{
    "success": true,
    "data": {
        "period": "2024-03",
        "totalCo2e": 45.67,
        "comparison": {
            "previousMonth": 52.34,
            "change": -12.7,
            "universityAverage": 48.9
        },
        "breakdown": {
            "travel": {
                "co2e": 25.4,
                "percentage": 55.6,
                "activities": 45
            },
            "energy": {
                "co2e": 18.2,
                "percentage": 39.8,
                "activities": 2
            },
            "waste": {
                "co2e": 2.07,
                "percentage": 4.6,
                "activities": 8
            }
        },
        "topActivities": [
            {
                "type": "รถยนต์",
                "co2e": 20.5,
                "count": 15
            }
        ],
        "achievements": [
            "ลด Carbon 12.7% จากเดือนที่แล้ว",
            "ใช้รถไฟฟ้ามากขึ้น 30%"
        ]
    }
}
```

### 4.8 Admin Endpoints

#### GET /admin/statistics
Get university-wide statistics (Admin only)

**Response (200):**
```json
{
    "success": true,
    "data": {
        "totalUsers": 12543,
        "activeUsers": 8234,
        "totalCo2eSaved": 45678.9,
        "facultyBreakdown": [
            {
                "faculty": "วิศวกรรมศาสตร์",
                "users": 2345,
                "avgCo2e": 34.5,
                "topPerformers": 123
            }
        ],
        "trends": {
            "dailyActive": [...],
            "co2eReduction": [...],
            "popularActivities": [...]
        }
    }
}
```

### 4.9 Error Responses

```json
{
    "success": false,
    "error": {
        "code": "ERROR_CODE",
        "message": "Error description",
        "details": {}
    }
}
```

Error Codes:
- `UNAUTHORIZED` - ไม่ได้เข้าสู่ระบบ (401)
- `FORBIDDEN` - ไม่มีสิทธิ์ (403)
- `NOT_FOUND` - ไม่พบข้อมูล (404)
- `VALIDATION_ERROR` - ข้อมูลไม่ถูกต้อง (400)
- `RATE_LIMIT` - เกิน rate limit (429)
- `SERVER_ERROR` - ข้อผิดพลาดภายใน (500)

---

## 5. การออกแบบ User Interface (UI Design)

### 5.1 Design System

#### Color Palette
```
Primary Colors:
- Green Primary: #4CAF50
- Green Light: #8BC34A
- Green Dark: #388E3C

Secondary Colors:
- Blue: #2196F3
- Orange: #FF9800
- Red: #F44336

Neutral Colors:
- Text Primary: #212121
- Text Secondary: #757575
- Background: #FAFAFA
- White: #FFFFFF
```

#### Typography
```
Headings: Kanit (Thai), Inter (English)
- H1: 32px, Bold
- H2: 24px, Semi-bold
- H3: 20px, Medium

Body: Sarabun (Thai), Roboto (English)
- Body 1: 16px, Regular
- Body 2: 14px, Regular
- Caption: 12px, Regular
```

### 5.2 Mobile App Screens

#### 5.2.1 Home/Dashboard Screen
```
┌─────────────────────────────────┐
│     🌍 EcoTrack                 │
│     สวัสดี, นักศึกษา             │
├─────────────────────────────────┤
│  ┌─────────────────────────┐    │
│  │   Today's Carbon        │    │
│  │   2.45 kg CO2e         │    │
│  │   ▼ -15% from average  │    │
│  └─────────────────────────┘    │
│                                  │
│  Points: 678 🏆  Streak: 7 🔥   │
│                                  │
│  ┌──────────────────────────┐   │
│  │    Quick Actions         │   │
│  │ [🚗] [⚡] [♻️] [📊]      │   │
│  └──────────────────────────┘   │
│                                  │
│  Recent Activities              │
│  ┌──────────────────────────┐   │
│  │ 🚇 รถไฟฟ้า 5.2 km       │   │
│  │ 💡 ไฟฟ้า 45 kWh         │   │
│  │ ♻️ รีไซเคิล 2.5 kg      │   │
│  └──────────────────────────┘   │
│                                  │
│ [🏠] [📊] [➕] [🏆] [👤]        │
└─────────────────────────────────┘
```

#### 5.2.2 Activity Recording Screen
```
┌─────────────────────────────────┐
│  ← บันทึกการเดินทาง             │
├─────────────────────────────────┤
│                                  │
│  เลือกประเภทการเดินทาง:         │
│  ┌──────────────────────────┐   │
│  │ 🚶 เดิน                  │   │
│  │ 🚴 จักรยาน              │   │
│  │ 🚇 รถไฟฟ้า  ✓           │   │
│  │ 🚌 รถเมล์               │   │
│  │ 🏍️ มอเตอร์ไซค์          │   │
│  │ 🚗 รถยนต์               │   │
│  └──────────────────────────┘   │
│                                  │
│  ระยะทาง:                       │
│  [  5.2  ] km                   │
│                                  │
│  วัตถุประสงค์:                  │
│  ⚪ เรียน ⚫ ทำงาน ⚪ ส่วนตัว    │
│                                  │
│  📍 บันทึกตำแหน่ง (optional)     │
│                                  │
│  ┌──────────────────────────┐   │
│  │    คำนวณ Carbon          │   │
│  │    0.104 kg CO2e         │   │
│  │    +26 points 🎉         │   │
│  └──────────────────────────┘   │
│                                  │
│        [ บันทึก ]                │
└─────────────────────────────────┘
```

#### 5.2.3 Gamification Screen
```
┌─────────────────────────────────┐
│  ← Achievements & Rewards        │
├─────────────────────────────────┤
│  Level 3   [▓▓▓▓▓░░░] 234/500   │
│                                  │
│  🏆 Leaderboard                  │
│  ┌──────────────────────────┐   │
│  │ 1. นักศึกษา A  2,345 pts │   │
│  │ 2. นักศึกษา B  2,234 pts │   │
│  │ 3. นักศึกษา C  2,156 pts │   │
│  │ ...                      │   │
│  │ 15. คุณ 👤    678 pts   │   │
│  └──────────────────────────┘   │
│                                  │
│  🎖️ My Badges (5/20)            │
│  ┌────┐ ┌────┐ ┌────┐          │
│  │ 🌱 │ │ 🚇 │ │ ♻️ │          │
│  └────┘ └────┘ └────┘          │
│                                  │
│  📈 Next Badge                   │
│  Green Commuter                 │
│  [▓▓▓▓▓▓▓░░░] 15/20            │
│  ใช้ขนส่งสาธารณะอีก 5 ครั้ง     │
└─────────────────────────────────┘
```

### 5.3 Web Application Layouts

#### 5.3.1 Dashboard Layout
```
┌──────────────────────────────────────────────────┐
│  EcoTrack  Dashboard  Reports  Goals  Profile    │
├──────────────────────────────────────────────────┤
│                                                  │
│  Welcome back, นักศึกษา!         Points: 678 🏆  │
│                                                  │
│  ┌────────────┬────────────┬────────────┐      │
│  │ Today      │ This Week  │ This Month │      │
│  │ 2.45 kg    │ 15.67 kg   │ 67.89 kg   │      │
│  │ ▼ -15%     │ ▼ -12%     │ ▲ +5%      │      │
│  └────────────┴────────────┴────────────┘      │
│                                                  │
│  ┌─────────────────┬──────────────────┐         │
│  │ Carbon by Type  │ Trend Chart      │         │
│  │ [Pie Chart]     │ [Line Graph]     │         │
│  └─────────────────┴──────────────────┘         │
│                                                  │
│  Recent Activities        Quick Actions          │
│  ┌──────────────┐        ┌──────────────┐      │
│  │ Activity List│        │ Action Btns  │      │
│  └──────────────┘        └──────────────┘      │
└──────────────────────────────────────────────────┘
```

### 5.4 UI Components

#### Button Styles
```css
.btn-primary {
  background: #4CAF50;
  color: white;
  border-radius: 8px;
  padding: 12px 24px;
}

.btn-secondary {
  background: transparent;
  color: #4CAF50;
  border: 2px solid #4CAF50;
}

.btn-icon {
  width: 48px;
  height: 48px;
  border-radius: 50%;
}
```

#### Card Component
```jsx
<Card>
  <CardHeader>
    <Icon /> Title
    <Badge>New</Badge>
  </CardHeader>
  <CardBody>
    Content
  </CardBody>
  <CardFooter>
    <Button>Action</Button>
  </CardFooter>
</Card>
```

---

## 6. การออกแบบความปลอดภัย (Security Design)

### 6.1 Authentication & Authorization

#### JWT Token Structure
```json
{
  "header": {
    "alg": "RS256",
    "typ": "JWT"
  },
  "payload": {
    "sub": "user_uuid",
    "email": "student@university.ac.th",
    "role": "student",
    "faculty": "Engineering",
    "iat": 1679529600,
    "exp": 1679616000
  }
}
```

#### Token Management
- Access Token: 15 minutes expiry
- Refresh Token: 7 days expiry
- Secure storage in httpOnly cookies
- Token rotation on refresh

### 6.2 Data Protection

#### Encryption
- Data at rest: AES-256-GCM
- Data in transit: TLS 1.3
- Database encryption: Transparent Data Encryption (TDE)
- Sensitive fields: Field-level encryption

#### Personal Data (PDPA Compliance)
```javascript
// Data minimization
const userPublicData = {
  id: user.id,
  name: user.name,
  faculty: user.faculty,
  points: user.points
  // No email, student_id, or location data
};

// Right to erasure
async function deleteUserData(userId) {
  // Anonymize activities
  await db.query(`
    UPDATE activities 
    SET user_id = 'deleted_user'
    WHERE user_id = $1
  `, [userId]);
  
  // Delete personal data
  await db.query(`
    DELETE FROM users WHERE id = $1
  `, [userId]);
}
```

### 6.3 API Security

#### Rate Limiting
```javascript
const rateLimits = {
  public: {
    windowMs: 15 * 60 * 1000, // 15 minutes
    max: 100 // requests
  },
  authenticated: {
    windowMs: 15 * 60 * 1000,
    max: 1000
  },
  sensitive: {
    windowMs: 15 * 60 * 1000,
    max: 10 // for password reset, etc.
  }
};
```

#### Input Validation
```javascript
const activitySchema = Joi.object({
  typeId: Joi.number().integer().required(),
  value: Joi.number().positive().max(1000).required(),
  date: Joi.date().max('now').required(),
  purpose: Joi.string().valid('work', 'study', 'personal'),
  notes: Joi.string().max(500),
  location: Joi.object({
    lat: Joi.number().min(-90).max(90),
    lng: Joi.number().min(-180).max(180)
  })
});
```

### 6.4 Security Headers
```javascript
app.use(helmet({
  contentSecurityPolicy: {
    directives: {
      defaultSrc: ["'self'"],
      styleSrc: ["'self'", "'unsafe-inline'"],
      scriptSrc: ["'self'"],
      imgSrc: ["'self'", "data:", "https:"],
      connectSrc: ["'self'", "https://api.ecotrack.university.ac.th"]
    }
  },
  hsts: {
    maxAge: 31536000,
    includeSubDomains: true,
    preload: true
  }
}));
```

### 6.5 Audit Logging
```javascript
const auditLog = {
  timestamp: new Date().toISOString(),
  userId: req.user?.id,
  action: 'UPDATE_PROFILE',
  resource: 'users',
  ip: req.ip,
  userAgent: req.headers['user-agent'],
  changes: {
    before: oldData,
    after: newData
  },
  result: 'success'
};

await db.query(
  'INSERT INTO audit_logs (data) VALUES ($1)',
  [JSON.stringify(auditLog)]
);
```

### 6.6 Security Monitoring

#### Metrics to Monitor
- Failed login attempts
- Unusual activity patterns
- API rate limit violations
- Data export requests
- Permission escalation attempts

#### Alert Thresholds
```javascript
const alertRules = {
  failedLogins: {
    threshold: 5,
    window: '5 minutes',
    action: 'lockAccount'
  },
  unusualActivity: {
    threshold: 100,
    window: '1 hour',
    action: 'notifyAdmin'
  },
  dataExport: {
    threshold: 10,
    window: '1 day',
    action: 'requireVerification'
  }
};
```

---

**หมายเหตุ:** เอกสารนี้เป็นแนวทางการออกแบบที่อาจมีการปรับเปลี่ยนตามความเหมาะสมในระหว่างการพัฒนา