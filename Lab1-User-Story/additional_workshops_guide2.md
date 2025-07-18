#### รูปแบบ "Living Museum"
- กลุ่มต่างๆ ตั้ง "station" ใน classroom
- ผู้ชมเดินไปตาม station และสังเกตการณ์
- แต่ละ station แสดง 5-7 นาที แล้วหมุนเวียน

#### Station Setup:
```
Station 1: น้องเอิร์น (Student Crisis)
Props: โทรศัพท์, ใบเสร็จ, สมุดบัญชี
Scene: ตรวจสอบยอดเงินและตกใจ

Station 2: พี่แอม (Young Professional)  
Props: โน๊ตบุ๊ค, payslip, calculator
Scene: วางแผนการเงินส่วนตัว

Station 3: ป้าสมจิต (Family Manager)
Props: ใบเสร็จหลายใบ, เงินสด, smartphone
Scene: คำนวณค่าใช้จ่ายครอบครัว

Station 4: น้องไอซ์ (Freelancer)
Props: laptop, invoice, multiple phones
Scene: จัดการรายได้ไม่แน่นอน

Station 5: พี่โอ๊ค (Executive)
Props: tablet, multiple bank statements
Scene: ดู portfolio และ investment

Station 6: ลุงสมชาย (Traditional Merchant)
Props: เงินสด, สมุดบันทึก, smartphone เก่า
Scene: นับเงินและกังวลการเกษียณ

Station 7: น้องเบส (High School Student)
Props: โทรศัพท์, catalog สินค้า, เงินเหรียญ
Scene: ฝันถึงสิ่งที่อยากซื้อ
```

### Phase 3: User Interview Simulation (30 นาที)

#### การสัมภาษณ์แบบ Speed Dating
- แต่ละ round 5 นาทีx
- กลุ่มผู้ชมหมุนเวียนไปสัมภาษณ์
- ใช้ structured interview questions

#### Interview Questions Framework:

**สำหรับ Financial Habits:**
```
1. "เล่าให้ฟังหน่อยว่าวันปกติคุณใช้เงินยังไง?"
2. "คุณรู้สึกยังไงเวลาเช็คยอดเงินในบัญชี?"
3. "เวลาซื้อของ คุณตัดสินใจยังไง?"
4. "คุณเคยมีปัญหาเงินไม่พอใช้มั้ย? แก้ยังไง?"
5. "ถ้ามีเงินเผื่อ คุณจะทำอะไร?"
```

**สำหรับ Technology Usage:**
```
1. "คุณใช้แอปอะไรเกี่ยวกับเงินบ้าง?"
2. "อะไรที่ทำให้คุณอยากใช้แอปใหม่?"
3. "คุณชอบแอปแบบไหน? ง่ายๆ หรือมีฟีเจอร์เยอะ?"
4. "เวลามีปัญหากับแอป คุณทำยังไง?"
```

**สำหรับ Pain Points Deep Dive:**
```
1. "อะไรที่รำคาญที่สุดเกี่ยวกับการจัดการเงิน?"
2. "คุณเคยอยากทำอะไรกับเงิน แต่ทำไม่ได้?"
3. "ถ้าคุณมีพลังวิเศษ จะแก้ปัญหาเงินยังไง?"
4. "อะไรที่คุณกลัวที่สุดเรื่องเงิน?"
```

### Phase 4: User Story Creation Workshop (35 นาที)

#### ขั้นตอนที่ 1: Pain Point Clustering (10 นาที)
```
กิจกรรม: Affinity Mapping
- เขียน pain points ที่พบลงใน sticky notes
- จัดกลุ่มตาม theme
- ตั้งชื่อแต่ละกลุ่ม

ตัวอย่าง Clusters:
🔴 Tracking & Awareness
🔵 Planning & Goal Setting  
🟢 Budgeting & Control
🟡 Investment & Growth
🟠 Emergency & Risk Management
🟣 Education & Learning
```

#### ขั้นตอนที่ 2: Cross-Persona Story Writing (20 นาที)
- แต่ละกลุ่มเขียน stories สำหรับ persona ที่สัมภาษณ์
- เน้น empathy และ real problems
- ใช้ข้อมูลจากการสัมภาษณ์จริง

#### ขั้นตอนที่ 3: Story Validation (5 นาที)
- กลุ่มเจ้าของ persona validate stories
- ปรับแก้ตาม feedback
- เพิ่มรายละเอียดที่ขาดหายไป

---

## ตัวอย่างผลลัพธ์ User Stories - Workshop 4

### Stories สำหรับน้องเอิร์น (University Student)

#### Story 1: การติดตามเงินแบบง่ายๆ
```
Story Title: Quick Expense Tracking

As น้องเอิร์น, นักศึกษาที่ใช้เงินแบบไม่คิด,
I want to quickly record my expenses with just a photo
So that I can understand where my money goes without extra effort

Context:
- When: ทุกครั้งที่ซื้อของ (ร้านกาแฟ, 7-11, canteen)
- Where: Mobile app ใช้ได้ทุกที่
- With whom: ใช้คนเดียว แต่อาจแชร์กับเพื่อน

Pain Points addressed:
- ไม่รู้ว่าเงินหายไปไหน
- ขี้เกียจบันทึกรายจ่าย
- ใช้จ่ายตามอารมณ์

Success Criteria:
- บันทึกรายจ่ายได้ใน 3 วินาที
- ใช้ AI แยกประเภทให้อัตโนมัติ
- เห็นสรุปการใช้จ่ายแบบ visual

Acceptance Criteria:
Given I just bought something and have the receipt
When I take a photo of the receipt in the app
Then the app should automatically extract amount, merchant, and category
And I should be able to confirm or edit the information quickly
And the expense should be added to my daily/monthly summary
And I should see my remaining budget for the day
```

#### Story 2: การแจ้งเตือนก่อนจ่ายเกิน
```
Story Title: Smart Spending Alert

As น้องเอิร์น, คนที่มักใช้เงินเกินงบ,
I want to get warnings before I overspend  
So that I can make better decisions and avoid running out of money

Context:
- When: ก่อนทำการชำระเงิน
- Where: Point of sale หรือก่อน confirm ใน app
- With whom: แจ้งเตือนส่วนตัว

Pain Points addressed:
- มักจะหมดเงินก่อนสิ้นเดือน
- ใช้จ่ายตามอารมณ์
- ไม่ได้ติดตามงบประมาณ

Success Criteria:
- ได้รับแจ้งเตือนก่อนใช้จ่ายเกิน
- เห็นผลกระทบต่องบรายวัน/รายเดือน
- มีทางเลือกอื่นแทน

Acceptance Criteria:
Given I'm about to make a purchase that would exceed my daily budget
When I scan QR code or enter payment amount
Then I should see a friendly warning about budget impact
And I should see how many days of budget this purchase represents
And I should get suggestions for alternatives or ways to adjust my budget
And I can choose to proceed anyway or cancel the purchase
```

### Stories สำหรับป้าสมจิต (Family Manager)

#### Story 3: งบประมาณครอบครัว
```
Story Title: Family Budget Management

As ป้าสมจิต, แม่บ้านที่ดูแลเงินครอบครัว,
I want to track and control family expenses by category
So that I can ensure we don't overspend and save for important goals

Context:
- When: ทุกวันเมื่อมีค่าใช้จ่าย
- Where: บ้าน, ตลาด, ร้านค้า
- With whom: สามีและลูกๆ

Pain Points addressed:
- ค่าใช้จ่ายครอบครัวเพิ่มขึ้นเรื่อยๆ
- ไม่รู้ว่าเงินหายไปหมวดไหนมาก
- ต้องประหยัดแต่ไม่รู้จะเริ่มยังไง

Success Criteria:
- ดูรายจ่ายแยกตามหมวดหมู่ได้
- เปรียบเทียบกับเดือนก่อนได้
- หาจุดที่ควรประหยัดได้

Acceptance Criteria:
Given I manage multiple family expense categories
When I view my monthly budget dashboard
Then I should see spending by category (food, utilities, education, etc.)
And I should see budget vs actual with clear visual indicators
And I should get suggestions for categories where we can save money
And I should be able to set spending limits for each category
```

#### Story 4: การแจ้งเตือนบิลต่างๆ
```
Story Title: Bill Payment Reminders

As ป้าสมจิต, คนที่ต้องจำวันชำระบิลหลายรายการ,
I want automatic reminders for all monthly bills
So that I never miss payments and avoid late fees

Context:
- When: ก่อนวันครบกำหนดชำระ 3-5 วัน
- Where: LINE notification หรือ SMS
- With whom: อาจต้องแจ้งสามีบางบิล

Pain Points addressed:
- ลืมจ่ายบิลและโดนค่าปรับ
- มีบิลหลายรายการ จำยาก
- บางบิลต้องจ่ายเป็นเงินสด

Success Criteria:
- ไม่เคยลืมจ่ายบิล
- รู้ล่วงหน้าว่าเดือนนี้ต้องจ่ายเท่าไหร่
- วางแผนกระแสเงินสดได้

Acceptance Criteria:
Given I have set up all my monthly bills in the app
When payment due dates are approaching
Then I should receive notifications 5 days, 2 days, and on the due date
And notifications should include amount due and payment method
And I should be able to mark bills as paid directly from the notification
And I should see a monthly overview of all upcoming bills
```

### Stories สำหรับน้องไอซ์ (Freelancer)

#### Story 5: การจัดการรายได้ไม่แน่นอน
```
Story Title: Irregular Income Management

As น้องไอซ์, freelancer ที่รายได้ไม่แน่นอน,
I want to automatically allocate income into different purposes
So that I can maintain stable cash flow despite irregular earnings

Context:
- When: เมื่อได้รับเงินจาก client
- Where: Mobile app เมื่อเงินเข้าบัญชี
- With whom: ใช้คนเดียว

Pain Points addressed:
- รายได้ไม่แน่นอน วางแผนยาก
- เดือนที่เงินเยอะใช้หมด เดือนที่เงินน้อยลำบาก
- ไม่รู้ว่าควรเก็บเท่าไหร่

Success Criteria:
- มีเงินใช้สม่ำเสมอทุกเดือน
- มีเงินฉุกเฉินเพียงพอ
- สามารถลงทุนในตัวเองได้

Acceptance Criteria:
Given I receive irregular payments from clients
When money comes into my account
Then the app should suggest allocation percentages (living expenses, emergency, business, taxes)
And I should be able to customize allocation rules based on my goals
And money should be automatically moved to designated savings accounts
And I should see projection of how long current savings will last
```

### Stories สำหรับพี่โอ๊ค (Executive)

#### Story 6: ภาพรวมทรัพย์สินและหนี้สิน
```
Story Title: Net Worth Dashboard

As พี่โอ๊ค, executive ที่มีสินทรัพย์หลากหลาย,
I want a consolidated view of all my assets and liabilities
So that I can make informed decisions about my financial portfolio

Context:
- When: สัปดาห์ละครั้งหรือเมื่อต้องตัดสินใจการเงิน
- Where: Mobile และ web dashboard
- With whom: อาจปรึกษาที่ปรึกษาการเงิน

Pain Points addressed:
- ข้อมูลการเงินกระจัดกระจาย
- ไม่เห็นภาพรวม net worth
- ตัดสินใจลงทุนใหม่ยาก

Success Criteria:
- เห็นมูลค่าทรัพย์สินรวมแบบ real-time
- ติดตาม ROI ของ investment ต่างๆ
- วางแผนการเงินได้ดีขึ้น

Acceptance Criteria:
Given I have connected all my financial accounts
When I view the net worth dashboard
Then I should see total assets, liabilities, and net worth with trend charts
And I should see performance of different investment categories
And I should get insights about asset allocation and rebalancing suggestions
And I should be able to run scenarios for major financial decisions
```

### Non-Functional Requirements Stories

#### Story 7: ความปลอดภัยข้อมูล
```
Story Title: Financial Data Security

As ทุกคนที่ใช้แอปการเงิน,
I want my financial data to be completely secure and private
So that I can trust the app with my sensitive information

Acceptance Criteria:
- All data encrypted end-to-end
- Biometric authentication required
- Session timeout after inactivity
- No data sharing without explicit consent
- Compliance with Thai personal data protection laws
```

#### Story 8: การทำงานแบบ Offline
```
Story Title: Offline Functionality

As ผู้ใช้ที่อาจไม่มี internet ตลอดเวลา,
I want to record expenses and view basic information offline
So that I can maintain my tracking habits regardless of connectivity

Acceptance Criteria:
- Can record expenses without internet
- Data syncs automatically when online
- Essential features work offline
- Clear indication of sync status
```

---

## Implementation ใน Trello และ Miro

### Trello Workflow สำหรับ Workshop 4

#### Board Structure: "MoneyWise User Stories"

**List 1: "Character Gallery" 🎭**
```
Cards:
- น้องเอิร์น - University Student [Label: Student Life]
- พี่แอม - Fresh Graduate [Label: Young Professional]  
- ป้าสมจิต - Family Manager [Label: Family]
- น้องไอซ์ - Freelancer [Label: Gig Economy]
- พี่โอ๊ค - Executive [Label: Professional]
- ลุงสมชาย - Merchant [Label: Traditional]
- น้องเบส - High School [Label: Teen]
```

**List 2: "Pain Points Library" 😰**
```
Cards organized by themes:
- 💸 Spending Awareness
- 📊 Budget Management  
- 💰 Saving Challenges
- 📱 Technology Barriers
- 👨‍👩‍👧‍👦 Family Coordination
- 💼 Income Variability
- 🎯 Goal Achievement
```

**List 3: "User Stories - In Progress" ✍️**
```
Cards ที่กำลังเขียนระหว่าง workshop:
- Template card format:
  Title: [Persona] - [Feature Name]
  Description: Full user story
  Acceptance Criteria: Checklist format
  Story Points: Fibonacci scale
  Priority: MoSCoW labels
```

**List 4: "User Stories - Ready for Review" 👀**
```
Stories ที่เขียนเสร็จแล้วรอ feedback
```

**List 5: "User Stories - Approved" ✅**
```
Stories ที่ผ่านการ review จาก persona owners
```

**List 6: "Epic Planning" 🗺️**
```
Cards สำหรับจัดกลุ่ม related stories:
- 📊 Expense Tracking Epic
- 💰 Budget Management Epic
- 🎯 Goal Setting Epic  
- 📈 Investment Tracking Epic
- 👨‍👩‍👧‍👦 Family Features Epic
- 🔔 Notifications & Alerts Epic
```

#### Custom Fields ใน Trello:
```
- Persona: Dropdown (เอิร์น, แอม, สมจิต, etc.)
- Priority: Dropdown (Must Have, Should Have, Could Have)
- Story Points: Number (1, 2, 3, 5, 8, 13, 21)
- Theme: Dropdown (Tracking, Budgeting, Goals, etc.)
- Status: Dropdown (Draft, Review, Approved, In Development)
```

#### Power-Ups ที่แนะนำ:
- **Voting Power-Up:** สำหรับ prioritize stories
- **Calendar Power-Up:** สำหรับ deadline และ milestones
- **Custom Fields Power-Up:** สำหรับ metadata
- **Butler Automation:** สำหรับ workflow automation

### Miro Template สำหรับ Workshop 4

#### Board Layout: "MoneyWise Story Mapping"

```
┌─────────────────────────────────────────────────────────────────┐
│                     MoneyWise Story Map                        │
│                 Personal Finance Management                    │
├─────────────────────────────────────────────────────────────────┤
│ Personas (Color-coded avatars):                                │
│ 🎓เอิร์น  👔แอม  👩‍👧‍👦สมจิต  💻ไอซ์  💼โอ๊ค  🛒สมชาย  📱เบส        │
├─────────────────────────────────────────────────────────────────┤
│ User Journey (Backbone Activities):                            │
│ [Setup] → [Track] → [Budget] → [Save] → [Invest] → [Review]   │
├─────────────────────────────────────────────────────────────────┤
│ Walking Skeleton (Key Tasks):                                  │
│ • Register     • Record expenses  • Set budgets              │
│ • Link accounts • Get insights    • Receive alerts           │
│ • Set goals    • Track progress   • Get recommendations       │
├─────────────────────────────────────────────────────────────────┤
│ User Stories (Swimming Lanes by Persona):                     │
│                                                               │
│ 🎓 Student Stories:  [Story cards in green]                   │
│ 👔 Professional:     [Story cards in blue]                    │
│ 👩‍👧‍👦 Family:        [Story cards in purple]                  │
│ 💻 Freelancer:       [Story cards in orange]                  │
│ 💼 Executive:        [Story cards in red]                     │
│ 🛒 Traditional:      [Story cards in brown]                   │
│ 📱 Teen:             [Story cards in yellow]                  │
│                                                               │
├─────────────────────────────────────────────────────────────────┤
│ Release Planning:                                              │
│ MVP (3 months) | V2 (6 months) | V3 (12 months)              │
│ Core Features  | Enhanced UX    | Advanced Features           │
└─────────────────────────────────────────────────────────────────┘
```

#### วิธีใช้ Miro Template:

**Phase 1: Character Mapping (10 นาที)**
- วางรูป avatar ของแต่ละ persona
- เขียน key pain points ใต้ avatar
- ใช้สีต่างกันสำหรับแต่ละ persona

**Phase 2: Journey Mapping (15 นาที)**
- วาง backbone activities ตาม user journey
- แต่ละ persona อาจมี journey เส้นทางต่างกัน
- ใช้ลูกศรเชื่อม activities

**Phase 3: Story Creation (30 นาที)**
- สร้าง sticky notes สำหรับแต่ละ story
- จัดเรียงใต้ activity ที่เกี่ยวข้อง
- ใช้สีตาม persona

**Phase 4: Prioritization (15 นาที)**
- ย้าย stories ลงใน release lanes
- ใช้ dot voting เพื่อ prioritize
- จัดกลุ่มเป็น epics

#### Miro Templates และ Frameworks:

**Empathy Map Template:**
```
For each persona:
┌─────────────┬─────────────┐
│    SAYS     │    THINKS   │
│ "เงินหมด    │ กังวลเรื่อง  │
│  เร็วจัง"    │ อนาคต       │
├─────────────┼─────────────┤
│    DOES     │    FEELS    │
│ เช็คแอป     │ เครียด      │
│ ธนาคารบ่อย  │ ไม่มั่นใจ   │
└─────────────┴─────────────┘
```

**Value Proposition Canvas:**
```
Customer Jobs:
- Manage monthly expenses
- Save for goals
- Understand spending patterns

Pain Points:
- Manual tracking is tedious
- No visibility into spending
- Hard to stick to budgets

Gain Creators:
- Automatic expense categorization
- Real-time spending alerts
- Gamified saving goals

Pain Relievers:
- Photo receipt capture
- Smart notifications
- Simple interface
```

---

## การประเมินผล Workshop 3 & 4

### Rubric การประเมิน (100 คะแนน)

#### Role-Playing Performance (30 คะแนน)
**Character Authenticity (15 คะแนน):**
- A (13-15): สมบทบาทสมจริง เข้าใจ persona ลึกซึ้ง แสดงออกได้น่าเชื่อ
- B (11-12): สมบทบาทดี เข้าใจ persona ส่วนใหญ่ แสดงออกเหมาะสม
- C (8-10): สมบทบาทปานกลาง เข้าใจ persona พื้นฐาน แสดงออกได้บ้าง
- D-F (0-7): สมบทบาทไม่น่าเชื่อ ไม่เข้าใจ persona หรือแสดงไม่ได้

**Pain Points Communication (15 คะแนน):**
- A (13-15): สื่อสาร pain points ได้ชัดเจนและสมจริง ทำให้ผู้ชมเข้าใจได้ดี
- B (11-12): สื่อสาร pain points ได้ดี ผู้ชมเข้าใจส่วนใหญ่
- C (8-10): สื่อสาร pain points ได้พื้นฐาน ผู้ชมเข้าใจบ้าง
- D-F (0-7): สื่อสาร pain points ไม่ชัดเจน ผู้ชมไม่เข้าใจ

#### Interview Skills (20 คะแนน)
**Question Quality (10 คะแนน):**
- A (9-10): ถามคำถามที่ลึกซึ้ง เจาะประเด็น ได้ข้อมูลที่มีคุณค่า
- B (7-8): ถามคำถามที่ดี ได้ข้อมูลที่เป็นประโยชน์
- C (5-6): ถามคำถามพื้นฐาน ได้ข้อมูลบ้าง
- D-F (0-4): ถามคำถามที่ไม่เกี่ยวข้อง หรือไม่ได้ข้อมูลที่มีประโยชน์

**Active Listening (10 คะแนน):**
- A (9-10): ฟังอย่างตั้งใจ ถามคำถาม follow-up ที่ดี
- B (7-8): ฟังดี มีคำถาม follow-up บ้าง
- C (5-6): ฟังปานกลาง คำถาม follow-up น้อย
- D-F (0-4): ไม่ค่อยฟัง ไม่มีคำถาม follow-up

#### User Story Quality (30 คะแนน)
**INVEST Compliance (15 คะแนน):**
- A (13-15): Stories ปฏิบัติตาม INVEST ครบถ้วน มีคุณภาพสูง
- B (11-12): Stories ปฏิบัติตาม INVEST ส่วนใหญ่ มีคุณภาพดี
- C (8-10): Stories ปฏิบัติตาม INVEST บ้าง มีคุณภาพปานกลาง
- D-F (0-7): Stories ไม่ปฏิบัติตาม INVEST คุณภาพต่ำ

**Empathy & Insight (15 คะแนน):**
- A (13-15): Stories แสดงความเข้าใจ persona ลึกซึ้ง แก้ปัญหาจริง
- B (11-12): Stories แสดงความเข้าใจ persona ดี แก้ปัญหาส่วนใหญ่
- C (8-10): Stories แสดงความเข้าใจ persona พื้นฐาน แก้ปัญหาบ้าง
- D-F (0-7): Stories ไม่แสดงความเข้าใจ persona ไม่แก้ปัญหาจริง

#### Collaboration & Presentation (20 คะแนน)
**Team Participation (10 คะแนน):**
- A (9-10): ทุกคนมีส่วนร่วม ทำงานร่วมกันได้ดีเยี่ยม
- B (7-8): ส่วนใหญ่มีส่วนร่วม ทำงานร่วมกันได้ดี
- C (5-6): บางคนมีส่วนร่วม ทำงานร่วมกันได้ปานกลาง
- D-F (0-4): น้อยคนมีส่วนร่วม ทำงานร่วมกันไม่ได้

**Communication Skills (10 คะแนน):**
- A (9-10): นำเสนอชัดเจน มั่นใจ ตอบคำถามได้ดี
- B (7-8): นำเสนอดี ตอบคำถามได้ส่วนใหญ่
- C (5-6): นำเสนอปานกลาง ตอบคำถามได้บ้าง
- D-F (0-4): นำเสนอไม่ชัดเจน ตอบคำถามไม่ได้

---

## ผลการเรียนรู้ที่คาดหวัง

### จาก Workshop 3 (ห้องสมุดดิจิทัล)
**Knowledge Gained:**
- เข้าใจความแตกต่างของ user needs ในบริบทการศึกษา
- รู้จักกับ institutional requirements และ constraints
- เข้าใจความสำคัญของ accessibility และ inclusivity

**Skills Developed:**
- การทำ user research ผ่าน role-playing
- การเขียน user stories สำหรับ diverse user groups
- การคิดเชิง system integration (library, academic, IT systems)

**Real-World Application:**
- เข้าใจปัญหาของระบบ legacy และการ modernization
- ความสำคัญของ user training และ change management
- การออกแบบสำหรับ different digital literacy levels

### จาก Workshop 4 (การเงินส่วนตัว)
**Knowledge Gained:**
- เข้าใจ financial behavior ของคนไทยในยุคดิจิทัล
- รู้จัก fintech trends และ user expectations
- เข้าใจความสำคัญของ security และ trust ใน financial apps

**Skills Developed:**
- การทำ empathy mapping และ behavioral analysis
- การเขียน user stories สำหรับ sensitive domains
- การคิดเชิง personalization และ AI-driven features

**Real-World Application:**
- เข้าใจ regulatory constraints ในอุตสาหกรรมการเงิน
- ความสำคัญของ user education และ financial literacy
- การออกแบบสำหรับ different economic backgrounds

---

## การเชื่อมโยงกับหลักสูตร

### ไปสู่สัปดาห์ที่ 2: Requirements Analysis & Prioritization
**จาก Workshop 3 & 4 จะนำไปใช้:**
- User stories ที่สร้างขึ้นเป็น input สำหรับการวิเคราะห์
- ฝึกใช้ MoSCoW method กับ stories จริง
- เรียนรู้การจัดการ conflicting requirements จาก different personas

### ไปสู่สัปดาห์ที่ 3: Documentation & Validation
**ข้อมูลที่จะใช้ต่อ:**
- User stories จะถูกขยายเป็น detailed requirements specifications
- Acceptance criteria จะกลายเป็น test cases
- Personas จะใช้ในการ validate requirements

### ไปสู่ Software Design Phase (สัปดาห์ 5-15)
**Foundation ที่สร้างไว้:**
- User stories เป็น input สำหรับ architectural decisions
- Persona insights จะนำไปสู่ UX/UI design choices
- Non-functional requirements จะกำหนด technical architecture

---

## Additional Resources สำหรับอาจารย์

### การเตรียม Workshop Materials

#### ชุดอุปกรณ์สำหรับ Role-Playing:
```
📝 Persona Cards (พิมพ์แล้ว):
- Character profiles พร้อมรูปภาพ
- Scenario scripts
- Pain points และ goals summary
- Digital behavior profiles

🎭 Props สำหรับแสดง:
- Smartphones (mockups)
- Receipt samples
- Bank statements (ปลอม)
- Cash และ cards (ปลอม)
- Laptops/tablets (ถ้ามี)

📋 Interview Forms:
- Structured question templates
- Observation sheets
- Pain point collection forms
- User story templates

🎯 Assessment Tools:
- Rubric printouts
- Peer evaluation forms
- Self-reflection questionnaires
```

#### Digital Templates:
```
📱 Trello Templates:
- Pre-configured boards
- Custom field setups
- Label systems
- Automation rules

🖼️ Miro Templates:
- Story mapping frameworks
- Empathy map templates
- Value proposition canvas
- User journey maps

📊 Google Sheets:
- Assessment tracking
- Story point estimation sheets
- Persona comparison matrices
```

### คำแนะนำการอำนวยความสะดวก

#### สำหรับ Role-Playing Phase:
```
🎬 ช่วยให้นักศึกษาเข้าถึงตัวละคร:
- เล่าเรื่องเพิ่มเติมเกี่ยวกับ personas
- ให้ดูตัวอย่าง video หรือ case studies
- สนับสนุนให้ใช้ props และ gestures
- สร้างบรรยากาศที่ปลอดภัยสำหรับการแสดง

🎙️ ช่วยใน Interview Phase:
- โชว์ตัวอย่างคำถามที่ดี
- แนะนำเทคนิค active listening
- ช่วยแก้ไขเมื่อ interview ติดขัด
- เตือนเรื่องเวลาและ objectives
```

#### สำหรับ Story Writing Phase:
```
✍️ คำแนะนำการเขียน:
- ให้ตัวอย่าง user story ที่ดี
- ช่วยปรับ wording ให้ชัดเจน
- แนะนำการหา root cause ของ pain points
- สนับสนุนการคิด out-of-the-box solutions

🔍 Quality Assurance:
- เช็ค INVEST criteria ระหว่างเขียน
- ช่วยให้ stories มี appropriate scope
- แนะนำการเขียน acceptance criteria
- ตรวจสอบ traceability กลับไปหา pain points
```

### การปรับใช้สำหรับบริบทต่างๆ

#### สำหรับ Online/Hybrid Classes:
```
💻 Digital Role-Playing:
- ใช้ breakout rooms สำหรับ character preparation
- Video presentation แทน live performance
- Screen sharing สำหรับ prop simulation
- Recording sessions เพื่อ review และ feedback

📱 Virtual Interview:
- ใช้ polling tools สำหรับ quick feedback
- Shared documents สำหรับ collaborative note-taking
- Chat functions สำหรับ Q&A
- Whiteboard tools สำหรับ visual mapping
```

#### สำหรับ International Students:
```
🌍 Cultural Adaptation:
- ปรับ personas ให้เหมาะกับ cultural background
- ใช้ universal scenarios (food, transportation, communication)
- แปลคำศัพท์เฉพาะทาง
- ให้ context เพิ่มเติมเกี่ยวกับ Thai business culture
```

#### สำหรับ Different Class Sizes:
```
👥 Small Classes (< 20 คน):
- เพิ่มเวลา interaction และ detailed feedback
- ให้ทุกกลุ่มแสดง role-play
- มี one-on-one coaching มากขึ้น

👫 Large Classes (> 40 คน):
- ใช้ gallery walk format
- เลือกแค่บางกลุ่มแสดง role-play
- ใช้ peer assessment มากขึ้น
- สร้าง standard templates ให้ใช้
```

---

## ตัวอย่างการใช้งานจริงใน Industry

### Workshop 3 Skills → Career Applications

#### UX Research Roles:
```
🔍 User Research Methods:
- Ethnographic studies ในองค์กรการศึกษา
- Stakeholder interviews สำหรับ institutional software
- Accessibility testing และ inclusive design
- Change management สำหรับ digital transformation

💼 Project Examples:
- University information systems redesign
- E-learning platform development
- Digital library modernization
- Student services digitalization
```

#### Product Management Roles:
```
📋 Requirements Management:
- Multi-stakeholder requirement gathering
- Academic vs. administrative needs balancing
- Compliance และ regulatory requirements
- Legacy system integration planning

🎯 Product Strategy:
- EdTech product development
- B2B software สำหรับ educational institutions
- SaaS platforms สำหรับ knowledge management
```

### Workshop 4 Skills → Career Applications

#### FinTech Industry:
```
💰 Financial Product Design:
- Personal finance management apps
- Investment platforms สำหรับ retail investors
- SME banking solutions
- Payment gateway development

📊 Behavioral Analytics:
- User financial behavior analysis
- Risk assessment algorithm design
- Personalization engine development
- Financial education content strategy
```

#### Consulting & Strategy:
```
🏢 Digital Transformation:
- Financial services modernization
- Customer journey optimization
- Regulatory compliance consulting
- Data privacy และ security strategy
```

---

## การพัฒนาต่อยอดสำหรับอาจารย์

### Advanced Workshop Variations

#### Workshop 3.5: Cross-Platform Integration
```
Scenario: ระบบ Smart Campus ที่เชื่อมต่อ:
- ระบบห้องสมุด
- ระบบการศึกษา (LMS)
- ระบบบริการนักศึกษา
- ระบบ IoT ในอาคาร

Focus: API design, data integration, user experience consistency
```

#### Workshop 4.5: Regulatory Compliance
```
Scenario: FinTech app ที่ต้องเป็นไปตาม:
- พ.ร.บ. คุ้มครองข้อมูลส่วนบุคคล
- กฎหมายการเงิน BOT
- International compliance (GDPR)

Focus: Compliance requirements, privacy by design, audit trails
```

### การสร้าง Assessment ที่ทันสมัย

#### Portfolio-Based Assessment:
```
📁 Student Portfolio Contents:
- Role-playing video recordings
- Interview transcripts และ analysis
- User story collections พร้อม reasoning
- Reflection essays เกี่ยวกับ learning process
- Peer feedback และ self-assessment

🏆 Grading Rubric:
- Process quality (research, analysis, collaboration)
- Output quality (stories, documentation, presentation)
- Learning reflection (growth mindset, critical thinking)
- Professional readiness (communication, empathy, problem-solving)
```

#### Industry Partnership:
```
🤝 Real Client Projects:
- ความร่วมมือกับ startups ท้องถิ่น
- University departments เป็น real clients
- NGOs ที่ต้องการ digital solutions
- Government agencies ที่เปิดรับ student projects

📈 Success Metrics:
- Client satisfaction scores
- Story quality และ implementability
- Student confidence ใน real-world application
- Industry readiness assessment
```

---

## สรุปและข้อเสนอแนะ

### Key Success Factors

#### สำหรับนักศึกษา:
```
🎭 การเข้าถึงตัวละคร:
- ใส่ใจในรายละเอียดของ persona
- ลืมตัวเองและเป็นตัวละครอย่างเต็มที่
- ฟังและตอบสนองอย่างเป็นธรรมชาติ

🔍 การสังเกตและวิเคราะห์:
- ตั้งใจฟังมากกว่าพูด
- ถามคำถามที่เจาะลึก
- มองหา pain points ที่แท้จริง

✍️ การแปลงเป็น User Stories:
- เน้นคุณค่าที่ user จะได้รับ
- ใช้ภาษาที่ user เข้าใจ
- คิดถึง edge cases และ constraints
```

#### สำหรับอาจารย์:
```
🎪 การสร้างบรรยากาศ:
- สร้างความปลอดภัยในการแสดงออก
- สนับสนุนความคิดสร้างสรรค์
- ให้ feedback ที่สร้างสรรค์

⚖️ การสมดุล Structure และ Flexibility:
- มี framework ที่ชัดเจน
- ปรับตามการตอบสนองของนักศึกษา
- ยอมรับความแตกต่างในการเรียนรู้

🔄 การ Iterate และปรับปรุง:
- เก็บ feedback จากทุก workshop
- ปรับปรุง personas และ scenarios
- พัฒนา materials ให้ดีขึ้นเรื่อยๆ
```

### ผลกระทบระยะยาว

#### ต่อการเรียนรู้:
- นักศึกษามี empathy และ user-centric mindset
- เข้าใจความสำคัญของ user research
- มีทักษะการสื่อสารและการทำงานร่วมกัน
- เตรียมพร้อมสำหรับการทำงานในอุตสาหกรรม

#### ต่อหลักสูตร:
- เป็น foundation ที่แข็งแกร่งสำหรับ software design
- เชื่อมโยง theory กับ practice ได้ดี
- สร้างความตื่นเต้นและ engagement ในการเรียน
- เตรียมความพร้อมสำหรับ capstone projects

### การประเมินความสำเร็จ

#### Short-term Indicators:
- Student engagement และ participation levels
- Quality ของ user stories ที่สร้างขึ้น
- Peer feedback scores และ collaboration quality
- Instructor observations ของ learning process

#### Long-term Indicators:
- Performance ในวิชาต่อๆ ไป (software design, project courses)
- Industry readiness เมื่อเข้าฝึกงานหรือทำงาน
- Alumni feedback เกี่ยวกับประโยชน์ของ workshop
- Employer feedback เกี่ยวกับ soft skills ของบัณฑิต

---

## บทสรุป

Workshop 3 และ 4 ได้รับการออกแบบมาเพื่อให้นักศึกษาวิศวกรรมซอฟต์แวร์ปี 2 ได้ประสบการณ์ที่ลึกซึ้งในการทำความเข้าใจ user needs ผ่านการ role-playing และ empathy building

**จุดแข็งของ Workshop เหล่านี้:**

1. **Real-world Relevance:** ใช้สถานการณ์จากชีวิตจริงที่นักศึกษาคุ้นเคย
2. **Experiential Learning:** เรียนรู้ผ่านการปฏิบัติและการแสดงบทบาท
3. **Empathy Development:** สร้างความเข้าใจในมุมมองของ users ที่แตกต่างกัน
4. **Collaborative Skills:** พัฒนาการทำงานร่วมกันและการสื่อสาร
5. **Industry Preparation:** เตรียมทักษะที่จำเป็นสำหรับการทำงานจริง

**การนำไปใช้:**
- สามารถปรับใช้กับ online หรือ hybrid classes
- เหมาะกับนักศึกษาที่มี background แตกต่างกัน
- สามารถขยายเป็น real client projects ได้
- เชื่อมโยงกับหลักสูตรภาคต่อไปได้ดี

Workshop เหล่านี้จะช่วยให้นักศึกษามีพื้นฐานที่แข็งแกร่งสำหรับการเป็น Software Engineer ที่เข้าใจและใส่ใจผู้ใช้ ซึ่งเป็นทักษะที่มีค่ามากในยุคดิจิทัลปัจจุบัน# Workshop 3 & 4: Role-Playing และ Real-Life Scenarios
**ENGSE206 - สัปดาห์ที่ 1 (ต่อ)**

---

## Workshop 3: ระบบจัดการห้องสมุดมหาวิทยาลัยแบบดิจิทัล
### "EduLib Connect" - Digital Library Management System

---

## บริบทและสถานการณ์

### มหาวิทยาลัย TechnoVerse
**ข้อมูลทั่วไป:**
- มหาวิทยาลัยเทคโนโลยี ก่อตั้งมา 25 ปี
- นักศึกษา 12,000 คน, อาจารย์ 800 คน, เจ้าหน้าที่ 300 คน
- 4 คณะหลัก: วิศวกรรมศาสตร์, วิทยาศาสตร์, บริหารธุรกิจ, ศิลปศาสตร์
- ห้องสมุดกลาง 1 แห่ง, ห้องสมุดคณะ 4 แห่ง

### สภาพปัจจุบันของห้องสมุด
**ปัญหาที่พบ:**
- ระบบการยืม-คืน ยังใช้บาร์โค้ดและลงทะเบียนกระดาษ
- ไม่ทราบว่าหนังสือที่ต้องการมีในชั้นหรือถูกยืมไป
- ต้องเดินไปค้นหาหนังสือที่แต่ละชั้น
- ไม่มีระบบจองล่วงหน้า
- การต่ออายุการยืมต้องมาที่ห้องสมุด
- ไม่มีระบบแนะนำหนังสือตามความสนใจ

**ทรัพยากรห้องสมุด:**
- หนังสือ: 150,000 เล่ม (ไทย 60%, อังกฤษ 40%)
- วารสาร: 800 ชื่อเรื่อง
- ฐานข้อมูลออนไลน์: 15 ฐาน
- ที่นั่งอ่านหนังสือ: 800 ที่นั่ง
- ห้องกลุ่ม: 20 ห้อง
- คอมพิวเตอร์: 100 เครื่อง

### เป้าหมายของระบบใหม่
**Vision:** "ห้องสมุดอัจฉริยะที่เชื่อมต่อความรู้กับผู้เรียน"

**Business Goals:**
1. เพิ่มการใช้งานทรัพยากรห้องสมุด 40%
2. ลดเวลาการค้นหาหนังสือ 70%
3. เพิ่มความพึงพอใจผู้ใช้เป็น 4.5/5
4. ลดงานเอกสารของเจ้าหน้าที่ 50%

---

## 6 Personas หลัก (สำหรับ Role-Playing)

### 1. น้องมิน - First-Year Student (นักศึกษาปี 1)
**ข้อมูลส่วนตัว:**
- อายุ 18 ปี, คณะวิศวกรรมศาสตร์ สาขาคอมพิวเตอร์
- มาจากต่างจังหวัด, พักหอพัก
- ยังไม่คุ้นเคยกับระบบมหาวิทยาลัย
- ใช้โซเชียลมีเดียเป็นหลัก (TikTok, Instagram)

**พฤติกรรมการใช้ห้องสมุด:**
- ไปห้องสมุด 2-3 ครั้ง/สัปดาห์
- มักหาหนังสือตำราเรียนพื้นฐาน
- ชอบนั่งทำงานกลุ่มกับเพื่อน
- ไม่เคยใช้ฐานข้อมูลออนไลน์

**Pain Points:**
- ไม่รู้ว่าหนังสืออยู่ที่ไหน หมายเลขเรียงยังไง
- ต้องเดินหาหนังสือหลายชั้น
- ไม่กล้าถามเจ้าหน้าที่
- ลืมวันส่งหนังสือบ่อยๆ
- ไม่รู้ว่ามีหนังสือเกี่ยวกับหัวข้อที่สนใจอีกมั้ย

**Goals:**
- หาหนังสือได้เร็วและง่าย
- ไม่ต้องกลัวทำผิดกฎระเบียบ
- ได้เรียนรู้การใช้ทรัพยากรอย่างถูกต้อง
- มีเพื่อนๆ ช่วยแนะนำหนังสือดีๆ

**Digital Comfort Level:** สูง (แต่เฉพาะ social apps)
**มคการฟ์:** การแจ้งเตือนผ่าน LINE หรือ push notification

### 2. พี่เอิร์ธ - Senior Student (นักศึกษาปี 4)
**ข้อมูลส่วนตัว:**
- อายุ 22 ปี, คณะบริหารธุรกิจ สาขาการตลาด
- ทำโครงงานจบ เรื่อง Digital Marketing Strategy
- เป็นหัวหน้าชมรมนักศึกษา
- มีประสบการณ์ทำงานพาร์ตไทม์

**พฤติกรรมการใช้ห้องสมุด:**
- ไปห้องสมุดทุกวัน ช่วงเย็น
- ต้องการหนังสือและงานวิจัยระดับสูง
- ใช้ฐานข้อมูลออนไลน์เป็น
- จองห้องกลุ่มสำหรับประชุมทีม

**Pain Points:**
- หนังสือใหม่ๆ มักถูกยืมหมด
- ฐานข้อมูลออนไลน์ล็อกอินยุ่งยาก
- ไม่สามารถจองหนังสือล่วงหน้าได้
- ต้องการเอกสารที่เกี่ยวข้องกับโครงงาน แต่ไม่รู้ว่ามีอะไรบ้าง
- เวลาในการค้นคว้าจำกัด

**Goals:**
- เข้าถึงข้อมูลระดับสูงได้รวดเร็ว
- จัดการการยืมหลายเล่มได้อย่างเป็นระบบ
- ได้รับการแนะนำเอกสารที่เกี่ยวข้องกับงานวิจัย
- ประสานงานกับทีมได้อย่างมีประสิทธิภาพ

**Digital Comfort Level:** สูงมาก
**การสื่อสาร:** Email, Microsoft Teams, LINE

### 3. อาจารย์ศรีไพร - Faculty Member (อาจารย์)
**ข้อมูลส่วนตัว:**
- อายุ 42 ปี, อาจารย์คณะวิทยาศาสตร์ สาขาฟิสิกส์
- ปริญญาเอก จากมหาวิทยาลัยในญี่ปุ่น
- สอนและทำวิจัยมา 12 ปี
- มีนักศึกษาใต้การดูแล 15 คน

**พฤติกรรมการใช้ห้องสมุด:**
- ไปห้องสมุด 1-2 ครั้ง/สัปดาห์
- ต้องการวารสารวิชาการระดับนานาชาติ
- ยืมหนังสือเพื่อเตรียมการสอน
- ต้องการห้องเงียบสำหรับการอ่านและเขียน

**Pain Points:**
- ฐานข้อมูลวารสารต่างชาติเข้าไม่ได้จากบ้าน
- ไม่ทราบว่ามีวารสารใหม่ๆ ที่เกี่ยวข้องกับงานวิจัย
- ต้องการหนังสือเฉพาะทางที่มีจำนวนจำกัด
- การขอซื้อหนังสือใหม่ใช้เวลานาน
- ไม่สามารถติดตามการยืมของนักศึกษาที่ปรึกษาได้

**Goals:**
- เข้าถึงทรัพยากรวิชาการได้ทุกที่ทุกเวลา
- ได้รับข้อมูลวารสารและหนังสือใหม่
- สามารถแนะนำทรัพยากรให้นักศึกษาได้
- มีพื้นที่เงียบสำหรับการทำงาน

**Digital Comfort Level:** กลาง-สูง
**การสื่อสาร:** Email เป็นหลัก, LINE สำหรับนักศึกษา

### 4. คุณรัตนา - Librarian (บรรณารักษ์)
**ข้อมูลส่วนตัว:**
- อายุ 35 ปี, บรรณารักษ์อาวุโส
- ทำงานที่ห้องสมุดมา 10 ปี
- จบปริญญาโทสารสนเทศศาสตร์
- รับผิดชอบระบบหมุนเวียนและบริการผู้ใช้

**พฤติกรรมการทำงาน:**
- เป็นคนแรกที่นักศึกษามาขอความช่วยเหลือ
- ต้องอัพเดทข้อมูลหนังสือใหม่ทุกวัน
- ประสานงานกับอาจารย์เรื่องการจัดซื้อ
- จัดกิจกรรมส่งเสริมการอ่าน

**Pain Points:**
- ต้องตอบคำถามซ้ำๆ เรื่องที่ตั้งหนังสือ
- ระบบเก่าช้าและมีข้อมูลไม่ครบ
- ไม่สามารถวิเคราะห์พฤติกรรมผู้ใช้ได้
- การทำรายงานสถิติใช้เวลานาน
- นักศึกษาไม่รู้วิธีใช้ทรัพยากรอย่างเต็มประสิทธิภาพ

**Goals:**
- ให้บริการที่รวดเร็วและถูกต้อง
- ลดงานประจำที่ซ้ำซาก
- ส่งเสริมการใช้ทรัพยากรห้องสมุดอย่างเต็มที่
- มีข้อมูลเพื่อปรับปรุงบริการ

**Digital Comfort Level:** สูง
**การสื่อสาร:** ระบบภายใน, Email, โทรศัพท์

### 5. น้องแบงค์ - Graduate Student (นักศึกษาปริญญาโท)
**ข้อมูลส่วนตัว:**
- อายุ 25 ปี, ปริญญาโท วิศวกรรมศาสตร์ สาขา AI
- ทำวิทยานิพนธ์เรื่อง Machine Learning in Healthcare
- ทำงานเป็น TA (Teaching Assistant)
- มีประสบการณ์ทำงานบริษัทเทคโนโลยี

**พฤติกรรมการใช้ห้องสมุด:**
- อยู่ห้องสมุดเกือบทุกวัน
- ต้องการบทความวิจัยล่าสุด
- ใช้ห้องกลุ่มสำหรับปรึกษาอาจารย์
- ค้นคว้าข้อมูลผ่านฐานข้อมูลต่างประเทศ

**Pain Points:**
- บทความที่ต้องการไม่ครบ หรือเก่า
- การเข้าถึงฐานข้อมูลนานาชาติมีข้อจำกัด
- ไม่มีระบบแจ้งเตือนเมื่อมีบทความใหม่
- ต้องการพื้นที่เงียบสำหรับการเขียนวิทยานิพนธ์
- การอ้างอิงเอกสารยุ่งยาก

**Goals:**
- เข้าถึงงานวิจัยล่าสุดในสาขา
- มีเครื่องมือช่วยในการจัดการอ้างอิง
- ได้รับการแนะนำงานวิจัยที่เกี่ยวข้อง
- มีพื้นที่เหมาะสำหรับการทำงานเข้มข้น

**Digital Comfort Level:** สูงมาก
**การสื่อสาร:** Slack, Discord, Email, LINE

### 6. คุณประยุทธ์ - IT Support (เจ้าหน้าที่ IT)
**ข้อมูลส่วนตัว:**
- อายุ 38 ปี, ผู้ดูแลระบบ IT ห้องสมุด
- จบปริญญาตรีวิศวกรรมคอมพิวเตอร์
- ทำงานที่มหาวิทยาลัยมา 8 ปี
- รับผิดชอบระบบคอมพิวเตอร์และเครือข่าย

**พฤติกรรมการทำงาน:**
- แก้ไขปัญหาระบบและอุปกรณ์
- อัพเดทซอฟต์แวร์และระบบรักษาความปลอดภัย
- ฝึกอบรมเจ้าหน้าที่ใช้ระบบใหม่
- ประสานงานกับผู้จำหน่ายระบบ

**Pain Points:**
- ระบบเก่ามีปัญหาบ่อยและซ่อมยาก
- ไม่มีระบบสำรองข้อมูลที่เชื่อถือได้
- ผู้ใช้ไม่เข้าใจการใช้งานระบบ
- การ integrate ระบบต่างๆ ยุ่งยาก
- ต้องดูแลระบบหลายแพลตฟอร์ม

**Goals:**
- มีระบบที่เสถียรและปลอดภัย
- ลดงาน maintenance และ support
- ผู้ใช้สามารถใช้งานได้เองโดยไม่ต้องขอความช่วยเหลือ
- มีข้อมูลสำหรับวางแผนระบบ

**Digital Comfort Level:** ผู้เชี่ยวชาญ
**การสื่อสาร:** ระบบ ticketing, Email, โทรศัพท์

---

## Role-Playing Activity Structure

### การเตรียมตัวสำหรับ Role-Playing (20 นาที)

#### ขั้นตอนที่ 1: Character Assignment
- แต่ละกลุ่ม (4-5 คน) ได้รับ persona 1 ตัว
- อ่านข้อมูล persona อย่างละเอียด
- อภิปรายเพื่อทำความเข้าใจ pain points และ goals
- เตรียมการแสดงบทบาท

#### ขั้นตอนที่ 2: Scenario Preparation
แต่ละกลุ่มเตรียม 3 สถานการณ์:

**สถานการณ์ A: วันธรรมดา (Typical Day)**
```
น้องมิน: เตรียมสอบกลางภาค วิชาคณิตศาสตร์
- ต้องหาหนังสือตำรา "Calculus for Engineers"
- ไม่รู้ว่าหนังสืออยู่ที่ไหน
- อยากได้แบบฝึกหัดเพิ่มเติม
- กลัวว่าจะหาไม่เจอและสอบไม่ทัน
```

**สถานการณ์ B: ช่วงสอบ (Exam Period)**
```
พี่เอิร์ธ: รีบทำโครงงานจบ
- ต้องการงานวิจัยเรื่อง Digital Marketing trends
- หนังสือที่ต้องการถูกยืมหมดแล้ว
- อยากจองล่วงหน้า เพราะต้องส่งงานอีก 2 สัปดาห์
- ต้องหาข้อมูลสถิติล่าสุด
```

**สถานการณ์ C: สถานการณ์ฉุกเฉิน (Emergency)**
```
อาจารย์ศรีไพร: เตรียมเอกสารสำหรับการประชุมวิชาการ
- ต้องการบทความใหม่ล่าสุดจากวารสาร Nature Physics
- ระบบฐานข้อมูลเข้าไม่ได้
- มีเวลาเหลือแค่ 1 วัน
- ต้องการสั่งพิมพ์เอกสารด่วน
```

#### ขั้นตอนที่ 3: Performance Preparation
- เขียน script สั้นๆ สำหรับแสดง (5-7 นาที)
- แบ่งบทบาทในกลุ่ม (narrator, main character, supporting characters)
- เตรียม props หรือการแสดงที่สร้างบรรยากาศ

### การแสดง Role-Playing (30 นาที)

#### รูปแบบการแสดง:
1. **Character Introduction (1 นาที):**
   - แนะนำตัวละครและบริบท
   - บอกข้อมูลพื้นฐานและความต้องการ

2. **Scenario Demonstration (3-4 นาที):**
   - แสดงสถานการณ์ปัญหาที่เกิดขึ้น
   - ให้เห็น pain points ที่ชัดเจน
   - แสดงความรู้สึกและผลกระทบ

3. **Wishful Thinking (1-2 นาที):**
   - แสดงสิ่งที่ตัวละครอยากให้ระบบช่วยแก้ไข
   - อธิบายโซลูชั่นในฝัน

### การสังเกตและ Note-Taking (กลุ่มผู้ชม)

#### แบบฟอร์มการสังเกต:
```
Persona: _______________
Observer Group: _______________

Pain Points ที่สังเกตได้:
1. _________________________________
2. _________________________________
3. _________________________________

Goals ที่ชัดเจน:
1. _________________________________
2. _________________________________
3. _________________________________

คำถามที่อยากถาม:
1. _________________________________
2. _________________________________

Ideas สำหรับ User Stories:
1. _________________________________
2. _________________________________
3. _________________________________
```

---

## User Story Workshop Phase (45 นาที)

### ขั้นตอนที่ 4: Cross-Group Interview (15 นาที)

#### การสัมภาษณ์แบบหมุนเวียน:
- กลุ่มผู้ชมสัมภาษณ์กลุ่มแสดง
- ใช้คำถาม 5W1H เพื่อเจาะลึก
- เน้นการทำความเข้าใจ motivation และ context

#### คำถามแนะนำ:
```
สำหรับ Pain Points:
- "ทำไมปัญหานี้ถึงสำคัญกับคุณ?"
- "บ่อยแค่ไหนที่คุณเจอปัญหานี้?"
- "คุณแก้ปัญหานี้ยังไงในปัจจุบัน?"

สำหรับ Goals:
- "สิ่งที่คุณต้องการจะช่วยคุณได้ยังไง?"
- "ถ้าได้สิ่งนี้ คุณจะใช้งานบ่อยไหม?"
- "มีอะไรอื่นที่สำคัญพอๆ กันมั้ย?"

สำหรับ Context:
- "ปกติคุณใช้ห้องสมุดเวลาไหน?"
- "คุณมาห้องสมุดกับใครบ้าง?"
- "คุณใช้เทคโนโลยีอะไรบ้างในชีวิตประจำวัน?"
```

### ขั้นตอนที่ 5: User Story Creation (20 นาที)

#### การเขียน Stories จากการสัมภาษณ์:
- แต่ละกลุ่มเขียน user stories สำหรับ persona ที่สัมภาษณ์
- ใช้ข้อมูลจากการแสดงและการสัมภาษณ์
- เน้นการแก้ปัญหาที่เกิดขึ้นจริง

#### Template สำหรับ User Story:
```
Story Title: _______________

As [Persona Name] (บอกบริบทเพิ่มเติม),
I want to [ความต้องการที่เฉพาะเจาะจง]
So that [ผลลัพธ์หรือคุณค่าที่ชัดเจน]

Context: 
- When: [สถานการณ์หรือเวลาที่เกิด]
- Where: [สถานที่หรือ platform]
- With whom: [คนอื่นที่เกี่ยวข้อง]

Pain Points addressed:
- [ปัญหาที่ story นี้แก้ไข]

Success Criteria:
- [วิธีรู้ว่า story สำเร็จ]
```

### ขั้นตอนที่ 6: Story Review และ Feedback (10 นาที)

#### การนำเสนอ Stories:
- แต่ละกลุ่มนำเสนอ 2-3 stories ที่ดีที่สุด
- กลุ่มเจ้าของ persona ให้ feedback ว่าเข้าใจถูกหรือไม่
- ปรับแก้ตาม feedback

---

## ตัวอย่างผลลัพธ์ที่คาดหวัง - Workshop 3

### Stories สำหรับน้องมิน (First-Year Student)

#### Story 1: หาหนังสือได้ง่าย
```
As น้องมิน, นักศึกษาปี 1 ที่ยังไม่คุ้นเคยระบบห้องสมุด,
I want to search for books using simple keywords and get visual directions
So that I can find the books I need without feeling lost or asking for help

Context:
- When: ช่วงเตรียมสอบหรือทำการบ้าน
- Where: มือถือหรือคอมพิวเตอร์ในห้องสมุด
- With whom: บางครั้งกับเพื่อน

Pain Points addressed:
- ไม่รู้ว่าหนังสืออยู่ที่ไหน
- กลัวถามเจ้าหน้าที่

Success Criteria:
- หาหนังสือที่ต้องการได้ภายใน 5 นาที
- มีแผนที่นำทางไปยังตำแหน่งหนังสือ
- มีข้อมูลว่าหนังสือมีในชั้นหรือถูกยืมไป

Acceptance Criteria:
Given I am looking for a specific textbook
When I search using course code or simple title
Then I should see the book's location with visual map
And I should see if the book is available or due date if borrowed
And I should get step-by-step directions from my current location
```

#### Story 2: การแจ้งเตือนผ่าน LINE
```
As น้องมิน, คนที่ใช้ LINE เป็นหลักและลืมเรื่องง่าย,
I want to receive book return reminders through LINE
So that I don't get fined for late returns and maintain good borrowing record

Context:
- When: 3 วัน และ 1 วันก่อนครบกำหนด
- Where: LINE personal chat
- With whom: ระบบแจ้งเตือนอัตโนมัติ

Pain Points addressed:
- ลืมวันส่งหนังสือบ่อยๆ
- กลัวโดนปรับ

Success Criteria:
- ได้รับการแจ้งเตือนทันเวลา
- สามารถต่ออายุการยืมผ่าน LINE ได้
- ไม่ต้องไปที่ห้องสมุดเพื่อต่ออายุ

Acceptance Criteria:
Given I have borrowed books from the library
When the return date is approaching (3 days and 1 day before)
Then I should receive LINE notification with book details and return date
And I should be able to extend the loan period directly from LINE
And I should see how many times I can still extend
```

### Stories สำหรับอาจารย์ศรีไพร (Faculty Member)

#### Story 3: เข้าถึงฐานข้อมูลจากบ้าน
```
As อาจารย์ศรีไพร, ผู้ที่ต้องค้นคว้างานวิจัยตลอดเวลา,
I want to access academic databases from home with single sign-on
So that I can continue my research work efficiently outside office hours

Context:
- When: เย็นและสุดสัปดาห์
- Where: บ้านหรือสถานที่อื่นนอกมหาวิทยาลัย
- With whom: ทำงานคนเดียวหรือกับนักศึกษาที่ปรึกษา

Pain Points addressed:
- ฐานข้อมูลวารสารต่างชาติเข้าไม่ได้จากบ้าน
- ต้องไปที่มหาวิทยาลัยเพื่อเข้าถึงข้อมูล

Success Criteria:
- เข้าถึงฐานข้อมูลได้ทุกที่ทุกเวลา
- ล็อกอินแค่ครั้งเดียวต่อวัน
- ดาวน์โหลดบทความได้เต็มตัว

Acceptance Criteria:
Given I am an authenticated faculty member
When I access library portal from outside campus
Then I should be able to log in with my university credentials
And I should have full access to all subscribed databases
And I should be able to download full-text articles
And my session should remain active for reasonable time
```

#### Story 4: การแนะนำงานวิจัยที่เกี่ยวข้อง
```
As อาจารย์ศรีไพร, ผู้ที่ต้องติดตามงานวิจัยใหม่ๆ,
I want to receive notifications about new publications in my field
So that I can stay current with research developments and cite relevant work

Context:
- When: เมื่อมีวารสารใหม่หรือบทความที่เกี่ยวข้อง
- Where: Email หรือผ่านระบบ portal
- With whom: ระบบ AI recommendation

Pain Points addressed:
- ไม่ทราบว่ามีวารสารใหม่ๆ ที่เกี่ยวข้องกับงานวิจัย
- ต้องติดตามด้วยตนเองใช้เวลามาก

Success Criteria:
- ได้รับข้อมูลงานวิจัยใหม่ที่เกี่ยวข้อง
- สามารถกำหนด keywords และ topics ที่สนใจ
- มีระบบกรองที่มีคุณภาพ

Acceptance Criteria:
Given I have set my research interests and keywords
When new publications matching my criteria are available
Then I should receive weekly digest of relevant articles
And I should be able to save interesting articles to my reading list
And I should see citation metrics and journal impact factors
```

### Stories สำหรับคุณรัตนา (Librarian)

#### Story 5: Dashboard สำหรับบรรณารักษ์
```
As คุณรัตนา, บรรณารักษ์ที่ต้องให้บริการและวิเคราะห์การใช้งาน,
I want a comprehensive dashboard showing real-time library usage statistics
So that I can provide better service and make data-driven decisions

Context:
- When: ตลอดวันทำการ
- Where: เคาน์เตอร์บริการและออฟฟิศ
- With whom: ทีมบรรณารักษ์และผู้บริหาร

Pain Points addressed:
- ไม่สามารถวิเคราะห์พฤติกรรมผู้ใช้ได้
- การทำรายงานสถิติใช้เวลานาน

Success Criteria:
- เห็นข้อมูลการใช้งานแบบ real-time
- สร้างรายงานได้อัตโนมัติ
- วิเคราะห์ trend และ pattern ได้

Acceptance Criteria:
Given I am logged into the librarian dashboard
When I view the main overview
Then I should see current occupancy, popular books, peak usage times
And I should be able to generate reports for any date range
And I should see alerts for overdue items or system issues
And I should have access to user behavior analytics
```

---

## เครื่องมือสำหรับ Implementation

### Trello Board Structure

#### List 1: "Personas & Characters"
```
Cards:
- น้องมิน - First Year Student [สีเขียว]
- พี่เอิร์ธ - Senior Student [สีฟ้า]  
- อาจารย์ศรีไพร - Faculty [สีม่วง]
- คุณรัตนา - Librarian [สีแดง]
- น้องแบงค์ - Graduate Student [สีเหลือง]
- คุณประยุทธ์ - IT Support [สีเทา]
```

#### List 2: "Pain Points Discovery"
```
Cards:
- Navigation Issues [Label: น้องมิน]
- Access Problems [Label: อาจารย์ศรีไพร]
- System Inefficiency [Label: คุณรัตนา]
- Research Limitations [Label: น้องแบงค์]
```

#### List 3: "User Stories - Draft"
```
Cards จะถูกสร้างระหว่าง workshop:
- [Persona Name] - [Short Title]
- ในแต่ละ card จะมี:
  - Full user story
  - Acceptance criteria
  - Story points
  - Priority label
```

#### List 4: "User Stories - Reviewed"
```
Cards ที่ผ่านการ review และปรับแก้แล้ว
```

#### List 5: "Epic Planning"
```
Cards สำหรับจัดกลุ่ม related stories:
- Search & Discovery Epic
- Access Management Epic  
- Notification System Epic
- Analytics & Reporting Epic
```

### Miro Template

#### Board Layout:
```
┌─────────────────────────────────────────────────────────┐
│                    EduLib Connect                      │
│                 Story Mapping Board                    │
├─────────────────────────────────────────────────────────┤
│ Personas Row:                                          │
│ [น้องมิน] [พี่เอิร์ธ] [อาจารย์] [คุณรัตนา] [น้องแบงค์] [คุณประยุทธ์] │
├─────────────────────────────────────────────────────────┤
│ User Journey (Backbone):                               │
│ [Discover] → [Search] → [Access] → [Use] → [Return] → [Review] │
├─────────────────────────────────────────────────────────┤
│ Walking Skeleton (Key Tasks):                          │
│ • Find books    • Reserve items   • Get notifications  │
│ • Access databases • Renew loans  • Get help          │
├─────────────────────────────────────────────────────────┤
│ User Stories (Detailed Requirements):                  │
│ [Story cards จะถูกเพิ่มในระหว่าง workshop]              │
│                                                        │
└─────────────────────────────────────────────────────────┘
```

#### Sticky Note Colors:
- **สีเขียว:** น้องมิน stories
- **สีฟ้า:** พี่เอิร์ธ stories  
- **สีม่วง:** อาจารย์ศรีไพร stories
- **สีแดง:** คุณรัตนา stories
- **สีเหลือง:** น้องแบงค์ stories
- **สีเทา:** คุณประยุทธ์ stories
- **สีส้ม:** Cross-persona/system stories

---

## Workshop 4: แอปพลิเคชันจัดการเงินส่วนตัว
### "MoneyWise" - Personal Finance Management App

---

## บริบทและสถานการณ์

### ปัญหาการจัดการเงินของคนไทย
**สถิติน่าห่วง:**
- คนไทย 70% ไม่มีการออมเงิน
- หนี้ครัวเรือนต่อ GDP 90.3%
- คนรุ่นใหม่ใช้จ่ายผ่าน mobile payment เพิ่มขึ้น 300%
- 60% ไม่รู้ว่าเงินหายไปไหน

**เป้าหมายของแอป MoneyWise:**
- ช่วยให้คนไทยจัดการเงินได้ดีขึ้น
- เสริมสร้างนิสัยการออมเงิน
- สร้างความตระหนักในการใช้จ่าย
- เข้าถึงได้ง่าย เหมาะกับ lifestyle คนไทย

### Market Context
**Target Users:** คนไทยอายุ 18-45 ปี
**Competitors:** Rabbit Finance, Jitta Wealth, Money Lover
**Unique Value:** เน้นความง่าย, gamification, และ community

---

## 7 Personas สำหรับ Role-Playing

### 1. น้องเอิร์น - นักศึกษามหาวิทยาลัย
**ข้อมูลส่วนตัว:**
- อายุ 20 ปี, ศึกษาอยู่ปี 3 คณะบริหารธุรกิจ
- รายได้จากงานพาร์ตไทม์ 8,000 บาท/เดือน
- ได้เงินจากพ่อแม่ 5,000 บาท/เดือน
- อาศัยในหอพัก ค่าใช้จ่าย 12,000 บาท/เดือน

**พฤติกรรมการใช้เงิน:**
- ใช้จ่ายผ่าน QR Code และบัตรเดบิต
- ชอบซื้อของออนไลน์ตาม trend
- มักจะหมดเงินก่อนสิ้นเดือน
- ไม่เคยบันทึกรายรับ-รายจ่าย

**Pain Points:**
- ไม่รู้ว่าเงินหายไปไหน
- ใช้จ่ายตามอารมณ์ (impulse buying)
- กังวลเรื่องเงินไม่พอใช้
- อยากออมแต่ไม่รู้วิธี

**Goals:**
- ควบคุมการใช้จ่ายได้ดีขึ้น
- ออมเงินไปซื้อโทรศัพท์ใหม่
- ไม่ต้องขอเงินพ่อแม่เพิ่ม
- เรียนรู้การวางแผนทางการเงิน

**Digital Behavior:** สูงมาก (Gen Z native)
**Communication:** LINE, Instagram, TikTok

**สถานการณ์สำหรับแสดง:**
```
Scene: "เดือนสั้น แต่เงินหมดก่อน"
เอิร์นกำลังดูในมือถือ พบว่าเงินในบัญชีเหลือ 200 บาท 
แต่ยังเหลือเวลาอีก 10 วัน กำลังคิดว่าจะขอเงินพ่อแม่
หรือกินมาม่าไปเรื่อยๆ
"ทำไมเงินหมดเร็วจัง ยังไม่ได้ซื้ออะไรเลย... หรือซื้อแล้วลืมไป?"
```

### 2. พี่แอม - Fresh Graduate ทำงานใหม่
**ข้อมูลส่วนตัว:**
- อายุ 22 ปี, ทำงานบริษัท IT มา 6 เดือน
- เงินเดือน 25,000 บาท/เดือน
- ย้ายมาอยู่กรุงเทพฯ ใหม่ๆ
- ส่งเงินกลับบ้าน 3,000 บาท/เดือน

**พฤติกรรมการใช้เงิน:**
- มีบัญชีธนาคาร 3 บัญชี
- ใช้ mobile banking และ e-wallet
- เริ่มสนใจการลงทุน
- ยังไม่มีแผนการเงินระยะยาว

**Pain Points:**
- ค่าใช้จ่ายในกรุงเทพฯ สูงกว่าที่คิด
- งานหนัก ไม่มีเวลาดูแลเรื่องเงิน
- อยากลงทุนแต่ไม่มีความรู้
- กังวลเรื่องเงินฉุกเฉิน

**Goals:**
- สร้างกองทุนฉุกเฉิน
- เริ่มลงทุนระยะยาว
- ซื้อประกันชีวิต
- วางแผนซื้อคอนโด

**Digital Behavior:** สูง (millennial early adopter)
**Communication:** LINE, Email, Facebook

**สถานการณ์สำหรับแสดง:**
```
Scene: "เงินเดือนขึ้นแต่เงินออมไม่เพิ่ม"
แอมเพิ่งได้เงินเดือนขึ้น 3,000 บาท แต่พอดูในบัญชีออมทรัพย์
เงินยังคงเท่าเดิม กำลังสงสัยว่าเงินที่เพิ่มขึ้นไปไหน
"เงินเดือนขึ้นแล้วนะ แต่ทำไมเงินในบัญชีไม่เพิ่มเลย 
คงต้องมาจริงจังกับการออมแล้วล่ะ"
```

### 3. ป้าสมจิต - แม่บ้านวัยกลางคน
**ข้อมูลส่วนตัว:**
- อายุ 42 ปี, แม่บ้าน มีลูก 2 คน
- สามีทำงานบริษัท รายได้ครัวเรือน 45,000 บาท/เดือน
- ดูแลค่าใช้จ่ายทั้งบ้าน
- เริ่มใช้ digital payment เมื่อ 2 ปีที่แล้ว

**พฤติกรรมการใช้เงิน:**
- จ่ายด้วยเงินสด 70%, QR Code 30%
- ซื้อของใช้ในบ้านและอาหาร
- มีการออมเงินประจำเดือน
- ระมัดระวังเรื่องการใช้จ่าย

**Pain Points:**
- ค่าใช้จ่ายครอบครัวเพิ่มขึ้นเรื่อยๆ
- ลูกโตขึ้น ค่าเรียนแพงขึ้น
- ไม่มีเวลาดูแลเรื่องการลงทุน
- กังวลเรื่องเงินกบเลี้ยงชีพ

**Goals:**
- ลดค่าใช้จ่ายที่ไม่จำเป็น
- ออมเงินเพื่อการศึกษาลูก
- เตรียมเงินยามเกษียณ
- สอนลูกเรื่องการใช้เงิน

**Digital Behavior:** ปานกลาง (ใช้แอปพื้นฐาน)
**Communication:** LINE, โทรศัพท์

**สถานการณ์สำหรับแสดง:**
```
Scene: "ค่าใช้จ่ายครอบครัวพุ่งแรง"
ป้าสมจิตกำลังดูใบเสร็จและบิลต่างๆ ในมือ พบว่าเดือนนี้
ใช้จ่ายเกินงบมาก กำลังนับเงินและคิดหาวิธีประหยัด
"เดือนนี้ใช้จ่ายเกิน 5,000 บาทเลย ต้องหาดูว่าจ่ายอะไรมากผิดปกติ
ลูกโตขึ้นค่าใช้จ่ายก็เพิ่มตาม"
```

### 4. น้องไอซ์ - Gen Z ทำงาน Freelance
**ข้อมูลส่วนตัว:**
- อายุ 24 ปี, ทำงาน Content Creator และ Graphic Designer
- รายได้ไม่แน่นอน 15,000-40,000 บาท/เดือน
- ทำงานจากบ้าน lifestyle แบบ digital nomad
- ใช้เทคโนโลยีเป็นหลักในชีวิต

**พฤติกรรมการใช้เงิน:**
- ใช้ e-wallet และ crypto wallet
- รายได้มาเป็นงวดๆ ไม่แน่นอน
- ใช้จ่ายในการลงทุนตัวเอง (course, equipment)
- ไม่มีรายจ่ายประจำมาก

**Pain Points:**
- รายได้ไม่แน่นอน วางแผนยาก
- ไม่มีสวัสดิการแบบพนักงาน
- ต้องจัดการภาษีเอง
- ค่าใช้จ่ายเครื่องมือทำงานสูง

**Goals:**
- สร้างรายได้ passive income
- ลงทุนในความรู้และทักษะ
- เตรียมเงินสำหรับ business ตัวเอง
- มีเงินฉุกเฉินเพื่อช่วงที่ไม่มีงาน

**Digital Behavior:** Expert level (early adopter)
**Communication:** Discord, Twitter, Instagram, LinkedIn

**สถานการณ์สำหรับแสดง:**
```
Scene: "เดือนนี้งานเยอะ เดือนหน้าไม่มีงาน"
ไอซ์เพิ่งได้รับเงินค่า project ก้อนใหญ่ 35,000 บาท 
แต่รู้ว่าเดือนหน้าไม่มีงานเข้า กำลังคิดว่าจะจัดสรรยังไง
"เดือนนี้เงินเยอะ แต่ต้องแบ่งไว้ใช้เดือนหน้าด้วย 
แล้วก็ต้องเก็บเงินไว้ซื้ออุปกรณ์ใหม่อีก"
```

### 5. พี่โอ๊ค - ผู้บริหารระดับกลาง
**ข้อมูลส่วนตัว:**
- อายุ 35 ปี, ผู้จัดการฝ่ายการตลาด
- เงินเดือน 80,000 บาท/เดือน + โบนัส
- แต่งงานแล้ว มีลูก 1 คน
- มีบ้านผ่อนและรถยนต์ 2 คัน

**พฤติกรรมการใช้เงิน:**
- มีการลงทุนหลากหลาย (หุ้น, กองทุน, อสังหาฯ)
- ใช้บัตรเครดิตหลายใบ
- มีประกันชีวิตและสุขภาพครอบครัว
- เน้นการวางแผนการเงินระยะยาว

**Pain Points:**
- ข้อมูลการเงินกระจัดกระจาย
- ไม่มีเวลาติดตาม portfolio
- ต้องการ optimize tax planning
- กังวลเรื่องการศึกษาลูกและเกษียณ

**Goals:**
- รวบรวมข้อมูลการเงินให้เป็นระบบ
- เพิ่มประสิทธิภาพการลงทุน
- วางแผนการเงินครอบครัวระยะยาว
- สร้าง passive income เพิ่ม

**Digital Behavior:** สูง (professional user)
**Communication:** Email, LINE, Microsoft Teams

**สถานการณ์สำหรับแสดง:**
```
Scene: "เงินเยอะแต่วุ่นวาย"
โอ๊คกำลังดูหน้าจอคอมพิวเตอร์ที่เปิด tab ธนาคาร 5 แท็บ
แอป investment 3 แอป และ spreadsheet การเงินส่วนตัว
"มีเงินอยู่หลายที่ แต่ไม่รู้ว่าภาพรวมเป็นยังไง 
จะดี dashboard เดียวจบ ดูได้ทุกอย่าง"
```

### 6. ลุงสมชาย - พ่อค้าแม่ค้าวัยใหญ่
**ข้อมูลส่วนตัว:**
- อายุ 55 ปี, ขายผลไม้ในตลาดสด
- รายได้ 20,000-30,000 บาท/เดือน (ขึ้นอยู่กับฤดูกาล)
- มีลูก 2 คน ทำงานแล้ว
- เพิ่งเริ่มใช้ QR Code payment

**พฤติกรรมการใช้เงิน:**
- ใช้เงินสดเป็นหลัก
- เก็บเงินในกระปุกและบัญชีออมทรัพย์
- ไม่ค่อยใช้บัตรเครดิต
- รายได้ขึ้นลงตามฤดูกาล

**Pain Points:**
- ไม่รู้วิธีบันทึกรายรับ-รายจ่าย
- เทคโนโลยีใหม่ๆ ใช้ไม่เป็น
- กังวลเรื่องเงินเกษียณ
- ต้องการวิธีออมที่ง่ายๆ

**Goals:**
- เรียนรู้การใช้เงินให้เป็นประโยชน์
- ออมเงินเกษียณ
- ไม่เป็นภาระลูกหลาน
- เข้าใจเทคโนโลยีพื้นฐาน

**Digital Behavior:** ต่ำ (พึ่งเริ่มเรียนรู้)
**Communication:** โทรศัพท์, LINE (ใช้ง่ายๆ)

**สถานการณ์สำหรับแสดง:**
```
Scene: "เงินมีแต่ไม่รู้ว่าเพียงพอมั้ย"
ลุงสมชายกำลังนับเงินสดที่เก็บไว้ในกระปุก และดูสมุดบัญชี
กำลังคิดว่าเงินที่มีจะพอใช้ยามเกษียณหรือไม่
"เก็บเงินมาตลอด แต่ไม่รู้ว่าพอใช้เกษียณมั้ย 
ลูกบอกให้ลงทุน แต่กลัวเงินหาย"
```

### 7. น้องเบส - นักเรียนมัธยมปลาย
**ข้อมูลส่วนตัว:**
- อายุ 17 ปี, ม.6 เตรียมสอบเข้ามหาวิทยาลัย
- ได้เงินจากพ่อแม่ 2,000 บาท/เดือน
- ทำงานพิเศษช่วงปิดเทอม
- เริ่มสนใจเรื่องการเงิน

**พฤติกรรมการใช้เงิน:**
- ใช้ e-wallet และ mobile banking
- ซื้อของออนไลน์บ่อย
- เริ่มหัดออมเงิน
- ไม่เคยมีบัตรเครดิต

**Pain Points:**
- เงินพ่อแม่ให้ไม่พอใช้
- อยากซื้อของแพงๆ แต่เงินไม่พอ
- ไม่รู้วิธีหาเงินเพิ่ม
- ไม่เข้าใจเรื่องการลงทุน

**Goals:**
- ออมเงินซื้อ gadget ที่อยาก
- เรียนรู้การหาเงินเพิ่ม
- เตรียมเงินค่าเรียนมหาวิทยาลัย
- เริ่มสร้างนิสัยการเงินที่ดี

**Digital Behavior:** สูงมาก (Gen Z)
**Communication:** TikTok, Instagram, LINE, Discord

**สถานการณ์สำหรับแสดง:**
```
Scene: "อยากได้ iPhone แต่เงินไม่พอ"
เบสกำลังดู iPhone รุ่นใหม่ที่ราคา 35,000 บาท 
แล้วดูเงินในบัญชีที่มีแค่ 3,500 บาท
"อยากได้มากกกก แต่ราคา 35,000 ต้องเก็บกี่ปีนี่ 
ถ้ามีแอปช่วยวางแผนออมคงจะดี"
```

---

## Role-Playing Workshop Structure

### Phase 1: Character Immersion (25 นาที)

#### ขั้นตอนที่ 1: Deep Character Study (15 นาที)
```
แต่ละกลุ่มได้รับ persona packet ที่มี:
1. Character profile ที่ละเอียด
2. Daily routine และ financial habits
3. Sample dialogue และ mannerisms
4. Key motivations และ fears
5. Technology comfort level
```

**Character Development Exercise:**
- **5 นาที:** อ่านและทำความเข้าใจตัวละคร
- **5 นาที:** สร้าง backstory เพิ่มเติม
- **5 นาที:** ฝึกการพูดและท่าทางของตัวละคร

#### ขั้นตอนที่ 2: Scenario Preparation (10 นาที)
แต่ละกลุ่มเตรียม 2 สถานการณ์:

**Scenario A: วิกฤตการเงิน (Financial Crisis)**
**Scenario B: การตัดสินใจการเงิน (Financial Decision)**

### Phase 2: Interactive Role-Playing (40 นาที)

#### รูปแบบ "Living Museum"
- กลุ่มต่างๆ ตั้ง "station" ใน classroom
- ผู้ชม