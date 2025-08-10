# บทเรียน: User Story และ วัตถุประสงค์
**สำหรับวิชา ENGSE206 - สัปดาห์ที่ 1**

---

## วัตถุประสงค์การเรียนรู้

เมื่อจบบทเรียนนี้ นักศึกษาจะสามารถ:

**ความรู้ (Knowledge)**
- อธิบายแนวคิดและหลักการของ User Story ในการพัฒนาซอฟต์แวร์
- เข้าใจโครงสร้างและองค์ประกอบของ User Story ที่มีคุณภาพ
- แยกแยะความแตกต่างระหว่าง User Story, Epic, และ Theme

**ทักษะ (Skills)**
- เขียน User Story ที่มีคุณภาพตาม INVEST criteria
- สร้าง Acceptance Criteria ที่ชัดเจนและสามารถทดสอบได้
- ประมาณขนาดและความซับซ้อนของ User Story (Story Points)

**การประยุกต์ใช้ (Application)**
- นำ User Story ไปใช้ในการสื่อสารกับ Stakeholders
- ใช้ User Story เป็นเครื่องมือในการวางแผนและจัดลำดับความสำคัญ
- ประยุกต์ใช้ User Story ในกระบวนการ Agile Development

---

## 1. บทนำ: ทำไม User Story จึงสำคัญ?

### ปัญหาของการเขียนความต้องการแบบดั้งเดิม

**ตัวอย่างความต้องการแบบเดิม:**
```
"ระบบต้องมีฟังก์ชันการล็อกอินที่รองรับ username และ password 
พร้อมทั้งมีการตรวจสอบความถูกต้องของข้อมูลและแสดงข้อผิดพลาด
เมื่อข้อมูลไม่ถูกต้อง"
```

**ปัญหาที่พบ:**
- เน้นที่ระบบมากกว่าผู้ใช้
- ไม่ชัดเจนว่าทำไมต้องมีฟีเจอร์นี้
- ยากต่อการเข้าใจสำหรับ Business Stakeholders
- ไม่ได้บอกถึงคุณค่าที่ผู้ใช้จะได้รับ

### แนวคิด User Story

User Story เป็นเครื่องมือที่ช่วยให้เราเขียนความต้องการซอฟต์แวร์โดยเน้นที่:
- **ผู้ใช้เป็นศูนย์กลาง** (User-Centered)
- **คุณค่าทางธุรกิจ** (Business Value)
- **การสื่อสารที่ง่าย** (Simple Communication)
- **ความยืดหยุ่น** (Flexibility)

---

## 2. โครงสร้างของ User Story

### รูปแบบพื้นฐาน (Basic Template)

```
As a [ประเภทผู้ใช้]
I want to [สิ่งที่ต้องการทำ]
So that [เหตุผลหรือคุณค่าที่ได้รับ]
```

**ตัวอย่าง:**
```
As a registered user
I want to log into my account
So that I can access my personal information and settings
```

### องค์ประกอบสำคัญ 3 ส่วน

#### 1. **Persona (Who)** - ใครเป็นผู้ใช้
- ระบุประเภทผู้ใช้อย่างชัดเจน
- ใช้ชื่อเฉพาะ (ถ้ามี) แทนคำทั่วไป

**ตัวอย่าง Personas:**
- As a **new customer**
- As a **premium subscriber**
- As a **system administrator**
- As a **mobile app user**

#### 2. **Feature/Capability (What)** - ต้องการทำอะไร
- บรรยายสิ่งที่ผู้ใช้ต้องการให้ระบบทำ
- เน้นที่ "อะไร" ไม่ใช่ "อย่างไร"

#### 3. **Benefit/Value (Why)** - ทำไมถึงต้องการ
- อธิบายคุณค่าหรือประโยชน์ที่ผู้ใช้จะได้รับ
- เชื่อมโยงกับเป้าหมายทางธุรกิจ

---

## 3. หลัก INVEST สำหรับ User Story คุณภาพ

### I - Independent (อิสระ)
Story ต้องไม่ขึ้นอยู่กับ Story อื่นมากเกินไป

**ดี:**
```
Story A: As a user, I want to create an account
Story B: As a user, I want to update my profile
```

**ไม่ดี:**
```
Story A: As a user, I want to enter my username
Story B: As a user, I want to enter my password
```

### N - Negotiable (เจรจาได้)
Story เป็นจุดเริ่มต้นของการสนทนา ไม่ใช่สัญญาที่ละเอียดทุกจุด

### E - Valuable (มีคุณค่า)
Story ต้องให้คุณค่าที่ชัดเจนกับผู้ใช้หรือธุรกิจ

### S - Estimable (ประมาณได้)
Story ต้องเข้าใจได้เพียงพอที่จะประมาณความพยายามในการพัฒนา

### S - Small (เล็ก)
Story ต้องเล็กพอที่จะทำเสร็จภายใน 1 Sprint

### T - Testable (ทดสอบได้)
Story ต้องมี criteria ที่ทดสอบได้ชัดเจน

---

## 4. Acceptance Criteria

### คืออะไร?
Acceptance Criteria คือเงื่อนไขที่ต้องเป็นจริงเพื่อให้ User Story ถือว่าเสร็จสมบูรณ์

### รูปแบบการเขียน

#### Given-When-Then Format
```
Given [สถานการณ์เริ่มต้น]
When [การกระทำ]
Then [ผลลัพธ์ที่คาดหวัง]
```

**ตัวอย่าง:**
```
User Story: As a user, I want to log into my account

Acceptance Criteria:
1. Given I am on the login page
   When I enter valid username and password
   Then I should be redirected to my dashboard

2. Given I am on the login page
   When I enter invalid credentials
   Then I should see an error message "Invalid username or password"

3. Given I enter wrong password 3 times
   When I try to login again
   Then my account should be temporarily locked for 15 minutes
```

#### Checklist Format
```
- User can enter username and password
- System validates credentials against database
- Valid login redirects to dashboard
- Invalid login shows error message
- Account locks after 3 failed attempts
```

---

## 5. Epic, Story, และ Task

### ลำดับชั้นของความต้องการ

```
Theme (ธีม)
├── Epic (เอปิก)
    ├── User Story (ยูเซอร์สตอรี่)
        ├── Task (งาน)
        ├── Task (งาน)
        └── Task (งาน)
    └── User Story (ยูเซอร์สตอรี่)
└── Epic (เอปิก)
```

### Epic
- ความต้องการขนาดใหญ่ที่ใช้เวลาหลาย Sprint
- ยังไม่ละเอียดพอที่จะพัฒนาได้ทันที
- ต้องแบ่งย่อยเป็น User Stories

**ตัวอย่าง Epic:**
```
Epic: User Account Management
As a user, I want to manage my account information 
so that I can keep my profile up-to-date and secure
```

### User Story
- ความต้องการที่เล็กพอทำเสร็จใน 1 Sprint
- มีคุณค่าที่ชัดเจนสำหรับผู้ใช้
- สามารถทดสอบและ Demo ได้

### Task
- งานย่อยทางเทคนิคที่ต้องทำเพื่อให้ Story สำเร็จ
- มักเป็นงานของ Developer โดยเฉพาะ

**ตัวอย่าง Tasks สำหรับ Login Story:**
- Create login API endpoint
- Design login UI mockup
- Implement password encryption
- Write unit tests for authentication
- Update user documentation

---

## 6. Story Points และการประมาณขนาด

### Story Points คืออะไร?
- หน่วยวัดความซับซ้อน ความพยายาม และความไม่แน่นอนของ User Story
- เป็นการประมาณแบบสัมพัทธ์ (Relative Estimation)
- ไม่ใช่เวลาจริง แต่เป็นการเปรียบเทียบความยาก

### Fibonacci Sequence
ใช้ลำดับ Fibonacci: **1, 2, 3, 5, 8, 13, 21, 34, 55, 89**

**หลักการ:**
- ยิ่งใหญ่ยิ่งไม่แน่นอน
- ช่องว่างที่เพิ่มขึ้นสะท้อนความไม่แน่นอน

### Planning Poker
1. ทีมได้รับ User Story
2. คุยกันเพื่อทำความเข้าใจ
3. แต่ละคนเลือก Story Point แบบลับ
4. เปิดการ์ดพร้อมกัน
5. หากไม่ตรงกัน อภิปรายและโหวตใหม่
6. ทำซ้ำจนได้ความเห็นตรงกัน

### ตัวอย่างการประมาณ
```
1 Point: แก้ bug เล็กน้อย, เปลี่ยน text
2 Points: เพิ่ม field ใหม่ในฟอร์ม
3 Points: สร้างหน้า CRUD อย่างง่าย
5 Points: Login system พื้นฐาน
8 Points: Payment integration
13 Points: Search with complex filters
21+ Points: ใหญ่เกินไป ต้องแบ่งย่อย
```

---

## 7. เทคนิคการเขียน User Story

### 1. เริ่มจาก User Journey
- วาด user journey map ก่อน
- ระบุจุดสำคัญที่ user ต้องการความช่วยเหลือ
- แปลงแต่ละจุดเป็น user stories

### 2. ใช้ Personas จริง
แทนที่จะเขียน "As a user" ให้ใช้ persona เฉพาะ:

**ไม่ดี:**
```
As a user, I want to search for products
```

**ดี:**
```
As a busy working mother shopping online,
I want to quickly filter products by price and brand
So that I can find what I need without wasting time
```

### 3. เน้นคุณค่า ไม่ใช่ฟีเจอร์

**ไม่ดี:**
```
As a user, I want a dashboard with charts
```

**ดี:**
```
As a sales manager,
I want to see my team's performance at a glance
So that I can identify who needs support and celebrate successes
```

### 4. ใช้ภาษาของ Business

**ไม่ดี:**
```
As a user, I want to authenticate via OAuth2
```

**ดี:**
```
As a new user,
I want to sign up using my Google account
So that I don't have to remember another password
```

---

## 8. ข้อผิดพลาดที่พบบ่อย

### 1. เขียนเป็น Technical Task
```
❌ As a developer, I want to implement REST API
✅ As a mobile user, I want to sync my data across devices
```

### 2. ขาดเหตุผล (So that...)
```
❌ As a user, I want to upload profile photo
✅ As a user, I want to upload profile photo 
   so that other users can recognize me easily
```

### 3. ใหญ่เกินไป
```
❌ As a user, I want a complete e-commerce system
✅ As a shopper, I want to add items to my shopping cart
   so that I can purchase multiple items at once
```

### 4. ไม่สามารถทดสอบได้
```
❌ As a user, I want the system to be user-friendly
✅ As a new user, I want to complete account registration in less than 2 minutes
   so that I can start using the service quickly
```

---

## 9. เครื่องมือสำหรับจัดการ User Stories

### Physical Tools
- **Story Cards:** การ์ดกระดาษสำหรับเขียน stories
- **Story Wall:** กำแพงหรือบอร์ดสำหรับจัดเรียง stories
- **Planning Poker Cards:** การ์ดสำหรับประมาณขนาด

### Digital Tools
- **Jira:** ครอบคลุม, มีฟีเจอร์มาก, เหมาะกับองค์กรใหญ่
- **Azure DevOps:** ผสานกับ Microsoft ecosystem
- **Trello:** ง่าย, เหมาะกับทีมเล็ก
- **Asana:** User-friendly, มี template
- **Monday.com:** Flexible, มี automation
- **Linear:** Modern, เน้น developer experience

### Story Mapping Tools
- **StoriesOnBoard:** เฉพาะสำหรับ story mapping
- **Miro/Mural:** Collaborative whiteboard
- **PivotalTracker:** มี story mapping built-in

---

## 10. การทำ Story Mapping

### ขั้นตอนการทำ Story Mapping

#### Step 1: User Activities (กิจกรรมหลัก)
ระบุกิจกรรมหลักที่ user ต้องทำตามลำดับเวลา

```
[Register] → [Browse] → [Select] → [Purchase] → [Track] → [Review]
```

#### Step 2: User Tasks (งานย่อย)
แบ่งย่อยแต่ละกิจกรรมเป็นงานเล็กๆ

```
Register:
- Enter personal info
- Verify email
- Set password

Browse:
- Search products
- Filter by category
- Compare items
```

#### Step 3: User Stories (รายละเอียด)
เขียน user stories สำหรับแต่ละ task

```
- As a new customer, I want to enter my email address
  so that I can create an account
- As a shopper, I want to filter products by price range
  so that I can find items within my budget
```

#### Step 4: Prioritize และ Release Planning
จัดลำดับความสำคัญและวางแผน release

```
Release 1 (MVP): Register, Browse, Select
Release 2: Purchase, Track  
Release 3: Review, Recommendations
```

### ประโยชน์ของ Story Mapping
- **เห็นภาพรวม:** มองเห็น user journey ทั้งหมด
- **การวางแผน:** จัดลำดับความสำคัญได้ดี
- **การสื่อสาร:** ทีมเข้าใจตรงกัน
- **การค้นหาช่องว่าง:** เห็นสิ่งที่ขาดหายไป

---

## 11. กิจกรรมปฏิบัติ

### Workshop 1: เขียน User Story
**สถานการณ์:** ระบบจองห้องประชุมออนไลน์สำหรับบริษัท

**ให้นักศึกษา:**
1. ระบุ 3 personas ที่แตกต่างกัน
2. เขียน 5 user stories สำหรับแต่ละ persona
3. สร้าง acceptance criteria สำหรับ 2 stories
4. ประมาณ story points

**ตัวอย่างผลลัพธ์:**
```
Persona 1: Office Employee
As an office employee,
I want to see available meeting rooms for next week
So that I can plan my meetings in advance

Acceptance Criteria:
- Given I select a date range
- When I click "Search"
- Then I see all available rooms with capacity and equipment info
```

### Workshop 2: Story Mapping
**สถานการณ์:** แอปพลิเคชันสั่งอาหารออนไลน์

**ขั้นตอน:**
1. วาด user journey map
2. ระบุ activities หลัก
3. แบ่งย่อยเป็น tasks
4. เขียน user stories
5. จัดลำดับความสำคัญ
6. วางแผน 3 releases

---

## 12. การประเมินและวัดผล

### Rubric การประเมิน User Story

#### ระดับดีเยี่ยม (A)
- ปฏิบัติตาม INVEST criteria ครบถ้วน
- มี acceptance criteria ที่ชัดเจนและทดสอบได้
- เน้นคุณค่าของผู้ใช้อย่างชัดเจน
- ใช้ภาษาที่เข้าใจง่ายสำหรับ stakeholders

#### ระดับดี (B)
- ปฏิบัติตาม INVEST criteria ส่วนใหญ่
- มี acceptance criteria พื้นฐาน
- ระบุคุณค่าได้แต่อาจไม่ชัดเจนมาก

#### ระดับปานกลาง (C)
- โครงสร้าง user story ถูกต้องพื้นฐาน
- Acceptance criteria ไม่สมบูรณ์
- คุณค่าไม่ชัดเจนหรือเป็นนามธรรม

#### ระดับต้องปรับปรุง (D-F)
- ไม่ปฏิบัติตาม INVEST criteria
- ขาด acceptance criteria
- เน้นที่ระบบมากกว่าผู้ใช้

### แบบฝึกหัด

#### แบบฝึกหัดที่ 1: ปรับปรุง User Story
ให้ปรับปรุง user stories ต่อไปนี้:

```
1. "ระบบต้องมีการล็อกอิน"
2. "As a user, I want to search"  
3. "As a developer, I want to implement database"
4. "As a user, I want a nice interface so that it looks good"
```

#### แบบฝึกหัดที่ 2: Story Estimation
ให้ประมาณ story points สำหรับ stories เหล่านี้:

```
1. Change footer text color
2. Add forgot password functionality  
3. Integrate with payment gateway
4. Create user dashboard with analytics
5. Implement two-factor authentication
```

---

## 13. สรุป

### Key Takeaways

1. **User Story คือเครื่องมือการสื่อสาร** ไม่ใช่เอกสารข้อมูลจำเพาะ
2. **เน้นที่คุณค่า** ไม่ใช่ฟีเจอร์
3. **ใช้ INVEST criteria** เป็นเกณฑ์วัดคุณภาพ
4. **Acceptance criteria สำคัญ** สำหรับการทดสอบ
5. **Story mapping ช่วยเห็นภาพรวม** และวางแผนได้ดี

### จุดสำคัญสำหรับการนำไปใช้

**ในการทำงานจริง:**
- User stories เป็นการเริ่มต้นการสนทนา ไม่ใช่สิ้นสุด
- ต้องมีการปรับปรุงและพัฒนาอย่างต่อเนื่อง
- ความร่วมมือระหว่างทีมเป็นสิ่งสำคัญ

**สำหรับการเรียนต่อ:**
- ศึกษา advanced techniques เช่น Impact Mapping
- เรียนรู้เครื่องมือต่างๆ เพิ่มเติม
- ฝึกฝนกับโปรเจคจริง

---

## แหล่งข้อมูลเพิ่มเติม

### หนังสือแนะนำ
- "User Stories Applied" โดย Mike Cohn
- "Agile Estimating and Planning" โดย Mike Cohn
- "User Story Mapping" โดย Jeff Patton

### เว็บไซต์และบทความ
- Mountain Goat Software (Mike Cohn's website)
- Atlassian Agile Guide
- Scrum.org User Story resources

### เครื่องมือที่แนะนำ
- **เริ่มต้น:** Trello + Story Templates
- **ทีมกลาง:** Jira + Confluence  
- **Enterprise:** Azure DevOps + Teams

**หมายเหตุ:** บทเรียนนี้เป็นส่วนหนึ่งของการเรียนรู้ Requirements Engineering ที่จะต่อยอดไปสู่การวิเคราะห์ การจัดลำดับความสำคัญ และการจัดการความต้องการในสัปดาห์ถัดไป