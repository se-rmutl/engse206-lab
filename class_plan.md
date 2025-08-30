
### ## **แผนการสอนฉบับสมบูรณ์ (15 สัปดาห์) - ENGSE206**

### **ส่วนที่ 1: การกำหนดความต้องการซอฟต์แวร์ (Requirements Engineering) - 4 สัปดาห์**
**เป้าหมาย:** สร้างเอกสาร Software Requirements Specification (SRS) ที่สมบูรณ์

#### **สัปดาห์ที่ 1: บทนำและการเก็บรวบรวมความต้องการ**
* **🎯 วัตถุประสงค์:** เข้าใจความสำคัญของ Requirements Engineering และสามารถเลือกใช้เทคนิคและเครื่องมือในการเก็บรวบรวมความต้องการเบื้องต้นได้
* **📚 หัวข้อ/เนื้อหาการสอน:**
    * [cite_start]ความสำคัญของการกำหนดความต้องการในการพัฒนาซอฟต์แวร์ [cite: 68]
    * [cite_start]ประเภทของความต้องการ (Functional, Non-functional, Domain) [cite: 69]
    * [cite_start]ภาพรวมกระบวนการวิศวกรรมความต้องการ (Elicitation, Analysis, Specification, Validation) [cite: 1487, 1488, 1489, 1490]
    * [cite_start]เทคนิคการเก็บรวบรวมความต้องการ: Interviews, Surveys, Observation [cite: 74]
    * [cite_start]Agile Requirements: User Stories, Epics และการทำ Story Mapping [cite: 76]
* **👨‍💻 กิจกรรมการเรียนการสอน:**
    * **ทฤษฎี:** บรรยายเชิงโต้ตอบ, อภิปรายกรณีศึกษาความล้มเหลวของโครงการจาก Requirements ที่ไม่ดี
    * [cite_start]**ปฏิบัติ (Workshop):** ฝึกจำลองการสัมภาษณ์ผู้ใช้ (User Interview Simulation) และสร้าง User Story Map สำหรับโครงงานตัวอย่าง [cite: 80]
* [cite_start]**🛠️ สื่อและเครื่องมือที่ใช้:** Miro, StoriesOnBoard (Story Mapping) [cite: 81][cite_start], JIRA, Azure DevOps (Requirements Management) [cite: 83]
* **📊 การประเมินผล:** User Story Map และเอกสารรวบรวมความต้องการเบื้องต้น

---

#### **สัปดาห์ที่ 2: การวิเคราะห์และการจัดลำดับความสำคัญ**
* **🎯 วัตถุประสงค์:** สามารถวิเคราะห์ความต้องการที่รวบรวมมาได้, จัดลำดับความสำคัญอย่างมีหลักการ และวิเคราะห์ผู้มีส่วนได้ส่วนเสีย
* **📚 หัวข้อ/เนื้อหาการสอน:**
    * [cite_start]เทคนิคการวิเคราะห์ความต้องการ (Requirements Analysis Techniques) [cite: 89, 94]
    * [cite_start]การวิเคราะห์ผู้มีส่วนได้ส่วนเสีย (Stakeholder Analysis) และ Stakeholder Matrix [cite: 91, 96]
    * [cite_start]เทคนิคการจัดลำดับความสำคัญ: MoSCoW, Kano Model, Value vs Effort Matrix [cite: 90, 95]
    * [cite_start]การจัดการความขัดแย้งของความต้องการ (Conflict Resolution) [cite: 92, 97]
* **👨‍💻 กิจกรรมการเรียนการสอน:**
    * **ทฤษฎี:** เปรียบเทียบข้อดี-ข้อเสียของเทคนิคการจัดลำดับความสำคัญแต่ละแบบ
    * [cite_start]**ปฏิบัติ (Workshop):** สร้าง Stakeholder Matrix และทำ Prioritization Exercise จาก User Stories ที่ได้ในสัปดาห์ที่ 1 [cite: 101]
* [cite_start]**🛠️ สื่อและเครื่องมือที่ใช้:** Stakeholder Analysis Canvas [cite: 103][cite_start], Prioritization Tools (Aha!, Excel Templates) [cite: 102]
* [cite_start]**📊 การประเมินผล:** รายงานการวิเคราะห์ความต้องการ (Requirements Analysis Report) [cite: 107]

---

#### **สัปดาห์ที่ 3: การเขียนเอกสารความต้องการ (SRS) และการตรวจสอบ (Software Modeling ด้วย UML)**
* **🎯 วัตถุประสงค์:** สามารถเขียนเอกสาร SRS ตามมาตรฐาน, สร้างแบบจำลอง UML เพื่ออธิบายฟังก์ชัน และเขียน Acceptance Criteria ที่ชัดเจน
* **📚 หัวข้อ/เนื้อหาการสอน:**
    * [cite_start]โครงสร้างและแนวปฏิบัติที่ดีในการเขียน Software Requirements Specification (SRS) ตามมาตรฐาน IEEE 830 [cite: 111, 112, 116]
    * **Software Modeling (UML):**
        * [cite_start]**Use Case Diagram:** เพื่อจำลองปฏิสัมพันธ์ระหว่างผู้ใช้ (Actor) กับระบบ [cite: 118]
        * **Activity Diagram:** เพื่ออธิบาย Workflow หรือขั้นตอนการทำงานที่ซับซ้อนใน Use Case
    * [cite_start]การเขียน User Stories ที่ดี และการกำหนด Acceptance Criteria ด้วยรูปแบบ Given-When-Then [cite: 113, 1909]
    * [cite_start]เทคนิคการเขียนความต้องการที่ชัดเจน (SMART Criteria) [cite: 117]
* **👨‍💻 กิจกรรมการเรียนการสอน:**
    * [cite_start]**ทฤษฎี:** วิเคราะห์ตัวอย่าง SRS ที่ดีและไม่ดี [cite: 122]
    * [cite_start]**ปฏิบัติ (Workshop):** เขียน SRS บางส่วนสำหรับโครงงานของตนเอง, วาด Use Case Diagram และ Activity Diagram, และฝึกเขียน Acceptance Criteria [cite: 123]
* [cite_start]**🛠️ สื่อและเครื่องมือที่ใช้:** Lucidchart, Draw.io (UML Diagrams) [cite: 125][cite_start], Confluence, Notion (Documentation) [cite: 126]
* [cite_start]**📊 การประเมินผล:** เอกสาร SRS (ฉบับร่าง) และ Use Case Models [cite: 129, 130]

---

#### **สัปดาห์ที่ 4: การบริหารจัดการและการต่อรองความต้องการ**
* **🎯 วัตถุประสงค์:** เข้าใจกระบวนการจัดการการเปลี่ยนแปลง และสามารถใช้ Prototype เพื่อตรวจสอบความถูกต้องของความต้องการกับผู้ใช้
* **📚 หัวข้อ/เนื้อหาการสอน:**
    * [cite_start]การบริหารจัดการการเปลี่ยนแปลง (Change Management) และกระบวนการ Change Control [cite: 133, 136]
    * [cite_start]Requirements Traceability และการวิเคราะห์ผลกระทบ (Impact Analysis) [cite: 134, 138]
    * [cite_start]กลยุทธ์การต่อรองความต้องการ (Negotiation Strategies) [cite: 134, 137]
    * [cite_start]การสร้างต้นแบบ (Prototyping) เพื่อตรวจสอบความต้องการ (Requirements Validation) [cite: 134, 139]
* **👨‍💻 กิจกรรมการเรียนการสอน:**
    * [cite_start]**ทฤษฎี:** กรณีศึกษาการจัดการการเปลี่ยนแปลงในโครงการจริง [cite: 142]
    * [cite_start]**ปฏิบัติ (Workshop):** จำลองสถานการณ์การจัดการ Change Request และสร้าง Prototype (Low-fidelity) เพื่อนำเสนอแนวคิด [cite: 143]
* [cite_start]**🛠️ สื่อและเครื่องมือที่ใช้:** Figma, Adobe XD, Balsamiq (Prototyping Tools) [cite: 145]
* [cite_start]**📊 การประเมินผล:** แผนการจัดการความต้องการ (Requirements Management Plan) [cite: 149][cite_start], Prototype และรายงานผลการ Validation [cite: 150]

---

### **ส่วนที่ 2: การออกแบบซอฟต์แวร์ (Software Design) - 10 สัปดาห์**
**เป้าหมาย:** สร้างเอกสาร Software Design Document (SDD) ที่สมบูรณ์

#### **สัปดาห์ที่ 5: หลักการออกแบบและสถาปัตยกรรมภาพรวม (High-Level)**
* **🎯 วัตถุประสงค์:** แปลง SRS สู่ภาพใหญ่ของสถาปัตยกรรม (High-Level Design) และเข้าใจหลักการพื้นฐานที่ทำให้การออกแบบมีคุณภาพ
* **📚 หัวข้อ/เนื้อหาการสอน:**
    * **Introduction to Software Design Document (SDD):** ความสำคัญและองค์ประกอบ
    * [cite_start]หลักการออกแบบพื้นฐาน: SOLID, DRY, KISS, YAGNI [cite: 154]
    * [cite_start]สถาปัตยกรรมพื้นฐาน: **3-Tier Architecture** (Presentation, Application, Data) และ **Component-based** [cite: 200]
    * **Software Modeling:** การใช้ **C4 Model** (C1: System Context, C2: Containers) เพื่อวาดแผนภาพสถาปัตยกรรม
* **👨‍💻 กิจกรรมการเรียนการสอน:**
    * **ปฏิบัติ (Workshop):** วาด C1 และ C2 Diagram สำหรับโครงงานของตนเองโดยใช้ Lucidchart หรือ Draw.io
* [cite_start]**🛠️ สื่อและเครื่องมือที่ใช้:** ArchiMate, Structurizr, Lucidchart [cite: 210, 431]
* **📊 การประเมินผล:** เอกสาร SDD ส่วนที่ 1: Architecture Design

---

#### **สัปดาห์ที่ 6: การออกแบบข้อมูลและฐานข้อมูล**
* **🎯 วัตถุประสงค์:** ออกแบบโครงสร้างข้อมูลเพื่อรองรับการทำงานของระบบ สามารถสร้าง ER Diagram และเข้าใจการเลือกใช้ฐานข้อมูล
* **📚 หัวข้อ/เนื้อหาการสอน:**
    * [cite_start]หลักการออกแบบฐานข้อมูลและการสร้างแบบจำลองข้อมูล (Data Modeling) [cite: 247]
    * **Software Modeling:** **Entity-Relationship (ER) Diagram**
    * การทำ Normalization พื้นฐาน
    * [cite_start]การตัดสินใจเลือกระหว่าง SQL vs NoSQL [cite: 248] (โดยใช้กรณีศึกษา TaskMaster Pro ที่ใช้ MongoDB)
* **👨‍💻 กิจกรรมการเรียนการสอน:**
    * **ปฏิบัติ (Workshop):** สร้าง ER Diagram สำหรับโครงงานของตนเอง
* [cite_start]**🛠️ สื่อและเครื่องมือที่ใช้:** MySQL Workbench, MongoDB Compass, ERD Plus [cite: 432]
* **📊 การประเมินผล:** เอกสาร SDD ส่วนที่ 2: Database Design

---

#### **สัปดาห์ที่ 7: การออกแบบ Low-Level, UML และ API**
* **🎯 วัตถุประสงค์:** เจาะลึกการออกแบบระดับ Component, สร้างแบบจำลอง UML และออกแบบ API ระหว่างส่วนต่างๆ
* **📚 หัวข้อ/เนื้อหาการสอน:**
    * [cite_start]หลักการ Abstraction, Encapsulation, Information Hiding [cite: 156][cite_start], Coupling และ Cohesion [cite: 160]
    * **Software Modeling (UML):**
        * **Class Diagram:** สำหรับการออกแบบโครงสร้างภายในของ Component
        * **Sequence Diagram:** สำหรับอธิบายลำดับการทำงานของ API หรือฟังก์ชันที่ซับซ้อน
    * หลักการออกแบบ RESTful API และการเขียน API Specification
* **👨‍💻 กิจกรรมการเรียนการสอน:**
    * **ปฏิบัติ (Workshop):** สร้าง Class Diagram และ Sequence Diagram สำหรับฟังก์ชันหลัก และร่างเอกสาร API Specification
* [cite_start]**🛠️ สื่อและเครื่องมือที่ใช้:** StarUML, Lucidchart (UML) [cite: 170][cite_start], Swagger, Postman (API Design) [cite: 437]
* **📊 การประเมินผล:** เอกสาร SDD ส่วนที่ 3: Low-Level Design & API Design

---

#### **สัปดาห์ที่ 8: สอบกลางภาค**
* [cite_start]**ขอบเขต:** เนื้อหาทั้งหมดตั้งแต่สัปดาห์ที่ 1-7 [cite: 33]

---

#### **สัปดาห์ที่ 9: การประยุกต์ใช้ Design Patterns**
* **🎯 วัตถุประสงค์:** ทำความเข้าใจและเลือกใช้ Design Patterns ที่เหมาะสมเพื่อปรับปรุงคุณภาพของงานออกแบบ
* **📚 หัวข้อ/เนื้อหาการสอน:**
    * [cite_start]ความสำคัญของ Design Patterns [cite: 31]
    * [cite_start]**Architectural Pattern:** MVC, MVP, MVVM [cite: 178]
    * [cite_start]**Essential GoF Patterns:** Factory, Singleton, Observer, Adapter [cite: 177, 179]
* **👨‍💻 กิจกรรมการเรียนการสอน:**
    * **ปฏิบัติ (Workshop):** วิเคราะห์ Class Diagram เดิม และ thảo luận เพื่อนำ Design Pattern มาปรับปรุงการออกแบบพร้อมให้เหตุผล
* [cite_start]**🛠️ สื่อและเครื่องมือที่ใช้:** Code examples, Pattern catalogs [cite: 190]
* **📊 การประเมินผล:** ปรับปรุงเอกสาร SDD โดยเพิ่มส่วนการอธิบาย Patterns ที่เลือกใช้

---

#### **สัปดาห์ที่ 10: การออกแบบ User Experience (UX) และ User Interface (UI)**
* **🎯 วัตถุประสงค์:** สามารถออกแบบระบบที่เน้นผู้ใช้เป็นศูนย์กลางและสร้างต้นแบบ (Prototype) ของหน้าจอได้
* **📚 หัวข้อ/เนื้อหาการสอน:**
    * [cite_start]กระบวนการ UX Design และ Design Thinking [cite: 272]
    * [cite_start]User Research, Persona, User Journey Mapping [cite: 272, 273]
    * [cite_start]หลักการออกแบบ UI, Wireframing, และ Prototyping [cite: 274, 278]
* **👨‍💻 กิจกรรมการเรียนการสอน:**
    * [cite_start]**ปฏิบัติ (Workshop):** สร้าง User Journey Map และ Wireframes สำหรับฟังก์ชันหลักของโครงงาน [cite: 283]
* [cite_start]**🛠️ สื่อและเครื่องมือที่ใช้:** Figma, Adobe XD, Sketch [cite: 284]
* [cite_start]**📊 การประเมินผล:** UI Design และ Interactive Prototype [cite: 290]

---

#### **สัปดาห์ที่ 11: Mobile และ Responsive Design**
* **🎯 วัตถุประสงค์:** เข้าใจหลักการและสามารถออกแบบ UI ที่รองรับการใช้งานบนอุปกรณ์พกพาได้
* **📚 หัวข้อ/เนื้อหาการสอน:**
    * [cite_start]กลยุทธ์ Mobile-first Design [cite: 293]
    * [cite_start]หลักการ Responsive Design [cite: 294]
    * [cite_start]Mobile UI/UX Design Patterns [cite: 298]
    * [cite_start]Platform-specific Design Guidelines (iOS, Android) [cite: 301]
* **👨‍💻 กิจกรรมการเรียนการสอน:**
    * **ปฏิบัติ (Workshop):** ปรับแก้ Wireframes ของตนเองให้เป็น Responsive Design
* [cite_start]**🛠️ สื่อและเครื่องมือที่ใช้:** Responsive Design Frameworks (Bootstrap, Tailwind CSS) [cite: 307][cite_start], Device Simulators [cite: 309]
* [cite_start]**📊 การประเมินผล:** Responsive Design Implementation (Prototype) [cite: 312]

---

#### **สัปดาห์ที่ 12: การทบทวนและปรับปรุงเอกสารออกแบบ (Design Review & Refinement)**
* **🎯 วัตถุประสงค์:** สามารถประเมินคุณภาพงานออกแบบของตนเองและผู้อื่น พร้อมให้ข้อมูลป้อนกลับที่สร้างสรรค์ และปรับปรุงเอกสาร SDD ให้สมบูรณ์
* **📚 หัวข้อ/เนื้อหาการสอน:**
    * [cite_start]เทคนิคการทำ Peer Review และ Collaborative Learning [cite: 50]
    * การใช้ Checklist ในการตรวจสอบคุณภาพของเอกสาร SRS และ SDD
    * การเขียน Version Control และ Change Log สำหรับเอกสาร
* **👨‍💻 กิจกรรมการเรียนการสอน:**
    * [cite_start]**ปฏิบัติ (Workshop):** **Design Review Session** ให้นักศึกษาแลกเปลี่ยนเอกสาร SDD กันเพื่อประเมินและให้ข้อเสนอแนะ [cite: 373]
* **📊 การประเมินผล:** การมีส่วนร่วมในการทำ Peer Review และเอกสาร SDD ฉบับสมบูรณ์

---

#### **สัปดาห์ที่ 13: ข้อควรพิจารณาด้าน Security และ Performance**
* **🎯 วัตถุประสงค์:** เข้าใจหลักการพื้นฐานในการออกแบบเพื่อความปลอดภัยและประสิทธิภาพ
* **📚 หัวข้อ/เนื้อหาการสอน:**
    * [cite_start]หลักการ Security-by-Design [cite: 316]
    * [cite_start]Authentication & Authorization Architecture พื้นฐาน (OAuth, JWT) [cite: 318, 323]
    * [cite_start]Data Protection และ Privacy-by-Design [cite: 319, 324]
    * [cite_start]Performance Patterns: Caching Strategies, Load Balancing [cite: 320, 325]
* **👨‍💻 กิจกรรมการเรียนการสอน:**
    * [cite_start]**ทฤษฎี:** วิเคราะห์ช่องโหว่ด้านความปลอดภัยที่อาจเกิดขึ้นจากการออกแบบ [cite: 328]
    * **ปฏิบัติ:** เพิ่มส่วน "Security & Performance Considerations" ในเอกสาร SDD
* [cite_start]**🛠️ สื่อและเครื่องมือที่ใช้:** OWASP Top 10, Security Architecture Templates [cite: 331, 333]

---

#### **สัปดาห์ที่ 14: ข้อควรพิจารณาด้าน DevOps และ Deployment**
* **🎯 วัตถุประสงค์:** เข้าใจภาพรวมของสถาปัตยกรรมสำหรับการนำซอฟต์แวร์ไปใช้งานจริง
* **📚 หัวข้อ/เนื้อหาการสอน:**
    * [cite_start]ภาพรวม CI/CD Pipeline Architecture [cite: 339]
    * [cite_start]แนวคิด Infrastructure as Code (IaC) [cite: 340]
    * [cite_start]แนวคิด Containerization (Docker) และ Orchestration (Kubernetes) [cite: 341]
    * [cite_start]Monitoring และ Observability Architecture [cite: 342]
* **👨‍💻 กิจกรรมการเรียนการสอน:**
    * [cite_start]**ทฤษฎี:** ศึกษา DevOps Architecture ของบริษัทชั้นนำ [cite: 350]
    * **ปฏิบัติ:** ออกแบบแผนภาพ Deployment Architecture อย่างง่ายสำหรับโครงงานของตนเอง
* [cite_start]**🛠️ สื่อและเครื่องมือที่ใช้:** CI/CD Tools (GitHub Actions) [cite: 352][cite_start], Docker, Kubernetes [cite: 353][cite_start], Terraform [cite: 354]

---

#### **สัปดาห์ที่ 15: โครงงานปฏิบัติการและการนำเสนอ**
* **🎯 วัตถุประสงค์:** รวบรวมองค์ความรู้ทั้งหมดเพื่อนำเสนอโครงงานออกแบบซอฟต์แวร์ที่สมบูรณ์แบบมืออาชีพ
* **📚 หัวข้อ/เนื้อหาการสอน:**
    * การสรุปและเชื่อมโยงเอกสาร SRS และ SDD
    * [cite_start]เทคนิคการนำเสนอผลงานแบบมืออาชีพ [cite: 362]
    * [cite_start]แนวโน้มอนาคตของการออกแบบซอฟต์แวร์ (AI-assisted Design, Low-code) [cite: 364, 367]
    * [cite_start]การพัฒนาสายอาชีพ (Career Path) ในสายงานออกแบบซอฟต์แวร์ [cite: 369]
* **👨‍💻 กิจกรรมการเรียนการสอน:**
    * [cite_start]**ปฏิบัติ:** **การนำเสนอโครงงานสุดท้าย** และ **Design Review Session** [cite: 373]
* [cite_start]**🛠️ สื่อและเครื่องมือที่ใช้:** Presentation Tools (PowerPoint, Figma Slides) [cite: 375]
* [cite_start]**📊 การประเมินผล:** โครงงานออกแบบซอฟต์แวร์ครบวงจร [cite: 381][cite_start], ทักษะการนำเสนอและการสื่อสาร [cite: 382]

---