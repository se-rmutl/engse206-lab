# ENGSE206: Software Requirements Specification and Design
## การกำหนดความต้องการและการออกแบบทางซอฟต์แวร์

**มหาวิทยาลัยเทคโนโลยีราชมงคลล้านนา (ดอยสะเก็ด)**  
**คณะวิศวกรรมศาสตร์ | ภาควิชาวิศวกรรมซอฟต์แวร์**  
**ปีการศึกษา 2568 | ภาคเรียนที่ 1**

---

## 📋 Course Overview

### รายละเอียดรายวิชา
- **รหัสวิชา**: ENGSE206
- **ชื่อวิชา**: การกำหนดความต้องการและการออกแบบทางซอฟต์แวร์
- **ชื่อภาษาอังกฤษ**: Software Requirements Specification and Design
- **หน่วยกิต**: 3(2-3-5) - ทฤษฎี 2 ชั่วโมง, ปฏิบัติ 3 ชั่วโมง, ศึกษาด้วยตนเอง 5 ชั่วโมง
- **ระยะเวลา**: 17 สัปดาห์ (สอบกลางภาคสัปดาห์ที่ 8, สอบปลายภาคสัปดาห์ที่ 17)

### วัตถุประสงค์รายวิชา
เมื่อสิ้นสุดรายวิชานี้ นักศึกษาจะสามารถ:
1. **วิเคราะห์และรวบรวมความต้องการ** ของระบบซอฟต์แวร์ได้อย่างเป็นระบบ
2. **สร้างเอกสาร SRS** (Software Requirements Specification) ตามมาตรฐานสากล
3. **ออกแบบสถาปัตยกรรมซอฟต์แวร์** ตั้งแต่ระดับ high-level ถึง low-level
4. **ใช้ Design Patterns และ UML** ในการแก้ปัญหาการออกแบบ
5. **สร้าง Software Design Document** ที่สมบูรณ์และพร้อมใช้งาน
6. **ออกแบบ UI/UX, Database และ API** สำหรับระบบจริง

---

## 🎯 Case Study: Agent Wallboard System

### เกี่ยวกับโครงการหลัก
ตลอดรายวิชานี้ เราจะใช้ **Agent Wallboard System** เป็น case study หลัก ซึ่งเป็น:
- 🏢 **ระบบ Real-time Monitoring** สำหรับ Call Center Operations
- 👥 **Multi-user System** รองรับ 4 บทบาท: Agent, Supervisor, Manager, Admin
- 💻 **Cross-platform Application**: Desktop (Electron.js) + Web Dashboard
- 🔄 **Real-time Communication**: WebSocket + REST API
- 🗄️ **Multi-database Architecture**: MSSQL (Master Data) + MongoDB (Real-time Data)

### ความซับซ้อนที่เหมาะสำหรับการเรียนรู้
- **14 User Stories** ครอบคลุม 5 Epic areas
- **13 Use Cases** พร้อม detailed scenarios
- **Real-time Requirements** สำหรับ status monitoring และ messaging
- **Performance & Security** considerations
- **Deployment & DevOps** considerations

---

## 📚 Course Structure

### 🔄 Phase 1: Requirements Engineering (สัปดาห์ 1-4) | 40% คะแนน
เรียนรู้การเก็บรวบรวม วิเคราะห์ และจัดทำเอกสารความต้องการซอฟต์แวร์

### 🏗️ Phase 2: Software Design (สัปดาห์ 5-16) | 60% คะแนน  
เรียนรู้การออกแบบซอฟต์แวร์ตั้งแต่สถาปัตยกรรมระดับสูงจนถึงรายละเอียดการ implement

---

## 📅 Weekly Schedule

### **ส่วนที่ 1: Requirements Engineering (4 สัปดาห์)**

#### 📊 สัปดาห์ที่ 1: บทนำและการเก็บรวบรวมความต้องการ
- **หัวข้อ**: Introduction to Requirements Engineering
- **เนื้อหา**: Requirements types, Gathering techniques, Agile requirements
- **Workshop**: User Interview Simulation, Story Mapping
- **เครื่องมือ**: Miro, JIRA, StoriesOnBoard
- **ผลงาน**: Initial Requirements Collection (15%)

#### 🎯 สัปดาห์ที่ 2: การวิเคราะห์และการจัดลำดับความสำคัญ
- **หัวข้อ**: Requirements Analysis & Prioritization
- **เนื้อหา**: MoSCoW, Kano Model, Stakeholder Analysis, Conflict Resolution
- **Workshop**: Prioritization Exercise, Stakeholder Mapping
- **เครื่องมือ**: Excel, Aha!, Stakeholder Canvas
- **ผลงาน**: Requirements Analysis Report (20%)

#### 📝 สัปดาห์ที่ 3: การเขียนเอกสาร SRS และ UML Modeling
- **หัวข้อ**: SRS Documentation & UML Use Cases
- **เนื้อหา**: IEEE 830, SMART Criteria, Use Case Diagrams, Activity Diagrams
- **Workshop**: SRS Writing, Use Case Development
- **เครื่องมือ**: Lucidchart, Draw.io, Confluence
- **ผลงาน**: SRS Document (Draft) (25%)

#### 🔄 สัปดาห์ที่ 4: การบริหารจัดการความต้องการ
- **หัวข้อ**: Requirements Management & Change Control
- **เนื้อหา**: Traceability, Impact Analysis, Prototyping, Validation
- **Workshop**: Change Management Simulation, Rapid Prototyping
- **เครื่องมือ**: Figma, Git, IBM DOORS
- **ผลงาน**: Final Requirements Package (20%)

### **ส่วนที่ 2: Software Design (12 สัปดาห์)**

#### 🏗️ สัปดาห์ที่ 5: หลักการออกแบบและสถาปัตยกรรมภาพรวม
- **หัวข้อ**: Design Principles & High-Level Architecture  
- **เนื้อหา**: SDD Introduction, SOLID Principles, 3-Tier Architecture, C4 Model (C1-C2)
- **Workshop**: System Context & Container Diagrams
- **เครื่องมือ**: Draw.io, Structurizr
- **ผลงาน**: Architecture Design (C1+C2) (15%)

#### 🎨 สัปดาห์ที่ 6: Design Patterns และ Architectural Patterns
- **หัวข้อ**: Software Design Patterns
- **เนื้อหา**: Creational, Structural, Behavioral Patterns, Real-time Patterns
- **Workshop**: Pattern Implementation Planning
- **เครื่องมือ**: PlantUML, Visual Studio Code
- **ผลงาน**: Design Patterns Strategy (10%)

#### 🔧 สัปดาห์ที่ 7: การออกแบบสถาปัตยกรรม - พื้นฐาน
- **หัวข้อ**: Component-Level Architecture
- **เนื้อหา**: C4 Model (C3), Component Design, Communication Patterns
- **Workshop**: Component Diagram & Interface Design
- **เครื่องมือ**: Lucidchart, PlantUML
- **ผลงาน**: Component Architecture Design (10%)

#### 📝 **สัปดาห์ที่ 8: สอบกลางภาค (20%)**

#### ⚙️ สัปดาห์ที่ 9: การออกแบบสถาปัตยกรรม - ขั้นสูง
- **หัวข้อ**: Low-Level Design & API Specifications
- **เนื้อหา**: C4 Model (C4), UML Class/Sequence Diagrams, REST API, WebSocket
- **Workshop**: Technical Specification Creation
- **เครื่องมือ**: PlantUML, Swagger Editor, Postman
- **ผลงาน**: Technical Specification (C4+UML+API) (15%)

#### 🗄️ สัปดาห์ที่ 10: การออกแบบฐานข้อมูล
- **หัวข้อ**: Database Design & Data Management
- **เนื้อหา**: ER Diagrams, SQL vs NoSQL, Multi-database Architecture, Performance Optimization
- **Workshop**: Complete Database Design
- **เครื่องมือ**: MySQL Workbench, MongoDB Compass
- **ผลงาน**: Database Design Document (15%)

#### 🎨 สัปดาห์ที่ 11: การออกแบบ UX และ UI
- **หัวข้อ**: User Experience & Interface Design
- **เนื้อหา**: User Research, Personas, User Journey Mapping, UI Design Principles
- **Workshop**: User Journey & Prototype Creation
- **เครื่องมือ**: Figma, Adobe XD
- **ผลงาน**: UX Research & UI Prototype (10%)

#### 📱 สัปดาห์ที่ 12: Mobile และ Responsive Design
- **หัวข้อ**: Multi-platform Design Considerations
- **เนื้อหา**: Responsive Design, Mobile-first Approach, Touch Interface
- **Workshop**: Responsive Design Implementation
- **เครื่องมือ**: Bootstrap, Tailwind CSS
- **ผลงาน**: Responsive Design Mockups (5%)

#### 🔍 สัปดาห์ที่ 13: การทบทวนและปรับปรุงเอกสาร
- **หัวข้อ**: Design Review & Integration
- **เนื้อหา**: Design Integration, Quality Assurance, Peer Review
- **Workshop**: Design Review Session, SDD Integration
- **เครื่องมือ**: Collaborative Review Tools
- **ผลงาน**: Integrated SDD + Peer Review (5%)

#### 🔒 สัปดาห์ที่ 14: Security และ Performance Design
- **หัวข้อ**: Security & Performance Architecture (Overview)
- **เนื้อหา**: Security-by-Design, Performance Optimization, Scalability
- **Workshop**: Security Checklist & Performance Planning
- **เครื่องมือ**: Security Analysis Tools
- **ผลงาน**: Security & Performance Document (5%)

#### 🚀 สัปดาห์ที่ 15: DevOps และ Deployment Design
- **หัวข้อ**: Deployment Architecture (Overview)
- **เนื้อหา**: CI/CD Pipeline, Infrastructure Design, Environment Management
- **Workshop**: Deployment Planning
- **เครื่องมือ**: Docker, Jenkins concepts
- **ผลงาน**: Deployment Architecture (5%)

#### 🎯 สัปดาห์ที่ 16: โครงงานปฏิบัติการและการนำเสนอ
- **หัวข้อ**: Final Project Presentation
- **เนื้อหา**: Professional Presentation, Complete SDD Integration
- **Workshop**: Final Project Preparation & Presentation
- **เครื่องมือ**: Presentation Tools, Demo Platforms
- **ผลงาน**: Complete SDD + Presentation (15%)

#### 📝 **สัปดาห์ที่ 17: สอบปลายภาค (30%)**

---

## 🏆 Assessment & Grading

### การประเมินผล (100%)

#### Requirements Engineering (40%)
| Assignment | คะแนน | สัปดาห์ | Description |
|------------|-------|---------|-------------|
| Initial Requirements Collection | 15% | 1 | User Stories + Stakeholder Analysis |
| Requirements Analysis Report | 20% | 2 | Prioritization + Conflict Resolution |
| SRS Document (Draft) | 25% | 3 | IEEE 830 + Use Cases |
| Final Requirements Package | 20% | 4 | Complete SRS + Traceability |
| **สอบกลางภาค** | **20%** | **8** | **Requirements + High-level Design** |

#### Software Design (60%)
| Assignment | คะแนน | สัปดาห์ | Description |
|------------|-------|---------|-------------|
| Architecture Design (C1+C2) | 15% | 5 | System Context + Containers |
| Design Patterns Strategy | 10% | 6 | Pattern Implementation Plan |
| Component Design (C3) | 10% | 7 | Component Architecture |
| Technical Specification (C4+UML) | 15% | 9 | Low-level Design + API |
| Database Design | 15% | 10 | Multi-database Architecture |
| UX/UI Design | 10% | 11 | User Experience Design |
| Integration Components | 20% | 12-15 | Security/Performance/DevOps |
| Final Project Presentation | 15% | 16 | Complete SDD |
| **สอบปลายภาค** | **30%** | **17** | **Complete Software Design** |

### เกณฑ์การให้คะแนน
- **A** (80-100%): งานมีคุณภาพสูง ครบถ้วน และสร้างสรรค์
- **B+** (75-79%): งานมีคุณภาพดี ครบถ้วนตามที่กำหนด
- **B** (70-74%): งานมีคุณภาพดีปานกลาง ครบถ้วนส่วนใหญ่
- **C+** (65-69%): งานผ่านเกณฑ์ แต่ยังต้องพัฒนา
- **C** (60-64%): งานผ่านเกณฑ์ขั้นต่ำ
- **F** (0-59%): งานไม่ผ่านเกณฑ์

---

## 🛠️ Tools & Technologies

### เครื่องมือที่ใช้ในรายวิชา

#### Requirements Engineering
- **Story Mapping**: Miro, StoriesOnBoard
- **Requirements Management**: JIRA, Azure DevOps, Confluence
- **Surveys**: Google Forms, Typeform
- **Documentation**: Notion, Confluence

#### Software Design  
- **Architecture Diagrams**: Draw.io, Lucidchart, Structurizr
- **UML Modeling**: PlantUML, Lucidchart
- **Database Design**: MySQL Workbench, MongoDB Compass
- **API Design**: Swagger Editor, Postman
- **UI/UX Design**: Figma, Adobe XD, Balsamiq
- **Prototyping**: Figma, InVision, Marvel

#### Development Environment
- **Code Editor**: Visual Studio Code
- **Version Control**: Git, GitHub
- **Documentation**: Markdown, GitHub Pages

---

## 📖 Learning Resources

### หนังสือและเอกสารหลัก
1. **"Software Engineering"** - Ian Sommerville
2. **"Writing Effective Use Cases"** - Alistair Cockburn  
3. **"Clean Architecture"** - Robert C. Martin
4. **"Design Patterns"** - Gang of Four
5. **"Designing Data-Intensive Applications"** - Martin Kleppmann

### Online Resources
- **IEEE Standards**: IEEE Std 830-1998 (SRS)
- **C4 Model**: https://c4model.com/
- **API Design**: https://swagger.io/resources/
- **UX Design**: https://www.interaction-design.org/
- **Software Architecture**: https://martinfowler.com/

### Community & Support
- **Course Forum**: GitHub Discussions
- **Office Hours**: ทุกวันอังคาร-พฤหัสบดี 14:00-16:00
- **Email Support**: instructor@university.ac.th

---

## 🎯 Learning Outcomes

เมื่อจบรายวิชานี้ นักศึกษาจะมีความสามารถ:

### 💼 Professional Skills
- **Business Analysis**: เก็บรวบรวมและวิเคราะห์ความต้องการทางธุรกิจ
- **System Architecture**: ออกแบบสถาปัตยกรรมระบบขนาดกลาง-ใหญ่
- **Technical Documentation**: สร้างเอกสารเทคนิคตามมาตรฐานสากล
- **Project Management**: จัดการโครงการ software design ตั้งแต่ต้นจนจบ

### 🛠️ Technical Skills  
- **Requirements Engineering**: IEEE 830, Use Cases, User Stories
- **Software Architecture**: C4 Model, 3-tier Architecture, Microservices
- **Design Patterns**: 23 GoF Patterns, Architectural Patterns
- **Database Design**: ER Modeling, SQL/NoSQL Selection, Performance Optimization
- **API Design**: RESTful services, WebSocket, OpenAPI/Swagger
- **UI/UX Design**: User Research, Wireframing, Prototyping

### 🎖️ Industry Readiness
- **Portfolio**: Complete project documentation ที่นำไปใช้สมัครงานได้
- **Modern Tools**: ประสบการณ์ใช้เครื่องมือที่ใช้ในอุตสาหกรรม
- **Best Practices**: การทำงานตามมาตรฐานและ best practices
- **Communication**: การนำเสนอและสื่อสารเทคนิคได้อย่างมืออาชีพ

---

## 📋 Prerequisites

### ความรู้พื้นฐานที่ต้องมี
- **Programming Fundamentals**: JavaScript, Python หรือภาษาใดก็ได้
- **Database Basics**: SQL พื้นฐาน, ความเข้าใจ RDBMS
- **Web Technologies**: HTML, CSS, HTTP Protocol เบื้องต้น
- **Software Engineering**: SDLC, Agile concepts เบื้องต้น

### Soft Skills ที่ควรมี
- **Communication**: ทักษะการสื่อสารและการนำเสนอ
- **Analytical Thinking**: ความสามารถในการวิเคราะห์และแก้ปัญหา
- **Teamwork**: การทำงานเป็นทีมและ peer review
- **Time Management**: การจัดการเวลาสำหรับ project ระยะยาว

---

## 🚀 Getting Started

### การเตรียมตัวก่อนเรียน
1. **ติดตั้งเครื่องมือพื้นฐาน**:
   - Git และ GitHub account
   - Visual Studio Code
   - Draw.io (หรือ Lucidchart account)
   - Figma account (สำหรับ UI/UX)

2. **ศึกษาพื้นฐาน**:
   - ทบทวนความรู้ Database และ SQL
   - อ่านเกี่ยวกับ Software Development Life Cycle
   - ทำความคุ้นเคยกับ Agile methodology

3. **เตรียมโปรเจกต์**:
   - คิดโปรเจกต์ที่อยากทำ (นอกเหนือจาก Agent Wallboard)
   - เตรียมใจสำหรับการเรียนรู้แบบ hands-on

### การติดตามความก้าวหน้า
- **Weekly Assignments**: ส่งงานตรงเวลาทุกสัปดาห์
- **Participation**: เข้าร่วม workshop และ peer review อย่างสม่ำเสมอ  
- **Final Project**: เริ่มวางแผนและทำงานอย่างต่อเนื่อง

---

## 🌟 Success Stories

### ตัวอย่างโปรเจกต์จากรุ่นก่อน
- **E-Learning Platform** - ระบบเรียนออนไลน์แบบ interactive
- **Hospital Management System** - ระบบจัดการโรงพยาบาลขนาดกลาง
- **Smart City IoT Platform** - ระบบจัดการข้อมูล IoT สำหรับเมืองอัจฉริยะ
- **Food Delivery Optimization** - ระบบเพิ่มประสิทธิภาพการส่งอาหาร

### Career Impact
นักศึกษาที่ผ่านรายวิชานี้สามารถทำงานในตำแหน่ง:
- **Business Analyst** - วิเคราะห์ความต้องการทางธุรกิจ
- **System Analyst** - ออกแบบและวิเคราะห์ระบบ  
- **Software Architect** - ออกแบบสถาปัตยกรรมซอฟต์แวร์
- **Technical Lead** - นำทีมพัฒนาระบบขนาดใหญ่
- **Product Owner** - จัดการ product development
- **UI/UX Designer** - ออกแบบประสบการณ์ผู้ใช้

---

## 📞 Contact Information

### อาจารย์ผู้สอน
- **ผู้สอน**: นายธนิต เกตุแก้ว
- **อีเมล**: thanit@rmutl.ac.th
- **Office**: ห้อง C-301 ชั้น 3 อาคารวิศวกรรมซอฟต์แวร์
- **Office Hours**: จันทร์-ศุกร์ 09:00-16:00 น.

### การสื่อสาร
- **Course Github**: [GitHub repositor](https://github.com/se-rmutl/engse206-lab) นี้
- **Announcements**: ผ่าน LMS และ GitHub
- **Emergency Contact**: Line หรือ Email

### การสนับสนุนเพิ่มเติม
- **TA Support**: นักศึกษาพี่เลี้ยงช่วยเหลือใน workshop
- **Peer Learning**: กลุ่มศึกษาและ study group
- **Industry Mentorship**: ผู้เชี่ยวชาญจากอุตสาหกรรมมาให้คำแนะนำ

---

## 📜 Course Policies

### การเข้าเรียน
- **Attendance**: บังคับเข้าเรียน ≥ 80% ของเวลาเรียนทั้งหมด
- **Late Policy**: งานส่งช้า หักคะแนน 10% ต่อวัน
- **Make-up**: สามารถชดเชยได้กรณีมีเหตุผลสมควร

### Academic Integrity
- **Original Work**: งานทั้งหมดต้องเป็นของตนเอง
- **Collaboration**: สนับสนุนการทำงานร่วมกัน แต่ต้องระบุแหล่งที่มา
- **AI Tools**: อนุญาตให้ใช้ AI เป็นเครื่องมือช่วย แต่ต้องระบุการใช้งาน

### Accessibility
- **Special Needs**: มีการสนับสนุนสำหรับนักศึกษาที่มีความต้องการพิเศษ
- **Technology**: ให้ความช่วยเหลือด้านเครื่องมือและเทคโนโลยี
- **Language**: รองรับทั้งภาษาไทยและภาษาอังกฤษ

---

## 🎉 Welcome to ENGSE206!

เตรียมตัวให้พร้อมสำหรับการเรียนรู้ที่จะเปลี่ยนชีวิตการทำงานของคุณ! 

รายวิชานี้จะทำให้คุณ:
- 🧠 **คิดเป็นระบบ** ในการแก้ปัญหาซับซ้อน
- 🛠️ **ใช้เครื่องมือมืออาชีพ** ได้อย่างคล่องแคล่ว  
- 📝 **สื่อสารเทคนิค** ได้อย่างมีประสิทธิภาพ
- 💼 **พร้อมสำหรับตลาดแรงงาน** ในยุคดิจิทัล

**มาเริ่มต้นการเดินทางสู่การเป็น Software Professional ที่แท้จริงกัน!** 🚀

---

[![GitHub stars](https://img.shields.io/github/stars/university/engse206?style=social)](https://github.com/university/engse206/stargazers)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Course: ENGSE206](https://img.shields.io/badge/Course-ENGSE206-blue.svg)](https://github.com/university/engse206)

**Last Updated**: March 2025 | **Version**: 2.0 | **Status**: Active 📚