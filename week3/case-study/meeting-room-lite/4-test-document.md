# Test Document
## ระบบจองห้องประชุม MeetingRoom Lite

**Document ID:** TD-MRL-001  
**Version:** 1.0  
**วันที่:** มีนาคม 2567  
**สถานะ:** Final  

---

## สารบัญ

1. [บทนำ (Introduction)](#1-บทนำ-introduction)
2. [Test Strategy](#2-test-strategy)
3. [Test Environment](#3-test-environment)
4. [Test Cases](#4-test-cases)
5. [Test Data](#5-test-data)
6. [Test Execution](#6-test-execution)
7. [Bug Report Template](#7-bug-report-template)
8. [Test Summary Report](#8-test-summary-report)

---

## 1. บทนำ (Introduction)

### 1.1 วัตถุประสงค์
เอกสารนี้กำหนดแนวทางการทดสอบระบบ MeetingRoom Lite เพื่อให้มั่นใจว่าระบบทำงานได้ตามความต้องการที่กำหนดใน SRS

### 1.2 ขอบเขตการทดสอบ
- **In Scope:** ทุก functional requirements ใน SRS
- **Out of Scope:** Performance testing, Security testing ขั้นสูง

### 1.3 เอกสารอ้างอิง
- SRS-MRL-001: Software Requirements Specification
- SDD-MRL-001: Software Design Document

---

## 2. Test Strategy

### 2.1 ระดับการทดสอบ (Test Levels)

1. **Unit Testing** - ทดสอบ functions/methods
2. **Integration Testing** - ทดสอบการทำงานร่วมกันของ components
3. **System Testing** - ทดสอบระบบทั้งหมด
4. **User Acceptance Testing (UAT)** - ทดสอบโดยผู้ใช้จริง

### 2.2 ประเภทการทดสอบ (Test Types)

- **Functional Testing** - ทดสอบ features ตาม requirements
- **UI Testing** - ทดสอบ user interface
- **API Testing** - ทดสอบ backend endpoints
- **Database Testing** - ทดสอบ data integrity
- **Usability Testing** - ทดสอบความง่ายในการใช้งาน

### 2.3 เกณฑ์การผ่าน (Pass Criteria)

- ทุก test cases ที่มี priority High ต้องผ่าน 100%
- Test cases priority Medium ต้องผ่านอย่างน้อย 90%
- ไม่มี critical bugs ที่ยังไม่ได้แก้ไข

---

## 3. Test Environment

### 3.1 Hardware Requirements
- Computer with 4GB RAM minimum
- Network connection

### 3.2 Software Requirements
- **OS:** Windows 10/11, macOS, Linux
- **Browsers:** Chrome, Firefox, Safari (latest versions)
- **Database:** PostgreSQL 14.x
- **Tools:** Postman, pgAdmin

### 3.3 Test Data Requirements
- Test users with different roles
- Sample room data
- Sample booking data

---

## 4. Test Cases

### 4.1 Authentication Test Cases

#### TC-001: User Registration - Valid Data
**Priority:** High  
**Preconditions:** ไม่มี user ที่ใช้ email เดียวกันในระบบ

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | เข้าหน้า Register | แสดง form ลงทะเบียน |
| 2 | กรอก email: test@example.com | ยอมรับ input |
| 3 | กรอก password: Test123! | ยอมรับ input |
| 4 | กรอก name: Test User | ยอมรับ input |
| 5 | คลิก "Register" | แสดงข้อความ "ลงทะเบียนสำเร็จ" |
| 6 | ตรวจสอบ database | มี user record ใหม่ |

**Test Data:**
```
Email: test@example.com
Password: Test123!
Name: Test User
```

#### TC-002: User Registration - Duplicate Email
**Priority:** High  
**Preconditions:** มี user ที่ใช้ email: existing@example.com อยู่แล้ว

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | เข้าหน้า Register | แสดง form ลงทะเบียน |
| 2 | กรอก email: existing@example.com | ยอมรับ input |
| 3 | กรอก password และ name | ยอมรับ input |
| 4 | คลิก "Register" | แสดง error "Email นี้ถูกใช้งานแล้ว" |

#### TC-003: User Login - Valid Credentials
**Priority:** High  
**Preconditions:** มี user ในระบบแล้ว

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | เข้าหน้า Login | แสดง form login |
| 2 | กรอก email ที่ถูกต้อง | ยอมรับ input |
| 3 | กรอก password ที่ถูกต้อง | ยอมรับ input |
| 4 | คลิก "Login" | เข้าสู่ระบบสำเร็จ |
| 5 | ตรวจสอบ | Redirect ไปหน้า Room List |
| 6 | ตรวจสอบ localStorage | มี token บันทึกอยู่ |

#### TC-004: User Login - Invalid Credentials
**Priority:** High  
**Preconditions:** ไม่มี

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | เข้าหน้า Login | แสดง form login |
| 2 | กรอก email/password ผิด | ยอมรับ input |
| 3 | คลิก "Login" | แสดง error "Email หรือ password ไม่ถูกต้อง" |

### 4.2 Room Management Test Cases

#### TC-005: View Room List
**Priority:** High  
**Preconditions:** Login แล้ว, มีห้องในระบบ

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | เข้าหน้า Rooms | แสดงรายการห้องทั้งหมด |
| 2 | ตรวจสอบข้อมูลห้อง | แสดงชื่อ, ความจุ, ชั้น |
| 3 | ตรวจสอบสถานะ | แสดงสถานะว่าง/ไม่ว่าง |

#### TC-006: Filter Rooms by Date/Time
**Priority:** Medium  
**Preconditions:** Login แล้ว, มีห้องและการจองในระบบ

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | เลือกวันที่ | Date picker ทำงาน |
| 2 | เลือกเวลา 10:00-12:00 | Time picker ทำงาน |
| 3 | ระบบ refresh | แสดงเฉพาะห้องที่ว่างในช่วงเวลานั้น |

#### TC-007: Admin Create Room
**Priority:** Medium  
**Preconditions:** Login ด้วย admin account

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | เข้าหน้า Admin | แสดง room management |
| 2 | คลิก "Add Room" | แสดง form เพิ่มห้อง |
| 3 | กรอกข้อมูลห้อง | Form validation ทำงาน |
| 4 | คลิก "Save" | ห้องใหม่ถูกเพิ่ม |
| 5 | ตรวจสอบ | ห้องใหม่แสดงในรายการ |

### 4.3 Booking Test Cases

#### TC-008: Create Booking - Success
**Priority:** High  
**Preconditions:** Login แล้ว, มีห้องว่าง

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | เลือกห้องที่ว่าง | แสดงปุ่ม "จอง" |
| 2 | คลิก "จอง" | แสดง booking form |
| 3 | กรอกข้อมูลการจอง | Form validation ทำงาน |
| 4 | คลิก "ยืนยัน" | แสดง "จองห้องสำเร็จ" |
| 5 | ตรวจสอบ database | มี booking record ใหม่ |

**Test Data:**
```
Room: ห้องประชุม A
Date: Tomorrow
Time: 09:00 - 10:00
Title: Test Meeting
```

#### TC-009: Create Booking - Conflict
**Priority:** High  
**Preconditions:** มีการจองในช่วงเวลาเดียวกันแล้ว

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | เลือกห้องและเวลาที่มีการจองแล้ว | ปุ่มจองแสดง "ไม่ว่าง" |
| 2 | พยายามจองผ่าน API | ได้รับ error 409 |
| 3 | ตรวจสอบ message | "ห้องไม่ว่างในช่วงเวลานี้" |

#### TC-010: View My Bookings
**Priority:** High  
**Preconditions:** มีการจองของ user

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | เข้าหน้า "My Bookings" | แสดงรายการการจอง |
| 2 | ตรวจสอบ sections | แยก upcoming/past |
| 3 | ตรวจสอบข้อมูล | แสดงวันที่, เวลา, ห้อง |

#### TC-011: Cancel Booking
**Priority:** High  
**Preconditions:** มีการจองในอนาคต

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | เลือกการจองที่ต้องการยกเลิก | แสดงปุ่ม "ยกเลิก" |
| 2 | คลิก "ยกเลิก" | แสดง confirmation dialog |
| 3 | ยืนยันการยกเลิก | แสดง "ยกเลิกสำเร็จ" |
| 4 | ตรวจสอบ | การจองหายจากรายการ |
| 5 | ตรวจสอบห้อง | ห้องแสดงสถานะว่าง |

### 4.4 API Test Cases

#### TC-012: API Authentication
**Priority:** High  
**Tool:** Postman

| Step | Action | Expected Result |
|------|--------|-----------------|
| 1 | Call API without token | Return 401 Unauthorized |
| 2 | Call API with invalid token | Return 401 Invalid token |
| 3 | Call API with valid token | Return 200 OK |

#### TC-013: API Input Validation
**Priority:** Medium  
**Tool:** Postman

| Test | Input | Expected Result |
|------|-------|-----------------|
| Email format | "notanemail" | 400 Bad Request |
| Password length | "123" | 400 "Password ต้องมีอย่างน้อย 6 ตัวอักษร" |
| Missing fields | {} | 400 "Required fields missing" |
| Invalid date | "2020-01-01" | 400 "Cannot book in the past" |

### 4.5 UI/UX Test Cases

#### TC-014: Responsive Design
**Priority:** Medium  
**Devices:** Desktop, Tablet, Mobile

| Device | Test | Expected Result |
|--------|------|-----------------|
| Desktop (1920x1080) | View all pages | Layout correct, no overflow |
| Tablet (768x1024) | View all pages | Responsive layout works |
| Mobile (375x667) | View all pages | Mobile-friendly layout |

#### TC-015: Browser Compatibility
**Priority:** Medium  
**Browsers:** Chrome, Firefox, Safari

| Browser | Test | Expected Result |
|---------|------|-----------------|
| Chrome 90+ | All features | Works correctly |
| Firefox 88+ | All features | Works correctly |
| Safari 14+ | All features | Works correctly |

---

## 5. Test Data

### 5.1 Test Users

| Email | Password | Role | Name |
|-------|----------|------|------|
| admin@test.com | Admin123! | admin | Test Admin |
| user1@test.com | User123! | user | Test User 1 |
| user2@test.com | User123! | user | Test User 2 |

### 5.2 Test Rooms

| Name | Capacity | Floor | Status |
|------|----------|-------|---------|
| Test Room A | 10 | 3 | active |
| Test Room B | 20 | 3 | active |
| Test Room C | 5 | 4 | active |
| Maintenance Room | 15 | 2 | inactive |

### 5.3 Test Bookings

| User | Room | Date | Time | Title |
|------|------|------|------|-------|
| user1@test.com | Test Room A | Tomorrow | 09:00-10:00 | Morning Meeting |
| user2@test.com | Test Room B | Tomorrow | 14:00-16:00 | Project Review |

---

## 6. Test Execution

### 6.1 Test Execution Steps

1. **Prepare Test Environment**
   - Clean database
   - Insert test data
   - Start servers

2. **Execute Test Cases**
   - Run in sequence
   - Document results
   - Take screenshots for failures

3. **Log Defects**
   - Use bug report template
   - Assign severity/priority
   - Attach evidence

### 6.2 Test Execution Schedule

| Phase | Duration | Test Cases |
|-------|----------|------------|
| Unit Testing | 2 days | Backend functions |
| Integration Testing | 2 days | API endpoints |
| System Testing | 3 days | All test cases |
| UAT | 2 days | Key user flows |

### 6.3 Test Execution Checklist

- [ ] Test environment ready
- [ ] Test data prepared
- [ ] Test tools installed
- [ ] Test cases reviewed
- [ ] Bug tracking system ready

---

## 7. Bug Report Template

### Bug Report Form

**Bug ID:** BUG-XXX  
**Date:** DD/MM/YYYY  
**Reporter:** Name  

**Summary:** [One line description]

**Severity:**
- [ ] Critical - System crash, data loss
- [ ] Major - Feature not working
- [ ] Minor - UI issues
- [ ] Trivial - Cosmetic issues

**Priority:**
- [ ] High - Fix immediately
- [ ] Medium - Fix in this release
- [ ] Low - Fix if time permits

**Environment:**
- Browser: 
- OS: 
- User Role:

**Steps to Reproduce:**
1. 
2. 
3. 

**Expected Result:**

**Actual Result:**

**Screenshots/Evidence:**

**Additional Notes:**

### Example Bug Report

**Bug ID:** BUG-001  
**Date:** 25/03/2567  
**Reporter:** Tester 1  

**Summary:** Cannot book room for time in the past

**Severity:** Minor  
**Priority:** Low  

**Environment:**
- Browser: Chrome 121
- OS: Windows 11
- User Role: Regular User

**Steps to Reproduce:**
1. Login as regular user
2. Select yesterday's date
3. Try to book any room

**Expected Result:**
Date picker should not allow past dates

**Actual Result:**
Can select past date but booking fails with error

**Screenshots/Evidence:**
[Screenshot attached]

---

## 8. Test Summary Report

### 8.1 Test Execution Summary

| Test Type | Total | Passed | Failed | Blocked | Pass Rate |
|-----------|-------|--------|--------|---------|-----------|
| Functional | 15 | 14 | 1 | 0 | 93% |
| API | 10 | 10 | 0 | 0 | 100% |
| UI/UX | 5 | 4 | 1 | 0 | 80% |
| **Total** | **30** | **28** | **2** | **0** | **93%** |

### 8.2 Defect Summary

| Severity | Open | Closed | Total |
|----------|------|--------|-------|
| Critical | 0 | 0 | 0 |
| Major | 0 | 1 | 1 |
| Minor | 1 | 2 | 3 |
| Trivial | 1 | 0 | 1 |
| **Total** | **2** | **3** | **5** |

### 8.3 Test Metrics

- **Test Coverage:** 95% of requirements tested
- **Defect Density:** 0.17 defects per test case
- **Test Execution Time:** 9 days
- **Retest Success Rate:** 100%

### 8.4 Recommendations

1. **Ready for Release:** ✅ Yes (with minor issues noted)
2. **Known Issues:**
   - Past date selection in date picker (Minor)
   - Mobile layout issue on Safari (Trivial)
3. **Future Improvements:**
   - Add automated testing
   - Improve error messages
   - Add more validation

### 8.5 Sign-off

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Test Lead | ____________ | ____________ | _____ |
| Project Manager | ____________ | ____________ | _____ |
| Product Owner | ____________ | ____________ | _____ |

---

## ภาคผนวก (Appendix)

### A. Test Tools

1. **Postman** - API testing
2. **Chrome DevTools** - UI debugging
3. **pgAdmin** - Database verification
4. **BrowserStack** - Cross-browser testing (optional)

### B. Test Scripts

**SQL Script for Test Data:**
```sql
-- Clean database
TRUNCATE TABLE bookings CASCADE;
TRUNCATE TABLE rooms CASCADE;
TRUNCATE TABLE users CASCADE;

-- Insert test users
INSERT INTO users (email, password, name, role) VALUES
('admin@test.com', '$2b$10$...', 'Test Admin', 'admin'),
('user1@test.com', '$2b$10$...', 'Test User 1', 'user'),
('user2@test.com', '$2b$10$...', 'Test User 2', 'user');

-- Insert test rooms
INSERT INTO rooms (name, capacity, floor) VALUES
('Test Room A', 10, 3),
('Test Room B', 20, 3),
('Test Room C', 5, 4);
```

### C. Automated Test Example

**Jest Test Example:**
```javascript
describe('Authentication API', () => {
  test('should register new user', async () => {
    const response = await request(app)
      .post('/api/v1/auth/register')
      .send({
        email: 'newuser@test.com',
        password: 'Test123!',
        name: 'New User'
      });
      
    expect(response.status).toBe(201);
    expect(response.body.success).toBe(true);
  });
  
  test('should not register duplicate email', async () => {
    const response = await request(app)
      .post('/api/v1/auth/register')
      .send({
        email: 'existing@test.com',
        password: 'Test123!',
        name: 'Existing User'
      });
      
    expect(response.status).toBe(400);
    expect(response.body.error.code).toBe('EMAIL_EXISTS');
  });
});
```

---

**หมายเหตุ:** เอกสารนี้เป็นแนวทางการทดสอบที่สามารถปรับเปลี่ยนได้ตามความเหมาะสม ควรอัพเดทผลการทดสอบอย่างสม่ำเสมอ