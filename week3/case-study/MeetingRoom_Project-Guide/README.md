# MeetingRoom Project Guide Document
## MeetingRoom Lite - ระบบจองห้องประชุมพื้นฐาน
**Version:** 1.0  
**Date:** มีนาคม 2024  
**Team:** Software Engineering Students  

### All-in-one document (สำหรับนักศึกษา)
  - เรียกว่า "Project Guide" แทน SRS
  - อธิบายว่าเป็นการผสม SRS + Design + Implementation

## เอกสารสรุปภาพรวมและแนวทางการทำงาน: โครงการ MeetingRoom Lite
เอกสาร Software Requirements Specification (SRS) แบบย่อ (Simplified SRS) สำหรับ **MeetingRoom Lite**
Scope และสร้างเอกสาร SRS ใหม่ที่เหมาะสมกับนักศึกษาปี 2 ให้ทำเสร็จใน 1 เดือน  

### 1. **ขอบเขตที่ทำได้จริงใน 1 เดือน**
- **5 Features หลัก** ที่ไม่ซับซ้อนเกินไป:
  - ✅ Register/Login
  - ✅ ดูห้องว่าง
  - ✅ จองห้อง
  - ✅ จัดการการจองของตนเอง
  - ✅ Admin จัดการห้อง

### 2. **Technical Stack ที่เรียนรู้ได้**
- **Frontend:** React.js (Hooks พื้นฐาน)
- **Backend:** Node.js + Express
- **Database:** PostgreSQL (3 tables เท่านั้น)
- **UI:** Bootstrap 5 (ไม่ต้องเขียน CSS เยอะ)

### 3. **Database Design แบบง่าย**
- เพียง 3 tables: users, rooms, bookings
- ไม่มี complex relationships
- มี SQL สำเร็จรูปให้

### 4. **Code Examples ที่ใช้ได้จริง**
- ตัวอย่าง API endpoints
- React component พื้นฐาน
- Express route handlers
- พร้อม copy ไปใช้ได้เลย

### 5. **แผน 4 สัปดาห์ที่ชัดเจน**
- **Week 1:** Setup & Backend
- **Week 2:** Frontend พื้นฐาน
- **Week 3:** เชื่อมต่อ Frontend-Backend
- **Week 4:** ปรับแต่ง และ Deploy

### 6. **ไม่มี Features ที่ซับซ้อน**
❌ ไม่ทำ:
- Email notifications (ต้องตั้งค่า SMTP)
- Calendar sync (ต้องเรียนรู้ OAuth)
- Recurring bookings (logic ซับซ้อน)
- Advanced reports (ต้องใช้ charting libraries)
- Real-time updates (ต้องใช้ WebSocket)

### 7. **Testing Guide ที่ทำตามได้**
- Manual testing checklist
- Test data SQL ที่พร้อมใช้
- ครอบคลุมทุก feature

### 8. **Learning Resources**
- Link ไปยัง tutorials ที่ดี
- Solutions สำหรับปัญหาที่พบบ่อย
- Code structure ที่ชัดเจน

## 📊 เปรียบเทียบ SRS ทั้ง 2 เวอร์ชัน:

| หัวข้อ | MeetingRoom Pro (Full) | MeetingRoom Lite (Student) |
|--------|------------------------|---------------------------|
| **ระยะเวลา** | 18 สัปดาห์ | 4 สัปดาห์ |
| **ทีมพัฒนา** | 8 คน | 1-2 คน |
| **Features** | 11 features | 5 features |
| **Database** | 10+ tables | 3 tables |
| **Architecture** | Microservices | Monolithic |
| **Authentication** | LDAP + JWT + 2FA | Simple JWT |
| **Notifications** | Email + SMS + Push | ไม่มี |
| **UI/UX** | Professional design | Bootstrap template |
| **Deployment** | Cloud + Docker | Heroku/Render |
| **Testing** | Automated tests | Manual testing |
| **Budget** | 3 ล้านบาท | ฟรี (ใช้ free tier) |

## 💡 คำแนะนำสำหรับนักศึกษา:

### 1. **การเริ่มต้นโปรเจค**
```bash
# 1. สร้าง folder structure
mkdir meetingroom-lite
cd meetingroom-lite
mkdir backend frontend

# 2. Setup backend
cd backend
npm init -y
npm install express pg bcrypt jsonwebtoken cors dotenv
npm install -D nodemon

# 3. Setup frontend  
cd ../frontend
npx create-react-app .
npm install axios react-router-dom bootstrap
```

### 2. **ลำดับการพัฒนาที่แนะนำ**
1. **เริ่มจาก Backend API ก่อน**
   - ทำ authentication ให้เสร็จ
   - ทดสอบด้วย Postman
   - ค่อยทำ features อื่น

2. **Frontend ทำทีละ page**
   - Login page ก่อน
   - Room list page
   - Booking form
   - My bookings

3. **Features ที่ควรทำให้เสร็จก่อน**
   - Login/Logout (พื้นฐานที่สุด)
   - View rooms (ง่ายที่สุด)
   - Create booking (core feature)

### 3. **Common Mistakes ที่ควรหลีกเลี่ยง**
1. ❌ อย่าทำ UI สวยก่อน functionality
2. ❌ อย่าเพิ่ม features ที่ไม่ได้อยู่ใน scope
3. ❌ อย่าลืมทำ error handling
4. ❌ อย่า hardcode ค่าต่างๆ
5. ❌ อย่าเก็บ sensitive data ใน Git

### 4. **Quick Win Features**
ถ้าเหลือเวลา สามารถเพิ่ม:
- 🎨 Dark mode toggle
- 📱 Better mobile UI
- 🔍 Search rooms by name
- 📊 Simple dashboard charts
- 🎯 Favorite rooms

### 5. **Deployment Options (ฟรี)**
1. **Backend:**
   - Render.com (ฟรี 750 ชม./เดือน)
   - Railway.app
   - Cyclic.sh

2. **Database:**
   - ElephantSQL (PostgreSQL ฟรี 20MB)
   - Supabase (ฟรี 500MB)
   
3. **Frontend:**
   - Netlify
   - Vercel
   - GitHub Pages

## 📝 Template Files เพื่อเริ่มต้น:

### 1. **package.json (Backend)**
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
    "pg": "^8.11.3",
    "bcrypt": "^5.1.1",
    "jsonwebtoken": "^9.0.2",
    "cors": "^2.8.5",
    "dotenv": "^16.3.1",
    "express-validator": "^7.0.1"
  },
  "devDependencies": {
    "nodemon": "^3.0.1"
  }
}
```

### 2. **.env (Backend)**
```env
PORT=5000
DATABASE_URL=postgresql://username:password@localhost:5432/meetingroom
JWT_SECRET=your-secret-key-here
NODE_ENV=development
```

### 3. **Basic Server Setup**
```javascript
// server.js
const express = require('express');
const cors = require('cors');
require('dotenv').config();

const app = express();

// Middleware
app.use(cors());
app.use(express.json());

// Routes
app.use('/api/auth', require('./routes/auth'));
app.use('/api/rooms', require('./routes/rooms'));
app.use('/api/bookings', require('./routes/bookings'));

// Error handling
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).json({ 
    success: false, 
    message: 'Something went wrong!' 
  });
});

const PORT = process.env.PORT || 5000;
app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
```

### การประเมินผล:
1. **ให้คะแนนตาม effort มากกว่า perfection**
2. **ดู problem-solving approach**
3. **ให้ bonus สำหรับ extra features ที่มีประโยชน์**
4. **ประเมิน code readability และ organization**

### งานที่แนะนำให้ทำในแต่ละสัปดาห์:
1. **Week 1:** Review database design
2. **Week 2:** Check API testing
3. **Week 3:** Review integration approach
4. **Week 4:** Final functionality check

---

เอกสาร SRS นี้ออกแบบมาให้นักศึกษาสามารถ:
- ✅ เข้าใจง่าย ไม่ซับซ้อน
- ✅ ทำตามได้จริงใน 1 เดือน
- ✅ เรียนรู้ Full-Stack Development
- ✅ มี code examples ที่ใช้ได้จริง
- ✅ มีแผนการทำงานที่ชัดเจน
---
