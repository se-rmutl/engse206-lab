# Software Requirements Specification (SRS)
## ระบบติดตาม Carbon Footprint - EcoTrack

**Document ID:** SRS-ECO-001  
**Version:** 1.0  
**วันที่:** มีนาคม 2568  
**สถานะ:** Final  
**จัดทำโดย:** ทีมวิศวกรรมซอฟต์แวร์ มหาวิทยาลัย  

---

## Revision History

| Version | วันที่ | ผู้แก้ไข | รายละเอียด |
|---------|--------|----------|-------------|
| 0.1 | 01/03/2568 | ทีมพัฒนา | ร่างเอกสารเบื้องต้น |
| 0.5 | 05/03/2568 | ทีมพัฒนา | เพิ่ม functional requirements |
| 0.8 | 08/03/2568 | ทีมพัฒนา | เพิ่ม use cases |
| 1.0 | 10/03/2568 | ทีมพัฒนา | เอกสารฉบับสมบูรณ์ |

---

## สารบัญ

1. [บทนำ (Introduction)](#1-บทนำ-introduction)
2. [คำอธิบายโดยรวม (Overall Description)](#2-คำอธิบายโดยรวม-overall-description)
3. [ความต้องการเฉพาะ (Specific Requirements)](#3-ความต้องการเฉพาะ-specific-requirements)
4. [ภาคผนวก (Appendices)](#4-ภาคผนวก-appendices)

---

## 1. บทนำ (Introduction)

### 1.1 วัตถุประสงค์ (Purpose)

เอกสาร Software Requirements Specification (SRS) ฉบับนี้มีวัตถุประสงค์เพื่อกำหนดความต้องการทั้งหมดของระบบ EcoTrack - แอปพลิเคชันติดตาม Carbon Footprint สำหรับนักศึกษาและบุคลากรมหาวิทยาลัย เพื่อสนับสนุนเป้าหมาย Carbon Neutral University 2030 เอกสารนี้จะเป็นข้อตกลงระหว่างผู้พัฒนาและผู้มีส่วนได้ส่วนเสีย เกี่ยวกับสิ่งที่ระบบจะทำ

### 1.2 ขอบเขต (Scope)

**ชื่อซอฟต์แวร์:** EcoTrack - Carbon Footprint Tracker  
**ประเภท:** Progressive Web Application และ Mobile Application

**สิ่งที่ระบบจะทำ:**
- บันทึกและติดตามกิจกรรมการเดินทางของผู้ใช้
- บันทึกการใช้พลังงาน (ไฟฟ้า น้ำ) รายเดือน
- จัดการและติดตามการทิ้งขยะและรีไซเคิล
- คำนวณ Carbon Footprint อัตโนมัติตามมาตรฐานสากล
- แสดงรายงานและสถิติแบบ real-time
- ระบบแต้มและรางวัล (Gamification)
- เปรียบเทียบข้อมูลกับผู้ใช้อื่นแบบไม่ระบุตัวตน
- ให้คำแนะนำการลด Carbon Footprint

**สิ่งที่ระบบจะไม่ทำ:**
- ไม่มีการซื้อขาย Carbon Credit
- ไม่มีการเชื่อมต่อกับ Social Media ภายนอก
- ไม่มีระบบการเงินหรือการชำระเงิน
- ไม่มีการติดตาม GPS แบบ real-time ตลอดเวลา

### 1.3 คำนิยาม คำย่อ และตัวย่อ

| คำศัพท์ | คำอธิบาย |
|---------|----------|
| **Carbon Footprint** | ปริมาณการปล่อยก๊าซเรือนกระจาที่เกิดจากกิจกรรมของบุคคล |
| **User** | นักศึกษาหรือบุคลากรมหาวิทยาลัยที่ลงทะเบียนในระบบ |
| **Admin** | ผู้ดูแลระบบที่มีสิทธิ์จัดการข้อมูลและดูรายงานรวม |
| **Carbon Points** | คะแนนที่ได้จากการทำกิจกรรมลด Carbon Footprint |
| **Badge** | เหรียญตราที่ได้รับจากการบรรลุเป้าหมายหรือทำกิจกรรมพิเศษ |
| **CO2e** | Carbon Dioxide Equivalent (หน่วยวัดการปล่อยก๊าซเรือนกระจก) |
| **Emission Factor** | ค่าสัมประสิทธิ์ที่ใช้คำนวณการปล่อย CO2 จากกิจกรรม |
| **SSO** | Single Sign-On (ระบบล็อกอินเดียว) |

### 1.4 เอกสารอ้างอิง (References)

1. IEEE Std 830-1998 - IEEE Recommended Practice for Software Requirements Specifications
2. แผนยุทธศาสตร์ Carbon Neutral University 2030
3. Thailand Greenhouse Gas Management Organization (TGO) Guidelines
4. ISO 14064-1:2018 Greenhouse gases - Part 1: Specification with guidance

### 1.5 ภาพรวม (Overview)

เอกสารนี้ประกอบด้วย 4 ส่วนหลัก:
- ส่วนที่ 1: บทนำและวัตถุประสงค์
- ส่วนที่ 2: คำอธิบายโดยรวมของระบบ
- ส่วนที่ 3: ความต้องการเฉพาะทั้ง Functional และ Non-functional
- ส่วนที่ 4: ภาคผนวกและข้อมูลเพิ่มเติม

---

## 2. คำอธิบายโดยรวม (Overall Description)

### 2.1 มุมมองผลิตภัณฑ์ (Product Perspective)

EcoTrack เป็น standalone application ที่ทำงานผ่าน web browser และ mobile application โดยมีฐานข้อมูลกลางสำหรับเก็บข้อมูลของมหาวิทยาลัย ระบบสามารถทำงาน offline ได้สำหรับการบันทึกข้อมูลพื้นฐาน และ sync ข้อมูลเมื่อมีการเชื่อมต่ออินเทอร์เน็ต

### 2.2 ฟังก์ชันของผลิตภัณฑ์ (Product Functions)

ฟังก์ชันหลักของระบบ:
1. **การจัดการผู้ใช้** - ลงทะเบียน, เข้าสู่ระบบ, จัดการโปรไฟล์
2. **การบันทึกกิจกรรม** - บันทึกการเดินทาง, การใช้พลังงาน, การจัดการขยะ
3. **การคำนวณ Carbon Footprint** - คำนวณอัตโนมัติตามสูตรมาตรฐาน
4. **การแสดงผลและรายงาน** - Dashboard, กราฟ, สถิติส่วนตัว
5. **ระบบแต้มและรางวัล** - Points, Badges, Leaderboard, Achievements
6. **การให้คำแนะนำ** - Tips การลด Carbon ตาม behavior pattern
7. **การจัดการระบบ** - Admin dashboard, รายงานระดับมหาวิทยาลัย

### 2.3 ลักษณะผู้ใช้ (User Characteristics)

**นักศึกษา (Students)**
- จำนวน: ประมาณ 12,000 คน
- อายุ: 18-25 ปี
- ทักษะเทคโนโลยี: สูง (digital natives)
- ความถี่การใช้งาน: ทุกวันถึง 2-3 ครั้งต่อสัปดาห์
- แรงจูงใจ: คะแนน, การแข่งขัน, social recognition

**บุคลากร (Staff)**
- จำนวน: ประมาณ 1,500 คน
- อายุ: 25-60 ปี
- ทักษะเทคโนโลยี: ปานกลางถึงสูง
- ความถี่การใช้งาน: สัปดาห์ละครั้งถึงทุกวัน
- แรงจูงใจ: ประหยัดค่าใช้จ่าย, ส่วนร่วมในพันธกิจมหาวิทยาลัย

**ผู้ดูแลระบบ (Administrators)**
- จำนวน: 3-5 คน
- ทักษะ: มีความรู้ด้าน IT และการจัดการสิ่งแวดล้อม
- ความถี่การใช้งาน: ทุกวันทำการ
- หน้าที่: ดูรายงาน, จัดการข้อมูล, ตั้งค่าระบบ

### 2.4 ข้อจำกัด (Constraints)

1. **ข้อจำกัดด้านเวลา** - ต้องพัฒนาและ deploy ภายใน 4 เดือน
2. **ข้อจำกัดด้านงบประมาณ** - งบประมาณรวม 800,000 บาท
3. **ข้อจำกัดด้านเทคโนโลยี** - ต้องใช้ infrastructure ของมหาวิทยาลัย
4. **ข้อจำกัดด้านกฎหมาย** - ต้องปฏิบัติตาม พ.ร.บ. คุ้มครองข้อมูลส่วนบุคคล
5. **ข้อจำกัดด้านมาตรฐาน** - ใช้สูตรคำนวณตามมาตรฐาน TGO และ ISO 14064
6. **ข้อจำกัดด้านภาษา** - รองรับภาษาไทยและอังกฤษ

### 2.5 สมมติฐานและการพึ่งพา (Assumptions and Dependencies)

**สมมติฐาน:**
- ผู้ใช้ทุกคนมี smartphone หรือสามารถเข้าถึงคอมพิวเตอร์ได้
- มหาวิทยาลัยมี infrastructure IT ที่สนับสนุนระบบ
- ผู้ใช้ยินดีให้ความร่วมมือในการบันทึกข้อมูล
- มีข้อมูล emission factors ที่เป็นมาตรฐานและเป็นปัจจุบัน

**การพึ่งพา:**
- ระบบ authentication ของมหาวิทยาลัย (SSO)
- Cloud services หรือ server ของมหาวิทยาลัย
- ข้อมูล emission factors จาก TGO
- ความร่วมมือจากนักศึกษาและบุคลากรในการใช้งาน

---

## 3. ความต้องการเฉพาะ (Specific Requirements)

### 3.1 ความต้องการด้านหน้าที่ (Functional Requirements)

#### FR-001: การลงทะเบียนและเข้าสู่ระบบ
**คำอธิบาย:** ระบบต้องอนุญาตให้ผู้ใช้ลงทะเบียนด้วย email มหาวิทยาลัยและเข้าสู่ระบบผ่าน SSO  
**ระดับความสำคัญ:** สูง  
**Input:** University email, ข้อมูลโปรไฟล์พื้นฐาน  
**Output:** Account ที่ถูกสร้างและ authenticated session  
**การประมวลผล:** 
- ตรวจสอบ email domain ของมหาวิทยาลัย (@university.ac.th)
- เชื่อมต่อกับระบบ SSO ของมหาวิทยาลัย
- สร้างโปรไฟล์ผู้ใช้ด้วยข้อมูลพื้นฐาน (ชื่อ, คณะ, สถานะ)
- ตั้งค่าเริ่มต้นสำหรับผู้ใช้ใหม่

#### FR-002: การบันทึกกิจกรรมการเดินทาง
**คำอธิบาย:** ระบบต้องอนุญาตให้ผู้ใช้บันทึกข้อมูลการเดินทางรายวัน  
**ระดับความสำคัญ:** สูง  
**Input:** ประเภทการเดินทาง, ระยะทาง/เวลา, วัตถุประสงค์, วันที่  
**Output:** การคำนวณ CO2e และอัพเดท Carbon Footprint  
**การประมวลผล:** 
- เลือกประเภท: เดิน, จักรยาน, รถไฟฟ้า, รถเมล์, รถยนต์ส่วนตัว, มอเตอร์ไซค์
- ระบุระยะทาง (กิโลเมตร) หรือเวลาเดินทาง (นาที)
- เลือกวัตถุประสงค์: เรียน, ทำงาน, ส่วนตัว, อื่นๆ
- คำนวณ CO2e อัตโนมัติตาม emission factors
- บันทึกข้อมูลและอัพเดทสถิติส่วนตัว

#### FR-003: การบันทึกการใช้พลังงาน
**คำอธิบาย:** ระบบต้องให้ผู้ใช้บันทึกข้อมูลการใช้พลังงานรายเดือน  
**ระดับความสำคัญ:** สูง  
**Input:** หน่วยการใช้ไฟฟ้า (kWh), หน่วยการใช้น้ำ (ลูกบาศก์เมตร), เดือน/ปี  
**Output:** การคำนวณ CO2e จากการใช้พลังงาน  
**การประมวลผล:** 
- กรอกค่าการใช้ไฟฟ้ารายเดือน
- กรอกค่าการใช้น้ำรายเดือน
- อัพโหลดรูปบิลเป็นหลักฐาน (ถ้าต้องการ)
- คำนวณ CO2e ตาม emission factors ของไฟฟ้าและน้ำ
- เปรียบเทียบกับเดือนก่อนหน้าและแสดงแนวโน้ม

#### FR-004: การจัดการขยะและรีไซเคิล
**คำอธิบาย:** ระบบต้องให้ผู้ใช้บันทึกการจัดการขยะและกิจกรรมรีไซเคิล  
**ระดับความสำคัญ:** กลาง  
**Input:** ประเภทขยะ, น้ำหนักโดยประมาณ, กิจกรรมรีไซเคิล  
**Output:** คะแนนจากการจัดการขยะและ impact calculation  
**การประมวลผล:** 
- เลือกประเภทขยะ: ทั่วไป, รีไซเคิล, อินทรีย์, อันตราย
- ระบุน้ำหนักโดยประมาณ (กิโลกรัม)
- บันทึกกิจกรรมรีไซเคิล (กระดาษ, พลาสติก, แก้ว, โลหะ)
- คำนวณผลกระทบเชิงบวกจากการรีไซเคิล
- ให้คะแนนพิเศษสำหรับกิจกรรมรีไซเคิล

#### FR-005: การคำนวณ Carbon Footprint
**คำอธิบาย:** ระบบต้องคำนวณ Carbon Footprint อัตโนมัติจากข้อมูลที่ผู้ใช้บันทึก  
**ระดับความสำคัญ:** สูง  
**Input:** ข้อมูลกิจกรรมทั้งหมดของผู้ใช้  
**Output:** ค่า CO2e รวมแยกตามประเภทกิจกรรมและช่วงเวลา  
**การประมวลผล:** 
- ใช้ emission factors ตามมาตรฐาน TGO
- คำนวณ CO2e จากการเดินทาง, การใช้พลังงาน
- รวมค่า CO2e ทั้งหมดเป็นรายวัน, รายสัปดาห์, รายเดือน
- หักค่า CO2e ที่ประหยัดได้จากการรีไซเคิล

#### FR-006: การแสดงผล Dashboard
**คำอธิบาย:** ระบบต้องแสดง dashboard แบบ real-time สำหรับผู้ใช้  
**ระดับความสำคัญ:** สูง  
**Input:** ข้อมูล Carbon Footprint และกิจกรรมของผู้ใช้  
**Output:** Dashboard ที่แสดงข้อมูลสถิติและแนวโน้ม  
**การประมวลผล:** 
- แสดง Carbon Footprint วันนี้/สัปดาห์นี้/เดือนนี้
- กราฟ pie chart แสดงสัดส่วนตามประเภทกิจกรรม
- กราฟเส้นแสดงแนวโน้มรายวัน/รายเดือน
- แสดงคะแนน, อันดับ, และ achievements
- Quick stats และ progress indicators

#### FR-007: ระบบแต้มและรางวัล (Gamification)
**คำอธิบาย:** ระบบต้องมีการให้คะแนนและรางวัลเพื่อสร้างแรงจูงใจ  
**ระดับความสำคัญ:** กลาง  
**Input:** กิจกรรมและความสำเร็จของผู้ใช้  
**Output:** คะแนน, badges, และ rankings  
**การประมวลผล:** 
- ให้ points จากการบันทึกกิจกรรมสม่ำเสมอ
- ให้ bonus points จากกิจกรรม eco-friendly
- สร้าง badges สำหรับ achievements ต่างๆ
- จัดอันดับผู้ใช้ภายในคณะและระดับมหาวิทยาลัย
- ระบบ level และ progression

#### FR-008: การสร้างรายงานสรุป
**คำอธิบาย:** ระบบต้องสร้างรายงานสรุป Carbon Footprint รายเดือน  
**ระดับความสำคัญ:** สูง  
**Input:** ข้อมูลกิจกรรมของผู้ใช้ในช่วงเวลาที่กำหนด  
**Output:** รายงาน PDF หรือ web report ที่ครอบคลุม  
**การประมวลผล:** 
- สรุป total CO2e รายเดือน
- กราฟแสดงแนวโน้มเปรียบเทียบกับเดือนก่อน
- เปรียบเทียบกับค่าเฉลี่ยของคณะและมหาวิทยาลัย
- แจกแจง breakdown ตามประเภทกิจกรรม
- คำแนะนำการปรับปรุง

#### 🎯 **Student Assignment Section (30%)**
**ให้นักศึกษาเขียน Functional Requirements ส่วนที่เหลือ:**

#### FR-009: การตั้งเป้าหมายส่วนตัว
**คำอธิบาย:** [ให้นักศึกษาเขียนคำอธิบายระบบตั้งเป้าหมายการลด Carbon]  
**ระดับความสำคัญ:** [ให้นักศึกษากำหนด]  
**Input:** [ให้นักศึกษาระบุ input ที่ต้องการ]  
**Output:** [ให้nักศึกษาระบุ output ที่คาดหวัง]  
**การประมวลผล:** [ให้นักศึกษาอธิบายขั้นตอนการประมวลผล]

#### FR-010: ระบบการแนะนำ (Recommendation System)
**คำอธิบาย:** [ให้นักศึกษาเขียนเกี่ยวกับระบบแนะนำการลด Carbon]  
**ระดับความสำคัญ:** [ให้นักศึกษากำหนด]  
**Input:** [ให้นักศึกษาระบุ]  
**Output:** [ให้นักศึกษาระบุ]  
**การประมวลผล:** [ให้นักศึกษาอธิบาย]

#### FR-011: การเปรียบเทียบและ Leaderboard
**คำอธิบาย:** [ให้นักศึกษาเขียนเกี่ยวกับระบบเปรียบเทียบผู้ใช้]  
**ระดับความสำคัญ:** [ให้นักศึกษากำหนด]  
**Input:** [ให้นักศึกษาระบุ]  
**Output:** [ให้นักศึกษาระบุ]  
**การประมวลผล:** [ให้นักศึกษาอธิบาย]

#### FR-012: Admin Dashboard และรายงานมหาวิทยาลัย
**คำอธิบาย:** [ให้นักศึกษาเขียนเกี่ยวกับระบบจัดการสำหรับ admin]  
**ระดับความสำคัญ:** [ให้นักศึกษากำหนด]  
**Input:** [ให้นักศึกษาระบุ]  
**Output:** [ให้นักศึกษาระบุ]  
**การประมวลผล:** [ให้นักศึกษาอธิบาย]

#### FR-013: การแจ้งเตือนและ Reminders
**คำอธิบาย:** [ให้นักศึกษาเขียนเกี่ยวกับระบบ notification]  
**ระดับความสำคัญ:** [ให้นักศึกษากำหนด]  
**Input:** [ให้นักศึกษาระบุ]  
**Output:** [ให้นักศึกษาระบุ]  
**การประมวลผล:** [ให้นักศึกษาอธิบาย]

### 3.2 ความต้องการด้านประสิทธิภาพ (Non-Functional Requirements)

#### PER-001: เวลาตอบสนอง
- หน้า dashboard ต้องโหลดภายใน 3 วินาที
- การบันทึกข้อมูลต้องประมวลผลภายใน 2 วินาที
- การคำนวณ Carbon Footprint ต้องเสร็จภายใน 1 วินาที
- API response time ต้องไม่เกิน 500 มิลลิวินาที

#### PER-002: ความจุผู้ใช้
- รองรับผู้ใช้พร้อมกัน 1,000 คน ในเวลาปกติ
- รองรับผู้ใช้พร้อมกัน 2,000 คน ในช่วง peak time
- รองรับการบันทึกข้อมูล 10,000 รายการต่อวัน

#### PER-003: ขนาดข้อมูล
- Mobile app ต้องมีขนาดไม่เกิน 50 MB
- ข้อมูล offline cache ไม่เกิน 100 MB
- รูปภาพที่อัพโหลดไม่เกิน 5 MB ต่อไฟล์

#### 🎯 **Student Assignment Section (30%)**
**ให้นักศึกษาเพิ่ม Non-Functional Requirements:**

#### PER-004: [ให้นักศึกษาตั้งชื่อ]
[ให้นักศึกษาเขียน Non-Functional requirement เกี่ยวกับ database, network, หรือ storage]

#### PER-005: [ให้นักศึกษาตั้งชื่อ]
[ให้นักศึกษาเขียนเพิ่มเติม]

### 3.3 ความต้องการด้านการใช้งาน (Usability Requirements)

#### USA-001: ความง่ายในการเรียนรู้
- ผู้ใช้ใหม่ต้องสามารถบันทึกกิจกรรมแรกได้ภายใน 3 นาที
- มี tutorial และ onboarding guide สำหรับผู้ใช้ใหม่
- Help documentation ต้องเข้าถึงได้ง่ายและครอบคลุม

#### USA-002: ความสอดคล้องของ Interface
- ใช้ design system ที่สอดคล้องกันทั่วทั้งแอป
- รองรับทั้งภาษาไทยและอังกฤษ
- มี dark mode และ light mode

#### USA-003: การเข้าถึง (Accessibility)
- ปฏิบัติตามมาตรฐาน WCAG 2.1 Level AA
- รองรับ screen reader
- คีย์บอร์ด navigation ที่สมบูรณ์

#### USA-004: ความพึงพอใจของผู้ใช้
- User satisfaction score เป้าหมาย > 4.0/5.0
- Task completion rate > 90%
- Error rate < 5%

### 3.4 ความต้องการด้านความน่าเชื่อถือ (Reliability Requirements)

#### REL-001: ความพร้อมใช้งาน
- ระบบต้องมี uptime อย่างน้อย 99.5% ในเวลาทำการ
- Downtime ที่วางแผนไว้ต้องไม่เกิน 4 ชั่วโมงต่อเดือน
- ระบบต้องกู้คืนได้ภายใน 2 ชั่วโมงหลังเกิดปัญหา

#### REL-002: การสำรองข้อมูล
- ทำ backup ข้อมูลอัตโนมัติทุกวันเวลา 02:00 น.
- เก็บ backup files อย่างน้อย 30 วัน
- ทดสอบการ restore ข้อมูลทุกเดือน

#### REL-003: ความถูกต้องของข้อมูล
- การคำนวณ Carbon Footprint ต้องมีความถูกต้อง 99.9%
- ข้อมูลที่บันทึกต้องไม่สูญหายหรือเสียหาย
- มีระบบ validation ข้อมูลก่อนบันทึก

#### 🎯 **Student Assignment Section (30%)**
**ให้นักศึกษาเพิ่ม Reliability Requirements:**

#### REL-004: [ให้นักศึกษาตั้งชื่อ]
[ให้นักศึกษาเขียน reliability requirement เกี่ยวกับ error handling, fault tolerance]

#### REL-005: [ให้นักศึกษาตั้งชื่อ]
[ให้นักศึกษาเขียนเพิ่มเติม]

### 3.5 ความต้องการด้านความปลอดภัย (Security Requirements)

#### SEC-001: การรักษาความปลอดภัยข้อมูล
- เข้ารหัสข้อมูลส่วนบุคคลด้วย AES-256
- ใช้ HTTPS สำหรับการสื่อสารทั้งหมด
- จัดเก็บ password ด้วย hashing algorithm ที่ปลอดภัย

#### SEC-002: การควบคุมการเข้าถึง
- ใช้ระบบ SSO ของมหาวิทยาลัยสำหรับ authentication
- แยกระดับสิทธิ์ระหว่าง user และ admin
- Session timeout หลังไม่ใช้งาน 30 นาที

#### SEC-003: การปฏิบัติตาม PDPA
- ขอความยินยอมก่อนเก็บข้อมูลส่วนบุคคล
- อนุญาตให้ผู้ใช้ลบหรือแก้ไขข้อมูลของตนเอง
- มีระบบ audit log สำหรับการเข้าถึงข้อมูล

#### SEC-004: การป้องกันการโจมตี
- ป้องกัน SQL Injection ด้วย parameterized queries
- ป้องกัน XSS ด้วย input validation และ output encoding
- ป้องกัน CSRF ด้วย tokens

#### 🎯 **Student Assignment Section (30%)**
**ให้นักศึกษาเพิ่ม Security Requirements:**

#### SEC-005: [ให้นักศึกษาตั้งชื่อ]
[ให้นักศึกษาเขียน security requirement เกี่ยวกับ API security, data privacy]

#### SEC-006: [ให้นักศึกษาตั้งชื่อ]
[ให้นักศึกษาเขียนเพิ่มเติม]

### 3.6 ความต้องการด้านการทำงานร่วมกัน (Compatibility Requirements)

#### COM-001: แพลตฟอร์มและเบราว์เซอร์
- รองรับ iOS 13.0+ และ Android 8.0+
- รองรับ Chrome 90+, Firefox 88+, Safari 14+, Edge 90+
- Progressive Web App ที่ทำงานได้บนทุกแพลตฟอร์ม

#### COM-002: ความละเอียดหน้าจอ
- รองรับหน้าจอขนาด 320px ถึง 2560px
- Responsive design สำหรับ mobile, tablet, desktop
- High DPI display support

#### COM-003: การทำงาน Offline
- บันทึกข้อมูลได้ในโหมด offline
- Sync ข้อมูลเมื่อกลับมา online
- Cache ข้อมูลสำคัญสำหรับการใช้งาน offline

### 3.7 ความต้องการด้าน Interface ภายนอก

#### 3.7.1 User Interface Requirements
- Progressive Web Application ที่ติดตั้งได้บน home screen
- Native mobile app สำหรับ iOS และ Android
- Responsive web interface สำหรับ desktop
- รองรับทั้งภาษาไทยและอังกฤษ
- Dark mode และ light mode

#### 3.7.2 Hardware Interface Requirements
- Camera access สำหรับการถ่ายรูปบิลและ QR code scanning
- GPS access สำหรับการติดตาม location (เมื่อได้รับอนุญาต)
- Push notification capability
- Local storage สำหรับ offline data

#### 3.7.3 Software Interface Requirements
- เชื่อมต่อกับระบบ SSO ของมหาวิทยาลัย
- Email service สำหรับส่ง notifications และ reports
- Cloud storage สำหรับ backup และ file uploads
- Analytics platform สำหรับติดตามการใช้งาน

#### 3.7.4 Communication Interface Requirements
- RESTful API architecture
- JSON data format สำหรับ API communication
- WebSocket สำหรับ real-time updates (optional)
- HTTPS encryption สำหรับทุก communications

---

## 4. ภาคผนวก (Appendices)

### ภาคผนวก A: Use Cases

#### Primary Actors (ผู้ใช้หลัก)
- **Student (นักศึกษา)** - ตัวแทนโดย "น้องเกม"
- **Staff (บุคลากร)** - ตัวแทนโดย "พี่พลอย"
- **System Administrator** - ตัวแทนโดย "คุณแอน"

#### Secondary Actors (ระบบภายนอก)
- **University SSO System** - ระบบ Single Sign-On ของมหาวิทยาลัย
- **Calculation Engine** - ระบบคำนวณ Carbon Footprint

---

#### UC-01: Authenticate User

**Primary Actor:** Student, Staff  
**Goal:** เข้าสู่ระบบผ่านบัญชีมหาวิทยาลัย  

**Preconditions:**
- มีบัญชีมหาวิทยาลัย
- ระบบ SSO ทำงานปกติ

**Main Success Scenario:**
1. ผู้ใช้เปิดแอป EcoTrack
2. คลิก "Login with University Account"
3. ระบบ redirect ไป University SSO
4. ผู้ใช้กรอก username/password
5. SSO ส่ง authentication token กลับ
6. ระบบสร้าง session และ redirect ไป Dashboard

**Alternative Flows:**
- 4a. รหัสผ่านผิด → แสดงข้อผิดพลาด
- 5a. SSO ไม่ทำงาน → แสดงข้อความระบบขัดข้อง

**Postconditions:**
- ผู้ใช้เข้าสู่ระบบสำเร็จ
- มี active session

---

#### UC-02: Log Transportation Activity

**Primary Actor:** Student, Staff  
**Goal:** บันทึกการเดินทางประจำวัน  

**Preconditions:**
- ผู้ใช้ login แล้ว

**Main Success Scenario:**
1. เลือกเมนู "บันทึกการเดินทาง"
2. เลือกประเภท: เดิน, จักรยาน, รถยนต์, รถเมล์, BTS/MRT
3. กรอกระยะทาง (กม.)
4. เลือกวันที่
5. คลิก "บันทึก"
6. ระบบคำนวณ CO₂ และแสดงผล

**Alternative Flows:**
- 3a. ระยะทาง ≤ 0 → แสดงข้อผิดพลาด
- 3b. ระยะทาง > 1000 กม. → ขอยืนยัน

**Postconditions:**
- ข้อมูลถูกบันทึก
- CO₂ ถูกคำนวณ
- Dashboard อัพเดท

---

#### UC-03: Log Energy Usage

**Primary Actor:** Student, Staff  
**Goal:** บันทึกการใช้พลังงาน (ไฟฟ้า/น้ำ)  

**Preconditions:**
- ผู้ใช้ login แล้ว
- มีข้อมูลจากบิลหรือมิเตอร์

**Main Success Scenario:**
1. เลือกเมนู "บันทึกการใช้พลังงาน"
2. เลือกประเภท: ไฟฟ้า หรือ น้ำ
3. กรอกจำนวนหน่วย
4. เลือกเดือน/ปี
5. คลิก "บันทึก"
6. ระบบคำนวณ CO₂ และแสดงผลเปรียบเทียบ

**Alternative Flows:**
- 3a. มีข้อมูลเดือนนั้นแล้ว → ถามว่าจะแทนที่หรือไม่
- 3b. หน่วยผิดปกติสูง → ขอยืนยัน

**Postconditions:**
- ข้อมูลพลังงานถูกบันทึก
- CO₂ ถูกคำนวณ

---

#### UC-04: Log Waste Management

**Primary Actor:** Student, Staff  
**Goal:** บันทึกการจัดการขยะและรีไซเคิล  

**Preconditions:**
- ผู้ใช้ login แล้ว

**Main Success Scenario:**
1. เลือกเมนู "บันทึกการจัดการขยะ"
2. เลือกประเภทขยะ: กระดาษ, พลาสติก, แก้ว, อลูมิเนียม, อื่นๆ
3. ระบุปริมาณ (กก. หรือ ชิ้น)
4. เลือกวิธีจัดการ: รีไซเคิล, บริจาค, ทิ้งทั่วไป
5. คลิก "บันทึก"
6. ระบบคำนวณ environmental impact

**Alternative Flows:**
- 3a. ปริมาณ ≤ 0 → แสดงข้อผิดพลาด

**Postconditions:**
- ข้อมูลขยะถูกบันทึก
- Recycling score อัพเดท

---

#### UC-05: View Personal Dashboard

**Primary Actor:** Student, Staff  
**Goal:** ดูภาพรวม Carbon Footprint ส่วนตัว  

**Preconditions:**
- ผู้ใช้ login แล้ว

**Main Success Scenario:**
1. เข้าหน้า Dashboard
2. ระบบแสดงข้อมูลวันนี้: CO₂ รวม, เปรียบเทียบเมื่อวาน
3. แสดงกราฟสัดส่วนตาม activity (Pie chart)
4. แสดงแนวโน้ม 7 วันล่าสุด (Line chart)
5. แสดงคะแนนและ badges
6. แสดงปุ่ม quick actions

**Alternative Flows:**
- 2a. ไม่มีข้อมูล → แสดง welcome message และ tutorial

**Postconditions:**
- ผู้ใช้เห็นสถานะปัจจุบัน

---

#### UC-06: View Carbon Reports

**Primary Actor:** Student, Staff  
**Goal:** ดูรายงาน Carbon Footprint แบบละเอียด  

**Preconditions:**
- ผู้ใช้ login แล้ว
- มีข้อมูลอย่างน้อย 3 วัน

**Main Success Scenario:**
1. เลือกเมนู "รายงานของฉัน"
2. เลือกประเภท: รายสัปดาห์, รายเดือน, เปรียบเทียบ
3. เลือกช่วงเวลา
4. คลิก "ดูรายงาน"
5. ระบบแสดงรายงานพร้อมกราฟและตาราง
6. แสดงการเปรียบเทียบและคำแนะนำ

**Alternative Flows:**
- 2a. ข้อมูลไม่เพียงพอ → แจ้งให้บันทึกข้อมูลเพิ่ม

**Postconditions:**
- ผู้ใช้ได้รับรายงานที่ต้องการ

---

#### UC-07: View Trend Analysis

**Primary Actor:** Student, Staff  
**Goal:** วิเคราะห์แนวโน้มการใช้งานระยะยาว  

**Preconditions:**
- ผู้ใช้ login แล้ว
- มีข้อมูลอย่างน้อย 1 เดือน

**Main Success Scenario:**
1. เลือกเมนู "วิเคราะห์แนวโน้ม"
2. เลือกช่วงเวลา: 1 เดือน, 3 เดือน, 6 เดือน
3. ระบบแสดงกราฟแนวโน้ม
4. แสดงการคาดการณ์อนาคต
5. แสดง insights และ recommendations

**Postconditions:**
- ผู้ใช้เห็นแนวโน้มระยะยาว

---

#### UC-08: View Leaderboard

**Primary Actor:** Student, Staff  
**Goal:** ดูการจัดอันดับและเปรียบเทียบกับผู้อื่น  

**Preconditions:**
- ผู้ใช้ login แล้ว

**Main Success Scenario:**
1. เลือกเมนู "Leaderboard"
2. เลือกขอบเขต: มหาวิทยาลัย, คณะ, แผนก
3. เลือกช่วงเวลา: สัปดาห์, เดือน, ตลอดกาล
4. ระบบแสดงอันดับ 1-10
5. ไฮไลท์ตำแหน่งของผู้ใช้
6. แสดงคะแนนและ badges ของแต่ละคน

**Alternative Flows:**
- 4a. ผู้ใช้น้อยกว่า 3 คน → แจ้งว่าผู้ใช้ไม่เพียงพอ

**Postconditions:**
- ผู้ใช้เห็นตำแหน่งของตนเอง

---

#### UC-09: Earn Badges & Points

**Primary Actor:** System (Automated)  
**Secondary Actor:** Student, Staff  
**Goal:** คำนวณและมอบ badges/points ตามกิจกรรม  

**Preconditions:**
- ผู้ใช้บันทึกกิจกรรม

**Main Success Scenario:**
1. ระบบตรวจสอบกิจกรรมที่บันทึก
2. คำนวณคะแนนตามกฎที่กำหนด
3. ตรวจสอบเงื่อนไข badges
4. อัพเดทคะแนนและมอบ badges
5. แจ้งเตือนผู้ใช้ (ถ้าได้ badge ใหม่)

**Business Rules:**
- เดิน/จักรยาน = bonus points
- Recycling = bonus points
- Streak (บันทึกต่อเนื่อง) = combo bonus

**Postconditions:**
- คะแนนและ badges อัพเดท

---

#### UC-10: Set Personal Goals

**Primary Actor:** Student, Staff  
**Goal:** ตั้งเป้าหมายการลด Carbon Footprint  

**Preconditions:**
- ผู้ใช้ login แล้ว
- มีข้อมูล baseline อย่างน้อย 1 สัปดาห์

**Main Success Scenario:**
1. เลือกเมนู "ตั้งเป้าหมาย"
2. ระบบแสดง baseline ปัจจุบัน
3. เลือกประเภทเป้าหมาย: ลด CO₂ %, เพิ่ม green transport %, ฯลฯ
4. ระบุ target value และ timeframe
5. คลิก "บันทึกเป้าหมาย"
6. ระบบสร้าง tracking plan

**Postconditions:**
- เป้าหมายถูกบันทึก
- ระบบเริ่ม track progress

---

#### UC-11: Access Admin Dashboard

**Primary Actor:** System Administrator  
**Goal:** เข้าถึงข้อมูลภาพรวมของระบบ  

**Preconditions:**
- ผู้ใช้มีสิทธิ์ admin
- Login แล้ว

**Main Success Scenario:**
1. เข้าหน้า Admin Dashboard
2. ระบบแสดงสถิติภาพรวม:
   - จำนวนผู้ใช้ active
   - กิจกรรมที่บันทึกวันนี้
   - CO₂ รวมของมหาวิทยาลัย
3. แสดงกราฟแนวโน้ม 30 วัน
4. แสดงการจัดอันดับคณะ
5. แสดงเมนูการจัดการ

**Alternative Flows:**
- 1a. ไม่มีสิทธิ์ → ปฏิเสธการเข้าถึง

**Postconditions:**
- Admin เห็นภาพรวมระบบ

---

#### UC-12: Generate System Reports

**Primary Actor:** System Administrator  
**Goal:** สร้างรายงานระบบเพื่อนำเสนอผู้บริหาร  

**Preconditions:**
- ผู้ใช้มีสิทธิ์ admin
- มีข้อมูลในระบบ

**Main Success Scenario:**
1. เข้าหน้า "สร้างรายงาน"
2. เลือกประเภท: ภาพรวมมหาวิทยาลัย, เปรียบเทียบคณะ, แนวโน้ม
3. เลือกช่วงเวลา
4. เลือกรูปแบบ: PDF, Excel, PowerPoint
5. คลิก "สร้างรายงาน"
6. ระบบประมวลผลและสร้างไฟล์
7. ดาวน์โหลดรายงาน

**Alternative Flows:**
- 6a. ข้อมูลไม่เพียงพอ → แจ้งและแนะนำช่วงเวลาอื่น

**Postconditions:**
- Admin ได้รับรายงานที่ต้องการ

---

#### UC-13: Manage Emission Factors

**Primary Actor:** System Administrator  
**Goal:** จัดการค่าคงที่สำหรับคำนวณ CO₂  

**Preconditions:**
- ผู้ใช้มีสิทธิ์ admin

**Main Success Scenario:**
1. เข้าหน้า "จัดการ Emission Factors"
2. ระบบแสดงตารางค่าคงที่ปัจจุบัน
3. เลือกแก้ไขค่าที่ต้องการ
4. กรอกค่าใหม่พร้อมแหล่งอ้างอิง
5. คลิก "บันทึก"
6. ระบบอัพเดทค่าและ recalculate ข้อมูลย้อนหลัง

**Business Rules:**
- ต้องมีแหล่งอ้างอิงที่เชื่อถือได้
- การเปลี่ยนแปลงมีผลย้อนหลัง 30 วัน

**Postconditions:**
- ค่าคงที่อัพเดท
- การคำนวณใช้ค่าใหม่

---

#### UC-14: Manage User Accounts

**Primary Actor:** System Administrator  
**Goal:** จัดการบัญชีผู้ใช้ในระบบ  

**Preconditions:**
- ผู้ใช้มีสิทธิ์ admin

**Main Success Scenario:**
1. เข้าหน้า "จัดการผู้ใช้"
2. ระบบแสดงรายการผู้ใช้ทั้งหมด
3. เลือกผู้ใช้ที่ต้องการจัดการ
4. เลือกการดำเนินการ:
   - ดูข้อมูลโดยละเอียด
   - ปิดใช้งานบัญชี
   - รีเซ็ตข้อมูล
   - เปลี่ยนสิทธิ์
5. ยืนยันการดำเนินการ

**Alternative Flows:**
- 4a. รีเซ็ตข้อมูล → ขอยืนยันเพิ่มเติม

**Postconditions:**
- บัญชีผู้ใช้อัพเดทตามที่ต้องการ

---

### การเชื่อมโยง Use Cases

#### ลำดับการใช้งานทั่วไป:
1. **UC-01** (Login) → **UC-05** (Dashboard)
2. **UC-05** → **UC-02/03/04** (Log Activities)
3. **UC-02/03/04** → **UC-09** (Auto earn points)
4. **UC-05** → **UC-06/07/08** (View Reports/Analysis)

#### Dependencies:
- UC-02, 03, 04 ต้องใช้ UC-01 ก่อน
- UC-09 trigger โดย UC-02, 03, 04
- UC-06, 07 ต้องมีข้อมูลจาก UC-02, 03, 04
- UC-11-14 ต้องใช้ UC-01 ด้วยสิทธิ์ admin

#### Technical Implementation Notes:
- ใช้ University SSO API สำหรับ UC-01
- Calculation Engine แยกเป็น microservice
- Real-time updates สำหรับ dashboard และ leaderboard
- Caching สำหรับข้อมูลที่ไม่เปลี่ยนแปลงบ่อย
- Background jobs สำหรับการคำนวณ points และ badges

### Traceability Matrix: Requirements to Use Cases

#### Epic to Use Case Mapping

| Epic | User Stories | Use Cases | Priority | Notes |
|------|-------------|-----------|----------|-------|
| **E01: User Onboarding** | US-01: เข้าสู่ระบบด้วย SSO | UC-01: Authenticate User | Must Have | Entry point |
| **E02: Activity Logging** | US-02: บันทึกการเดินทาง | UC-02: Log Transportation | Must Have | Core feature |
| | US-03: บันทึกการใช้พลังงาน | UC-03: Log Energy Usage | Must Have | Core feature |
| | (Future) บันทึกการจัดการขยะ | UC-04: Log Waste Management | Should Have | Release 2 |
| **E03: Feedback & Visualization** | US-04: ดู Dashboard ส่วนตัว | UC-05: View Personal Dashboard | Must Have | User engagement |
| | US-06: ดูรายงานสรุปรายเดือน | UC-06: View Carbon Reports | Should Have | Analysis |
| | (Enhanced) ดูแนวโน้ม | UC-07: View Trend Analysis | Could Have | Advanced |
| **E04: Gamification** | US-05: ระบบแต้มและ Badges | UC-08: View Leaderboard | Should Have | Motivation |
| | US-07: ตั้งเป้าหมายส่วนตัว | UC-10: Set Personal Goals | Could Have | Personalization |
| **E05: Administration** | US-08: Admin Dashboard | UC-11: Access Admin Dashboard | Won't Have (MVP) | Future |
| | (Admin) สร้างรายงานระบบ | UC-12: Generate System Reports | Won't Have (MVP) | Future |
| | (Admin) จัดการค่าคงที่ | UC-13: Manage Emission Factors | Won't Have (MVP) | Future |
| | (Admin) จัดการผู้ใช้ | UC-14: Manage User Accounts | Won't Have (MVP) | Future |

### Persona to Use Case Mapping

#### น้องเกม (นักศึกษาผู้รักการแข่งขัน) 🏆

| Use Case | Frequency | Importance | User Experience Focus |
|----------|-----------|------------|----------------------|
| UC-01: Authenticate User | Once per session | Critical | Quick & seamless login |
| UC-02: Log Transportation | Daily | High | Fast data entry, 1-minute rule |
| UC-03: Log Energy Usage | Monthly | Medium | Simple form, validation |
| UC-05: View Personal Dashboard | Multiple daily | High | Real-time updates, visual appeal |
| UC-08: View Leaderboard & Badges | Daily | High | Competition, achievements |
| UC-06: View Carbon Reports | Weekly | Medium | Progress tracking |

#### พี่พลอย (บุคลากรสายรักษ์โลก) 🌍

| Use Case | Frequency | Importance | User Experience Focus |
|----------|-----------|------------|----------------------|
| UC-01: Authenticate User | Once per session | Critical | Security, trust |
| UC-02: Log Transportation | Daily | High | Accuracy, detailed options |
| UC-03: Log Energy Usage | Monthly | High | Precise calculations |
| UC-05: View Personal Dashboard | Daily | High | Meaningful insights |
| UC-06: View Carbon Reports | Weekly | High | Detailed analysis, trends |
| UC-07: View Trend Analysis | Monthly | High | Long-term patterns |
| UC-10: Set Personal Goals | Monthly | High | Goal setting, progress tracking |

#### คุณแอน (ผู้ดูแลระบบ) 📊

| Use Case | Frequency | Importance | User Experience Focus |
|----------|-----------|------------|----------------------|
| UC-01: Authenticate User | Daily | Critical | Admin privileges |
| UC-11: Access Admin Dashboard | Daily | Critical | Comprehensive overview |
| UC-12: Generate System Reports | Weekly | High | Flexible reporting |
| UC-13: Manage Emission Factors | Monthly | Medium | Data management |
| UC-14: Manage User Accounts | As needed | Medium | User administration |

### MoSCoW Analysis with Use Cases

#### Must Have (Release 1 - MVP)
- **UC-01: Authenticate User** - No system access without this
- **UC-02: Log Transportation** - Core data collection
- **UC-03: Log Energy Usage** - Core data collection
- **UC-05: View Personal Dashboard** - User feedback loop

#### Should Have (Release 1 Enhancement)
- **UC-08: View Leaderboard & Badges** - User engagement driver
- **UC-06: View Carbon Reports** - Analysis capability

#### Could Have (Release 2)
- **UC-04: Log Waste Management** - Additional data source
- **UC-07: View Trend Analysis** - Advanced analytics
- **UC-10: Set Personal Goals** - Personalization

#### Won't Have This Time (Future Releases)
- **UC-11: Access Admin Dashboard** - Complex feature
- **UC-12: Generate System Reports** - Administrative tool
- **UC-13: Manage Emission Factors** - Configuration management
- **UC-14: Manage User Accounts** - User administration

### Business Value vs Technical Complexity Matrix

```
High Business Value │ UC-05 Dashboard    │ UC-08 Leaderboard │
                    │ UC-02 Transport    │ UC-06 Reports     │
                    │ UC-03 Energy       │                   │
────────────────────┼──────────────────  ┼─────────────────── │
                    │ UC-04 Waste        │ UC-11 Admin       │
Low Business Value  │ UC-10 Goals        │ UC-12 System Rpt  │
                    │                    │ UC-13 Config      │
                    │                    │ UC-14 User Mgmt   │
                    └────────────────────┴─────────────────── ┘
                   Low Technical        High Technical
                   Complexity           Complexity

Legend:
- Top-left: Quick wins (implement first)
- Top-right: Major projects (implement second)
- Bottom-left: Fill-ins (implement when time allows)
- Bottom-right: Questionable (evaluate carefully)
```

### Implementation Roadmap

#### Sprint 1 (Weeks 1-2): Foundation
- UC-01: Authenticate User
- UC-02: Log Transportation (basic)
- UC-03: Log Energy Usage (basic)

#### Sprint 2 (Weeks 3-4): Core Loop
- UC-05: View Personal Dashboard
- Enhance UC-02 & UC-03 with validation

#### Sprint 3 (Weeks 5-6): Engagement
- UC-08: View Leaderboard & Badges
- Basic gamification system

#### Sprint 4 (Weeks 7-8): Analysis
- UC-06: View Carbon Reports
- Data export functionality

#### Future Sprints:
- UC-04, UC-07, UC-10 (User enhancements)
- UC-11, UC-12, UC-13, UC-14 (Admin features)

### Success Metrics per Use Case

| Use Case | Success Metric | Target Value |
|----------|---------------|--------------|
| UC-01 | Login success rate | >95% |
| UC-02 | Daily logging rate | >70% of active users |
| UC-03 | Monthly logging rate | >80% of active users |
| UC-05 | Dashboard load time | <3 seconds |
| UC-08 | Leaderboard engagement | >50% weekly views |
| UC-06 | Report generation | >30% monthly usage |

This traceability matrix ensures that every requirement from the Requirements Analysis Document is properly addressed by corresponding use cases, and provides clear guidance for implementation priorities.

### ภาคผนวก B: ข้อมูลเทคนิค

#### B.1 Emission Factors (ตามมาตรฐาน TGO)

| กิจกรรม | Emission Factor | หน่วย |
|---------|-----------------|-------|
| รถยนต์ส่วนตัว (เบนซิน) | 0.21 | kg CO2e/km |
| รถยนต์ส่วนตัว (ดีเซล) | 0.26 | kg CO2e/km |
| มอเตอร์ไซค์ | 0.11 | kg CO2e/km |
| รถเมล์ (NGV) | 0.04 | kg CO2e/km |
| รถไฟฟ้า BTS/MRT | 0.02 | kg CO2e/km |
| จักรยาน | 0 | kg CO2e/km |
| เดิน | 0 | kg CO2e/km |
| ไฟฟ้า (การไฟฟ้าฯ) | 0.5610 | kg CO2e/kWh |
| น้ำประปา | 0.2720 | kg CO2e/m³ |

#### B.2 ระบบคะแนนและรางวัล

| กิจกรรม | Points | เงื่อนไข |
|---------|--------|---------|
| บันทึกการเดินทาง | 5 | ต่อครั้ง |
| บันทึกการใช้พลังงาน | 10 | ต่อเดือน |
| บันทึกการรีไซเคิล | 15 | ต่อครั้ง |
| ใช้ขนส่งสาธารณะ | 20 | bonus ต่อครั้ง |
| เดิน/จักรยาน | 25 | bonus ต่อครั้ง |
| ลดการใช้พลังงาน | 50 | เมื่อลดได้ 10% |
| ใช้งานต่อเนื่อง 7 วัน | 100 | streak bonus |

#### B.3 Badge Categories

| Badge | เงื่อนไข | คะแนนที่ได้ |
|-------|---------|-------------|
| Eco Starter | บันทึกกิจกรรม 7 วันติดต่อกัน | 50 |
| Green Commuter | ใช้ขนส่งสาธารณะ 20 ครั้ง | 100 |
| Energy Saver | ลดการใช้ไฟฟ้า 10% เป็นเวลา 1 เดือน | 150 |
| Recycle Master | รีไซเคิล 50 kg | 100 |
| Zero Hero | Zero carbon day 5 วัน | 200 |
| Carbon Cutter | ลด carbon footprint 25% ใน 1 เดือน | 300 |
| Eco Warrior | ใช้งานครบ 6 เดือน | 500 |
| Green Champion | อันดับ Top 10 ของคณะ | 1000 |

### ภาคผนวก C: การวิเคราะห์ความเสี่ยง

| ความเสี่ยง | ความน่าจะเป็น | ผลกระทบ | แนวทางจัดการ |
|-----------|--------------|---------|--------------|
| ผู้ใช้ไม่บันทึกข้อมูลสม่ำเสมอ | สูง | สูง | Gamification, push notifications, incentives |
| ข้อมูล emission factors เปลี่ยนแปลง | ปานกลาง | ปานกลาง | ระบบอัพเดทแบบ configurable |
| ระบบล่มในช่วงใช้งานหนัก | ต่ำ | สูง | Load balancing, cloud auto-scaling |
| ข้อกังวลเรื่องความเป็นส่วนตัว | ปานกลาง | สูง | PDPA compliance, transparency |
| การยอมรับจากผู้ใช้ต่ำ | ปานกลาง | สูง | User engagement strategies, training |

#### 🎯 **Student Assignment Section (30%)**
**ให้นักศึกษาเพิ่มการวิเคราะห์ความเสี่ยง:**

| ความเสี่ยง | ความน่าจะเป็น | ผลกระทบ | แนวทางจัดการ |
|-----------|--------------|---------|--------------|
| [ให้นักศึกษาระบุความเสี่ยงใหม่] | [สูง/กลาง/ต่ำ] | [สูง/กลาง/ต่ำ] | [ให้นักศึกษาระบุวิธีจัดการ] |
| [ให้นักศึกษาระบุ] | [สูง/กลาง/ต่ำ] | [สูง/กลาง/ต่ำ] | [ให้นักศึกษาระบุ] |
| [ให้นักศึกษาระบุ] | [สูง/กลาง/ต่ำ] | [สูง/กลาง/ต่ำ] | [ให้นักศึกษาระบุ] |

### ภาคผนวก D: อภิธานศัพท์

| คำศัพท์ | คำอธิบาย |
|---------|----------|
| Carbon Neutral | สถานะที่การปล่อยและการดูดซับ CO2 อยู่ในสมดุล |
| Emission Factor | ค่าสัมประสิทธิ์ที่ใช้คำนวณการปล่อย CO2 จากกิจกรรม |
| Gamification | การนำกลไกและองค์ประกอบของเกมมาใช้ในบริบทอื่น |
| Leaderboard | ตารางแสดงอันดับผลงานของผู้ใช้ |
| Progressive Web App | แอปพลิเคชันเว็บที่ทำงานเหมือน native app |
| Single Sign-On (SSO) | ระบบที่ผู้ใช้ล็อกอินครั้งเดียวใช้ได้หลายระบบ |
| Streak | การทำกิจกรรมอย่างต่อเนื่องติดต่อกัน |

#### 🎯 **Student Assignment Section (30%)**
**ให้นักศึกษาเพิ่มคำศัพท์ในอภิธานศัพท์:**

| คำศัพท์ | คำอธิบาย |
|---------|----------|
| [ให้นักศึกษาเพิ่มคำศัพท์] | [ให้นักศึกษาอธิบาย] |
| [ให้นักศึกษาเพิ่ม] | [ให้นักศึกษาอธิบาย] |
| [ให้นักศึกษาเพิ่ม] | [ให้นักศึกษาอธิบาย] |
| [ให้นักศึกษาเพิ่ม] | [ให้นักศึกษาอธิบาย] |

### ภาคผนวก E: เกณฑ์การยอมรับ (Acceptance Criteria)

#### E.1 เกณฑ์ระดับระบบ
- ผู้ใช้สามารถลงทะเบียนและเข้าสู่ระบบผ่าน SSO ได้ 100%
- การคำนวณ Carbon Footprint มีความถูกต้อง 99.9%
- ระบบตอบสนองภายใน 3 วินาที 95% ของเวลา
- Mobile app ใช้งานได้บน iOS และ Android ตามที่กำหนด
- รองรับผู้ใช้พร้อมกัน 1,000 คนโดยไม่มีปัญหา

#### E.2 เกณฑ์ระดับผู้ใช้
- ผู้ใช้ใหม่สามารถบันทึกกิจกรรมแรกได้ภายใน 3 นาที
- User satisfaction score อย่างน้อย 4.0/5.0
- Task completion rate อย่างน้อย 90%
- การใช้งานต่อเนื่อง (retention rate) อย่างน้อย 60% หลังใช้ 1 เดือน

#### 🎯 **Student Assignment Section (30%)**
**ให้นักศึกษาเพิ่มเกณฑ์การยอมรับ:**

#### E.3 เกณฑ์เพิ่มเติม
- [ให้นักศึกษาเขียนเกณฑ์การยอมรับเพิ่มเติม เช่น เกณฑ์ความปลอดภัย, การประหยัดพลังงาน]

#### E.4 เกณฑ์ประสิทธิภาพเฉพาะ
- [ให้นักศึกษาเขียนเกณฑ์ที่วัดผลได้เฉพาะสำหรับ EcoTrack]

---

**หมายเหตุ:** เอกสารนี้เป็น Pure Software Requirements Specification ตามมาตรฐาน IEEE 830 โดยเน้นที่ **ความต้องการ** เท่านั้น ไม่รวมรายละเอียดด้าน design, implementation, testing methods หรือ project management

**สำหรับนักศึกษา:**
- ศึกษาส่วนที่ให้มา (70%) เพื่อเข้าใจรูปแบบการเขียน SRS ที่ถูกต้องตามมาตรฐาน IEEE 830
- ทำ assignments ในส่วนที่กำหนด (🎯 30%) เพื่อฝึกทักษะการวิเคราะห์และเขียน requirements
- ใช้เอกสารนี้เป็นพื้นฐานสำหรับการเขียน Software Design Document ในขั้นตอนถัดไป

**การใช้งานเอกสาร:**
1. อ่านและเข้าใจโครงสร้าง SRS ตามมาตรฐาน IEEE 830
2. ศึกษาวิธีการเขียน functional และ non-functional requirements ที่วัดผลได้
3. เรียนรู้การเขียน use cases ที่ครอบคลุมและมีคุณภาพ
4. ฝึกการวิเคราะห์ความเสี่ยงและการเขียน acceptance criteria
5. ใช้เป็น template สำหรับโปรเจคด้านสิ่งแวดล้อมและความยั่งยืน

**คุณภาพของ SRS นี้:**
- ✅ ปฏิบัติตาม IEEE 830 standard อย่างเคร่งครัด
- ✅ เน้น requirements เท่านั้น ไม่ปะปนกับ design/implementation
- ✅ ใช้ภาษาที่ชัดเจน เฉพาะเจาะจง วัดผลได้
- ✅ ครอบคลุม functional และ non-functional requirements อย่างสมบูรณ์
- ✅ มีการอ้างอิงมาตรฐานสากล (TGO, ISO 14064)
- ✅ เหมาะสำหรับโปรเจคด้าน sustainability และ environmental technology

**Next Steps:**
หลังจากทำ SRS เสร็จแล้ว นักศึกษาสามารถนำไปสู่ขั้นตอนต่อไป:

- Software Design Document (SDD)
- Implementation Guide
- Test Document
