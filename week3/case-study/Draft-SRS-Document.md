# Software Requirements Specification (SRS)
## ระบบติดตาม Carbon Footprint - EcoTrack Mini
### Student Edition (3-Week Sprint)

**Document ID:** SRS-ECO-MINI-001  
**Version:** 1.0  
**วันที่:** มีนาคม 2567  
**สถานะ:** Final  
**จัดทำโดย:** นักศึกษาวิศวกรรมซอฟต์แวร์ ปี 2  
**ระยะเวลาพัฒนา:** 3 สัปดาห์  
**เป้าหมาย:** Learning by Doing - สร้างประสบการณ์จริงในการพัฒนาซอฟต์แวร์

---

## 📋 สารบัญ

1. [บทนำและวัตถุประสงค์](#1-บทนำและวัตถุประสงค์)
2. [ขอบเขตโครงการ (Mini Scope)](#2-ขอบเขตโครงการ-mini-scope)
3. [Personas (เฉพาะหลัก)](#3-personas-เฉพาะหลัก)
4. [User Stories สำหรับ 3 สัปดาห์](#4-user-stories-สำหรับ-3-สัปดาห์)
5. [Technical Requirements](#5-technical-requirements)
6. [Sprint Planning (3 Weeks)](#6-sprint-planning-3-weeks)
7. [Architecture & Database Design](#7-architecture--database-design)
8. [Implementation Checklist](#8-implementation-checklist)

---

## 1. บทนำและวัตถุประสงค์

### 1.1 Project Overview
**EcoTrack Mini** เป็นระบบติดตาม Carbon Footprint แบบ minimalist ที่ออกแบบมาเฉพาะสำหรับนักศึกษาปี 2 ให้สามารถพัฒนาเสร็จภายใน **3 สัปดาห์** และได้ประสบการณ์การพัฒนาซอฟต์แวร์ครบวงจร

### 1.2 Learning Objectives (3 สัปดาห์)
- ✅ **Week 1:** ทำความเข้าใจ Requirements + Setup
- ✅ **Week 2:** พัฒนา Core Features
- ✅ **Week 3:** Testing + Deployment + Demo

### 1.3 Success Criteria
- [ ] มี Web App ที่ทำงานได้
- [ ] ผู้ใช้สามารถบันทึกกิจกรรมและเห็น CO2 ได้
- [ ] Deploy บน internet
- [ ] Demo ให้เพื่อนและอาจารย์ได้

---

## 2. ขอบเขตโครงการ (Mini Scope)

### 🎯 เก็บเฉพาะ CORE ที่จำเป็น

#### ✅ สิ่งที่จะทำ (Super Simple MVP)
1. **หน้า Home** - แนะนำแอป + Quick Add
2. **ระบบผู้ใช้** - เฉพาะ Name (ไม่ต้อง register/login)
3. **บันทึกกิจกรรม** - เฉพาะการเดินทาง 3 ประเภท
4. **แสดงผล** - Dashboard เบื้องต้น
5. **คำนวณ CO2** - สูตรง่ายๆ

#### ❌ สิ่งที่ตัดออก (เพื่อประหยัดเวลา)
- ~~ระบบ Authentication (Login/Register)~~
- ~~การจัดการ Profile~~
- ~~การแก้ไข/ลบข้อมูล~~
- ~~กราฟแสดงแนวโน้ม~~
- ~~การเปรียบเทียบ~~
- ~~Gamification~~
- ~~Mobile app~~
- ~~ระบบ Admin~~

### 🏆 Definition of Success
> **"ผู้ใช้สามารถกรอกชื่อ → บันทึกการเดินทางวันนี้ → เห็นว่าปล่อย CO2 เท่าไหร่"**

---

## 3. Personas (เฉพาะหลัก)

### 👤 Primary Persona: น้องเอิร์ท - นักศึกษาทั่วไป

**ข้อมูลพื้นฐาน:**
- อายุ 19 ปี, นักศึกษาปี 2
- ใช้ smartphone + laptop
- พักหอพัก, เดินทางด้วยวิธีต่างๆ

**การใช้งานปัจจุบัน:**
- ไปเรียนด้วยการเดิน/รถเมล์/มอเตอร์ไซค์รับจ้าง
- อยากรู้ว่าการเดินทางส่งผลต่อสิ่งแวดล้อมยังไง
- ไม่อยากใช้แอปที่ซับซ้อน

**Pain Points:**
> "ไม่รู้ว่าการเดินทางของฉันส่งผลต่อ Carbon เท่าไหร่"
> "อยากช่วยโลกแต่ไม่รู้จะเริ่มยังไง"

**Goals:**
- รู้ CO2 ที่ตัวเองปล่อยจากการเดินทาง
- เปรียบเทียบวิธีการเดินทางต่างๆ
- ใช้งานง่าย ไม่ซับซ้อน

**User Journey (ที่คาดหวัง):**
```
เข้าเว็บ → กรอกชื่อ → เลือกวิธีเดินทาง → ใส่ระยะทาง → เห็น CO2 → เข้าใจผลกระทบ
```

---

## 4. User Stories สำหรับ 3 สัปดาห์

### 🔹 EPIC 1: User Setup (Super Simple)

#### US-01: เข้าใช้งานแบบไม่ต้อง Login
```
As a นักศึกษา
I want to เริ่มใช้งานโดยแค่กรอกชื่อ
So that ฉันไม่ต้องเสียเวลาสร้างบัญชี

Acceptance Criteria:
✅ มีหน้า Welcome page
✅ กรอกชื่อแล้วเข้าใช้ได้ทันที
✅ ชื่อแสดงใน header

Story Points: 2
Priority: Must Have
Sprint: 1
```

### 🔹 EPIC 2: Activity Tracking (Core Feature)

#### US-02: บันทึกการเดินทางด้วยการเดิน
```
As a นักศึกษา
I want to บันทึกว่าวันนี้เดิน 2 กิโลเมตร
So that ฉันรู้ว่าการเดินไม่ทำให้เกิด CO2

Acceptance Criteria:
✅ เลือก "เดิน" จาก dropdown
✅ ใส่ระยะทาง (กม.)
✅ คลิก Save แล้วเห็นผล CO2 = 0

Story Points: 3
Priority: Must Have
Sprint: 2
```

#### US-03: บันทึกการเดินทางด้วยรถเมล์
```
As a นักศึกษา
I want to บันทึกว่าวันนี้นั่งรถเมล์ 5 กิโลเมตร
So that ฉันรู้ว่าปล่อย CO2 เท่าไหร่

Acceptance Criteria:
✅ เลือก "รถเมล์" จาก dropdown
✅ ใส่ระยะทาง 5 กม.
✅ เห็น CO2 = 0.2 kg (5 × 0.04)

Story Points: 2
Priority: Must Have
Sprint: 2
```

#### US-04: บันทึกการเดินทางด้วยรถยนต์
```
As a นักศึกษา
I want to บันทึกว่าวันนี้นั่งรถยนต์ 10 กิโลเมตร
So that ฉันรู้ว่าปล่อย CO2 เท่าไหร่

Acceptance Criteria:
✅ เลือก "รถยนต์" จาก dropdown
✅ ใส่ระยะทาง 10 กม.
✅ เห็น CO2 = 2.1 kg (10 × 0.21)

Story Points: 2
Priority: Must Have
Sprint: 2
```

### 🔹 EPIC 3: Results Display

#### US-05: ดู CO2 รวมของวันนี้
```
As a นักศึกษา
I want to เห็นสรุป CO2 ที่ปล่อยวันนี้
So that ฉันรู้ผลกระทบรวม

Acceptance Criteria:
✅ แสดง Total CO2 Today
✅ แสดงจำนวนกิจกรรม
✅ แสดงรายการกิจกรรมวันนี้

Story Points: 3
Priority: Must Have
Sprint: 2
```

#### US-06: เปรียบเทียบวิธีการเดินทาง
```
As a นักศึกษา
I want to เห็นว่าถ้าเปลี่ยนวิธีเดินทางจะได้ CO2 เท่าไหร่
So that ฉันเลือกวิธีที่ดีต่อสิ่งแวดล้อม

Acceptance Criteria:
✅ แสดงตัวอย่าง: "10 กม. ด้วยวิธีต่างๆ"
✅ เดิน: 0 kg CO2
✅ รถเมล์: 0.4 kg CO2  
✅ รถยนต์: 2.1 kg CO2

Story Points: 2
Priority: Should Have
Sprint: 3
```

---

## 5. Technical Requirements

### 5.1 Technology Stack (เลือกแบบง่าย)

#### Frontend Options:
**🔵 Option A: Vanilla (แนะนำสำหรับมือใหม่)**
```
HTML + CSS + JavaScript
Bootstrap 5 (styling)
Chart.js (optional ถ้ามีเวลา)
```

**🔵 Option B: Modern (ถ้ามีพื้นฐาน React)**
```
React.js (Create React App)
Tailwind CSS / Material-UI
```

#### Backend Options:
**🔵 Option A: No Backend (แนะนำ)**
```
Frontend-only app
localStorage สำหรับเก็บข้อมูล
Deploy บน GitHub Pages
```

**🔵 Option B: Simple Backend**
```
Node.js + Express.js
JSON file เป็น database
Deploy บน Render.com
```

### 5.2 Data Structure (เฉพาะที่จำเป็น)

#### User Object (Local Storage)
```javascript
const user = {
  name: "ชื่อผู้ใช้",
  createdAt: "2024-03-20"
};
```

#### Activity Object
```javascript
const activity = {
  id: "unique-id",
  date: "2024-03-20",
  type: "walking", // walking, bus, car
  distance: 5, // กิโลเมตร
  co2: 0, // kg CO2
  timestamp: "2024-03-20T10:30:00Z"
};
```

#### Emission Factors (ค่าคงที่)
```javascript
const EMISSION_FACTORS = {
  walking: 0,      // kg CO2 per km
  bus: 0.04,       // kg CO2 per km
  car: 0.21        // kg CO2 per km
};
```

---

## 6. Sprint Planning (3 Weeks)

### 📅 Timeline Overview
```
Week 1: Setup + Foundation (7 days)
Week 2: Core Development (7 days)  
Week 3: Polish + Deploy (7 days)
```

---

### 🗓️ **WEEK 1: Foundation & Learning**

#### วัน 1-2: Project Setup
**Goals:** เตรียมทุกอย่างให้พร้อม
- [ ] ตั้งทีม + แบ่งหน้าที่
- [ ] ทำความเข้าใจ Requirements
- [ ] เลือก Technology Stack
- [ ] Setup development environment
- [ ] สร้าง GitHub repository

**Deliverables:**
- GitHub repo พร้อม basic structure
- README.md อธิบายโครงการ
- Technology stack ตัดสินใจแล้ว

#### วัน 3-4: Design & Wireframe
**Goals:** วางแผนการออกแบบ
- [ ] สร้าง wireframe (บนกระดาษหรือ Figma)
- [ ] กำหนด color scheme
- [ ] เขียน HTML structure
- [ ] Setup CSS framework

**Deliverables:**
- Wireframe ของหน้าหลัก
- Basic HTML pages
- CSS structure

#### วัน 5-7: Basic Frontend
**Goals:** สร้างโครงสร้างหน้าเว็บ
- [ ] **US-01:** หน้า Welcome + กรอกชื่อ
- [ ] Navigation structure
- [ ] Responsive layout
- [ ] Local Storage setup

**Deliverables:**
- Working welcome page
- Name input functional
- Basic navigation

---

### 🗓️ **WEEK 2: Core Development**

#### วัน 8-10: Activity Tracking
**Goals:** สร้าง core features
- [ ] **US-02:** บันทึกการเดิน
- [ ] **US-03:** บันทึกรถเมล์
- [ ] **US-04:** บันทึกรถยนต์
- [ ] CO2 calculation engine

**Deliverables:**
- Activity input form
- CO2 calculation working
- Data saving to localStorage

#### วัน 11-12: Dashboard
**Goals:** แสดงผลข้อมูล
- [ ] **US-05:** Dashboard แสดง CO2 วันนี้
- [ ] Activity list
- [ ] Summary statistics
- [ ] Basic styling

**Deliverables:**
- Working dashboard
- CO2 summary display
- Activity history

#### วัน 13-14: Enhancement
**Goals:** ปรับปรุง UX
- [ ] **US-06:** การเปรียบเทียบ (ถ้ามีเวลา)
- [ ] Error handling
- [ ] Input validation
- [ ] Mobile responsive

**Deliverables:**
- Comparison feature (optional)
- Better UX/UI
- Mobile-friendly

---

### 🗓️ **WEEK 3: Testing & Deployment**

#### วัน 15-17: Testing & Bug Fix
**Goals:** ทดสอบและแก้ไข
- [ ] Manual testing ทุก features
- [ ] Cross-browser testing
- [ ] Mobile testing
- [ ] Bug fixes
- [ ] Performance optimization

**Test Cases:**
```
✅ กรอกชื่อ → เข้าใช้ได้
✅ บันทึกเดิน 5 กม. → CO2 = 0
✅ บันทึกรถเมล์ 5 กม. → CO2 = 0.2
✅ บันทึกรถยนต์ 5 กม. → CO2 = 1.05
✅ Dashboard แสดงผลถูกต้อง
✅ Mobile responsive
```

#### วัน 18-19: Deployment
**Goals:** นำเว็บขึ้น internet
- [ ] เลือก hosting platform
- [ ] Deploy บน GitHub Pages / Netlify
- [ ] ทดสอบ production
- [ ] แก้ไข deployment issues

**Deployment Options:**
- **GitHub Pages** (ฟรี, ง่าย)
- **Netlify** (ฟรี, auto-deploy)
- **Vercel** (ฟรี, fast)

#### วัน 20-21: Demo Preparation
**Goals:** เตรียมการนำเสนอ
- [ ] สร้าง demo script
- [ ] เตรียม test data
- [ ] สร้าง presentation slides
- [ ] ซ้อมการ demo

**Demo Structure (5 นาที):**
1. แนะนำ EcoTrack Mini (30 วินาที)
2. Demo การใช้งาน (3 นาที)
3. แสดง technology ที่ใช้ (1 นาที)
4. Q&A (30 วินาที)

---

## 7. Architecture & Database Design

### 7.1 System Architecture (แบบง่าย)

```
┌─────────────────────────────────────┐
│        Frontend (Browser)           │
│  ┌───────────┬──────────────────┐   │
│  │    UI     │   Local Storage  │   │
│  │  Layer    │    (Database)    │   │
│  └───────────┴──────────────────┘   │
│           JavaScript Logic          │
└─────────────────────────────────────┘
```

### 7.2 Local Storage Schema

#### Key: `ecotrack_user`
```json
{
  "name": "น้องเอิร์ท",
  "createdAt": "2024-03-20T10:00:00Z"
}
```

#### Key: `ecotrack_activities`
```json
[
  {
    "id": "act_001",
    "date": "2024-03-20",
    "type": "walking",
    "distance": 2,
    "co2": 0,
    "timestamp": "2024-03-20T08:30:00Z"
  },
  {
    "id": "act_002", 
    "date": "2024-03-20",
    "type": "bus",
    "distance": 5,
    "co2": 0.2,
    "timestamp": "2024-03-20T12:00:00Z"
  }
]
```

### 7.3 File Structure (Frontend Only)

```
ecotrack-mini/
├── index.html
├── css/
│   ├── style.css
│   └── bootstrap.min.css (CDN)
├── js/
│   ├── app.js (main logic)
│   ├── storage.js (localStorage functions)
│   └── calculator.js (CO2 calculations)
├── images/
│   └── icons/ (transportation icons)
├── README.md
└── docs/
    └── demo-script.md
```

---

## 8. Implementation Checklist

### 🔧 Week 1 Checklist

#### Development Setup
- [ ] สร้าง GitHub repository
- [ ] Clone repo ทุกคน
- [ ] Setup VS Code + extensions
- [ ] เลือก CSS framework (Bootstrap)
- [ ] สร้าง basic HTML structure

#### Basic Pages
- [ ] `index.html` - Welcome page
- [ ] `dashboard.html` - Main app page  
- [ ] `about.html` - About page (optional)
- [ ] Navigation between pages

#### Welcome Page Features
- [ ] กรอกชื่อผู้ใช้
- [ ] บันทึกใน localStorage
- [ ] Redirect ไป dashboard
- [ ] Validation (ชื่อไม่ว่าง)

### 🔧 Week 2 Checklist

#### Activity Input Form
- [ ] Dropdown เลือกประเภท (เดิน/รถเมล์/รถยนต์)
- [ ] Input ระยะทาง (number, min=0)
- [ ] ปุ่ม Save
- [ ] Clear form หลัง save

#### CO2 Calculation
- [ ] Function คำนวณ CO2
- [ ] Emission factors ถูกต้อง
- [ ] แสดงผลทันทีหลัง save
- [ ] บันทึกลง localStorage

#### Dashboard
- [ ] แสดงชื่อผู้ใช้
- [ ] Total CO2 วันนี้
- [ ] รายการกิจกรรมวันนี้
- [ ] สถิติพื้นฐาน (จำนวนกิจกรรม)

### 🔧 Week 3 Checklist

#### Testing
- [ ] ทดสอบบน Chrome, Firefox, Safari
- [ ] ทดสอบบน mobile
- [ ] ทดสอบ edge cases (ระยะทาง 0, ข้อมูลผิด)
- [ ] ทดสอบ localStorage (clear data, reload)

#### Polish
- [ ] เพิ่ม loading states
- [ ] Error messages ที่เข้าใจง่าย
- [ ] Responsive design
- [ ] Icons และ visual elements

#### Deployment
- [ ] Build production version
- [ ] Deploy บน GitHub Pages
- [ ] ทดสอบ production URL
- [ ] Update README.md

#### Demo Preparation  
- [ ] เตรียม demo data
- [ ] ซ้อมการ demo
- [ ] สร้าง presentation (3-5 slides)
- [ ] เตรียมตอบคำถาม

---

## 9. Code Examples (Quick Start)

### 9.1 HTML Structure

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EcoTrack Mini</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet">
    <link href="css/style.css" rel="stylesheet">
</head>
<body>
    <!-- Welcome Page -->
    <div id="welcome-page" class="container mt-5">
        <div class="text-center">
            <h1>🌱 EcoTrack Mini</h1>
            <p>ติดตาม Carbon Footprint จากการเดินทาง</p>
            
            <div class="card mt-4" style="max-width: 400px; margin: 0 auto;">
                <div class="card-body">
                    <input type="text" id="userName" class="form-control" placeholder="กรอกชื่อของคุณ">
                    <button onclick="startApp()" class="btn btn-success mt-3 w-100">เริ่มใช้งาน</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Dashboard Page -->
    <div id="dashboard-page" class="container mt-3" style="display: none;">
        <nav class="navbar">
            <span class="navbar-brand">สวัสดี <span id="displayName"></span>! 🌱</span>
        </nav>

        <!-- Add Activity Form -->
        <div class="card mt-4">
            <div class="card-header">บันทึกการเดินทาง</div>
            <div class="card-body">
                <div class="row">
                    <div class="col-md-4">
                        <select id="activityType" class="form-select">
                            <option value="walking">🚶 เดิน</option>
                            <option value="bus">🚌 รถเมล์</option>
                            <option value="car">🚗 รถยนต์</option>
                        </select>
                    </div>
                    <div class="col-md-4">
                        <input type="number" id="distance" class="form-control" placeholder="ระยะทาง (กม.)" min="0" step="0.1">
                    </div>
                    <div class="col-md-4">
                        <button onclick="addActivity()" class="btn btn-primary w-100">บันทึก</button>
                    </div>
                </div>
            </div>
        </div>

        <!-- Summary -->
        <div class="card mt-4">
            <div class="card-header">สรุปวันนี้</div>
            <div class="card-body">
                <h3>CO2 รวม: <span id="totalCO2">0</span> kg</h3>
                <p>กิจกรรม: <span id="activityCount">0</span> ครั้ง</p>
            </div>
        </div>

        <!-- Activity List -->
        <div class="card mt-4">
            <div class="card-header">รายการกิจกรรมวันนี้</div>
            <div class="card-body">
                <div id="activityList">
                    <p class="text-muted">ยังไม่มีกิจกรรม</p>
                </div>
            </div>
        </div>
    </div>

    <script src="js/app.js"></script>
</body>
</html>
```

### 9.2 JavaScript Logic

```javascript
// app.js
const EMISSION_FACTORS = {
    walking: 0,
    bus: 0.04,
    car: 0.21
};

const ACTIVITY_NAMES = {
    walking: '🚶 เดิน',
    bus: '🚌 รถเมล์', 
    car: '🚗 รถยนต์'
};

// Initialize app
window.onload = function() {
    const user = localStorage.getItem('ecotrack_user');
    if (user) {
        showDashboard();
    }
};

// Start app with user name
function startApp() {
    const name = document.getElementById('userName').value.trim();
    if (!name) {
        alert('กรุณากรอกชื่อ');
        return;
    }
    
    // Save user
    localStorage.setItem('ecotrack_user', JSON.stringify({
        name: name,
        createdAt: new Date().toISOString()
    }));
    
    showDashboard();
}

// Show dashboard
function showDashboard() {
    const user = JSON.parse(localStorage.getItem('ecotrack_user'));
    
    document.getElementById('welcome-page').style.display = 'none';
    document.getElementById('dashboard-page').style.display = 'block';
    document.getElementById('displayName').textContent = user.name;
    
    loadTodayData();
}

// Add new activity
function addActivity() {
    const type = document.getElementById('activityType').value;
    const distance = parseFloat(document.getElementById('distance').value);
    
    if (!distance || distance <= 0) {
        alert('กรุณาใส่ระยะทางที่ถูกต้อง');
        return;
    }
    
    // Calculate CO2
    const co2 = distance * EMISSION_FACTORS[type];
    
    // Create activity object
    const activity = {
        id: 'act_' + Date.now(),
        date: new Date().toISOString().split('T')[0],
        type: type,
        distance: distance,
        co2: co2,
        timestamp: new Date().toISOString()
    };
    
    // Save to localStorage
    let activities = JSON.parse(localStorage.getItem('ecotrack_activities') || '[]');
    activities.push(activity);
    localStorage.setItem('ecotrack_activities', JSON.stringify(activities));
    
    // Clear form
    document.getElementById('distance').value = '';
    
    // Refresh display
    loadTodayData();
    
    // Show result
    alert(`บันทึกสำเร็จ! CO2 ที่เกิดขึ้น: ${co2.toFixed(2)} kg`);
}

// Load today's data
function loadTodayData() {
    const today = new Date().toISOString().split('T')[0];
    const activities = JSON.parse(localStorage.getItem('ecotrack_activities') || '[]');
    
    // Filter today's activities
    const todayActivities = activities.filter(act => act.date === today);
    
    // Calculate totals
    const totalCO2 = todayActivities.reduce((sum, act) => sum + act.co2, 0);
    const activityCount = todayActivities.length;
    
    // Update display
    document.getElementById('totalCO2').textContent = totalCO2.toFixed(2);
    document.getElementById('activityCount').textContent = activityCount;
    
    // Update activity list
    displayActivityList(todayActivities);
}

// Display activity list
function displayActivityList(activities) {
    const listElement = document.getElementById('activityList');
    
    if (activities.length === 0) {
        listElement.innerHTML = '<p class="text-muted">ยังไม่มีกิจกรรม</p>';
        return;
    }
    
    let html = '';
    activities.forEach(activity => {
        html += `
            <div class="border-bottom py-2">
                <strong>${ACTIVITY_NAMES[activity.type]}</strong> 
                ${activity.distance} กม. 
                <span class="text-success">CO2: ${activity.co2.toFixed(2)} kg</span>
            </div>
        `;
    });
    
    listElement.innerHTML = html;
}
```

### 9.3 CSS Styling

```css
/* style.css */
:root {
    --primary-color: #28a745;
    --secondary-color: #6c757d;
    --success-color: #20c997;
    --warning-color: #ffc107;
    --danger-color: #dc3545;
    --light-bg: #f8f9fa;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: var(--light-bg);
    color: #333;
}

.navbar {
    background-color: var(--primary-color);
    color: white;
    padding: 1rem;
    border-radius: 0.5rem;
    margin-bottom: 1rem;
}

.navbar-brand {
    color: white !important;
    font-weight: 600;
}

.card {
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    border: none;
    border-radius: 0.75rem;
}

.card-header {
    background-color: var(--primary-color);
    color: white;
    font-weight: 600;
    border-radius: 0.75rem 0.75rem 0 0 !important;
}

.btn-success {
    background-color: var(--primary-color);
    border-color: var(--primary-color);
}

.btn-success:hover {
    background-color: #218838;
    border-color: #1e7e34;
}

.activity-item {
    background-color: white;
    border: 1px solid #dee2e6;
    border-radius: 0.5rem;
    padding: 1rem;
    margin-bottom: 0.5rem;
    transition: all 0.3s ease;
}

.activity-item:hover {
    box-shadow: 0 4px 15px rgba(0,0,0,0.1);
    transform: translateY(-2px);
}

.co2-display {
    font-size: 2rem;
    font-weight: bold;
    color: var(--primary-color);
}

.stat-card {
    text-align: center;
    padding: 1.5rem;
}

.stat-number {
    font-size: 2.5rem;
    font-weight: bold;
    color: var(--primary-color);
}

.stat-label {
    color: var(--secondary-color);
    font-size: 0.9rem;
    text-transform: uppercase;
    letter-spacing: 0.5px;
}

@media (max-width: 768px) {
    .container {
        padding: 0 1rem;
    }
    
    .card-body {
        padding: 1rem;
    }
    
    .row .col-md-4 {
        margin-bottom: 0.5rem;
    }
}

/* Loading animation */
.loading {
    border: 3px solid #f3f3f3;
    border-top: 3px solid var(--primary-color);
    border-radius: 50%;
    width: 30px;
    height: 30px;
    animation: spin 1s linear infinite;
    margin: 0 auto;
}

@keyframes spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
}

/* Welcome page styling */
#welcome-page {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
}

#welcome-page h1 {
    font-size: 3rem;
    color: var(--primary-color);
    margin-bottom: 1rem;
}

#welcome-page p {
    font-size: 1.2rem;
    color: var(--secondary-color);
    margin-bottom: 2rem;
}
```

---

## 10. Testing Plan (สำหรับสัปดาห์ที่ 3)

### 10.1 Manual Test Cases

#### Test Case 1: User Setup
```
Test ID: TC-001
Description: ผู้ใช้สามารถเริ่มใช้งานได้

Steps:
1. เปิด index.html
2. กรอกชื่อ "น้องเอิร์ท"
3. คลิก "เริ่มใช้งาน"

Expected Result:
✅ หน้า welcome หายไป
✅ หน้า dashboard แสดง
✅ แสดง "สวัสดี น้องเอิร์ท!"
✅ localStorage มีข้อมูล user
```

#### Test Case 2: Add Walking Activity
```
Test ID: TC-002
Description: บันทึกการเดิน

Steps:
1. เลือก "เดิน" 
2. ใส่ระยะทาง 5
3. คลิก "บันทึก"

Expected Result:
✅ Alert แสดง "CO2 ที่เกิดขึ้น: 0.00 kg"
✅ Total CO2 แสดง 0.00 kg
✅ Activity count แสดง 1
✅ รายการแสดง "เดิน 5 กม."
```

#### Test Case 3: Add Bus Activity
```
Test ID: TC-003
Description: บันทึกรถเมล์

Steps:
1. เลือก "รถเมล์"
2. ใส่ระยะทาง 10
3. คลิก "บันทึก"

Expected Result:
✅ Alert แสดง "CO2 ที่เกิดขึ้น: 0.40 kg"
✅ Total CO2 แสดง 0.40 kg
✅ Activity count แสดง 2 (รวมกับก่อนหน้า)
```

#### Test Case 4: Mobile Responsive
```
Test ID: TC-004
Description: ใช้งานบน mobile ได้

Steps:
1. เปิดใน Chrome DevTools
2. เลือก iPhone/Android size
3. ทดสอบทุกฟีเจอร์

Expected Result:
✅ Layout ไม่เสีย
✅ ปุ่มกดได้
✅ Input ใช้งานได้
✅ Text อ่านได้
```

### 10.2 Cross-Browser Testing

| Browser | Version | Status | Notes |
|---------|---------|--------|-------|
| Chrome | Latest | ✅ | Primary testing |
| Firefox | Latest | ⚠️ | Check localStorage |
| Safari | Latest | ⚠️ | iOS compatibility |
| Edge | Latest | ✅ | Windows testing |

### 10.3 Performance Testing

#### Quick Performance Checks:
- [ ] Page load time < 3 seconds
- [ ] No console errors
- [ ] localStorage < 5MB
- [ ] Images optimized
- [ ] CSS/JS minified (production)

---

## 11. Deployment Guide

### 11.1 GitHub Pages Deployment

#### Step 1: Prepare Repository
```bash
# 1. Create repository structure
ecotrack-mini/
├── index.html
├── css/
├── js/
├── images/
└── README.md

# 2. Commit all files
git add .
git commit -m "Complete EcoTrack Mini v1.0"
git push origin main
```

#### Step 2: Enable GitHub Pages
1. ไป GitHub repository
2. Settings → Pages
3. Source: Deploy from branch
4. Branch: main
5. Folder: / (root)
6. Save

#### Step 3: Access Your Site
- URL จะเป็น: `https://username.github.io/ecotrack-mini`
- รอ 5-10 นาที สำหรับ deployment

### 11.2 Alternative: Netlify

#### Quick Deploy:
1. ไป [netlify.com](https://netlify.com)
2. Drag & drop โฟลเดอร์โครงการ
3. Get instant URL
4. Optional: Connect to GitHub for auto-deploy

### 11.3 Pre-Deployment Checklist

- [ ] ทดสอบ local ครบทุก features
- [ ] ไม่มี console errors
- [ ] Mobile responsive ใช้งานได้
- [ ] localStorage ทำงาน
- [ ] Links ทั้งหมดถูกต้อง
- [ ] README.md เขียนเสร็จ

---

## 12. Demo Script (5 นาที)

### 🎯 Demo Structure

#### Opening (30 วินาที)
> "สวัสดีครับ วันนี้ผมจะ demo **EcoTrack Mini** ระบบติดตาม Carbon Footprint ที่ทีมเราพัฒนาใน 3 สัปดาห์
> 
> **เป้าหมาย:** ช่วยให้นักศึกษารู้ว่าการเดินทางแต่ละวันปล่อย CO2 เท่าไหร่"

#### Demo Flow (3 นาที)

**Step 1: User Setup (30 วินาที)**
```
- เปิดเว็บ ecotrack-mini.github.io
- แสดงหน้า Welcome
- กรอกชื่อ "Demo User"
- คลิก "เริ่มใช้งาน"
```

**Step 2: บันทึกการเดิน (45 วินาที)**
```
- เลือก "เดิน"
- ใส่ระยะทาง 3 กม.
- คลิก "บันทึก"
- อธิบาย: "การเดินไม่ปล่อย CO2 เลย"
```

**Step 3: บันทึกรถเมล์ (45 วินาที)**
```
- เลือก "รถเมล์"  
- ใส่ระยะทาง 5 กม.
- คลิก "บันทึก"
- อธิบาย: "รถเมล์ปล่อย CO2 แค่ 0.2 kg"
```

**Step 4: บันทึกรถยนต์ (45 วินาที)**
```
- เลือก "รถยนต์"
- ใส่ระยะทาง 5 กม.  
- คลิก "บันทึก"
- อธิบาย: "รถยนต์ปล่อย CO2 มากถึง 1.05 kg!"
```

**Step 5: ดู Summary (15 วินาที)**
```
- แสดง Total CO2: 1.25 kg
- แสดงจำนวนกิจกรรม: 3 ครั้ง
- แสดงรายการกิจกรรม
```

#### Technical Overview (1 นาที)
> "**เทคโนโลยีที่ใช้:**
> - Frontend: HTML, CSS, JavaScript, Bootstrap
> - Database: LocalStorage (ไม่ต้อง server)
> - Deployment: GitHub Pages
> - **ใช้เวลาพัฒนา:** 3 สัปดาห์พอดี"

#### Q&A (30 วินาที)
**คำถามที่คาดว่าจะถูกถาม:**
- Q: "ข้อมูลเก็บไว้ไหน?" → A: "LocalStorage ในเบราว์เซอร์"
- Q: "สูตรคำนวณ CO2 มาจากไหน?" → A: "จากองค์การบริหารจัดการก๊าซเรือนกระจก (TGO)"
- Q: "ต่อยอดยังไง?" → A: "เพิ่ม login, กราฟ, เปรียบเทียบกับเพื่อน"

### 🎭 Demo Tips
- **เตรียม demo data** ล่วงหน้า
- **ทดสอบ internet** ก่อน demo
- **เตรียม backup** (screenshots)
- **ซ้อมให้คล่อง** 2-3 รอบ
- **พูดชัด ๆ** และ**มั่นใจ**

---

## 13. Grading Rubric (เกณฑ์การให้คะแนน)

### 📊 คะแนนรวม 100 คะแนน

#### 1. Functionality (40 คะแนน)
| Feature | คะแนน | เกณฑ์ |
|---------|-------|-------|
| User Setup | 8 | กรอกชื่อเข้าใช้ได้ |
| Activity Tracking | 16 | บันทึก 3 ประเภทได้ |
| CO2 Calculation | 8 | คำนวณถูกต้อง |
| Dashboard | 8 | แสดงสรุปได้ |

#### 2. Technical Quality (25 คะแนน)
- **Code Quality (10 คะแนน)**
  - เขียนโค้ดเป็นระเบียบ
  - มี comments อธิบาย
  - ใช้ naming convention ที่ดี

- **User Interface (10 คะแนน)**
  - Design สวยงาม
  - ใช้งานง่าย
  - Mobile responsive

- **Error Handling (5 คะแนน)**
  - Validation input
  - แสดง error message
  - Handle edge cases

#### 3. Process (20 คะแนน)
- **Sprint Management (10 คะแนน)**
  - ทำตาม sprint plan
  - แบ่งงานชัดเจน
  - มี daily progress

- **Version Control (5 คะแนน)**
  - ใช้ Git ถูกต้อง
  - Commit messages ดี
  - Collaboration ผ่าน GitHub

- **Documentation (5 คะแนน)**
  - README.md ครบถ้วน
  - User manual
  - Code comments

#### 4. Deployment (10 คะแนน)
- **Working Website (8 คะแนน)**
  - Deploy สำเร็จ
  - ใช้งานได้จริง
  - ไม่มี broken links

- **Performance (2 คะแนน)**
  - Load เร็ว
  - ไม่มี console errors

#### 5. Presentation (5 คะแนน)
- **Demo Quality (3 คะแนน)**
  - Demo คล่อง
  - แสดงครบ features
  - เวลาพอดี

- **Q&A (2 คะแนน)**
  - ตอบคำถามได้
  - อธิบายเทคนิคได้

### 🏆 เกรดเกณฑ์
- **A (90-100):** ครบทุกอย่าง + extra features
- **B+ (85-89):** ครบ core features + ดี 1-2 ด้าน
- **B (80-84):** ครบ core features พื้นฐาน
- **C+ (75-79):** ขาด minor features
- **C (70-74):** ขาด major features แต่ demo ได้
- **D (60-69):** ทำไม่เสร็จ แต่มี progress
- **F (<60):** ไม่ส่งหรือไม่ทำงาน

---

## 14. Success Stories & Learning Outcomes

### 🎯 Expected Learning Outcomes

#### Technical Skills
- ✅ **Web Development Basics**
  - HTML structure และ semantic markup
  - CSS styling และ responsive design
  - JavaScript DOM manipulation
  - LocalStorage และ data persistence

- ✅ **Software Engineering Process**
  - Requirements analysis
  - Sprint planning และ time management
  - Version control ด้วย Git
  - Testing และ debugging

#### Soft Skills
- ✅ **Project Management**
  - แบ่งงานตาม timeline
  - ทำงานเป็นทีม
  - แก้ปัญหาเฉพาะหน้า

- ✅ **Communication**
  - เขียน documentation
  - Present งานต่อหน้าคน
  - รับ feedback และปรับปรุง

### 🏆 Success Criteria

#### Minimum Success (ผ่านเกณฑ์)
- [ ] มี working website ที่ deploy แล้ว
- [ ] ผู้ใช้บันทึกกิจกรรมและเห็น CO2 ได้
- [ ] Demo ได้ครบ 5 นาที
- [ ] ทุกคนในทีมมีส่วนร่วม

#### Good Success (เกรด B+)
- [ ] UI สวยงามและใช้งานง่าย
- [ ] Mobile responsive ใช้งานได้ดี
- [ ] Code มี quality และ documentation ดี
- [ ] Extra features (เช่น comparison table)

#### Excellent Success (เกรด A)
- [ ] Innovation หรือ creative features
- [ ] Performance optimization
- [ ] Advanced UI/UX design
- [ ] การ present ที่โดดเด่น

---

## 15. Troubleshooting Guide

### 🚨 Common Issues & Solutions

#### Issue 1: LocalStorage ไม่ทำงาน
**Symptoms:** ข้อมูลหายเมื่อ refresh
**Solutions:**
- ตรวจสอบ browser support
- ใช้ try-catch กับ localStorage
- ทดสอบใน incognito mode
- เช็ค browser storage quota

```javascript
// Safe localStorage usage
function saveData(key, data) {
    try {
        localStorage.setItem(key, JSON.stringify(data));
    } catch (e) {
        console.error('LocalStorage failed:', e);
        alert('ไม่สามารถบันทึกข้อมูลได้');
    }
}
```

#### Issue 2: GitHub Pages ไม่แสดงผล
**Symptoms:** 404 Error หรือ blank page
**Solutions:**
- ตรวจสอบ file names (case-sensitive)
- รอ 5-10 นาที หลัง deploy
- เช็ค repository settings
- ตรวจสอบ index.html อยู่ใน root

#### Issue 3: Mobile Layout เสีย
**Symptoms:** UI ไม่ responsive
**Solutions:**
- เพิ่ม viewport meta tag
- ใช้ Bootstrap grid system
- ทดสอบใน Chrome DevTools
- เช็ค CSS media queries

#### Issue 4: CO2 คำนวณผิด
**Symptoms:** ตัวเลข CO2 ไม่ถูกต้อง
**Solutions:**
- เช็ค emission factors
- ตรวจสอบ data types (string vs number)
- ใช้ parseFloat() กับ input
- ทดสอบด้วย calculator

```javascript
// Safe number parsing
function parseDistance(input) {
    const distance = parseFloat(input);
    return isNaN(distance) ? 0 : distance;
}
```

### 🛠️ Development Tools

#### Debugging Tools
- **Chrome DevTools** - inspect elements, console logs
- **Lighthouse** - performance analysis
- **Responsive Design Mode** - mobile testing
- **Application Tab** - localStorage inspection

#### Code Quality Tools
- **HTML Validator** - w3.org/markup-validator
- **CSS Validator** - jigsaw.w3.org/css-validator
- **JSHint** - jshint.com (JavaScript linting)
- **Prettier** - code formatting

---

## 16. การต่อยอดโครงการ (Future Enhancements)

### 🚀 Phase 2 Ideas (หลัง 3 สัปดาห์)

#### เพิ่มฟีเจอร์ใหม่
- [ ] **ระบบ Login/Register** - user accounts
- [ ] **แก้ไข/ลบข้อมูล** - edit activities
- [ ] **กราฟแสดงแนวโน้ม** - weekly/monthly charts
- [ ] **การเปรียบเทียบ** - กับค่าเฉลี่ย, เพื่อน
- [ ] **Goals & Targets** - ตั้งเป้าลด CO2
- [ ] **Gamification** - points, badges, leaderboard

#### ปรับปรุงเทคนิค
- [ ] **Backend Database** - MySQL/PostgreSQL
- [ ] **API Development** - RESTful endpoints
- [ ] **Authentication** - JWT tokens
- [ ] **Progressive Web App** - offline capability
- [ ] **Data Analytics** - usage statistics
- [ ] **Mobile App** - React Native/Flutter

#### Advanced Features
- [ ] **Social Sharing** - แชร์ผลลัพธ์
- [ ] **Group Challenges** - แข่งขันลด CO2
- [ ] **Carbon Offset** - คำนวณการชดเชย
- [ ] **Route Optimization** - แนะนำเส้นทางประหยัด
- [ ] **Integration** - กับ Google Maps, Fitness apps

### 🎓 Learning Path ต่อไป

#### เทคโนโลยีที่ควรเรียนต่อ
1. **Database Management**
   - SQL fundamentals
   - Database design
   - ORM (Sequelize, Prisma)

2. **Backend Development**
   - Node.js + Express.js
   - API design patterns
   - Authentication & authorization

3. **Advanced Frontend**
   - React.js/Vue.js framework
   - State management
   - Build tools (Webpack, Vite)

4. **DevOps & Deployment**
   - Docker containers
   - Cloud platforms (AWS, Google Cloud)
   - CI/CD pipelines

---

## 17. Resources & References

### 📚 Learning Materials

#### Web Development
- **HTML/CSS/JS:** [MDN Web Docs](https://developer.mozilla.org/)
- **Bootstrap:** [getbootstrap.com](https://getbootstrap.com/)
- **JavaScript:** [javascript.info](https://javascript.info/)
- **Git/GitHub:** [git-scm.com](https://git-scm.com/docs)

#### Carbon Footprint Data
- **TGO (Thailand):** [tgo.or.th](http://www.tgo.or.th/)
- **EPA Calculator:** [epa.gov](https://www.epa.gov/energy/greenhouse-gas-equivalencies-calculator)
- **Carbon Trust:** [carbontrust.com](https://www.carbontrust.com/)

#### Development Tools
- **VS Code:** [code.visualstudio.com](https://code.visualstudio.com/)
- **Chrome DevTools:** [developers.google.com](https://developers.google.com/web/tools/chrome-devtools)
- **GitHub Pages:** [pages.github.com](https://pages.github.com/)
- **Netlify:** [netlify.com](https://netlify.com/)

### 🎯 Example Projects
- **Simple Calculator:** แนวทางการใช้ localStorage
- **Todo App:** พื้นฐานการจัดการ data
- **Weather App:** การเรียก API และแสดงผล
- **Portfolio Website:** การ deploy และ responsive design

### 👥 Community Support
- **Stack Overflow:** แก้ปัญหาการเขียนโค้ด
- **GitHub:** ดูโค้ดตัวอย่างจากคนอื่น
- **Discord/Slack:** หาชุมชนนักพัฒนา
- **YouTube:** tutorial videos

---

## 18. Final Checklist

### ✅ สัปดาห์ที่ 3 - Ready for Demo

#### Technical Completion
- [ ] **Core Features Working**
  - User setup (name input)
  - Activity tracking (3 types)
  - CO2 calculation (correct)
  - Dashboard display (summary)

- [ ] **Quality Assurance**
  - No console errors
  - Mobile responsive
  - Cross-browser tested
  - Input validation working

- [ ] **Deployment Ready**
  - GitHub repository updated
  - Website deployed online
  - URL accessible publicly
  - All features work in production

#### Documentation Complete
- [ ] **README.md** ครบถ้วน
- [ ] **User manual** (วิธีใช้งาน)
- [ ] **Code comments** อธิบายสำคัญ
- [ ] **Demo script** เตรียมไว้

#### Team Preparation
- [ ] **Role assignment** สำหรับ demo
- [ ] **Demo rehearsal** ซ้อมแล้ว 2-3 รอบ
- [ ] **Q&A preparation** เตรียมตอบคำถาม
- [ ] **Backup plan** กรณีเทคนิคมีปัญหา

#### Final Review
- [ ] **Feature completeness** ตาม requirements
- [ ] **User experience** ใช้งานง่าย
- [ ] **Performance** โหลดเร็ว ไม่ค้าง
- [ ] **Professional appearance** ดูน่าเชื่อถือ

---

## 🎉 สรุป: EcoTrack Mini Success Formula

### 🏆 Key Success Factors

#### 1. **Start Simple** 
ไม่ต้องทำให้ซับซ้อน เริ่มจากฟีเจอร์พื้นฐานที่ทำงานได้ก่อน

#### 2. **Focus on User Value**
ผู้ใช้ต้องเห็นคุณค่า (รู้ CO2 ที่ปล่อย) ได้ทันทีหลังใช้งาน

#### 3. **Learn by Doing**
เรียนรู้เทคโนโลยีผ่านการทำโครงการจริง ไม่ใช่แค่ทฤษฎี

#### 4. **Team Collaboration**
แบ่งงานชัดเจน ช่วยเหลือกัน และติดต่อสื่อสารสม่ำเสมอ

#### 5. **Iterative Development**
ทำทีละส่วน ทดสอบบ่อยๆ และปรับปรุงอย่างต่อเนื่อง

### 🌱 Environmental Impact
แม้โครงการจะเล็ก แต่สร้างความตระหนักเรื่อง Carbon Footprint ให้กับนักศึกษาและคนที่เห็น demo

### 💻 Technical Learning
ได้ประสบการณ์การพัฒนาเว็บแอปพลิเคชันครบวงจร ตั้งแต่ design, coding, testing, ไปจนถึง deployment

### 🚀 Future Ready
สร้างพื้นฐานที่แข็งแกร่งสำหรับการพัฒนาโปรเจคที่ซับซ้อนมากขึ้นในอนาคต

---

**Remember: "Perfect is the enemy of good"**

เป้าหมายไม่ใช่สร้างแอปที่สมบูรณ์แบบ แต่เป็นการสร้างแอปที่**ทำงานได้**และ**มีประโยชน์** ภายในเวลาที่กำหนด

### 🎯 Final Motivation

> **"ใน 3 สัปดาห์นี้ คุณจะได้เรียนรู้:**
> - การวิเคราะห์ความต้องการ
> - การออกแบบระบบ  
> - การเขียนโปรแกรม
> - การทำงานเป็นทีม
> - การนำเสนอผลงาน
> 
> **และที่สำคัญที่สุด: ความมั่นใจว่าคุณสามารถสร้างซอฟต์แวร์ที่มีประโยชน์ได้จริง!"**

**Good luck with your EcoTrack Mini project! 🌱💻✨**

---

*Document End*

**Total Pages:** ~50 pages  
**Estimated Reading Time:** 2-3 hours  
**Implementation Time:** 3 weeks  
**Team Size:** 4-5 students  
**Difficulty Level:** Beginner to Intermediate  

*"Small steps toward big changes - both in software and sustainability!"* 🌍