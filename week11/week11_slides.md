# ENGSE206: Software Requirements Specification and Design
## สัปดาห์ที่ 11: User Experience & Interface Design
### มหาวิทยาลัยเทคโนโลยีราชมงคลล้านนา (ดอยสะเก็ด)

---

# Session 1.1: Introduction to UX/UI (45 นาที)

---

## Slide 1: Today's Agenda & Learning Objectives

### 📅 วันนี้เรียนอะไร?
```
Session 1: Introduction to UX/UI (45 min)
- UX vs UI คืออะไร
- ทำไม UX/UI สำคัญ
- User-Centered Design Process
- Design Principles

Session 2: User Research & Personas (45 min)
- วิธีทำ User Research
- การสร้าง Personas
- Agent Wallboard Case Study

Session 3: User Journey & UI Basics (30 min)
- User Journey Mapping
- Design Systems
- Figma Quick Demo
```

### 🎯 Learning Objectives
หลังเรียนวันนี้ นักศึกษาจะสามารถ:
- ✅ อธิบายความแตกต่างระหว่าง UX และ UI
- ✅ ทำ user research และสร้าง personas
- ✅ สร้าง user journey map
- ✅ ใช้ Figma พื้นฐานได้

---

## Slide 2: Course Progress - เรามาถึงไหนแล้ว

### 📊 Week 1-11 Overview
```
✅ Week 1-4:  Requirements Engineering (SRS, Use Cases)
✅ Week 5-7:  Design Principles & Patterns
✅ Week 8:    Midterm Exam
✅ Week 9:    Advanced Architecture (Microservices)
✅ Week 10:   Database Design (ER Diagram, Schema)
➡️ Week 11:   UX/UI Design ← เรียนวันนี้
📍 Week 12:   Mobile & Responsive Design
📍 Week 13:   Security & Performance
📍 Week 14:   DevOps & Deployment
📍 Week 15:   Final Project Presentation
```

### 🎯 Today's Focus
**จาก Technical Design → User-Facing Design**
- จนถึง Week 10: Backend, Database, Architecture
- Week 11-12: Frontend, User Interface, User Experience
- ต่อจากนี้: Integration ทุกอย่างเข้าด้วยกัน

---

## Slide 3: The $500 Million Question

### 🚨 Case Study: Why UX/UI Matters

**NASA Mars Climate Orbiter (1999)**
- ค่าใช้จ่าย: $327.6 million
- ผลลัพธ์: สูญหายในบรรยากาศของดาวอังคาร
- สาเหตุ: **Interface error** - ทีมหนึ่งใช้ metric, อีกทีมใช้ imperial units
- Software interface ไม่ชัดเจน ว่าใช้หน่วยอะไร

**Therac-25 Radiation Therapy (1985-1987)**
- ผลลัพธ์: ผู้ป่วย 6 คนเสียชีวิต
- สาเหตุ: **Poor UI design** - interface ซับซ้อน ง่ายต่อการกดผิด
- ไม่มี clear feedback เมื่อตั้งค่าผิด

### 💡 Key Lesson
> "Good UX/UI is not just about beauty.  
> It's about safety, usability, and success."

---

## Slide 4: UX vs UI - ความแตกต่างที่ต้องเข้าใจ

### 🎨 คำจำกัดความ

**UX (User Experience)**
> ความรู้สึกและประสบการณ์โดยรวมของผู้ใช้เมื่อโต้ตอบกับผลิตภัณฑ์

**UI (User Interface)**
> ส่วนต่อประสานที่ผู้ใช้เห็นและโต้ตอบด้วย

---

### 📊 เปรียบเทียบ UX vs UI

| Aspect | UX | UI |
|--------|----|----|
| **Focus** | HOW it works | HOW it looks |
| **Goal** | Solve problems | Visual appeal |
| **Skills** | Research, Analysis | Visual design |
| **Tools** | Interviews, Analytics | Figma, Sketch |
| **Output** | Journey maps, Wireframes | Mockups, Prototypes |
| **Measure** | Task completion, Satisfaction | Visual consistency |

---

### 🏠 House Analogy

```
Building a House:

UX = Architecture (โครงสร้าง)
- Floor plan ดีไหม?
- ห้องครัวอยู่ใกล้ห้องกินข้าวไหม?
- บันไดปลอดภัยไหม?
- น้ำไหลดีไหม?

UI = Interior Design (ตแกตกแต่ง)
- สีสวยไหม?
- เฟอร์นิเจอร์เข้ากันไหม?
- แสงสว่างเหมาะสมไหม?
- สไตล์สวยไหม?

Need Both!
บ้านที่ดี = Architecture ดี + Interior ดี
Product ที่ดี = UX ดี + UI ดี
```

---

## Slide 5: Real-World Example - Instagram

### 📱 Instagram: UX + UI Working Together

**UX Decisions:**
```
✓ Feed แบบ infinite scroll (ไม่ต้องคลิกหน้าถัดไป)
✓ Double-tap to like (gesture ง่าย)
✓ Stories หายใน 24 ชม. (FOMO effect)
✓ Post ง่าย: เลือกรูป → Filter → Share (3 steps)
```

**UI Decisions:**
```
✓ Color scheme: White + Blue + Orange (clean & energetic)
✓ Bottom navigation (thumb-friendly)
✓ Heart icon สีแดง (emotional connection)
✓ Consistent spacing & grid
```

**Result:**
- 2+ billion active users
- Average time spent: 30+ min/day
- Good UX + Good UI = Success!

---

## Slide 6: UX ≠ UI - But Why Confusion?

### 🤔 ทำไมคนมักสับสน?

**1. Overlap ในการทำงาน**
```
UX Designer → สร้าง wireframe (มี UI elements)
UI Designer → คิด interaction (มี UX thinking)
```

**2. Modern Role: Product Designer**
```
Product Designer = UX + UI + Strategy
ต้องรู้ทั้ง research และ visual design
```

**3. เครื่องมือเดียวกัน**
```
Figma, Adobe XD → ใช้ได้ทั้ง UX และ UI
```

### ✅ ข้อสรุป
- UX และ UI ต่างกัน แต่ **ทำงานร่วมกัน**
- UX เน้น **ฟังก์ชัน** (function)
- UI เน้น **รูปแบบ** (form)
- **ต้องดีทั้งคู่** product ถึงจะดี

---

## Slide 7: User-Centered Design (UCD) Process

### 🔄 UCD คืออะไร?
> กระบวนการออกแบบที่ใส่ใจผู้ใช้งานตั้งแต่เริ่มต้น

### 4 Phases of UCD

```
        ┌─────────────────────┐
        │   1. UNDERSTAND     │
        │   - Research users  │
        │   - Identify needs  │
        └──────────┬──────────┘
                   ↓
        ┌─────────────────────┐
        │   2. EXPLORE        │
        │   - Brainstorm      │
        │   - Sketch ideas    │
        └──────────┬──────────┘
                   ↓
        ┌─────────────────────┐
        │   3. PROTOTYPE      │
        │   - Build mockups   │
        │   - Get feedback    │
        └──────────┬──────────┘
                   ↓
        ┌─────────────────────┐
        │   4. EVALUATE       │
        │   - Test with users │
        │   - Iterate         │
        └──────────┬──────────┘
                   │
                   └──→ Back to UNDERSTAND (ถ้ายังไม่ดี)
```

---

### 🎯 Key Principles

**1. Early focus on users**
- เริ่มจาก user research ก่อนออกแบบ
- อย่าสมมติว่ารู้ว่า user ต้องการอะไร

**2. Empirical measurement**
- วัดผลจากการใช้งานจริง
- ใช้ data, ไม่ใช่ opinion

**3. Iterative design**
- ออกแบบ → ทดสอบ → ปรับปรุง → ซ้ำ
- ไม่มี perfect แต่แรก

---

## Slide 8: 10 Essential UI Design Principles

### 🎨 Principles ที่ต้องรู้

**1. Clarity (ความชัดเจน)**
```
✓ User ต้องเข้าใจได้ทันทีว่าต้องทำอะไร
✗ อย่าใช้คำที่คลุมเครือ
```

**2. Consistency (ความสม่ำเสมอ)**
```
✓ Elements เหมือนกัน → พฤติกรรมเหมือนกัน
✓ Colors, fonts, spacing → consistent
```

**3. Feedback (การตอบสนอง)**
```
✓ แจ้งให้ user รู้ว่าระบบกำลังทำอะไร
✓ Loading, success, error states
```

**4. Hierarchy (ลำดับความสำคัญ)**
```
✓ สิ่งสำคัญต้องเด่นกว่า
✓ ใช้ size, color, position
```

**5. Simplicity (ความเรียบง่าย)**
```
✓ Less is more
✓ 1 หน้า = 1 เป้าหมายหลัก
```

---

**6. Affordance (การบ่งบอกการใช้งาน)**
```
✓ ปุ่มต้องดูเหมือนปุ่ม (กดได้)
✓ Link ควรมีสีต่างและ underline
```

**7. Accessibility (การเข้าถึง)**
```
✓ ออกแบบให้ทุกคนใช้ได้
✓ Color contrast ≥ 4.5:1
✓ Font size ≥ 16px
```

**8. Error Prevention (ป้องกันข้อผิดพลาด)**
```
✓ Disable ปุ่มที่ใช้ไม่ได้
✓ Confirmation สำหรับ critical actions
✓ Clear error messages
```

**9. Responsiveness (การตอบสนอง)**
```
✓ < 0.1s = instant
✓ < 1s = good
✓ > 10s = user gives up
```

**10. Familiar Patterns (รูปแบบคุ้นเคย)**
```
✓ ใช้ patterns ที่ users รู้จัก
✓ Search box มี 🔍 icon
✓ Settings ใช้ ⚙️ icon
```

---

## Slide 9: Agent Wallboard System - Our Case Study

### 📊 ระบบที่เราจะออกแบบวันนี้

**Agent Wallboard System**
- Call Center management system
- Real-time agent monitoring
- Multi-user application

### 👥 4 User Types

**🎧 Agent** (Call Center Staff)
```
Goals:
- เปลี่ยนสถานะได้รวดเร็ว
- อ่านข้อความจาก supervisor
- ดูสถิติของตัวเอง

Pain Points:
- ระบบเดิมช้า
- UI ซับซ้อน
- ไม่มี real-time updates
```

**👨‍💼 Supervisor** (Team Leader)
```
Goals:
- Monitor team real-time
- ส่งข้อความถึง agents
- ดู team performance

Pain Points:
- ดู agent หลายคนพร้อมกันยาก
- ต้อง switch หลายหน้าจอ
- ข้อมูล update ช้า
```

**🏢 Operations Manager**
```
Goals:
- ดู performance overall
- สร้าง reports
- Optimize resources

Pain Points:
- ข้อมูลกระจัดกระจาย
- ต้องทำ report manual
- ไม่มี historical data
```

**🔧 System Admin**
```
Goals:
- จัดการ users และ permissions
- Monitor system health
- Troubleshoot issues

Pain Points:
- ไม่มี centralized admin panel
- Deployment ซับซ้อน
- ไม่มี logs ที่ดี
```

---

## Slide 10: Why UX/UI Matters - Statistics

### 📊 ข้อมูลที่น่าสนใจ

**ROI of Good UX:**
```
💰 Every $1 invested in UX = $100 return (ROI 10,000%)
📈 Good UX increases conversion by 400%
⏱️ 88% of users won't return after bad UX
🎯 First impression = 94% design-related
```

**Cost of Bad UX:**
```
❌ 70% of projects fail due to poor UX
💸 Fixing errors after release = 100x more expensive
⏰ Users leave if page loads > 3 seconds
😤 62% of users uninstall app due to poor UX
```

**Industry Data:**
```
📱 Companies with UX teams grow 2x faster
🏆 75% of users judge credibility by design
⭐ 52% of users won't recommend due to poor mobile UX
```

### 💡 Key Takeaway
> "Good UX/UI is not a cost. It's an investment."

---

## Slide 11: Activity Preview - What We'll Do Today

### 🎯 3-Hour Workshop

**Activity 1: User Interview & Persona (90 min)**
```
1. Role-play interview (30 min)
   - แบ่งกลุ่ม 4-5 คน
   - สัมภาษณ์แบบ user

2. Analyze data (15 min)
   - หา pain points
   - หา goals

3. Create Persona in Figma (30 min)
   - ใช้ template
   - ใส่ข้อมูลจาก interview

4. Present (15 min)
   - แต่ละกลุ่มนำเสนอ 2 นาที
```

**Activity 2: User Journey Mapping (90 min)**
```
1. Define scenario (10 min)
   - เลือก scenario ที่สำคัญ

2. Map journey (50 min)
   - 4-6 phases
   - Actions, Thoughts, Emotions
   - Pain points, Opportunities

3. Emotion graph (10 min)
   - วาด happiness curve

4. Identify insights (15 min)
   - Top 3 pain points
   - Top 3 opportunities

5. Present (5 min)
```

---

# Session 1.2: User Research & Personas (45 นาที)

---

## Slide 12: User Research - Foundation of Good UX

### 🔍 User Research คืออะไร?
> กระบวนการเก็บข้อมูลเพื่อเข้าใจพฤติกรรม ความต้องการ และ pain points ของผู้ใช้

### ❓ ทำไมต้องทำ?
```
✓ เข้าใจ real needs (ไม่ใช่ assumptions)
✓ หา pain points ที่แก้ได้
✓ Validate ideas ก่อนทำ
✓ ลดความเสี่ยง (ไม่ต้อง rebuild)
✓ Save time & money
```

### ⚠️ Common Mistakes
```
❌ "เรารู้ว่า users ต้องการอะไร" → Assumptions
❌ "เราเป็น users เอง" → Biased
❌ "ไม่มีเวลาทำ research" → Waste more time later
❌ "ถาม stakeholders ก็พอ" → Not real users
```

---

## Slide 13: User Research Methods

### 📊 2 ประเภทหลัก

**1. Qualitative Research (เชิงคุณภาพ)**
```
🎯 Goal: เข้าใจ WHY และ HOW

Methods:
- User Interviews (1-on-1)
- Focus Groups (6-10 คน)
- Contextual Inquiry (สังเกตที่ทำงาน)
- Diary Studies (บันทึกประจำวัน)

Output:
- Pain points
- User stories
- Quotes
- Insights
```

**2. Quantitative Research (เชิงปริมาณ)**
```
🎯 Goal: วัดผล WHAT และ HOW MANY

Methods:
- Surveys (แบบสอบถาม)
- Analytics (Google Analytics)
- A/B Testing
- Heatmaps (Hotjar)

Output:
- Statistics
- Metrics
- Trends
- Numbers
```

---

### 🎯 เมื่อไหร่ใช้อะไร?

| Phase | Method | Why |
|-------|--------|-----|
| **Discovery** | Interviews | เข้าใจปัญหา |
| **Ideation** | Surveys | Validate ideas |
| **Design** | Usability Testing | Test prototypes |
| **Launch** | Analytics | Measure success |
| **Iterate** | A/B Testing | Optimize |

---

## Slide 14: User Interviews - How to Do It Right

### 📝 Interview Structure (30 min)

```
1. INTRO (5 min)
━━━━━━━━━━━━━━━━━━━━━━━
- แนะนำตัว
- อธิบายวัตถุประสงค์
- ขอบันทึกเสียง (consent)
- ทำให้ผู้ถูกสัมภาษณ์สบายใจ

2. WARM-UP (3 min)
━━━━━━━━━━━━━━━━━━━━━━━
- คำถามง่ายๆ
- เกี่ยวกับตัวเอง
- เรื่องทั่วไป

3. MAIN QUESTIONS (20 min)
━━━━━━━━━━━━━━━━━━━━━━━
- Current process
- Pain points
- Goals & needs
- ถาม "Why" 5 ครั้ง (5 Whys)

4. WRAP-UP (2 min)
━━━━━━━━━━━━━━━━━━━━━━━
- สรุป
- ถามเพิ่มเติม
- ขอบคุณ
```

---

### ✅ Do's

```
✓ ถามคำถามปลายเปิด (Open-ended)
   - "อธิบายวันทำงานของคุณ?"
   - "ปัญหาที่เจอบ่อยที่สุดคืออะไร?"

✓ ฟังมากกว่าพูด (80% listening)

✓ ถาม "Why" ซ้ำๆ เจาะลึก

✓ สังเกต body language

✓ บันทึกทุกอย่าง (notes + recording)

✓ Silent probe (เงียบ 3-5 วินาที รอให้พูดต่อ)
```

### ❌ Don'ts

```
✗ ถามคำถามปลายปิด
   - "คุณชอบระบบนี้ไหม?" (ใช่/ไม่ใช่)

✗ ใส่ความเชื่อของตัวเอง (Leading questions)
   - "ระบบนี้ดีใช่ไหม?" ❌

✗ แนะนำ solution ตอนสัมภาษณ์

✗ ขัดจังหวะ

✗ ตัดสิน (judgmental)
```

---

## Slide 15: Sample Interview Questions

### 🎧 For Agent (Call Center Staff)

**Background:**
```
1. บอกเกี่ยวกับงานของคุณหน่อย?
2. วันทำงานปกติเป็นยังไง?
3. ใช้เครื่องมืออะไรในการทำงานบ้าง?
```

**Current Problems:**
```
4. ปัญหาที่เจอบ่อยที่สุดคืออะไร?
5. อะไรทำให้คุณรู้สึกหงุดหงิด?
6. ใช้เวลานานที่สุดในการทำอะไร?
```

**Goals & Needs:**
```
7. อะไรคือความสำเร็จในการทำงานของคุณ?
8. ถ้าจะเปลี่ยนอะไรได้ 1 อย่าง จะเป็นอะไร?
9. Feature ที่อยากให้มีมากที่สุดคืออะไร?
```

---

### 👨‍💼 For Supervisor

**Monitoring:**
```
1. คุณติดตามทีมยังไง?
2. ต้องดูข้อมูลอะไรบ้างแบบ real-time?
3. เมื่อไหร่ที่ต้อง intervene?
```

**Communication:**
```
4. ติดต่อกับ agents ยังไง?
5. ส่งข้อความบ่อยแค่ไหน?
6. มีปัญหาในการสื่อสารไหม?
```

**Reporting:**
```
7. ต้องทำ report อะไรบ้าง?
8. ใช้เวลานานแค่ไหน?
9. ข้อมูลอะไรที่ขาดไป?
```

---

## Slide 16: Personas - Bringing Users to Life

### 🎭 Persona คืออะไร?
> ตัวแทนสมมติของกลุ่มผู้ใช้ ที่สร้างจากข้อมูล research จริง

### 🎯 ทำไมต้องทำ Persona?

**Benefits:**
```
✓ ทีมเข้าใจ users เหมือนกัน
✓ เกิด empathy กับ users
✓ ตัดสินใจง่ายขึ้น ("Nok จะชอบไหม?")
✓ Focus priorities
✓ Communicate กับ stakeholders ได้ดีขึ้น
```

**Without Persona:**
```
❌ ทุกคนจินตนาการ user คนละแบบ
❌ Design ไม่มี focus
❌ Arguments ใช้ opinion แทน data
❌ Build features ที่ไม่มีใครใช้
```

---

## Slide 17: Anatomy of a Good Persona

### 📋 องค์ประกอบหลัก

```
┌────────────────────────────────────┐
│  PERSONA CARD                      │
├────────────────────────────────────┤
│                                    │
│  [Photo]  "Representative Quote"   │
│                                    │
│  Name: [Real-sounding name]        │
│  Age: [Age range]                  │
│  Role: [Job title]                 │
│  Experience: [Years in role]       │
│                                    │
├────────────────────────────────────┤
│  🎯 GOALS (3-5 items)              │
│  - What they want to achieve       │
│                                    │
│  😫 PAIN POINTS (3-5 items)        │
│  - What frustrates them            │
│                                    │
│  💻 TECH BEHAVIOR                  │
│  - Tech savviness: ■■■□□ (3/5)     │
│  - Devices & tools used            │
│                                    │
│  📊 DEMOGRAPHICS (optional)        │
│  - Education, Location, etc.       │
│                                    │
└────────────────────────────────────┘
```

---

### ✅ Good Persona Checklist

```
✓ Based on REAL research data
✓ Specific และ realistic
✓ Include goals AND pain points
✓ Has a memorable name
✓ Quote ที่เป็นตัวแทน
✓ Visual (มีรูปภาพ)
✓ 1-2 หน้า (อ่านได้ใน 5 นาที)
```

### ❌ Bad Persona Warning Signs

```
✗ Made up (ไม่มี research)
✗ Generic มากเกินไป
✗ เยอะเกินไป (>5 personas)
✗ น้อยเกินไป (<2 personas)
✗ Focus แค่ demographics
✗ ไม่มี goals/pain points
```

---

## Slide 18: Agent Wallboard - Sample Persona

### 🎧 Persona: "Nok" (Agent)

```
👤 Nok Suriyawong, 25 ปี
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

💼 Role: Customer Service Agent
📅 Experience: 2 ปี
🎓 Education: ปวส. การตลาด
📍 Location: กรุงเทพฯ
💻 Tech Savvy: ■■■□□ (3/5)

💬 Quote:
"ถ้าเปลี่ยนสถานะได้เร็วขึ้น 
 ฉันจะรับสายได้มากขึ้น"

🎯 GOALS:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
1. เปลี่ยนสถานะได้รวดเร็ว (1-2 คลิก)
2. อ่านข้อความจาก supervisor ทันที
3. ดูสถิติของตัวเองได้ง่าย
4. ไม่พลาดการเปลี่ยนแปลง
5. ทำงานได้อย่างมีประสิทธิภาพ

😫 PAIN POINTS:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
1. ระบบเดิมช้า ต้องรอโหลด 10-15 วินาที
2. เปลี่ยนสถานะแล้วไม่ update ทันที
3. หาปุ่มเปลี่ยนสถานะไม่เจอ
4. Notification มาไม่ชัดเจน พลาดบ่อย
5. ต้อง refresh เองถึงจะเห็นข้อมูลใหม่

💻 TECH BEHAVIOR:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
- ใช้คอมพิวเตอร์ทั้งวัน (8-10 ชม.)
- Windows 10, Chrome browser
- ไม่ค่อยชอบระบบซับซ้อน
- ต้องการ keyboard shortcuts
- มือถือ: Android, LINE, Facebook

📊 A DAY IN THE LIFE:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
08:45 - มาถึงออฟฟิศ เปิดเครื่อง
09:00 - เปลี่ยนสถานะเป็น Available
09:05 - เริ่มรับสายแรก
12:00 - Break เที่ยง (30 นาที)
12:30 - กลับมารับสายต่อ
15:00 - Break สั้น (15 นาที)
17:45 - ปิดสถานะ สรุปงาน
18:00 - กลับบ้าน

🎨 DESIGN IMPLICATIONS:
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
→ Status button ต้องใหญ่ เด่น เห็นง่าย
→ Real-time updates (WebSocket)
→ Clear notifications with sound
→ Keyboard shortcuts (F2=Available)
→ Minimal UI, focus on essential info
```

---

## Slide 19: Creating Personas - Step by Step

### 📝 Process

**Step 1: Analyze Research Data (30 min)**
```
- Review interview notes
- Highlight key insights
- Look for patterns
- Group similar behaviors
```

**Step 2: Identify User Segments (15 min)**
```
- กลุ่ม users ที่มี goals/behaviors คล้ายกัน
- Agent Wallboard → 4 segments:
  * Agents (front-line)
  * Supervisors (team leaders)
  * Managers (executives)
  * Admins (IT staff)
```

**Step 3: Create Persona for Each Segment (45 min)**
```
- เลือก segment หนึ่ง
- รวม insights จาก research
- สร้างเรื่องราวของ persona
- ใส่รายละเอียดให้สมจริง
```

**Step 4: Validate & Refine (30 min)**
```
- แสดงให้ stakeholders ดู
- ถามว่า realistic ไหม
- ปรับแก้ตาม feedback
```

---

### 💡 Pro Tips

```
✓ ใช้ชื่อจริง (ไม่ใช่ "User A", "User B")
✓ ใส่รูปที่เป็นธรรมชาติ (ไม่ใช่ stock photos แบบ generic)
✓ Quote ต้องมาจากคำพูดจริง
✓ Focus on behaviors มากกว่า demographics
✓ 1 persona per page (อ่านง่าย)
✓ Print และติดฝาผนัง (remind ทีมตลอด)
```

---

# Session 1.3: User Journey & UI Design Basics (30 นาที)

---

## Slide 20: User Journey Mapping - See Through User's Eyes

### 🗺️ User Journey Map คืออะไร?
> แผนภาพที่แสดงประสบการณ์ของผู้ใช้ตั้งแต่เริ่มต้นจนจบในการทำภารกิจหนึ่งๆ

### 🎯 ทำไมต้องทำ?

**Benefits:**
```
✓ เห็นภาพรวม end-to-end experience
✓ หา pain points ในแต่ละขั้นตอน
✓ Identify opportunities ที่จะปรับปรุง
✓ เข้าใจ emotions ของ user
✓ Prioritize improvements
✓ Align ทีมให้เห็นภาพเดียวกัน
```

---

## Slide 21: Journey Map Components

### 📊 องค์ประกอบหลัก

```
1. PERSONA
   - ใคร? (Nok, Agent)

2. SCENARIO
   - ทำอะไร? (เปลี่ยนสถานะเป็น Available)
   - เมื่อไหร่? (เช้าวันจันทร์)
   - ทำไม? (เพื่อเริ่มรับสาย)

3. PHASES
   - ขั้นตอนใหญ่ๆ (4-6 phases)
   - เช่น: Arrival → Login → Dashboard → Status Change

4. ACTIONS
   - ทำอะไรในแต่ละ phase?
   - เปิดคอมพิวเตอร์, พิมพ์ password, คลิกปุ่ม

5. THOUGHTS
   - คิดอะไร? (💭)
   - "หวังว่าจะโหลดเร็วๆ"

6. EMOTIONS
   - รู้สึกอย่างไร? (😊😐😟😰)
   - Happy, Neutral, Anxious, Stressed

7. PAIN POINTS
   - ปัญหาที่เจอ (❗)
   - ระบบช้า, หาปุ่มไม่เจอ

8. OPPORTUNITIES
   - แก้ยังไง? (💡)
   - Auto-login, Keyboard shortcuts
```

---

## Slide 22: Sample Journey Map - Agent

### 🎧 Scenario: เช้าวันจันทร์ - เปลี่ยนสถานะเป็น Available

```
PHASE 1: Arrival (8:45-8:47 AM)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Actions:
- เปิดคอมพิวเตอร์
- รอ Windows boot up
- เปิด Agent Desktop app

💭 "หวังว่าระบบจะเร็ววันนี้"
😊 Emotion: 😐 Neutral

❗ Pain: App โหลดช้า (30 วินาที)
💡 Opportunity: Show loading progress


PHASE 2: Login (8:47-8:48 AM)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Actions:
- พิมพ์ username & password
- คลิก Login button
- รอ authentication

💭 "Password ยากจำจัง"
😊 Emotion: 😟 Anxious

❗ Pain: Password ซับซ้อนเกินไป
💡 Opportunity: Biometric login


PHASE 3: Find Status Button (8:48-8:49 AM)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Actions:
- มองหาปุ่มเปลี่ยนสถานะ
- สแกนหน้าจอ
- พบปุ่ม

💭 "ปุ่มอยู่ไหนนะ?"
😊 Emotion: 😟 Confused

❗ Pain: Status button ไม่เด่น
💡 Opportunity: Make it prominent


PHASE 4: Change Status (8:49-8:49:30 AM)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Actions:
- คลิก dropdown
- เลือก "Available"
- รอ update

💭 "Update แล้วหรือยัง?"
😊 Emotion: 😰 Stressed

❗ Pain: ไม่มี feedback, ช้า
💡 Opportunity: Instant feedback


PHASE 5: Ready (8:49:30 AM)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Actions:
- เห็นสถานะเปลี่ยน (สีเขียว)
- พร้อมรับสาย

💭 "โอเค พร้อมแล้ว!"
😊 Emotion: 😊 Relieved

✅ Success!
```

---

### 📈 Emotion Graph

```
Happiness
    😃 |                        ●●●
    😊 |                    ●●●
    😐 | ●●●            ●●●
    😟 |    ●●●    ●●●
    😰 |       ●●●
       └──────────────────────────
       Phase Phase Phase Phase Phase
         1     2     3     4     5
```

**Key Insight:**
- Emotional low point = Phase 3-4
- ต้องแก้เร่งด่วน: Status button visibility & feedback

---

## Slide 23: Design Systems - Consistency at Scale

### 🎨 Design System คืออะไร?
> ชุดของ components, patterns, และ guidelines ที่ช่วยให้ออกแบบได้สม่ำเสมอ

### 🎯 ทำไมต้องมี?

**Benefits:**
```
✓ Consistency ทั่วทั้งแอป
✓ ออกแบบเร็วขึ้น (reuse components)
✓ Dev-Design collaboration ดีขึ้น
✓ Scale ได้ง่าย
✓ Maintain ง่ายขึ้น
✓ Onboard คนใหม่เร็วขึ้น
```

---

## Slide 24: Agent Wallboard Design System

### 🎨 Color System

**Status Colors (Semantic)**
```
🟢 Available  : #10B981  สถานะพร้อม
🔵 Active     : #3B82F6  กำลังคุยสาย
🟡 Wrap-up    : #F59E0B  สรุปงาน
🔴 Break      : #EF4444  พัก
⚫ Offline    : #6B7280  ออฟไลน์
```

**UI Colors**
```
Primary   : #3B82F6  (Blue) - Main actions
Success   : #22C55E  (Green) - Confirmations
Warning   : #F97316  (Orange) - Warnings
Error     : #DC2626  (Red) - Errors
Info      : #0EA5E9  (Sky Blue) - Info messages
```

**Neutral Colors**
```
Background: #FFFFFF  (White)
Surface:    #F9FAFB  (Light Gray)
Border:     #E5E7EB  (Gray)
Text:       #111827  (Almost Black)
Text 2nd:   #6B7280  (Medium Gray)
```

---

### ✅ Accessibility Check
```
Status Colors on White Background:
✓ Green (#10B981) - Contrast 3.5:1 ✅
✓ Blue (#3B82F6) - Contrast 4.8:1 ✅
✓ Red (#EF4444) - Contrast 4.2:1 ✅

All pass WCAG AA (≥ 3:1 for large text)
```

---

## Slide 25: Typography System

### 🔤 Font Family
```
Primary: 'Inter', sans-serif
- Modern, clean, readable
- Excellent for UI
- Variable font (flexible)
- Free & open source

Fallback: -apple-system, BlinkMacSystemFont, 
          'Segoe UI', system-ui, sans-serif
```

### 📏 Type Scale
```
Display:  48px / 700 (Bold)     - Hero sections
H1:       36px / 700 (Bold)     - Page titles
H2:       30px / 600 (Semibold) - Section headers
H3:       24px / 600 (Semibold) - Subsections
Body:     16px / 400 (Regular)  - Main content
Small:    14px / 400 (Regular)  - Labels, captions
Tiny:     12px / 400 (Regular)  - Footnotes
```

### 📐 Line Heights
```
Tight:    1.2 - Headers
Normal:   1.5 - Body text
Relaxed:  1.75 - Long-form content
```

---

## Slide 26: Spacing System - 8px Grid

### 📏 Why 8px Grid?
```
✓ เป็น standard ของอุตสาหกรรม
✓ Divisible by 2, 4 (flexible)
✓ Sharp ทุก screen resolution
✓ Easy to scale (8, 16, 24, 32)
```

### 🎯 Spacing Scale
```
xs:   4px  (0.5 × 8)  - Tight spacing
sm:   8px  (1 × 8)    - Default gap
md:   16px (2 × 8)    - Component padding
lg:   24px (3 × 8)    - Section spacing
xl:   32px (4 × 8)    - Large sections
2xl:  48px (6 × 8)    - Page margins
3xl:  64px (8 × 8)    - Hero sections
```

### 🎨 Usage Examples
```
Button padding:      12px 24px (md)
Card padding:        16px (md)
Card margin:         24px (lg)
Section gap:         32px (xl)
Page container:      48px (2xl)
Hero top margin:     64px (3xl)
```

---

## Slide 27: Component Library Preview

### 🧩 Core Components

**Buttons**
```
Primary:   Blue background, white text
Secondary: White background, blue border
Danger:    Red background, white text
Ghost:     Transparent, text only

Sizes:
- Small:  32px height
- Medium: 40px height (default)
- Large:  48px height

States:
- Default
- Hover (darker)
- Active (darkest)
- Disabled (gray)
- Loading (spinner)
```

**Cards**
```
Agent Card:
- 280px × 120px
- 16px padding
- 12px border-radius
- Shadow: 0 2px 8px rgba(0,0,0,0.08)
- Border: 1px solid #E5E7EB
- Hover: shadow เข้มขึ้น
```

**Status Badge**
```
- 24px height
- 12px padding (horizontal)
- 12px border-radius (pill shape)
- Background: status color (20% opacity)
- Text: status color (solid)
- Icon + Text
```

**Inputs**
```
Text Input:
- 40px height
- 8px 12px padding
- 8px border-radius
- Border: 1px solid #D1D5DB
- Focus: blue border + shadow

States:
- Default
- Focus
- Error (red border)
- Disabled (gray background)
```

---

## Slide 28: Introduction to Figma

### 🎨 Figma คืออะไร?
> Web-based design tool สำหรับ UI/UX design และ prototyping

### ⭐ ทำไมใช้ Figma?

**Pros:**
```
✓ ฟรีสำหรับนักศึกษา
✓ Cloud-based (ใช้ได้ทุกที่)
✓ Real-time collaboration
✓ Version control อัตโนมัติ
✓ Prototyping built-in
✓ Developer handoff ง่าย
✓ Community resources มากมาย
✓ Plugins ecosystem ใหญ่
```

**vs. Other Tools:**
```
Adobe XD:   ดี แต่ต้องติดตั้ง, Adobe ecosystem
Sketch:     Mac only, ราคาแพง
Invision:   Prototyping focus, ไม่ design
Axure:      Complex, learning curve สูง

→ Figma = Best for learning + collaboration
```

---

## Slide 29: Figma Interface - Quick Tour

### 🖥️ Main Areas

```
┌─────────────────────────────────────────────┐
│  Tools    [Figma Logo]    File  Edit  View  │ Top Bar
├────┬────────────────────────────────────┬────┤
│    │                                    │    │
│  L │                                    │  R │
│  E │        CANVAS                      │  I │
│  F │    (Your designs here)             │  G │
│  T │                                    │  H │
│    │                                    │  T │
│  P │                                    │    │
│  A │                                    │  P │
│  N │                                    │  A │
│  E │                                    │  N │
│  L │                                    │  E │
│    │                                    │  L │
├────┴────────────────────────────────────┴────┤
│            BOTTOM BAR (zoom, etc)            │
└─────────────────────────────────────────────┘

Left Panel:  Layers, Assets, Pages
Canvas:      Your design workspace
Right Panel: Design properties, Prototype
```

---

### 🛠️ Essential Tools (Top Bar)

```
V - Move/Select      (เลือกและเคลื่อนย้าย)
F - Frame            (สร้างกรอบ/หน้าจอ)
R - Rectangle        (วาดสี่เหลี่ยม)
O - Ellipse          (วาดวงกลม)
T - Text             (ใส่ text)
H - Hand             (เลื่อนดู canvas)
K - Scale            (ขยาย/ลดขนาด)
```

### ⌨️ Essential Shortcuts

```
Cmd/Ctrl + D     - Duplicate
Cmd/Ctrl + G     - Group
Cmd/Ctrl + C/V   - Copy/Paste
Shift + A        - Auto Layout
Option/Alt       - Measure distance
Space + Drag     - Pan canvas
Cmd/Ctrl + /     - Search everything
```

---

## Slide 30: Figma Key Concepts

### 1️⃣ Frames
```
= หน้าจอ/artboard ของคุณ
- ใช้สร้างแต่ละ screen
- มี preset sizes (Desktop, Mobile, etc.)
- Nested ได้ (frame ใน frame)
```

### 2️⃣ Components
```
= Reusable UI elements
- Button, Card, Input, etc.
- แก้ master → instances เปลี่ยนตาม
- เหมือน "class" ใน programming

Example:
Master: Primary Button (blue)
Instances: 
- Login button
- Submit button  
- Confirm button
(แก้สีที่ master → ทุก instance เปลี่ยนด้วย)
```

### 3️⃣ Auto Layout
```
= Flexbox สำหรับ Figma
- จัด elements แบบ flexible
- ปรับขนาดอัตโนมัติ
- Horizontal/Vertical stacking

Use for:
- Button groups
- Navigation bars
- Lists
- Cards
```

### 4️⃣ Constraints
```
= กำหนดว่า element "ติด" ที่ไหน
- Left, Right, Top, Bottom, Center
- Scale (ขยายตาม parent)

Example:
- Logo: ติดซ้ายบน
- Logout button: ติดขวาบน
- Footer: ติดล่างสุด
```

### 5️⃣ Prototyping
```
= เชื่อม frames = interactive prototype
- Click → Navigate
- Hover → Show overlay
- Drag → Swipe
- Smart Animate → Smooth transitions
```

---

## Slide 31: Live Demo - Creating a Simple Button

### 👨‍💻 Follow Along (5 นาที)

**Step 1: Create Frame (30 วินาที)**
```
- Press F (Frame tool)
- Select "Desktop" preset (1440×900)
- Click to create
```

**Step 2: Add Rectangle (30 วินาที)**
```
- Press R (Rectangle tool)
- Draw rectangle (120px × 40px)
- Corner radius: 8px
```

**Step 3: Style the Button (1 นาที)**
```
- Fill: #3B82F6 (Primary blue)
- Remove border/stroke
```

**Step 4: Add Text (30 วินาที)**
```
- Press T (Text tool)
- Type "Button"
- Font: Inter, 16px, Semibold
- Color: White (#FFFFFF)
- Center text in rectangle
```

**Step 5: Apply Auto Layout (30 วินาที)**
```
- Select both text + rectangle
- Press Shift + A
- Padding: 12px horizontal, 8px vertical
- Spacing: 8px
```

**Step 6: Make Component (30 วินาที)**
```
- Select button
- Right-click → Create Component
- Name: "Button/Primary"
```

**Step 7: Add Hover State (1 นาที)**
```
- Click component
- Add Interaction: On Hover
- Change fill to darker blue (#2563EB)
```

✅ **Done!** คุณมี reusable button component แล้ว

---

## Slide 32: Workshop Time - What's Next

### 🎯 ต่อไปเราจะทำอะไร (3 ชั่วโมง)

**Activity 1: User Interview & Persona (90 min)**
```
09:00-10:30

สิ่งที่คุณจะได้:
✅ ประสบการณ์ interview จริง
✅ 1 Persona Card สมบูรณ์
✅ เข้าใจ user needs ลึกซึ้ง

เตรียม:
- Figma account (สมัครฟรี)
- Download Persona template
- เตรียม interview questions
```

**☕ Break (15 min)**
```
10:30-10:45
```

**Activity 2: User Journey Mapping (90 min)**
```
10:45-12:15

สิ่งที่คุณจะได้:
✅ 1 Complete User Journey Map
✅ Emotion Graph
✅ Pain Points & Opportunities Analysis

เตรียม:
- Journey Map template
- เลือก scenario
```

---

## Slide 33: Materials Checklist

### 📁 ที่ต้องเตรียม (ดาวน์โหลดจาก LMS)

**Templates:**
```
☐ Figma Persona Template
☐ Journey Map Template
☐ Interview Questions List
☐ Design System Kit
```

**References:**
```
☐ Agent Wallboard SRS
☐ Use Cases Document
☐ User Stories
```

**Tools:**
```
☐ Figma Account (ฟรี)
  → figma.com/signup-education
☐ Chrome/Firefox browser
☐ Notepad สำหรับ interview notes
```

---

## Slide 34: Homework Preview (งานบ้าน)

### 📦 Assignment: Complete UX Research & UI Prototype

**Due:** สัปดาห์หน้า (ก่อนเรียน)
**Weight:** 10% ของเกรดรวม

### 📋 What to Submit:

**Part 1: UX Research (30%)**
```
1. Refined Persona Card
   - เพิ่มรายละเอียดจาก workshop
   - Professional visual design

2. Enhanced Journey Map
   - เพิ่ม touchpoints, channels
   - Complete analysis
```

**Part 2: UI Design (70%)**
```
1. Wireframes (20%)
   - 5-7 screens, mid-fidelity

2. Hi-Fi UI Design (30%)
   - 3-4 screens, full design

3. Interactive Prototype (20%)
   - Connected flows
   - Working interactions
```

---

## Slide 35: Evaluation Criteria Summary

### 📊 Grading (10% Total)

```
UX Research (30 points = 3%)
├── Persona (15 pts)
│   ✓ Complete & realistic
│   ✓ Based on research
│   ✓ Professional design
│
└── Journey Map (15 pts)
    ✓ 5+ phases
    ✓ Detailed analysis
    ✓ Emotion graph

UI Design (70 points = 7%)
├── Wireframes (20 pts)
│   ✓ 5-7 screens
│   ✓ Clear hierarchy
│   ✓ Logical flow
│
├── Hi-Fi Design (30 pts)
│   ✓ 3-4 screens
│   ✓ Design system applied
│   ✓ Professional quality
│
└── Prototype (20 pts)
    ✓ Interactive
    ✓ Working flows
    ✓ Smooth transitions
```

---

## Slide 36: Tips for Success

### 💡 Do's

```
✅ Start early (อย่ารอวันสุดท้าย)
✅ Base Persona on real research
✅ Use real content (ไม่ใช่ Lorem Ipsum)
✅ Follow design system consistently
✅ Test prototype หลายรอบ
✅ Ask for feedback early
✅ Save work often (Figma auto-saves)
✅ Export backup PDF
```

### ❌ Don'ts

```
❌ ทำ Persona แบบ generic
❌ Skip user research
❌ Inconsistent design
❌ ลืม check accessibility (contrast)
❌ Submit ไม่ test prototype
❌ รอถึงนาทีสุดท้าย
❌ ลืม export backup
```

---

## Slide 37: Resources & Getting Help

### 📚 Learning Resources

**Figma:**
```
🎥 Figma YouTube Channel
   - Official tutorials
   - Beginner to advanced

🌐 Figma Community
   - Free templates
   - Plugins
   - Inspiration

📖 Figma Learn
   - Interactive courses
   - Best practices
```

**UX/UI:**
```
📚 Nielsen Norman Group
   - UX research articles
   - Usability guidelines

🎨 Laws of UX
   - lawsofux.com
   - Design principles

💼 Dribbble & Behance
   - Design inspiration
   - Real-world examples
```

---

### 💬 Getting Help

```
📧 Email: instructor@rmutl.ac.th
💬 Slack: #engse206-week11
⏰ Office Hours: อังคาร-พฤหัสบดี 14:00-16:00
📚 LMS: เอกสารและ templates ครบ
```

### 🤝 Study Groups

```
แนะนำให้ทำงานเป็นกลุ่ม:
- แชร์ feedback
- Review ซึ่งกันและกัน
- แลกเปลี่ยนไอเดีย

แต่ submit แยกคน!
```

---

## Slide 38: Key Takeaways

### 🎯 สิ่งสำคัญที่ต้องจำ

**1. UX ≠ UI (But work together)**
```
UX = How it works (function)
UI = How it looks (form)
ต้องดีทั้งคู่
```

**2. User-Centered Design**
```
เริ่มจาก users เสมอ
Research → Design → Test → Iterate
```

**3. Personas & Journey Maps**
```
เครื่องมือเข้าใจ users
Base on real data, not assumptions
```

**4. Design Systems**
```
Consistency is key
Reusable components
Scalable และ maintainable
```

**5. Practice Makes Perfect**
```
Figma ต้องฝึก
Workshop วันนี้เป็นจุดเริ่มต้น
งานบ้านคือการฝึกจริงๆ
```

---

## Slide 39: Inspiration - Great UX/UI Examples

### 🌟 Apps to Study

**Excellent UX:**
```
✓ Airbnb - Trust & simplicity
✓ Uber - Minimal steps
✓ Duolingo - Gamification
✓ Spotify - Personalization
```

**Excellent UI:**
```
✓ Apple - Consistency & elegance
✓ Stripe - Professional & clean
✓ Notion - Flexible & powerful
✓ Linear - Fast & beautiful
```

**Agent Wallboard Inspiration:**
```
✓ Slack - Real-time communication
✓ Asana - Task management
✓ Tableau - Data visualization
✓ Zendesk - Support dashboard
```

### 💡 Homework
**Analyze 1 app you love:**
- What makes it great UX?
- What makes it beautiful UI?
- What can we learn?

---

## Slide 40: Let's Get Started! 🚀

### ✅ Ready for Workshop?

**Check:**
```
☐ Figma account พร้อม
☐ Templates downloaded
☐ Materials พร้อม
☐ เข้าใจ objectives
☐ มีคำถามถาม (ถ้ามี)
```

### 🎯 Today's Goals

```
By end of today:
✅ 1 Complete Persona Card
✅ 1 User Journey Map
✅ Hands-on Figma experience
✅ Ready สำหรับงานบ้าน
```

### 💪 Let's Begin!

```
"Good design is obvious.
Great design is transparent."
- Joe Sparano

"Design is not just what it looks like.
Design is how it works."
- Steve Jobs
```

**→ Break 5 นาที แล้วเริ่ม Workshop! 🎉**

---

## 📝 Quick Reference Card

### ⌨️ Figma Shortcuts
```
V - Select          Cmd+D - Duplicate
F - Frame           Cmd+G - Group
R - Rectangle       Shift+A - Auto Layout
T - Text            

V - Select          Cmd+D - Duplicate
F - Frame           Cmd+G - Group
R - Rectangle       Shift+A - Auto Layout
T - Text            Cmd+/ - Search
Space+Drag - Pan    Option - Measure
```

### 🎨 Design Tokens
```
Colors:
- Available: #10B981
- Active: #3B82F6
- Break: #EF4444

Spacing:
- sm: 8px
- md: 16px
- lg: 24px
- xl: 32px

Typography:
- H1: 36px/Bold
- Body: 16px/Regular
- Small: 14px/Regular
```

### 📋 Component Sizes
```
Button: 40px height
Card: 16px padding
Input: 40px height
Icon: 20px or 24px
```

---

# End of Lecture Slides (40 slides)

---

# Appendix: Additional Slides (Optional)

## Bonus Slide 1: Common UX Mistakes in Call Center Systems

### ❌ Real-World Problems

**1. Information Overload**
```
Problem:
หน้าจอเยอะเกินไป แสดงข้อมูลทั้งหมดพร้อมกัน

Impact:
- Agent งง ไม่รู้จะดูที่ไหน
- ตัดสินใจช้า
- Stress เพิ่ม

Solution:
- Progressive disclosure
- แสดงเฉพาะที่จำเป็น
- Hide secondary info
```

**2. Poor Real-Time Updates**
```
Problem:
ข้อมูลไม่ update ทันที ต้อง refresh เอง

Impact:
- พลาดการเปลี่ยนแปลง
- ตัดสินใจผิด
- Coordination แย่

Solution:
- WebSocket real-time
- Visual indicators
- Sound notifications
```

**3. Complex Status Changes**
```
Problem:
เปลี่ยนสถานะ 5-7 คลิก

Impact:
- เสียเวลา
- ทำผิดง่าย
- Productivity ลด

Solution:
- 1-2 clicks maximum
- Keyboard shortcuts
- Quick actions
```

---

## Bonus Slide 2: Accessibility Deep Dive

### ♿ WCAG 2.1 Guidelines

**Level A (Minimum)**
```
✓ Text alternatives for images
✓ Keyboard accessible
✓ No time limits
✓ No flashing content
```

**Level AA (Recommended)**
```
✓ Color contrast ≥ 4.5:1 (text)
✓ Color contrast ≥ 3:1 (large text/UI)
✓ Resize text to 200%
✓ Focus visible
✓ Multiple ways to navigate
```

**Level AAA (Enhanced)**
```
✓ Color contrast ≥ 7:1
✓ Sign language for audio
✓ Extended audio descriptions
```

### 🎯 Agent Wallboard Compliance

```
Target: WCAG AA
✅ Color contrast checked
✅ Keyboard navigation
✅ Screen reader support
✅ Focus indicators
✅ Alternative text
✅ Resize up to 200%
```

---

## Bonus Slide 3: Mobile Considerations (Preview Week 12)

### 📱 Agent Wallboard on Mobile?

**Current: Desktop Only**
```
Pros:
✓ Full screen real estate
✓ Keyboard shortcuts
✓ Multi-monitor support

Cons:
✗ Tied to desk
✗ No flexibility
✗ Remote work limited
```

**Future: Mobile Support**
```
Use Cases:
- Supervisor monitoring on-the-go
- Break time checking
- Emergency notifications
- Remote agents

Challenges:
- Smaller screen
- Touch interface
- Network reliability
- Battery life

→ Week 12 เราจะเรียนเรื่องนี้!
```

---

## Bonus Slide 4: Advanced Figma Features

### 🚀 Pro Features (เรียนต่อเอง)

**Variants (Component States)**
```
1 Component, Multiple States:
- Button: Default, Hover, Active, Disabled
- Input: Empty, Filled, Error, Focused
- Card: Default, Selected, Loading

Benefits:
- Easier to maintain
- Consistent behavior
- Faster prototyping
```

**Variables (Design Tokens)**
```
Global values:
- Colors: primary, secondary
- Spacing: sm, md, lg
- Typography: sizes, weights

Change once → Update everywhere
```

**Interactive Components**
```
Hover, click states ใน component
ไม่ต้องสร้าง variant ใหม่

Example:
Button → Hover → Darker automatically
```

**Plugins**
```
Must-have:
- Unsplash: Free photos
- Iconify: 100k+ icons
- Content Reel: Realistic content
- Contrast: Check accessibility
- Autoflow: Flowcharts
```

---

## Bonus Slide 5: Career Paths in UX/UI

### 💼 Job Opportunities

**UX Designer**
```
Focus: Research, strategy, flows
Skills: Empathy, analysis, communication
Tools: Miro, FigJam, UserTesting
Salary: 25-120K/month (Thailand)
```

**UI Designer**
```
Focus: Visual design, components
Skills: Typography, color, layout
Tools: Figma, Principle, Adobe
Salary: 25-100K/month
```

**Product Designer**
```
Focus: End-to-end design
Skills: UX + UI + Business
Tools: All of the above
Salary: 30-150K/month
```

**UX Researcher**
```
Focus: User studies, testing
Skills: Statistics, interview, analysis
Tools: Maze, Lookback, Optimal Workshop
Salary: 30-130K/month
```

### 🎓 How to Start?

```
1. Build Portfolio (3-5 projects)
2. Practice daily (Daily UI Challenge)
3. Network (UX Thailand, events)
4. Learn continuously (courses, books)
5. Contribute (open source, community)
```

---

## Bonus Slide 6: Real Project Timeline

### 📅 Agent Wallboard - UX/UI Phase

**Week 1-2: Research (10-15 days)**
```
- Stakeholder interviews
- User observations
- Competitive analysis
- Survey distribution
- Data analysis
```

**Week 3-4: Definition (10 days)**
```
- Personas creation
- Journey mapping
- Requirements workshop
- Feature prioritization
```

**Week 5-6: Design (15 days)**
```
- Wireframes (3-5 days)
- Design system (3-5 days)
- Hi-fi mockups (5-7 days)
- Review & iterate
```

**Week 7-8: Prototype & Test (10 days)**
```
- Interactive prototype (3-4 days)
- Usability testing (3-4 days)
- Iterate based on feedback
- Final handoff
```

**Total: 8 weeks (2 months)**

### 💡 In Reality:
```
Agile: Continuous design
Sprints: 2-week cycles
Always iterating
Never truly "done"
```

---

## Bonus Slide 7: Design System Examples

### 🎨 Famous Design Systems

**Material Design (Google)**
```
Philosophy: Material metaphor
Components: 50+ components
Usage: Android, web, Flutter
Free: Yes
Docs: material.io
```

**Human Interface Guidelines (Apple)**
```
Philosophy: Clarity, deference, depth
Platforms: iOS, iPadOS, macOS, watchOS
Usage: Apple ecosystem
Free: Yes
Docs: developer.apple.com/design
```

**Ant Design (Alibaba)**
```
Philosophy: Natural, certain, meaningful
Components: 60+ components
Usage: Enterprise applications
Free: Yes, open source
Docs: ant.design
```

**Carbon (IBM)**
```
Philosophy: Inclusive, beautiful, consistent
Components: 70+ components
Usage: Enterprise software
Free: Yes, open source
Docs: carbondesignsystem.com
```

### 💡 Learn from the Best
```
Study their:
- Component structure
- Documentation style
- Usage guidelines
- Accessibility approach
```

---

## Bonus Slide 8: Tools Comparison

### 🛠️ Design Tools Landscape 2024

| Feature | Figma | Adobe XD | Sketch | Invision |
|---------|-------|----------|--------|----------|
| **Price** | Free | $10/mo | $99/year | $15/mo |
| **Platform** | Web | Win/Mac | Mac only | Web |
| **Collab** | ✅✅✅ | ✅✅ | ✅ | ✅✅ |
| **Prototype** | ✅✅✅ | ✅✅ | ✅ | ✅✅✅ |
| **Dev Handoff** | ✅✅✅ | ✅✅ | ✅✅ | ✅✅ |
| **Plugins** | 1000+ | 500+ | 1000+ | Limited |
| **Learning** | Easy | Easy | Medium | Easy |

### 🏆 Winner: Figma
```
Why:
✓ Free for students
✓ Web-based (works anywhere)
✓ Best collaboration
✓ Huge community
✓ Industry standard
✓ Constantly improving

→ ใช้ในคอร์สนี้และอุตสาหกรรม
```

---

## Bonus Slide 9: Next Week Preview

### 📱 Week 12: Mobile & Responsive Design

**Topics:**
```
1. Mobile-First Approach
   - ทำไมต้อง mobile first
   - Mobile vs Desktop thinking

2. Touch Interface Design
   - Touch targets (min 44×44px)
   - Gestures (tap, swipe, pinch)
   - Thumb zones

3. Responsive Design
   - Breakpoints
   - Flexible layouts
   - Adaptive components

4. Progressive Web Apps
   - Web app ที่เหมือน native
   - Offline capability
   - Push notifications
```

**Workshop:**
```
ทำ Agent Wallboard Mobile Version:
- Mobile wireframes
- Responsive components
- Touch-optimized UI
```

---

## Bonus Slide 10: Q&A Preparation

### ❓ Common Questions

**Q: ต้องเก่ง design มาก่อนไหม?**
```
A: ไม่ต้อง! UX/UI เรียนรู้ได้
   - เริ่มจาก principles
   - ฝึก ฝึก ฝึก
   - ดู feedback ปรับปรุง
```

**Q: ต้องใช้ Figma Pro ไหม?**
```
A: ไม่ต้อง! Free เพียงพอ
   - Education account ฟรี
   - Unlimited files
   - 3 projects (ฟรี)
   → เพียงพอสำหรับคอร์ส
```

**Q: ทำงานกลุ่มได้ไหม?**
```
A: Workshop: ได้ (กลุ่ม 4-5 คน)
   Homework: Submit แยกคน
   → แต่ช่วยกัน review ได้
```

**Q: ถ้าติด Figma จะถามใครดี?**
```
A: หลายทาง:
   1. Office hours
   2. Slack channel
   3. Figma Community
   4. YouTube tutorials
   5. เพื่อนในห้อง
```

**Q: งานบ้านยากไหม?**
```
A: พอดีกับเวลา:
   - Workshop: 3 ชม. ทำ 40%
   - Homework: 8-10 ชม. ทำอีก 60%
   → เริ่มเร็ว อย่ารอวันสุดท้าย
```

---

# 🎓 END OF LECTURE SLIDES

**Total: 40 Main Slides + 10 Bonus Slides**

**Timing:**
- Session 1.1: Introduction to UX/UI (Slides 1-11) - 45 min
- Session 1.2: User Research & Personas (Slides 12-19) - 45 min  
- Session 1.3: Journey & UI Basics (Slides 20-32) - 30 min
- Wrap-up & Workshop Prep (Slides 33-40) - 10 min (buffer)

**Total: 2 hours 10 minutes (includes buffer)**

---

## 📖 Instructor Notes

### Session 1.1 (45 min) - Slides 1-11
```
00:00-05:00  Introduction (Slides 1-2)
             - Agenda, objectives
             - Course progress

05:00-15:00  Why UX/UI Matters (Slides 3-5)
             - Case studies
             - UX vs UI
             - Real-world examples

15:00-25:00  UCD & Principles (Slides 6-8)
             - User-Centered Design process
             - 10 UI Design Principles
             - Interactive discussion

25:00-35:00  Case Study (Slides 9-10)
             - Agent Wallboard intro
             - 4 user types
             - Statistics

35:00-45:00  Activity Preview (Slide 11)
             - Workshop overview
             - Q&A
```

### Session 1.2 (45 min) - Slides 12-19
```
00:00-10:00  User Research (Slides 12-15)
             - What & Why
             - Methods
             - How to interview

10:00-20:00  Sample Questions (Slides 15-16)
             - Agent questions
             - Supervisor questions
             - Discussion

20:00-35:00  Personas (Slides 16-18)
             - What & Why
             - Anatomy
             - Sample persona

35:00-45:00  Creating Personas (Slide 19)
             - Process
             - Tips
             - Q&A
```

### Session 1.3 (30 min) - Slides 20-32
```
00:00-10:00  Journey Mapping (Slides 20-22)
             - What & Why
             - Components
             - Sample journey

10:00-15:00  Design Systems (Slides 23-27)
             - What & Why
             - Agent Wallboard system
             - Components

15:00-25:00  Figma Intro (Slides 28-31)
             - Why Figma
             - Interface tour
             - Concepts
             - LIVE DEMO (5 min)

25:00-30:00  Wrap-up (Slide 32)
             - Workshop transition
             - Q&A
```

### Wrap-up (10 min) - Slides 33-40
```
00:00-03:00  Materials Check (Slide 33)
03:00-05:00  Homework Preview (Slide 34)
05:00-07:00  Tips & Resources (Slides 35-37)
07:00-10:00  Inspiration & Start (Slides 38-40)
```

---

## 🎯 Teaching Tips

### Engagement Strategies
```
✓ Ask questions throughout
✓ Show real examples (apps, websites)
✓ Live demos (Figma)
✓ Share personal stories
✓ Encourage discussion
✓ Use humor appropriately
✓ Check for understanding
```

### Common Student Questions
```
1. "Do I need to be artistic?"
   → No! UX/UI is problem-solving first

2. "Figma vs Photoshop?"
   → Different tools for different jobs

3. "How long to learn?"
   → Basics in weeks, mastery in years

4. "Portfolio requirements?"
   → 3-5 projects, process > pretty

5. "Job prospects?"
   → Growing field, good demand
```

### Troubleshooting
```
If students struggle:
- Simplify examples
- Show step-by-step
- Provide templates
- Pair programming
- Extra office hours

If too fast:
- Add more examples
- More Q&A time
- Slower demos

If too slow:
- Skip bonus slides
- Faster transitions
- Combine examples
```

---

## 📚 References & Credits

### Images & Examples
```
- Agent Wallboard System: Original design
- UI Examples: Public domain / CC0
- Icons: Lucide Icons (ISC License)
- Photos: Unsplash (Free to use)
```

### Content Sources
```
- Nielsen Norman Group
- Material Design Guidelines
- Human Interface Guidelines
- Figma Best Practices
- WCAG 2.1 Standards
```

### Recommended Reading
```
- "Don't Make Me Think" - Steve Krug
- "The Design of Everyday Things" - Don Norman
- "Sprint" - Jake Knapp
- "Refactoring UI" - Adam Wathan
```

---

**Slides prepared by:** ENGSE206 Teaching Team
**Last updated:** 2024
**Version:** 1.0