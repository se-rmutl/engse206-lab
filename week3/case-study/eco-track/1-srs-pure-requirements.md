# Software Requirements Specification (SRS)
## ระบบติดตาม Carbon Footprint - EcoTrack

**Document ID:** SRS-ECO-001  
**Version:** 1.0  
**วันที่:** มีนาคม 2567  
**สถานะ:** Final  
**จัดทำโดย:** ทีมวิศวกรรมซอฟต์แวร์ มหาวิทยาลัย  

---

## Revision History

| Version | วันที่ | ผู้แก้ไข | รายละเอียด |
|---------|--------|----------|-------------|
| 0.1 | 01/03/2567 | ทีมพัฒนา | ร่างเอกสารเบื้องต้น |
| 0.5 | 05/03/2567 | ทีมพัฒนา | เพิ่ม functional requirements |
| 0.8 | 08/03/2567 | ทีมพัฒนา | เพิ่ม use cases |
| 1.0 | 10/03/2567 | ทีมพัฒนา | เอกสารฉบับสมบูรณ์ |

---

## สารบัญ

1. [บทนำ (Introduction)](#1-บทนำ-introduction)
2. [คำอธิบายโดยรวม (Overall Description)](#2-คำอธิบายโดยรวม-overall-description)
3. [ความต้องการเฉพาะ (Specific Requirements)](#3-ความต้องการเฉพาะ-specific-requirements)
4. [Use Cases](#4-use-cases)
5. [ภาคผนวก (Appendices)](#5-ภาคผนวก-appendices)

---

## 1. บทนำ (Introduction)

### 1.1 วัตถุประสงค์ (Purpose)

เอกสาร Software Requirements Specification (SRS) ฉบับนี้ระบุข้อกำหนดสำหรับแอปพลิเคชัน "EcoTrack" ซึ่งเป็นเครื่องมือสำหรับนักศึกษาและบุคลากรของมหาวิทยาลัยในการติดตาม วิเคราะห์ และลดการปล่อยก๊าซเรือนกระจา (Carbon Footprint) ของตนเอง เพื่อสนับสนุนเป้าหมาย Carbon Neutral University 2030

### 1.2 ขอบเขต (Scope)

**ชื่อซอฟต์แวร์:** EcoTrack - Carbon Footprint Tracker  
**ประเภท:** Mobile & Web Application

**สิ่งที่ระบบจะทำ:**
- บันทึกและติดตามการเดินทาง (รถยนต์, รถไฟฟ้า, จักรยาน, เดิน)
- บันทึกการใช้พลังงาน (ไฟฟ้า, น้ำ)
- จัดการและติดตามการทิ้งขยะและรีไซเคิล
- คำนวณ Carbon Footprint อัตโนมัติ
- แสดงรายงานและสถิติแบบ Real-time
- ระบบ Gamification และการให้คะแนน
- เปรียบเทียบข้อมูลกับผู้ใช้อื่นแบบไม่ระบุตัวตน
- ให้คำแนะนำในการลด Carbon Footprint

**สิ่งที่ระบบจะไม่ทำ:**
- ไม่มีการซื้อขาย Carbon Credit
- ไม่มีการเชื่อมต่อกับระบบภายนอกมหาวิทยาลัย
- ไม่มีการแชร์ข้อมูลส่วนตัวไปยัง Social Media
- ไม่มีระบบการเงินหรือการชำระเงิน

### 1.3 คำนิยาม คำย่อ และตัวย่อ

| คำศัพท์ | คำอธิบาย |
|---------|----------|
| **Carbon Footprint** | ปริมาณการปล่อยก๊าซเรือนกระจาที่เกิดจากกิจกรรมของบุคคล |
| **User** | นักศึกษาหรือบุคลากรมหาวิทยาลัยที่ลงทะเบียนในระบบ |
| **Admin** | ผู้ดูแลระบบที่มีสิทธิ์จัดการข้อมูลและดูรายงานรวม |
| **Carbon Points** | คะแนนที่ได้จากการทำกิจกรรมลด Carbon |
| **Badge** | เหรียญตราที่ได้รับจากการบรรลุเป้าหมาย |
| **CO2e** | Carbon Dioxide Equivalent (หน่วยวัด Carbon) |
| **kWh** | Kilowatt-hour (หน่วยการใช้ไฟฟ้า) |

### 1.4 เอกสารอ้างอิง (References)

1. IEEE Std 830-1998 - IEEE Recommended Practice for Software Requirements Specifications
2. แผนยุทธศาสตร์ Carbon Neutral University 2030
3. มาตรฐาน ISO 14064-1:2018 Greenhouse gases
4. Thailand Greenhouse Gas Management Organization (TGO) Guidelines

### 1.5 ภาพรวม (Overview)

เอกสารนี้ประกอบด้วย 5 ส่วนหลัก:
- ส่วนที่ 1: บทนำและวัตถุประสงค์
- ส่วนที่ 2: คำอธิบายโดยรวมของระบบ
- ส่วนที่ 3: ความต้องการเฉพาะทั้ง Functional และ Non-functional
- ส่วนที่ 4: Use Cases และ Scenarios
- ส่วนที่ 5: ภาคผนวกและข้อมูลเพิ่มเติม

---

## 2. คำอธิบายโดยรวม (Overall Description)

### 2.1 มุมมองผลิตภัณฑ์ (Product Perspective)

EcoTrack เป็นระบบ standalone application ที่ทำงานผ่าน mobile และ web browser มีฐานข้อมูลกลางสำหรับเก็บข้อมูลของมหาวิทยาลัย และสามารถทำงาน offline mode สำหรับการบันทึกข้อมูลพื้นฐาน

### 2.2 ฟังก์ชันของผลิตภัณฑ์ (Product Functions)

ฟังก์ชันหลักของระบบ:
1. **การจัดการผู้ใช้** - ลงทะเบียน, เข้าสู่ระบบ, จัดการโปรไฟล์
2. **การบันทึกกิจกรรม** - บันทึกการเดินทาง, พลังงาน, ขยะ
3. **การคำนวณ Carbon** - คำนวณอัตโนมัติตามสูตรมาตรฐาน TGO
4. **การแสดงผลและรายงาน** - Dashboard, กราฟ, สถิติ
5. **ระบบ Gamification** - Points, Badges, Leaderboard
6. **การให้คำแนะนำ** - Tips การลด Carbon ตาม behavior
7. **การจัดการระบบ** - Admin dashboard, รายงานรวม

### 2.3 ลักษณะผู้ใช้ (User Characteristics)

**นักศึกษา (Students)**
- จำนวน: ประมาณ 12,000 คน
- อายุ: 18-25 ปี
- ทักษะ: ใช้ smartphone และ social media เป็น
- ความถี่: ใช้งานทุกวันถึง 2-3 ครั้งต่อสัปดาห์
- แรงจูงใจ: คะแนน, badges, การแข่งขันกับเพื่อน

**บุคลากร (Staff)**
- จำนวน: ประมาณ 1,500 คน
- อายุ: 25-60 ปี
- ทักษะ: ใช้คอมพิวเตอร์พื้นฐานได้
- ความถี่: ใช้งานสัปดาห์ละครั้ง
- แรงจูงใจ: ลดค่าใช้จ่าย, สุขภาพ, สิ่งแวดล้อม

**ผู้ดูแลระบบ (Administrators)**
- จำนวน: 3-5 คน
- ทักษะ: มีความรู้ด้าน IT และสิ่งแวดล้อม
- ความถี่: ใช้งานทุกวัน
- หน้าที่: ดูรายงาน, จัดการข้อมูล, ตั้งค่าระบบ

### 2.4 ข้อจำกัด (Constraints)

1. **ข้อจำกัดด้านเวลา** - ต้องพัฒนาให้เสร็จภายใน 3 เดือน
2. **ข้อจำกัดด้านงบประมาณ** - งบประมาณ 500,000 บาท
3. **ข้อจำกัดด้านเทคโนโลยี** - ต้องใช้ cloud services ของมหาวิทยาลัย
4. **ข้อจำกัดด้านกฎหมาย** - ต้องปฏิบัติตาม PDPA
5. **ข้อจำกัดด้านมาตรฐาน** - ต้องใช้สูตรคำนวณตามมาตรฐาน TGO

### 2.5 สมมติฐานและการพึ่งพา (Assumptions and Dependencies)

**สมมติฐาน:**
- ผู้ใช้ทุกคนมี smartphone หรือคอมพิวเตอร์
- มหาวิทยาลัยมีโครงสร้างพื้นฐาน IT ที่พร้อม
- ผู้ใช้ยินดีแชร์ข้อมูลเพื่อสิ่งแวดล้อม
- มีข้อมูล emission factors ที่เป็นมาตรฐาน

**การพึ่งพา:**
- ระบบ authentication ของมหาวิทยาลัย
- Cloud infrastructure ของมหาวิทยาลัย
- ข้อมูล emission factors จาก TGO
- ความร่วมมือจากนักศึกษาและบุคลากร

---

## 3. ความต้องการเฉพาะ (Specific Requirements)

### 3.1 ความต้องการด้านหน้าที่ (Functional Requirements)

#### FR-001: การลงทะเบียนและเข้าสู่ระบบ
**คำอธิบาย:** ระบบต้องอนุญาตให้ผู้ใช้ลงทะเบียนด้วย email มหาวิทยาลัย และเข้าสู่ระบบด้วย Single Sign-On (SSO)  
**ระดับความสำคัญ:** สูง  
**Acceptance Criteria:**
- ระบบต้องตรวจสอบ email domain ของมหาวิทยาลัย
- รองรับ SSO ผ่านระบบกลางของมหาวิทยาลัย
- บันทึก profile พื้นฐาน (ชื่อ, คณะ, ประเภทผู้ใช้)
- Session timeout หลังไม่ใช้งาน 30 นาที

#### FR-002: การบันทึกการเดินทาง
**คำอธิบาย:** ระบบต้องอนุญาตให้ผู้ใช้บันทึกข้อมูลการเดินทางในแต่ละวัน  
**ระดับความสำคัญ:** สูง  
**Acceptance Criteria:**
- เลือกประเภท: เดิน, จักรยาน, รถไฟฟ้า, รถเมล์, รถยนต์, มอเตอร์ไซค์
- ระบุระยะทาง (km) หรือเวลา (นาที)
- บันทึกวัตถุประสงค์การเดินทาง (เรียน, ทำงาน, ส่วนตัว)
- คำนวณ CO2e อัตโนมัติตาม emission factors
- สามารถแก้ไขข้อมูลย้อนหลังได้ไม่เกิน 7 วัน

#### FR-003: การบันทึกการใช้พลังงาน
**คำอธิบาย:** ระบบต้องมีฟังก์ชันให้ผู้ใช้กรอกข้อมูลการใช้พลังงาน  
**ระดับความสำคัญ:** สูง  
**Acceptance Criteria:**
- บันทึกการใช้ไฟฟ้า (kWh) รายเดือน
- บันทึกการใช้น้ำ (หน่วย) รายเดือน
- อัพโหลดรูปบิลหรือมิเตอร์เป็นหลักฐาน
- ระบบ OCR อ่านตัวเลขอัตโนมัติ (optional)
- เปรียบเทียบกับเดือนก่อนหน้า

#### FR-004: การจัดการขยะและรีไซเคิล
**คำอธิบาย:** ระบบต้องให้ผู้ใช้บันทึกการจัดการขยะ  
**ระดับความสำคัญ:** กลาง  
**Acceptance Criteria:**
- บันทึกประเภทขยะ: ทั่วไป, รีไซเคิล, อินทรีย์, อันตราย
- ระบุน้ำหนักโดยประมาณ (kg)
- บันทึกกิจกรรมรีไซเคิล (ขวด, กระดาษ, พลาสติก)
- ได้รับ bonus points สำหรับการรีไซเคิล

#### FR-005: ระบบแต้มและ Gamification
**คำอธิบาย:** ระบบต้องมีการให้คะแนนและ rewards  
**ระดับความสำคัญ:** กลาง  
**Acceptance Criteria:**
- ได้ points จากการบันทึกกิจกรรม
- ได้ bonus points จากกิจกรรม eco-friendly
- มี badges สำหรับ achievements (10+ ประเภท)
- มี levels และ progression system
- แสดง leaderboard แยกตามคณะ

#### FR-006: รายงานสรุปรายเดือน
**คำอธิบาย:** ระบบต้องสร้างรายงานสรุม Carbon Footprint  
**ระดับความสำคัญ:** สูง  
**Acceptance Criteria:**
- แสดง total CO2e รายเดือน
- กราฟแสดงแนวโน้ม (trend)
- เปรียบเทียบกับค่าเฉลี่ยของมหาวิทยาลัย
- breakdown ตามประเภทกิจกรรม
- export เป็น PDF

#### FR-007: การแสดงผล Dashboard
**คำอธิบาย:** ระบบต้องแสดง dashboard แบบ real-time  
**ระดับความสำคัญ:** สูง  
**Acceptance Criteria:**
- แสดง Carbon Footprint วันนี้/สัปดาห์นี้/เดือนนี้
- Pie chart แจกแจงตามประเภทกิจกรรม
- Progress bar เทียบกับเป้าหมายส่วนตัว
- Quick stats (points, rank, streak)
- การแสดงผลต้องใช้เวลาไม่เกิน 3 วินาที

#### FR-008: ระบบการแนะนำ
**คำอธิบาย:** ระบบต้องให้คำแนะนำการลด Carbon  
**ระดับความสำคัญ:** กลาง  
**Acceptance Criteria:**
- แนะนำ tips ตาม behavior ของผู้ใช้
- daily eco tips แบบ push notification
- suggest alternatives (เช่น ใช้รถไฟฟ้าแทนรถยนต์)
- คำนวณ potential savings

#### FR-009: การตั้งเป้าหมายส่วนตัว
**คำอธิบาย:** ผู้ใช้สามารถตั้งเป้าหมายการลด Carbon  
**ระดับความสำคัญ:** กลาง  
**Acceptance Criteria:**
- ตั้งเป้าหมายรายเดือน (% reduction)
- track progress แบบ real-time
- reminder notifications
- celebration เมื่อบรรลุเป้าหมาย

#### FR-010: Admin Dashboard
**คำอธิบาย:** ระบบจัดการสำหรับ admin  
**ระดับความสำคัญ:** กลาง  
**Acceptance Criteria:**
- ดู overview statistics ของทั้งมหาวิทยาลัย
- generate รายงานแยกตามคณะ
- จัดการ badges และ rewards
- ส่ง announcements ถึงผู้ใช้
- export ข้อมูลเป็น CSV

### 3.2 ความต้องการที่ไม่ใช่ด้านหน้าที่ (Non-functional Requirements)

#### NFR-001: ประสิทธิภาพ (Performance)
- หน้า dashboard โหลดภายใน 3 วินาที
- รองรับผู้ใช้พร้อมกัน 1,000 คน
- Response time API < 2 วินาที
- Database query < 1 วินาที
- Mobile app ขนาด < 50 MB

#### NFR-002: ความปลอดภัย (Security)
- เข้ารหัสข้อมูลด้วย AES-256
- ใช้ HTTPS สำหรับทุก connections
- ปฏิบัติตาม PDPA
- Regular security audits
- Backup ข้อมูลทุกวัน

#### NFR-003: ความสามารถในการใช้งาน (Usability)
- ผู้ใช้ใหม่บันทึกกิจกรรมแรกได้ภายใน 3 นาที
- User satisfaction score > 4.0/5.0
- รองรับ Thai และ English
- Accessible ตามมาตรฐาน WCAG 2.1 Level AA
- Tutorial และ onboarding guide

#### NFR-004: ความเข้ากันได้ (Compatibility)
- iOS 13.0+ และ Android 8.0+
- Chrome, Firefox, Safari, Edge เวอร์ชันล่าสุด
- Responsive design สำหรับ mobile/tablet/desktop
- Offline mode สำหรับ basic features

#### NFR-005: ความน่าเชื่อถือ (Reliability)
- Uptime 99.5%
- Mean Time Between Failures (MTBF) > 720 hours
- Mean Time To Repair (MTTR) < 4 hours
- Data consistency 99.99%
- Graceful degradation

#### NFR-006: ความสามารถในการขยายตัว (Scalability)
- รองรับผู้ใช้เพิ่มได้ถึง 50,000 คน
- Horizontal scaling capability
- Database partitioning ready
- Microservices architecture

### 3.3 ความต้องการด้าน Interface ภายนอก (External Interface Requirements)

#### User Interfaces
- Mobile app native UI (iOS/Android)
- Web responsive design
- Dark mode support
- Customizable dashboard
- Multi-language support

#### Hardware Interfaces
- GPS สำหรับ tracking การเดินทาง (optional)
- Camera สำหรับ scan QR code และถ่ายรูปบิล
- Push notifications

#### Software Interfaces
- University SSO system
- Email service (SMTP)
- Cloud storage (AWS S3 compatible)
- Analytics platform (Google Analytics)

#### Communications Interfaces
- RESTful API
- WebSocket for real-time updates
- JSON data format
- OAuth 2.0 authentication

---

## 4. Use Cases

### 4.1 Use Case Diagram

```
                    EcoTrack System
    ┌────────────────────────────────────────────────┐
    │                                                │
    │    ○ UC-01: Register/Login                    │
    │    │                                           │
    │    ○ UC-02: Record Travel                     │
    │    │                                           │
    │    ○ UC-03: Record Energy Usage               │
    │    │                                           │
User ──┼────○ UC-04: Record Waste Management         │
    │    │                                           │
    │    ○ UC-05: View Dashboard                    │
    │    │                                           │
    │    ○ UC-06: Set Personal Goals                │
    │    │                                           │
    │    ○ UC-07: View Reports                      │
    │    │                                           │
    │    ○ UC-08: Earn Badges                       │
    │    │                                           │
    │                                                │
Admin ─┼────○ UC-09: Manage System                   │
    │    │                                           │
    │    ○ UC-10: Generate University Reports       │
    │                                                │
    └────────────────────────────────────────────────┘
```

### 4.2 Use Case Descriptions

#### UC-01: Register/Login
**Primary Actor:** User  
**Preconditions:** มี email มหาวิทยาลัย  
**Main Flow:**
1. ผู้ใช้เข้าหน้า login
2. เลือก "Sign in with University Account"
3. ระบบ redirect ไป SSO
4. ผู้ใช้กรอก credentials
5. ระบบตรวจสอบและสร้าง profile
6. แสดง onboarding tutorial (ครั้งแรก)
7. เข้าสู่ dashboard

**Alternative Flow:**
- 4a. Credentials ไม่ถูกต้อง: แสดง error
- 5a. ผู้ใช้ใหม่: สร้าง profile ใหม่

**Postconditions:** ผู้ใช้เข้าสู่ระบบและมี active session

#### UC-02: Record Travel
**Primary Actor:** User  
**Preconditions:** Login แล้ว  
**Main Flow:**
1. ผู้ใช้เลือก "บันทึกการเดินทาง"
2. เลือกประเภทการเดินทาง
3. ระบุระยะทางหรือเวลา
4. เลือกวัตถุประสงค์
5. ระบบคำนวณ CO2e
6. แสดงผลและ points ที่ได้
7. บันทึกข้อมูล

**Alternative Flow:**
- 3a. ใช้ GPS tracking: ระบบคำนวณระยะทางอัตโนมัติ
- 5a. เลือกการเดินทางที่เป็นมิตร: ได้ bonus points

**Postconditions:** ข้อมูลการเดินทางถูกบันทึกและ carbon footprint อัพเดท

#### UC-03: Record Energy Usage
**Primary Actor:** User  
**Preconditions:** Login แล้ว  
**Main Flow:**
1. ผู้ใช้เลือก "บันทึกการใช้พลังงาน"
2. เลือกประเภท (ไฟฟ้า/น้ำ)
3. กรอกหน่วยการใช้งาน
4. อัพโหลดรูปบิล (optional)
5. ระบบคำนวณ CO2e
6. เปรียบเทียบกับเดือนก่อน
7. บันทึกข้อมูล

**Alternative Flow:**
- 4a. ใช้ OCR: ระบบอ่านตัวเลขอัตโนมัติ
- 6a. ใช้ลดลง: แสดง congratulations

**Postconditions:** ข้อมูลพลังงานถูกบันทึก

#### UC-04: Record Waste Management
**Primary Actor:** User  
**Preconditions:** Login แล้ว  
**Main Flow:**
1. ผู้ใช้เลือก "บันทึกการจัดการขยะ"
2. เลือกประเภทขยะ
3. ระบุน้ำหนักโดยประมาณ
4. บันทึกกิจกรรมรีไซเคิล
5. ระบบคำนวณ impact
6. แสดง points และ tips
7. บันทึกข้อมูล

**Postconditions:** ข้อมูลขยะถูกบันทึก

#### UC-05: View Dashboard
**Primary Actor:** User  
**Preconditions:** Login แล้ว  
**Main Flow:**
1. ผู้ใช้เข้า dashboard
2. ระบบแสดง current carbon footprint
3. แสดงกราฟและ statistics
4. แสดง points และ ranking
5. แสดง daily tips
6. ผู้ใช้สามารถ customize widgets

**Postconditions:** ผู้ใช้เห็นข้อมูลล่าสุด

#### UC-06: Set Personal Goals
**Primary Actor:** User  
**Preconditions:** มีข้อมูลอย่างน้อย 1 เดือน  
**Main Flow:**
1. ผู้ใช้เลือก "ตั้งเป้าหมาย"
2. เลือกประเภทเป้าหมาย
3. กำหนดเป้า (% reduction)
4. กำหนดระยะเวลา
5. ระบบแสดง feasibility
6. ยืนยันเป้าหมาย
7. ตั้ง reminders

**Postconditions:** เป้าหมายถูกบันทึก

#### UC-07: View Reports
**Primary Actor:** User  
**Preconditions:** มีข้อมูลการใช้งาน  
**Main Flow:**
1. ผู้ใช้เลือก "รายงาน"
2. เลือกช่วงเวลา
3. ระบบ generate รายงาน
4. แสดงกราฟและตาราง
5. เปรียบเทียบกับค่าเฉลี่ย
6. Option to export PDF

**Postconditions:** รายงานถูกแสดง

#### UC-08: Earn Badges
**Primary Actor:** User  
**Preconditions:** ทำกิจกรรมตามเงื่อนไข  
**Main Flow:**
1. ผู้ใช้ทำกิจกรรมครบตามเกณฑ์
2. ระบบตรวจสอบ achievement
3. แสดง notification "New Badge!"
4. อัพเดท profile และ points
5. แชร์ achievement (optional)

**Postconditions:** Badge ถูกเพิ่มใน profile

#### UC-09: Manage System
**Primary Actor:** Admin  
**Preconditions:** มีสิทธิ์ admin  
**Main Flow:**
1. Admin เข้า admin dashboard
2. ดู system statistics
3. จัดการ users/badges/rewards
4. ส่ง announcements
5. ตั้งค่า emission factors
6. Generate reports

**Postconditions:** ระบบถูกอัพเดท

#### UC-10: Generate University Reports
**Primary Actor:** Admin  
**Preconditions:** มีข้อมูลเพียงพอ  
**Main Flow:**
1. Admin เลือก "University Report"
2. กำหนด parameters (คณะ, ช่วงเวลา)
3. ระบบรวบรวมข้อมูล
4. สร้างรายงานและกราฟ
5. Export เป็น PDF/Excel
6. ส่ง email ถึงผู้บริหาร

**Postconditions:** รายงานถูกสร้างและส่ง

---

## 5. ภาคผนวก (Appendices)

### ภาคผนวก A: Emission Factors

| กิจกรรม | Emission Factor | หน่วย |
|---------|-----------------|-------|
| รถยนต์ส่วนตัว | 0.21 | kg CO2e/km |
| มอเตอร์ไซค์ | 0.11 | kg CO2e/km |
| รถเมล์ | 0.04 | kg CO2e/km |
| รถไฟฟ้า | 0.02 | kg CO2e/km |
| จักรยาน | 0 | kg CO2e/km |
| เดิน | 0 | kg CO2e/km |
| ไฟฟ้า | 0.5610 | kg CO2e/kWh |
| น้ำประปา | 0.2720 | kg CO2e/m³ |

### ภาคผนวก B: Badge Categories

| Badge | เงื่อนไข | Points |
|-------|---------|--------|
| Eco Starter | บันทึกกิจกรรม 7 วันติดต่อกัน | 50 |
| Green Commuter | ใช้ขนส่งสาธารณะ 20 ครั้ง | 100 |
| Energy Saver | ลดการใช้ไฟ 10% | 150 |
| Zero Hero | Zero carbon day 5 วัน | 200 |
| Recycle Master | รีไซเคิล 50 kg | 100 |
| Carbon Cutter | ลด carbon 25% ใน 1 เดือน | 300 |
| Eco Warrior | ครบ 6 เดือนในระบบ | 500 |
| Green Champion | Top 10 ของคณะ | 1000 |

### ภาคผนวก C: การวิเคราะห์ความเสี่ยง

| ความเสี่ยง | ความน่าจะเป็น | ผลกระทบ | การป้องกัน |
|-----------|--------------|---------|-----------|
| ผู้ใช้ไม่บันทึกข้อมูล | สูง | สูง | Gamification, reminders |
| ข้อมูลไม่ถูกต้อง | ปานกลาง | ปานกลาง | Validation, verification |
| ระบบล่ม | ต่ำ | สูง | Backup, redundancy |
| Privacy concerns | ปานกลาง | สูง | PDPA compliance, transparency |

### ภาคผนวก D: อภิธานศัพท์

| คำศัพท์ | คำอธิบาย |
|---------|----------|
| Carbon Neutral | การปล่อยและดูดซับ carbon สมดุล |
| Emission Factor | ค่าสัมประสิทธิ์การปล่อย CO2 |
| Gamification | การใช้กลไกเกมในแอปพลิเคชัน |
| Leaderboard | ตารางแสดงอันดับผู้ใช้ |
| OCR | Optical Character Recognition |
| SSO | Single Sign-On |
| Streak | การทำกิจกรรมต่อเนื่อง |

---

**หมายเหตุ:** เอกสารนี้เป็น living document ที่อาจมีการแก้ไขตามความเหมาะสม การเปลี่ยนแปลงทุกครั้งต้องผ่านการอนุมัติจาก stakeholders