# Software Requirements Specification (SRS)
## MeetingRoom Pro - ระบบจองห้องประชุมออนไลน์

**Version:** 1.0  
**Date:** March 2024  
**Status:** Final  
**Organization:** Software Engineering Department  

---

## Document Control

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 0.1 | 01/03/2024 | Development Team | Initial Draft |
| 0.5 | 10/03/2024 | Development Team | Added Functional Requirements |
| 0.8 | 15/03/2024 | Development Team | Added Use Cases and Test Plans |
| 1.0 | 20/03/2024 | Development Team | Final Version - Ready for Review |

## Approval

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Project Manager | _______________ | _______________ | _____ |
| Technical Lead | _______________ | _______________ | _____ |
| QA Manager | _______________ | _______________ | _____ |
| Client Representative | _______________ | _______________ | _____ |

---

## Table of Contents

1. [Introduction](#1-introduction)
   - 1.1 [Purpose](#11-purpose)
   - 1.2 [Scope](#12-scope)
   - 1.3 [Definitions, Acronyms, and Abbreviations](#13-definitions-acronyms-and-abbreviations)
   - 1.4 [References](#14-references)
   - 1.5 [Overview](#15-overview)

2. [Overall Description](#2-overall-description)
   - 2.1 [Product Perspective](#21-product-perspective)
   - 2.2 [Product Functions](#22-product-functions)
   - 2.3 [User Classes and Characteristics](#23-user-classes-and-characteristics)
   - 2.4 [Operating Environment](#24-operating-environment)
   - 2.5 [Design and Implementation Constraints](#25-design-and-implementation-constraints)
   - 2.6 [User Documentation](#26-user-documentation)
   - 2.7 [Assumptions and Dependencies](#27-assumptions-and-dependencies)

3. [Specific Requirements](#3-specific-requirements)
   - 3.1 [External Interface Requirements](#31-external-interface-requirements)
   - 3.2 [Functional Requirements](#32-functional-requirements)
   - 3.3 [Non-functional Requirements](#33-non-functional-requirements)

4. [Use Cases and Scenarios](#4-use-cases-and-scenarios)
   - 4.1 [Use Case Diagram](#41-use-case-diagram)
   - 4.2 [Detailed Use Cases](#42-detailed-use-cases)
   - 4.3 [User Stories](#43-user-stories)

5. [System Architecture](#5-system-architecture)
   - 5.1 [Architecture Overview](#51-architecture-overview)
   - 5.2 [Component Diagram](#52-component-diagram)
   - 5.3 [Database Design](#53-database-design)

6. [Validation and Verification](#6-validation-and-verification)
   - 6.1 [Test Strategy](#61-test-strategy)
   - 6.2 [Acceptance Criteria](#62-acceptance-criteria)
   - 6.3 [Traceability Matrix](#63-traceability-matrix)

7. [Project Management](#7-project-management)
   - 7.1 [Development Timeline](#71-development-timeline)
   - 7.2 [Risk Management](#72-risk-management)
   - 7.3 [Resource Planning](#73-resource-planning)

8. [Appendices](#8-appendices)
   - 8.1 [Glossary](#81-glossary)
   - 8.2 [Analysis Models](#82-analysis-models)
   - 8.3 [Supporting Information](#83-supporting-information)

---

## 1. Introduction

### 1.1 Purpose

เอกสารนี้เป็น Software Requirements Specification (SRS) สำหรับระบบ MeetingRoom Pro ซึ่งเป็นระบบจองห้องประชุมออนไลน์แบบครบวงจร โดยมีวัตถุประสงค์เพื่อ:

1. **กำหนดความต้องการ** ทั้งด้าน functional และ non-functional requirements อย่างชัดเจน
2. **เป็นข้อตกลง** ระหว่างทีมพัฒนา ผู้บริหาร และผู้ใช้งานระบบ
3. **เป็นแนวทาง** สำหรับการออกแบบ พัฒนา และทดสอบระบบ
4. **ใช้อ้างอิง** ในการติดตามความคืบหน้าและการตรวจรับงาน

**Target Audience:**
- Development Team (Developers, Designers, Testers)
- Project Stakeholders (Project Managers, Product Owners)
- End Users (Employees, Managers, Administrators)
- Quality Assurance Team
- Technical Writers

### 1.2 Scope

**Product Name:** MeetingRoom Pro

**Product Vision:** "To be the most efficient and user-friendly meeting room booking system that maximizes resource utilization and enhances workplace productivity"

**In-Scope Features:**
1. **User Management System**
   - User registration and authentication
   - Role-based access control (RBAC)
   - Profile management
   - Integration with corporate LDAP/AD

2. **Room Booking System**
   - Real-time room availability
   - Advanced and instant booking
   - Recurring bookings
   - Conflict resolution

3. **Notification System**
   - Email notifications
   - SMS alerts
   - Push notifications
   - Customizable reminders

4. **Reporting & Analytics**
   - Usage statistics
   - Occupancy reports
   - Booking trends
   - Custom reports

5. **Administrative Functions**
   - Room management
   - Equipment management
   - User administration
   - System configuration

**Out-of-Scope Features:**
- Video conferencing integration
- Payment processing
- Catering management
- Visitor management
- Facility maintenance tracking

**Expected Benefits:**
- **Reduce booking time** from 15 minutes to 2 minutes (87% reduction)
- **Eliminate double bookings** by 100%
- **Increase room utilization** by 30%
- **Save administrative time** by 5 hours per week
- **Improve user satisfaction** to 90%

### 1.3 Definitions, Acronyms, and Abbreviations

| Term | Definition |
|------|------------|
| **API** | Application Programming Interface - ช่องทางการเชื่อมต่อระหว่างระบบ |
| **Admin** | Administrator - ผู้ดูแลระบบที่มีสิทธิ์สูงสุด |
| **Booking** | การจองห้องประชุมในช่วงเวลาที่กำหนด |
| **Conflict** | การจองที่ทับซ้อนกันในห้องและเวลาเดียวกัน |
| **Dashboard** | หน้าจอหลักที่แสดงข้อมูลสรุป |
| **LDAP** | Lightweight Directory Access Protocol - ระบบจัดการข้อมูลผู้ใช้ |
| **Push Notification** | การแจ้งเตือนแบบ real-time บนอุปกรณ์ mobile |
| **RBAC** | Role-Based Access Control - การควบคุมสิทธิ์ตามบทบาท |
| **Room** | ห้องประชุมที่สามารถจองได้ในระบบ |
| **SRS** | Software Requirements Specification |
| **SSO** | Single Sign-On - การ login ครั้งเดียวใช้ได้หลายระบบ |
| **Session** | ช่วงเวลาที่ผู้ใช้ login อยู่ในระบบ |
| **UI/UX** | User Interface/User Experience |
| **UTC** | Coordinated Universal Time |
| **2FA** | Two-Factor Authentication - การยืนยันตัวตน 2 ชั้น |

### 1.4 References

1. **IEEE Std 830-1998** - IEEE Recommended Practice for Software Requirements Specifications
2. **ISO/IEC 25010:2011** - Systems and software Quality Requirements and Evaluation (SQuaRE)
3. **WCAG 2.1** - Web Content Accessibility Guidelines
4. **OWASP Top 10** - Web Application Security Risks
5. **Company IT Security Policy v3.0** - Internal security guidelines
6. **Meeting Room Usage Policy v2.1** - Corporate meeting room policies
7. **Brand Guidelines v1.5** - UI/UX design standards

### 1.5 Overview

เอกสารนี้แบ่งออกเป็น 8 หมวดหลัก:

- **หมวด 1-2:** อธิบายภาพรวมของระบบ บริบท และข้อจำกัดต่างๆ
- **หมวด 3:** ระบุ requirements ทั้งหมดอย่างละเอียด (11 SMART requirements)
- **หมวด 4:** แสดง use cases และ scenarios การใช้งาน
- **หมวด 5:** อธิบายสถาปัตยกรรมระบบ
- **หมวด 6:** กำหนดแนวทางการ validation และ verification
- **หมวด 7:** แผนการบริหารจัดการโครงการ (18 สัปดาห์)
- **หมวด 8:** ข้อมูลเพิ่มเติมและภาคผนวก

---

## 2. Overall Description

### 2.1 Product Perspective

MeetingRoom Pro เป็นระบบ web-based application ที่พัฒนาขึ้นใหม่ทั้งหมด (greenfield project) โดยไม่ได้เป็นส่วนหนึ่งของระบบใดที่มีอยู่ แต่ต้องสามารถเชื่อมต่อกับระบบภายนอกได้

#### System Context Diagram

```
┌─────────────────────────────────────────────────────────────────┐
│                        External Systems                          │
├─────────────────┬─────────────────┬─────────────┬──────────────┤
│   LDAP/AD       │   Email Server  │   SMS Gateway │   Calendar  │
│   Directory     │   (SMTP)        │               │   Systems   │
└────────▲────────┴────────▲────────┴───────▲──────┴──────▲───────┘
         │                 │                 │              │
         │                 │                 │              │
┌────────┴─────────────────┴─────────────────┴──────────────┴───────┐
│                                                                    │
│                        MeetingRoom Pro System                      │
│  ┌──────────────┐  ┌──────────────┐  ┌────────────────────────┐  │
│  │ Web Portal   │  │ Mobile Apps  │  │ Admin Dashboard        │  │
│  │ (React)      │  │ (iOS/Android)│  │ (React + Analytics)    │  │
│  └──────┬───────┘  └──────┬───────┘  └──────────┬─────────────┘  │
│         │                 │                       │                │
│  ┌──────┴─────────────────┴───────────────────────┴────────────┐  │
│  │                    API Gateway (REST/GraphQL)                │  │
│  └──────┬───────────────────────────────────────────────────────┘  │
│         │                                                          │
│  ┌──────┴────────┬─────────────────┬─────────────┬─────────────┐ │
│  │ Auth Service  │ Booking Service │ Notification │ Reporting   │ │
│  │               │                 │ Service      │ Service     │ │
│  └───────────────┴─────────────────┴──────────────┴─────────────┘ │
│                                                                    │
│  ┌──────────────────────────────────────────────────────────────┐ │
│  │               Database Layer (PostgreSQL)                     │ │
│  └──────────────────────────────────────────────────────────────┘ │
└────────────────────────────────────────────────────────────────────┘
```

#### System Interfaces

1. **LDAP/Active Directory Integration**
   - Protocol: LDAP v3
   - Purpose: User authentication และ synchronization
   - Frequency: Real-time for auth, daily sync for user data

2. **Email Server (SMTP)**
   - Protocol: SMTP with TLS
   - Purpose: Send notifications และ confirmations
   - Service: SendGrid หรือ AWS SES

3. **SMS Gateway**
   - Protocol: REST API
   - Purpose: Send SMS reminders
   - Service: Twilio หรือ local provider

4. **Calendar Systems**
   - Protocols: CalDAV, Exchange Web Services
   - Purpose: Sync bookings กับ personal calendars
   - Systems: Outlook, Google Calendar

### 2.2 Product Functions

#### Function Hierarchy

```
MeetingRoom Pro
├── User Management
│   ├── Registration & Authentication
│   ├── Profile Management
│   ├── Password Management
│   └── Role & Permission Management
│
├── Room Booking
│   ├── Room Search & Filter
│   ├── Availability Check
│   ├── Create Booking
│   ├── Modify Booking
│   ├── Cancel Booking
│   └── Recurring Bookings
│
├── Notification System
│   ├── Email Notifications
│   ├── SMS Alerts
│   ├── Push Notifications
│   └── In-app Notifications
│
├── Reporting & Analytics
│   ├── Usage Reports
│   ├── Occupancy Analytics
│   ├── Trend Analysis
│   └── Custom Reports
│
└── Administration
    ├── Room Management
    ├── Equipment Management
    ├── User Administration
    ├── System Configuration
    └── Audit Logs
```

### 2.3 User Classes and Characteristics

#### 1. Regular Employee (80% of users)

**Characteristics:**
- Age: 25-45 ปี
- Technical skill: Intermediate
- Usage frequency: 2-3 ครั้ง/สัปดาห์
- Primary device: Desktop (70%), Mobile (30%)

**Needs:**
- Quick booking process
- Easy room search
- Clear notifications
- Mobile access

**User Persona - "สมชาย พนักงานขาย"**
- ต้องการจองห้องประชุมเร็วๆ สำหรับ meeting กับลูกค้า
- ใช้ smartphone เป็นหลักเมื่ออยู่นอกออฟฟิศ
- ต้องการ notification ที่ชัดเจน

#### 2. Manager/Team Lead (15% of users)

**Characteristics:**
- Age: 30-50 ปี
- Technical skill: Intermediate
- Usage frequency: 5-10 ครั้ง/สัปดาห์
- Primary device: Desktop (80%), Mobile (20%)

**Needs:**
- Recurring bookings
- Team booking management
- Usage reports
- Priority booking

**User Persona - "วิภา ผู้จัดการฝ่ายการตลาด"**
- จองห้องประชุมสำหรับ weekly team meeting
- ต้องการดูรายงานการใช้งานของทีม
- ต้องการจัดการการจองของลูกทีม

#### 3. Administrator (5% of users)

**Characteristics:**
- Age: 25-40 ปี
- Technical skill: Advanced
- Usage frequency: Daily
- Primary device: Desktop (100%)

**Needs:**
- Full system control
- Detailed analytics
- User management
- System monitoring

**User Persona - "ธนากร IT Administrator"**
- ดูแลระบบทั้งหมด
- จัดการ user accounts และ permissions
- Monitor system performance
- Generate executive reports

### 2.4 Operating Environment

#### Hardware Platform

**Server Requirements:**
- CPU: 8 cores minimum
- RAM: 16GB minimum
- Storage: 500GB SSD
- Network: 1Gbps connection
- Redundancy: Active-passive failover

**Client Requirements:**
- Desktop: Any computer with modern web browser
- Mobile: iOS 12+ or Android 8+
- Minimum screen resolution: 1024x768

#### Software Platform

**Server Software:**
- OS: Ubuntu 20.04 LTS or CentOS 8
- Web Server: Nginx 1.18+
- Application Server: Node.js 16+
- Database: PostgreSQL 13+
- Cache: Redis 6+
- Message Queue: RabbitMQ 3.8+

**Client Software:**
- Web Browsers: Chrome 90+, Firefox 88+, Safari 14+, Edge 90+
- Mobile OS: iOS 12+, Android 8+

### 2.5 Design and Implementation Constraints

#### Technical Constraints

1. **Programming Languages:**
   - Backend: Node.js with TypeScript
   - Frontend: React with TypeScript
   - Mobile: React Native
   - Database: SQL with PostgreSQL

2. **Architecture:**
   - Must follow microservices architecture
   - RESTful API design principles
   - Implement API versioning
   - Use containerization (Docker)

3. **Security:**
   - All communication via HTTPS
   - Data encryption at rest and in transit
   - Implement OWASP security guidelines
   - Regular security audits required

#### Business Constraints

1. **Budget:** Maximum 3,000,000 THB
2. **Timeline:** 18 weeks from kickoff to deployment
3. **Team Size:** Maximum 8 developers
4. **Licensing:** Must use open-source or company-licensed software

#### Regulatory Constraints

1. **Data Protection:**
   - Comply with PDPA (Personal Data Protection Act)
   - Data retention policy (maximum 2 years)
   - Right to be forgotten implementation

2. **Accessibility:**
   - WCAG 2.1 Level AA compliance
   - Support for screen readers
   - Keyboard navigation support

### 2.6 User Documentation

1. **User Manual** - Comprehensive guide สำหรับ end users
2. **Administrator Guide** - System administration และ configuration
3. **API Documentation** - สำหรับ developers และ integrations
4. **Quick Start Guide** - 1-page guide สำหรับ new users
5. **Video Tutorials** - 5-10 นาที tutorials สำหรับ key features
6. **FAQ Section** - Common questions และ troubleshooting

### 2.7 Assumptions and Dependencies

#### Assumptions

1. **Infrastructure:**
   - องค์กรมี network infrastructure ที่เสถียร
   - มี internet bandwidth เพียงพอ (minimum 100 Mbps)
   - มี backup power สำหรับ servers

2. **Users:**
   - ทุกคนมี corporate email address
   - ผู้ใช้มีความรู้พื้นฐานการใช้ web browser
   - ผู้ใช้มี smartphone สำหรับรับ notifications

3. **Integration:**
   - LDAP/AD system พร้อมใช้งานและ stable
   - Email server รองรับ volume สูง
   - Calendar systems มี API ที่เข้าถึงได้

#### Dependencies

1. **External Services:**
   - LDAP/AD for authentication
   - SMTP server for emails
   - SMS gateway service
   - Cloud hosting provider

2. **Third-party Libraries:**
   - React 18+ for frontend
   - Express.js for backend
   - Passport.js for authentication
   - Socket.io for real-time updates

3. **Development Tools:**
   - Git for version control
   - Jenkins for CI/CD
   - Jest for testing
   - Docker for containerization

---

## 3. Specific Requirements

### 3.1 External Interface Requirements

#### 3.1.1 User Interfaces

**UI-001: Responsive Web Design**
- ระบบต้องแสดงผลได้ดีบนทุกขนาดหน้าจอ (Responsive Design)
- รองรับ breakpoints: Mobile (< 768px), Tablet (768-1024px), Desktop (> 1024px)
- ใช้ Material Design หรือ Ant Design เป็น design system

**UI-002: Accessibility Standards**
- รองรับ screen readers (JAWS, NVDA)
- Keyboard navigation สำหรับทุก functions
- Color contrast ratio ≥ 4.5:1 (WCAG AA)
- Alt text สำหรับทุกรูปภาพ

**UI-003: Multi-language Support**
- รองรับภาษาไทยและอังกฤษ
- สามารถเปลี่ยนภาษาได้ทันทีโดยไม่ต้อง refresh
- Date/time format ตาม locale

#### 3.1.2 Hardware Interfaces

**HI-001: Server Hardware**
- รองรับ virtualization (VMware, Hyper-V)
- Hardware load balancer support
- SAN/NAS storage compatibility

**HI-002: Client Hardware**
- ไม่ต้องการ special hardware
- รองรับ touch screen สำหรับ tablets
- Camera access สำหรับ QR code scanning (future feature)

#### 3.1.3 Software Interfaces

**SI-001: LDAP/Active Directory**
```
Interface: LDAP v3
Protocol: LDAPS (port 636)
Authentication: Simple bind with service account
Attributes: sAMAccountName, mail, displayName, memberOf
Sync Frequency: Real-time for auth, nightly for full sync
```

**SI-002: Email Service**
```
Interface: SMTP
Protocol: SMTP with STARTTLS
Port: 587
Authentication: API key or username/password
Rate Limit: 100 emails/minute
Templates: HTML with plain text fallback
```

**SI-003: SMS Gateway**
```
Interface: REST API
Protocol: HTTPS
Authentication: Bearer token
Format: JSON
Rate Limit: 50 SMS/minute
Character Limit: 160 characters (70 for Thai)
```

**SI-004: Calendar Integration**
```
Outlook:
- Protocol: Exchange Web Services (EWS)
- Authentication: OAuth 2.0
- Operations: Create, Update, Delete events

Google Calendar:
- Protocol: Calendar API v3
- Authentication: OAuth 2.0
- Operations: Create, Update, Delete events
```

#### 3.1.4 Communications Interfaces

**CI-001: API Communication**
- Protocol: HTTPS only (TLS 1.2+)
- Format: RESTful JSON API
- Authentication: JWT tokens
- Rate limiting: 1000 requests/hour/user
- API versioning: URL path (e.g., /api/v1/)

**CI-002: Real-time Updates**
- Protocol: WebSocket Secure (WSS)
- Library: Socket.io
- Events: Room status changes, booking updates
- Reconnection: Automatic with exponential backoff

### 3.2 Functional Requirements

#### REQ-F001: User Registration and Authentication ✓

**Description:** ระบบต้องจัดการ user registration, authentication, และ session management อย่างปลอดภัย

**Category:** User Management  
**Priority:** High  
**Requirement Type:** Functional  
**Source:** Business Requirements Document v1.2  
**Rationale:** เป็นพื้นฐานสำหรับการควบคุมการเข้าถึงและรักษาความปลอดภัย

**SMART Criteria:**
- **Specific:** User registration ด้วย email verification, login ด้วย username/password หรือ SSO
- **Measurable:** Registration success rate > 95%, Login time < 3 seconds
- **Achievable:** ใช้ standard authentication libraries
- **Relevant:** ตอบสนอง security requirements
- **Time-bound:** Complete ภายใน Sprint 2

**Acceptance Criteria:**
```gherkin
Feature: User Registration
  Scenario: Successful Registration
    Given I am on the registration page
    When I enter valid email "user@company.com"
    And I enter password "SecurePass123!"
    And I confirm password "SecurePass123!"
    And I accept terms and conditions
    And I click "Register"
    Then I should see "Registration successful"
    And I should receive verification email within 2 minutes
    And The email should contain activation link

  Scenario: Email Verification
    Given I received verification email
    When I click the activation link
    Then My account should be activated
    And I should be redirected to login page
    And I should see "Account activated successfully"

  Scenario: Login with Credentials
    Given I have an activated account
    When I enter username "user@company.com"
    And I enter password "SecurePass123!"
    And I click "Login"
    Then I should be logged in within 3 seconds
    And I should see the main dashboard
    And Session should be created with 8-hour timeout

  Scenario: Account Lockout
    Given I have an account
    When I enter wrong password 5 times consecutively
    Then My account should be locked for 30 minutes
    And I should receive security alert email
    And I should see "Account locked due to multiple failed attempts"
```

**Technical Requirements:**
- Password complexity: Minimum 8 characters, 1 uppercase, 1 number, 1 special character
- Password hashing: bcrypt with salt rounds = 10
- Session storage: Redis with TTL = 8 hours
- Email verification token: JWT with 24-hour expiration
- Account lockout: 5 failed attempts = 30 minutes lock

**Dependencies:** Email service (REQ-F004), LDAP integration

**Test Cases:**
1. Valid registration with corporate email
2. Invalid registration with personal email
3. Password mismatch validation
4. Duplicate email prevention
5. Session timeout after 8 hours
6. Concurrent login prevention (optional)

---

#### REQ-F002: Room Search and Availability ✓

**Description:** ระบบต้องมี search engine ที่มีประสิทธิภาพสำหรับค้นหาห้องประชุมตาม criteria ต่างๆ

**Category:** Room Booking  
**Priority:** High  
**Requirement Type:** Functional  
**Source:** User Requirements Workshop  
**Rationale:** Core feature ที่ users ใช้บ่อยที่สุด

**SMART Criteria:**
- **Specific:** Search by date, time, capacity, equipment, location
- **Measurable:** Search results < 3 seconds, Accuracy > 99%
- **Achievable:** ใช้ indexed database queries
- **Relevant:** ตอบสนองความต้องการหลักของผู้ใช้
- **Time-bound:** Complete ภายใน Sprint 3

**Acceptance Criteria:**
```gherkin
Feature: Room Search
  Scenario: Basic Search
    Given I am on room search page
    When I select date "2024-04-01"
    And I select time "10:00 - 12:00"
    And I click "Search"
    Then I should see available rooms within 3 seconds
    And Results should show room name, capacity, and equipment
    And Results should be sorted by relevance

  Scenario: Advanced Search
    Given I am on advanced search
    When I set minimum capacity to "10"
    And I select equipment "Projector, Whiteboard"
    And I select floor "5"
    And I select date range "2024-04-01 to 2024-04-05"
    Then I should see filtered results
    And Only rooms matching ALL criteria should appear

  Scenario: Real-time Updates
    Given I am viewing search results
    When Another user books a room
    Then The room status should update within 30 seconds
    And The room should show as "Booked"
    And I should not be able to select it

  Scenario: No Results
    Given I search for rooms
    When No rooms match my criteria
    Then I should see "No rooms available"
    And System should suggest alternative times
    And System should suggest similar rooms
```

**Technical Requirements:**
- Search index: Elasticsearch หรือ PostgreSQL full-text search
- Caching: Redis for frequent searches
- Real-time updates: WebSocket for status changes
- Response time: 95th percentile < 3 seconds
- Pagination: 20 results per page

**Search Filters:**
- Date and time range
- Room capacity (min/max)
- Equipment checklist
- Building and floor
- Room type (meeting, conference, training)
- Accessibility features

**Dependencies:** Database indexing, WebSocket service

---

#### REQ-F003: Room Booking Management ✓

**Description:** ระบบต้องจัดการ lifecycle ของการจองห้องประชุมตั้งแต่การสร้าง แก้ไข จนถึงยกเลิก

**Category:** Room Booking  
**Priority:** High  
**Requirement Type:** Functional  
**Source:** Business Requirements Document v1.2  
**Rationale:** Core business function ที่ต้องมีความน่าเชื่อถือสูง

**SMART Criteria:**
- **Specific:** CRUD operations for bookings with conflict prevention
- **Measurable:** Zero double bookings, Booking completion < 5 seconds
- **Achievable:** ใช้ database transactions และ locking
- **Relevant:** ตอบโจทย์ปัญหาการจองซ้ำซ้อน
- **Time-bound:** Complete ภายใน Sprint 4

**Acceptance Criteria:**
```gherkin
Feature: Room Booking
  Scenario: Successful Booking
    Given I selected an available room
    When I enter meeting title "Project Review"
    And I enter attendees count "8"
    And I select equipment "Projector"
    And I add description "Quarterly review meeting"
    And I click "Book Room"
    Then Booking should be confirmed within 5 seconds
    And I should see confirmation with booking ID
    And I should receive confirmation email
    And Room should be marked as booked

  Scenario: Double Booking Prevention
    Given A room is already booked for "10:00-12:00"
    When I try to book same room for "11:00-13:00"
    Then System should detect conflict
    And Show error "Room already booked"
    And Suggest alternative rooms or times
    And Booking should not be created

  Scenario: Modify Booking
    Given I have a future booking (> 2 hours)
    When I click "Edit Booking"
    And I change time to "14:00-16:00"
    And I click "Update"
    Then Booking should be updated
    And I should receive update confirmation
    And Old time slot should be released

  Scenario: Cancel Booking
    Given I have a future booking (> 1 hour)
    When I click "Cancel Booking"
    And I confirm cancellation
    Then Booking should be cancelled
    And Room should become available
    And I should receive cancellation email
    And Attendees should be notified

  Scenario: Recurring Booking
    Given I need weekly team meeting
    When I select "Recurring"
    And I choose "Weekly on Monday"
    And I set end date "2024-12-31"
    And I click "Book Series"
    Then All occurrences should be booked
    And I should see list of all bookings
    And I can modify single or all occurrences
```

**Technical Requirements:**
- Database transactions with ACID compliance
- Optimistic locking for conflict prevention
- Booking ID format: YYYYMMDD-XXXX (e.g., 20240401-0001)
- Maximum booking duration: 8 hours
- Maximum advance booking: 90 days
- Minimum booking duration: 30 minutes

**Business Rules:**
- Users can book maximum 5 rooms simultaneously
- Managers can override bookings with notification
- Cancellation deadline: 1 hour before start
- Modification deadline: 2 hours before start
- No-show tracking: 3 no-shows = warning

**Dependencies:** Notification system (REQ-F004), Database transactions

---

#### REQ-F004: Notification System ✓

**Description:** ระบบต้องส่งการแจ้งเตือนหลายช่องทางเพื่อให้ผู้ใช้ไม่พลาดการประชุม

**Category:** Communication  
**Priority:** Medium  
**Requirement Type:** Functional  
**Source:** User Feedback Sessions  
**Rationale:** ลด no-show rate และเพิ่มประสิทธิภาพการใช้ห้อง

**SMART Criteria:**
- **Specific:** Multi-channel notifications (Email, SMS, Push)
- **Measurable:** Delivery rate > 99%, Delivery time < 1 minute
- **Achievable:** ใช้ reliable third-party services
- **Relevant:** ช่วยลด meeting no-shows
- **Time-bound:** Complete ภายใน Sprint 5

**Acceptance Criteria:**
```gherkin
Feature: Notifications
  Scenario: Booking Confirmation
    Given I successfully booked a room
    When Booking is completed
    Then I should receive email within 1 minute
    And Email should contain:
      | Field | Content |
      | Room | Meeting Room A |
      | Date | 2024-04-01 |
      | Time | 10:00-12:00 |
      | Booking ID | 20240401-0001 |
      | Calendar file | .ics attachment |

  Scenario: Reminder Notifications
    Given I have a booking at 10:00
    When Current time is 09:30 (30 min before)
    Then I should receive first reminder via email
    When Current time is 09:55 (5 min before)
    Then I should receive final reminder via push notification
    And Reminder should include room location

  Scenario: Cancellation Notification
    Given Someone cancelled a room I'm invited to
    When Cancellation is processed
    Then I should receive immediate notification
    And Calendar event should be removed
    And Email should explain cancellation reason

  Scenario: Notification Preferences
    Given I am in notification settings
    When I disable SMS notifications
    And I enable only email for reminders
    Then System should respect my preferences
    And I should only receive email reminders
```

**Technical Requirements:**
- Email service: SendGrid or AWS SES
- SMS service: Twilio or local provider
- Push service: Firebase Cloud Messaging
- Template engine: Handlebars or similar
- Retry mechanism: 3 attempts with exponential backoff
- Delivery tracking and logs

**Notification Types:**
1. Booking confirmation
2. Booking modification
3. Booking cancellation
4. Reminder (30 min, 5 min)
5. No-show warning
6. System maintenance
7. Room unavailable

**Dependencies:** Email service, SMS gateway, Push notification service

---

#### REQ-F005: Reporting and Analytics ✓

**Description:** ระบบต้องสร้างรายงานเชิงวิเคราะห์สำหรับการตัดสินใจเชิงธุรกิจ

**Category:** Analytics  
**Priority:** Medium  
**Requirement Type:** Functional  
**Source:** Management Requirements  
**Rationale:** ช่วยในการวางแผนและจัดสรรทรัพยากรอย่างมีประสิทธิภาพ

**SMART Criteria:**
- **Specific:** Automated reports with drill-down capabilities
- **Measurable:** Report generation < 30 seconds, Data accuracy 100%
- **Achievable:** ใช้ reporting engine และ caching
- **Relevant:** ตอบโจทย์ management decisions
- **Time-bound:** Complete ภายใน Sprint 8

**Acceptance Criteria:**
```gherkin
Feature: Reports and Analytics
  Scenario: View Dashboard
    Given I am a manager
    When I access analytics dashboard
    Then I should see:
      | Metric | Display |
      | Room utilization | 75% average |
      | Popular rooms | Top 5 list |
      | Peak hours | Heat map |
      | Booking trends | Line chart |
      | Department usage | Pie chart |

  Scenario: Generate Custom Report
    Given I need specific data
    When I select date range "2024-01-01 to 2024-03-31"
    And I select metrics "Utilization, Cancellations"
    And I group by "Department"
    And I click "Generate Report"
    Then Report should be ready within 30 seconds
    And I can download as PDF or Excel
    And Data should match source records

  Scenario: Scheduled Reports
    Given I want weekly reports
    When I create scheduled report
    And I set frequency "Every Monday 8:00"
    And I add recipients "manager@company.com"
    Then Report should be sent automatically
    And Include comparison with previous period
```

**Report Types:**
1. **Utilization Report**
   - Room usage percentage
   - Peak vs off-peak analysis
   - Capacity vs actual usage

2. **Booking Analytics**
   - Total bookings by period
   - Cancellation rate
   - No-show rate
   - Average booking duration

3. **Department Report**
   - Usage by department
   - Cost allocation (if applicable)
   - Trending analysis

4. **Executive Summary**
   - KPI dashboard
   - YoY comparison
   - Recommendations

**Technical Requirements:**
- Reporting engine: Jasper Reports or similar
- Data warehouse: Separate analytics database
- ETL process: Nightly data sync
- Caching: Pre-calculated metrics
- Export formats: PDF, Excel, CSV

**Dependencies:** Database read replicas, ETL pipeline

---

#### REQ-F006: User Profile Management ✓

**Description:** ระบบต้องให้ผู้ใช้จัดการข้อมูลส่วนตัวและ preferences ได้

**Category:** User Management  
**Priority:** Low  
**Requirement Type:** Functional  
**Source:** User Requirements  
**Rationale:** เพิ่ม user experience และ personalization

**SMART Criteria:**
- **Specific:** Edit profile, preferences, and view booking history
- **Measurable:** Profile update < 2 seconds, History load < 5 seconds
- **Achievable:** Standard CRUD operations
- **Relevant:** Improve user satisfaction
- **Time-bound:** Complete ภายใน Sprint 6

**Acceptance Criteria:**
```gherkin
Feature: User Profile
  Scenario: Update Profile
    Given I am in my profile page
    When I update phone number "0812345678"
    And I change notification preferences
    And I click "Save"
    Then Changes should be saved immediately
    And I should see success message
    And New settings should take effect

  Scenario: View Booking History
    Given I want to see my past bookings
    When I click "Booking History"
    Then I should see list of all bookings
    And I can filter by date range
    And I can search by room name
    And I can export to Excel

  Scenario: Favorite Rooms
    Given I frequently use certain rooms
    When I mark room as favorite
    Then Room should appear in favorites list
    And Favorites should appear first in search
    And I can manage favorites list
```

**Profile Fields:**
- Display name
- Phone number (for SMS)
- Department
- Notification preferences
- Language preference
- Default booking duration
- Favorite rooms

**Dependencies:** User authentication system

---

#### REQ-F007: Room Resource Management ✓

**Description:** ระบบต้องจัดการข้อมูลห้องประชุมและอุปกรณ์ประกอบ

**Category:** Administration  
**Priority:** Medium  
**Requirement Type:** Functional  
**Source:** Admin Requirements  
**Rationale:** จำเป็นสำหรับการบำรุงรักษาข้อมูลให้เป็นปัจจุบัน

**SMART Criteria:**
- **Specific:** CRUD operations for rooms and equipment
- **Measurable:** Update time < 3 seconds, Bulk operations < 30 seconds
- **Achievable:** Standard admin interface
- **Relevant:** Keep room data accurate
- **Time-bound:** Complete ภายใน Sprint 7

**Acceptance Criteria:**
```gherkin
Feature: Room Management
  Scenario: Add New Room
    Given I am an administrator
    When I click "Add Room"
    And I enter room details:
      | Field | Value |
      | Name | Conference Room A |
      | Capacity | 20 |
      | Floor | 5 |
      | Equipment | Projector, Whiteboard |
    And I upload room photos
    And I click "Create"
    Then Room should be added to system
    And Room should be available for booking
    And Search index should be updated

  Scenario: Temporary Close Room
    Given A room needs maintenance
    When I set room status to "Maintenance"
    And I set period "2024-04-01 to 2024-04-03"
    Then Room should be unavailable for booking
    And Existing bookings should be notified
    And Alternative rooms should be suggested

  Scenario: Bulk Import
    Given I have Excel file with 50 rooms
    When I upload the file
    And I map columns to fields
    And I click "Import"
    Then All rooms should be imported
    And Validation errors should be shown
    And Success count should be displayed
```

**Room Attributes:**
- Basic: Name, capacity, floor, building
- Equipment: List of available equipment
- Features: Windows, air conditioning, accessibility
- Photos: Multiple images
- Status: Available, Maintenance, Retired
- Rules: Min/max duration, advance booking limit

**Dependencies:** File upload service, Image storage

---

#### REQ-F008: Access Control and Permissions ✓

**Description:** ระบบต้องควบคุมสิทธิ์การเข้าถึงตามบทบาทของผู้ใช้ (RBAC)

**Category:** Security  
**Priority:** High  
**Requirement Type:** Functional  
**Source:** Security Requirements  
**Rationale:** ป้องกันการเข้าถึงข้อมูลโดยไม่ได้รับอนุญาต

**SMART Criteria:**
- **Specific:** Role-based permissions with inheritance
- **Measurable:** Permission check < 100ms, 100% accuracy
- **Achievable:** ใช้ proven RBAC patterns
- **Relevant:** Ensure data security
- **Time-bound:** Complete ภายใน Sprint 3

**Acceptance Criteria:**
```gherkin
Feature: Access Control
  Scenario: Role-based Access
    Given I am a regular employee
    When I try to access admin panel
    Then I should see "Access Denied"
    And I should be redirected to dashboard
    And Attempt should be logged

  Scenario: Permission Inheritance
    Given Manager role includes Employee permissions
    When I am assigned Manager role
    Then I should have all Employee permissions
    And I should have additional Manager permissions
    And Permissions should be real-time

  Scenario: Dynamic Permission
    Given Admin grants me "View All Bookings"
    When I access booking reports
    Then I should see all department bookings
    And Permission should be audited
    And Can be revoked anytime
```

**Role Hierarchy:**
```
Super Admin
    ├── Admin
    │   ├── Manage Rooms
    │   ├── Manage Users
    │   └── View All Reports
    ├── Manager
    │   ├── Override Bookings
    │   ├── View Team Reports
    │   └── Employee Permissions
    └── Employee
        ├── Create Booking
        ├── View Own Bookings
        └── Update Profile
```

**Permission Matrix:**
| Action | Employee | Manager | Admin | Super Admin |
|--------|----------|---------|-------|-------------|
| Book Room | ✓ | ✓ | ✓ | ✓ |
| View Own Bookings | ✓ | ✓ | ✓ | ✓ |
| View Team Bookings | ✗ | ✓ | ✓ | ✓ |
| Override Booking | ✗ | ✓ | ✓ | ✓ |
| Manage Rooms | ✗ | ✗ | ✓ | ✓ |
| Manage Users | ✗ | ✗ | ✓ | ✓ |
| System Config | ✗ | ✗ | ✗ | ✓ |

**Dependencies:** Authentication system, Audit logging

---

#### REQ-F009: Calendar Integration ✓

**Description:** ระบบต้องซิงค์การจองกับ personal calendar ของผู้ใช้

**Category:** Integration  
**Priority:** Low  
**Requirement Type:** Functional  
**Source:** User Requests  
**Rationale:** ลดการจัดการ calendar หลายที่

**SMART Criteria:**
- **Specific:** Two-way sync with Outlook and Google Calendar
- **Measurable:** Sync delay < 5 minutes, Success rate > 95%
- **Achievable:** ใช้ standard calendar APIs
- **Relevant:** Improve user workflow
- **Time-bound:** Complete ภายใน Sprint 10

**Acceptance Criteria:**
```gherkin
Feature: Calendar Sync
  Scenario: Connect Calendar
    Given I want to sync with Outlook
    When I click "Connect Calendar"
    And I authorize with Microsoft
    Then Connection should be established
    And Past bookings should sync
    And Future bookings should sync

  Scenario: Automatic Sync
    Given My calendar is connected
    When I create new booking
    Then Calendar event should be created within 5 minutes
    And Event should include room location
    And Event should have meeting details

  Scenario: Conflict Detection
    Given I have calendar event at 10:00
    When I try to book room at 10:00
    Then System should warn about conflict
    And Show existing calendar event
    And Allow override if needed
```

**Supported Calendars:**
- Microsoft Outlook (Exchange/Office 365)
- Google Calendar
- CalDAV compatible calendars

**Sync Features:**
- Event creation on booking
- Event update on modification
- Event deletion on cancellation
- Conflict warnings
- Optional: Import existing events

**Dependencies:** OAuth implementation, Calendar APIs

---

#### REQ-F010: Mobile Application ✓

**Description:** ระบบต้องมี mobile app สำหรับ iOS และ Android

**Category:** Platform  
**Priority:** Medium  
**Requirement Type:** Functional  
**Source:** Business Strategy  
**Rationale:** รองรับ mobile workforce และ quick bookings

**SMART Criteria:**
- **Specific:** Native mobile apps with core features
- **Measurable:** App size < 50MB, Load time < 3 seconds
- **Achievable:** ใช้ React Native
- **Relevant:** 30% of bookings from mobile
- **Time-bound:** Complete ภายใน Sprint 12

**Acceptance Criteria:**
```gherkin
Feature: Mobile App
  Scenario: Quick Booking
    Given I open mobile app
    When I tap "Quick Book"
    Then I should see nearby available rooms
    And I can book with 2 taps
    And Booking should be confirmed

  Scenario: QR Code Booking
    Given I am at a meeting room
    When I scan QR code on door
    Then Room details should appear
    And I can book instantly
    And Current availability shown

  Scenario: Push Notifications
    Given I enabled notifications
    When My meeting is in 5 minutes
    Then I should receive push notification
    And Tapping should open booking details
    And Show navigation to room
```

**Mobile Features:**
- Quick booking
- QR code scanning
- Push notifications
- Offline viewing
- Biometric authentication
- Room navigation

**Platform Requirements:**
- iOS 12+ (iPhone and iPad)
- Android 8+ (phones and tablets)
- React Native framework
- Code sharing > 80%

**Dependencies:** Mobile app stores, Push notification services

---

#### REQ-F011: Audit Trail and Compliance ✓

**Description:** ระบบต้องบันทึก audit trail สำหรับ compliance และ security

**Category:** Security/Compliance  
**Priority:** High  
**Requirement Type:** Functional  
**Source:** Compliance Requirements  
**Rationale:** ตาม PDPA และ security policy

**SMART Criteria:**
- **Specific:** Log all critical actions with timestamps
- **Measurable:** Zero log loss, Query time < 10 seconds
- **Achievable:** ใช้ structured logging
- **Relevant:** Meet compliance requirements
- **Time-bound:** Complete ภายใน Sprint 9

**Acceptance Criteria:**
```gherkin
Feature: Audit Trail
  Scenario: Action Logging
    Given Any user action occurs
    When Action is completed
    Then Log entry should be created with:
      | Field | Content |
      | Timestamp | ISO 8601 format |
      | User ID | Unique identifier |
      | Action | Specific action type |
      | Resource | Affected resource |
      | IP Address | Client IP |
      | Result | Success/Failure |

  Scenario: Audit Search
    Given I am an auditor
    When I search logs for user "john@company.com"
    And Date range "2024-03-01 to 2024-03-31"
    Then All matching logs should appear
    And I can export to CSV
    And Personal data should be masked

  Scenario: Compliance Report
    Given Monthly compliance check
    When I generate PDPA report
    Then Report should show:
      | Metric | Status |
      | Data access logs | Complete |
      | Permission changes | Tracked |
      | Data retention | Compliant |
      | User consent | Recorded |
```

**Audit Events:**
- Authentication (login, logout, failed attempts)
- Authorization (permission changes)
- Data access (view, create, update, delete)
- Configuration changes
- Bulk operations
- Report generation
- Data exports

**Technical Requirements:**
- Centralized logging (ELK stack or similar)
- Log retention: 2 years
- Log integrity (tamper-proof)
- Real-time alerting for suspicious activities
- SIEM integration ready

**Dependencies:** Logging infrastructure, SIEM system

---

### 3.3 Non-functional Requirements

#### REQ-NF001: Performance Requirements ✓

**Description:** ระบบต้องมีประสิทธิภาพเพียงพอสำหรับการใช้งานจริง

**Category:** Performance  
**Priority:** High  
**Requirement Type:** Non-functional  
**Source:** Performance Analysis  

**Performance Metrics:**

| Operation | Requirement | Target | Max |
|-----------|------------|--------|-----|
| Page Load | Initial load | < 2s | 3s |
| API Response | 95th percentile | < 500ms | 1s |
| Search Results | Full search | < 3s | 5s |
| Booking Creation | End-to-end | < 5s | 8s |
| Report Generation | Standard report | < 30s | 60s |
| Concurrent Users | Normal load | 200 | 500 |
| Transactions/min | Booking operations | 50 | 100 |

**Scalability Requirements:**
- Horizontal scaling for application servers
- Database read replicas for reporting
- CDN for static assets
- Auto-scaling based on load

**Resource Utilization:**
- CPU usage < 70% under normal load
- Memory usage < 80% of allocated
- Database connections < 80% of pool
- Network bandwidth < 50% of capacity

---

#### REQ-NF002: Security Requirements ✓

**Description:** ระบบต้องมีมาตรการรักษาความปลอดภัยที่เข้มงวด

**Category:** Security  
**Priority:** High  
**Requirement Type:** Non-functional  
**Source:** Security Policy v3.0  

**Security Measures:**

1. **Authentication & Authorization**
   - Multi-factor authentication (MFA) optional
   - OAuth 2.0 for third-party integration
   - JWT tokens with 8-hour expiration
   - Refresh token rotation

2. **Data Protection**
   - TLS 1.2+ for all communications
   - AES-256 encryption for sensitive data at rest
   - Column-level encryption for PII
   - Secure key management (HSM or KMS)

3. **Application Security**
   - Input validation on all fields
   - SQL injection prevention (prepared statements)
   - XSS protection (CSP headers)
   - CSRF tokens for state-changing operations
   - Rate limiting per user/IP

4. **Infrastructure Security**
   - Web Application Firewall (WAF)
   - DDoS protection
   - Regular security scanning
   - Penetration testing annually

**Compliance Requirements:**
- OWASP Top 10 mitigation
- PDPA compliance for personal data
- ISO 27001 alignment
- Regular security audits

---

#### REQ-NF003: Usability Requirements ✓

**Description:** ระบบต้องใช้งานง่ายและเป็นมิตรกับผู้ใช้ทุกระดับ

**Category:** Usability  
**Priority:** Medium  
**Requirement Type:** Non-functional  
**Source:** UX Research  

**Usability Metrics:**

| Metric | Target | Measurement |
|--------|--------|-------------|
| Learning Time | < 10 minutes | Time to first successful booking |
| Task Success Rate | > 95% | Completed bookings/attempts |
| Error Rate | < 5% | Errors per session |
| User Satisfaction | > 4.5/5 | Post-booking survey |
| Task Efficiency | < 5 clicks | Clicks to complete booking |

**Accessibility Requirements:**
- WCAG 2.1 Level AA compliance
- Screen reader compatibility (JAWS, NVDA)
- Keyboard navigation for all functions
- High contrast mode
- Font size adjustment (100-200%)
- Alternative text for images
- Captions for videos

**User Interface Standards:**
- Consistent design language
- Clear error messages with solutions
- Contextual help and tooltips
- Progressive disclosure
- Mobile-first responsive design
- Support Thai and English languages

---

#### REQ-NF004: Reliability Requirements ✓

**Description:** ระบบต้องมีความเสถียรและพร้อมใช้งานตลอดเวลา

**Category:** Reliability  
**Priority:** High  
**Requirement Type:** Non-functional  
**Source:** SLA Requirements  

**Availability Targets:**

| Metric | Requirement | Annual Downtime |
|--------|-------------|-----------------|
| System Uptime | 99.5% | < 44 hours |
| Core Functions | 99.9% | < 9 hours |
| Planned Maintenance | < 4 hrs/month | < 48 hours |
| Recovery Time (RTO) | < 4 hours | N/A |
| Recovery Point (RPO) | < 1 hour | N/A |

**Fault Tolerance:**
- Redundant servers (N+1)
- Database replication (master-slave)
- Automatic failover
- Circuit breaker pattern
- Graceful degradation
- Retry with exponential backoff

**Backup & Recovery:**
- Daily automated backups
- Point-in-time recovery
- Backup retention: 30 days
- Monthly DR drills
- Geo-redundant backup storage

---

#### REQ-NF005: Maintainability Requirements ✓

**Description:** ระบบต้องง่ายต่อการบำรุงรักษาและพัฒนาต่อ

**Category:** Maintainability  
**Priority:** Medium  
**Requirement Type:** Non-functional  
**Source:** Development Best Practices  

**Code Quality Metrics:**
- Code coverage > 80%
- Cyclomatic complexity < 10
- Technical debt ratio < 5%
- Documentation coverage > 90%

**Maintainability Practices:**
- Modular architecture
- Microservices design
- API versioning
- Comprehensive logging
- Monitoring and alerting
- Automated deployment (CI/CD)
- Infrastructure as Code
- Container orchestration

**Documentation Requirements:**
- API documentation (OpenAPI/Swagger)
- Code documentation (JSDoc)
- Architecture diagrams
- Deployment guides
- Troubleshooting guides
- Change logs

---

## 4. Use Cases and Scenarios

### 4.1 Use Case Diagram

```
┌─────────────────────────────────────────────────────────────────┐
│                      MeetingRoom Pro System                      │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   ┌─────────────┐         ┌─────────────┐    ┌──────────────┐ │
│   │   Register  │         │    Login    │    │View Available│ │
│   │   Account   │         │             │    │    Rooms     │ │
│   └──────┬──────┘         └──────┬──────┘    └──────┬───────┘ │
│          │                        │                   │         │
│          │      ┌─────────────────┴────────┐         │         │
│          └─────►│     Authenticate User    │◄────────┘         │
│                 └─────────────┬────────────┘                   │
│                               │                                 │
│  ┌────────────────────────────┼──────────────────────────────┐ │
│  │                            │                              │ │
│  │  ┌──────────────┐    ┌────▼─────┐    ┌──────────────┐   │ │
│  │  │Search Rooms  │───►│   Book    │───►│Send          │   │ │
│  │  │by Criteria   │    │   Room    │    │Confirmation  │   │ │
│  │  └──────────────┘    └───────────┘    └──────────────┘   │ │
│  │                                                           │ │
│  │  ┌──────────────┐    ┌───────────┐    ┌──────────────┐   │ │
│  │  │View Bookings │───►│  Modify   │───►│   Cancel     │   │ │
│  │  │              │    │  Booking  │    │   Booking    │   │ │
│  │  └──────────────┘    └───────────┘    └──────────────┘   │ │
│  │                                                           │ │
│  └───────────────────────────────────────────────────────────┘ │
│                                                                 │
│  Employee ──────────────────────────────────────────────────    │
│     👤                                                          │
│                                                                 │
│  Manager ───┬───────────────────────────────────────────────    │
│     👤      │                                                   │
│             │  ┌──────────────┐    ┌──────────────┐            │
│             └─►│View Team     │───►│  Override    │            │
│                │Reports       │    │  Bookings    │            │
│                └──────────────┘    └──────────────┘            │
│                                                                 │
│  Admin ─────┬───────────────────────────────────────────────    │
│     👤      │                                                   │
│             │  ┌──────────────┐    ┌──────────────┐            │
│             ├─►│Manage Rooms  │    │Manage Users  │            │
│             │  └──────────────┘    └──────────────┘            │
│             │  ┌──────────────┐    ┌──────────────┐            │
│             └─►│View System   │    │  Configure   │            │
│                │Reports       │    │  System      │            │
│                └──────────────┘    └──────────────┘            │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 4.2 Detailed Use Cases

#### UC-001: Book Meeting Room

**Use Case Name:** Book Meeting Room  
**ID:** UC-001  
**Priority:** High  
**Actor:** Employee, Manager  
**Description:** ผู้ใช้ต้องการจองห้องประชุมสำหรับการประชุมในอนาคต

**Preconditions:**
- ผู้ใช้ login เข้าระบบแล้ว
- มีห้องประชุมว่างในระบบ

**Basic Flow:**
1. ผู้ใช้เลือก "Book Room" จากเมนูหลัก
2. ระบบแสดงหน้า search พร้อม calendar view
3. ผู้ใช้เลือกวันที่และเวลาที่ต้องการ
4. ระบบแสดงรายการห้องที่ว่าง
5. ผู้ใช้เลือกห้องที่ต้องการ
6. ผู้ใช้กรอกรายละเอียดการประชุม:
   - Meeting title (required)
   - Number of attendees
   - Equipment needed
   - Description (optional)
7. ผู้ใช้คลิก "Confirm Booking"
8. ระบบตรวจสอบความพร้อมของห้องอีกครั้ง
9. ระบบบันทึกการจองและสร้าง booking ID
10. ระบบแสดงหน้า confirmation
11. ระบบส่ง email confirmation

**Alternative Flows:**

**4a. ไม่มีห้องว่างในช่วงเวลาที่เลือก:**
1. ระบบแสดงข้อความ "No rooms available"
2. ระบบแนะนำช่วงเวลาอื่นที่ใกล้เคียง
3. ผู้ใช้เลือกเวลาใหม่หรือยกเลิก

**8a. ห้องถูกจองในระหว่างการกรอกข้อมูล:**
1. ระบบแสดง error "Room no longer available"
2. ระบบแสดงห้องอื่นที่ว่าง
3. ผู้ใช้เลือกห้องใหม่

**Postconditions:**
- การจองถูกบันทึกในระบบ
- ห้องถูก block ในช่วงเวลาที่จอง
- ผู้ใช้ได้รับ confirmation email

**Business Rules:**
- จองได้ล่วงหน้าสูงสุด 90 วัน
- จองได้ขั้นต่ำ 30 นาที สูงสุด 8 ชั่วโมง
- ต้องจองล่วงหน้าอย่างน้อย 15 นาที

---

#### UC-002: Search Available Rooms

**Use Case Name:** Search Available Rooms  
**ID:** UC-002  
**Priority:** High  
**Actor:** All Users  
**Description:** ผู้ใช้ค้นหาห้องประชุมที่ว่างตามเงื่อนไขที่ต้องการ

**Preconditions:**
- ผู้ใช้ login เข้าระบบแล้ว

**Basic Flow:**
1. ผู้ใช้เลือก "Search Rooms"
2. ระบบแสดงหน้า search form
3. ผู้ใช้กรอกเงื่อนไขการค้นหา:
   - Date and time (required)
   - Capacity (optional)
   - Floor/Building (optional)
   - Equipment (optional)
4. ผู้ใช้คลิก "Search"
5. ระบบค้นหาห้องที่ตรงเงื่อนไข
6. ระบบแสดงผลการค้นหาพร้อม:
   - Room name and photo
   - Capacity
   - Available equipment
   - Location (floor, building)
7. ผู้ใช้เลือกดูรายละเอียดห้อง

**Alternative Flows:**

**6a. ไม่พบห้องที่ตรงเงื่อนไข:**
1. ระบบแสดง "No rooms match your criteria"
2. ระบบแนะนำให้ปรับเงื่อนไข
3. ระบบแสดงห้องที่ใกล้เคียงที่สุด

**Special Requirements:**
- ผลการค้นหาต้องแสดงภายใน 3 วินาที
- รองรับการ filter แบบ real-time
- แสดงสถานะห้องแบบ real-time

---

#### UC-003: Modify Booking

**Use Case Name:** Modify Booking  
**ID:** UC-003  
**Priority:** Medium  
**Actor:** Booking Owner, Manager  
**Description:** ผู้ใช้ต้องการแก้ไขการจองที่มีอยู่

**Preconditions:**
- มีการจองที่ active อยู่
- เวลาการจองอยู่ในอนาคต > 2 ชั่วโมง

**Basic Flow:**
1. ผู้ใช้เข้า "My Bookings"
2. ระบบแสดงรายการการจองที่ active
3. ผู้ใช้เลือก booking ที่ต้องการแก้ไข
4. ผู้ใช้คลิก "Modify"
5. ระบบแสดง form พร้อมข้อมูลเดิม
6. ผู้ใช้แก้ไขข้อมูล:
   - Time (check availability)
   - Room (if changing)
   - Attendees
   - Equipment
7. ผู้ใช้คลิก "Update Booking"
8. ระบบตรวจสอบและอัพเดต
9. ระบบส่ง notification ให้ attendees

**Alternative Flows:**

**6a. เวลาหรือห้องใหม่ไม่ว่าง:**
1. ระบบแสดง conflict message
2. ระบบแนะนำตัวเลือกอื่น
3. ผู้ใช้เลือกตัวเลือกใหม่

**Business Rules:**
- แก้ไขได้จนถึง 2 ชั่วโมงก่อนเวลาประชุม
- Manager สามารถแก้ไขการจองของทีมได้
- การแก้ไขต้องแจ้ง attendees ทุกคน

---

#### UC-004: Cancel Booking

**Use Case Name:** Cancel Booking  
**ID:** UC-004  
**Priority:** Medium  
**Actor:** Booking Owner, Manager, Admin  
**Description:** ผู้ใช้ต้องการยกเลิกการจองห้องประชุม

**Preconditions:**
- มีการจองที่ active
- เวลาการจองอยู่ในอนาคต > 1 ชั่วโมง

**Basic Flow:**
1. ผู้ใช้เข้า "My Bookings"
2. ผู้ใช้เลือก booking ที่ต้องการยกเลิก
3. ผู้ใช้คลิก "Cancel Booking"
4. ระบบแสดง confirmation dialog
5. ผู้ใช้ระบุเหตุผล (optional)
6. ผู้ใช้ยืนยันการยกเลิก
7. ระบบยกเลิกการจอง
8. ระบบส่ง cancellation notice
9. ระบบ release ห้องให้ว่าง

**Alternative Flows:**

**3a. เวลาน้อยกว่า 1 ชั่วโมง:**
1. ระบบแสดง warning
2. ต้องการ manager approval
3. Manager approve/reject

**Business Rules:**
- ยกเลิกได้จนถึง 1 ชั่วโมงก่อนเวลาประชุม
- Late cancellation ต้อง track
- 3 late cancellations = warning

---

#### UC-005: Generate Usage Report

**Use Case Name:** Generate Usage Report  
**ID:** UC-005  
**Priority:** Medium  
**Actor:** Manager, Admin  
**Description:** ผู้ใช้ต้องการดูรายงานการใช้งานห้องประชุม

**Preconditions:**
- ผู้ใช้มีสิทธิ์ดูรายงาน
- มีข้อมูลการจองในระบบ

**Basic Flow:**
1. ผู้ใช้เข้าเมนู "Reports"
2. ผู้ใช้เลือกประเภทรายงาน:
   - Utilization Report
   - Booking Summary
   - Department Usage
3. ผู้ใช้กำหนด parameters:
   - Date range
   - Department (optional)
   - Room/Building (optional)
4. ผู้ใช้คลิก "Generate"
5. ระบบประมวลผลข้อมูล
6. ระบบแสดงรายงานพร้อม charts
7. ผู้ใช้สามารถ:
   - View online
   - Download (PDF/Excel)
   - Schedule regular reports

**Report Contents:**
- Total bookings
- Utilization rate
- Peak hours heatmap
- Popular rooms ranking
- Cancellation statistics
- No-show tracking

---

### 4.3 User Stories

#### Epic 1: Room Booking Experience

**US-001: Quick Room Search**
```
As an employee
I want to quickly find available meeting rooms
So that I can book a room without wasting time

Acceptance Criteria:
- Search results appear within 3 seconds
- Can filter by capacity, equipment, and location
- Shows room photos and amenities
- One-click booking from search results
```

**US-002: Instant Booking**
```
As a frequent user
I want to book my favorite room with minimal clicks
So that I can quickly secure a room for urgent meetings

Acceptance Criteria:
- "Quick Book" option on dashboard
- Remember my preferences
- Book favorite room in 2 clicks
- Show my recent bookings
```

**US-003: Recurring Meetings**
```
As a team leader
I want to book recurring meetings
So that I don't have to book weekly meetings manually

Acceptance Criteria:
- Support daily, weekly, monthly patterns
- Can set end date or number of occurrences
- Can modify single or all occurrences
- Shows all occurrences before confirming
```

#### Epic 2: Mobile Experience

**US-004: Mobile Booking**
```
As a mobile user
I want to book rooms from my phone
So that I can manage bookings while away from desk

Acceptance Criteria:
- Responsive design works on all devices
- Touch-friendly interface
- GPS-based room suggestions
- Works offline (view only)
```

**US-005: QR Code Check-in**
```
As an employee
I want to check-in using QR code
So that I can confirm my attendance quickly

Acceptance Criteria:
- QR code at room entrance
- Scan to check-in
- Extend booking if needed
- Release room if not checked in
```

#### Epic 3: Analytics and Insights

**US-006: Department Analytics**
```
As a department manager
I want to see my team's room usage
So that I can optimize our meeting culture

Acceptance Criteria:
- Department-specific dashboard
- Meeting duration trends
- Busy hours identification
- Cost allocation (if applicable)
```

**US-007: Executive Dashboard**
```
As an executive
I want to see high-level utilization metrics
So that I can make informed facility decisions

Acceptance Criteria:
- Real-time utilization rate
- Trend analysis over time
- Comparative analysis by building/floor
- Predictive analytics for capacity planning
```

---

## 5. System Architecture

### 5.1 Architecture Overview

#### High-Level Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                           Presentation Layer                         │
├─────────────────────┬─────────────────────┬────────────────────────┤
│   Web Application   │   Mobile Apps       │   Admin Dashboard      │
│   (React + Redux)   │   (React Native)    │   (React + D3.js)      │
└─────────────────────┴─────────────────────┴────────────────────────┘
                                    │
                                    ▼
┌─────────────────────────────────────────────────────────────────────┐
│                           API Gateway Layer                          │
├─────────────────────────────────────────────────────────────────────┤
│              Kong/Express Gateway (Rate Limiting, Auth)              │
└─────────────────────────────────────────────────────────────────────┘
                                    │
                                    ▼
┌─────────────────────────────────────────────────────────────────────┐
│                         Business Logic Layer                         │
├──────────────┬──────────────┬──────────────┬───────────────────────┤
│Auth Service  │Booking Service│Notification  │Analytics Service     │
│(Node.js)     │(Node.js)      │Service       │(Python)              │
│              │               │(Node.js)     │                      │
├──────────────┼──────────────┼──────────────┼───────────────────────┤
│User Service  │Room Service   │Report Service│Integration Service   │
│(Node.js)     │(Node.js)      │(Node.js)     │(Node.js)             │
└──────────────┴──────────────┴──────────────┴───────────────────────┘
                                    │
                                    ▼
┌─────────────────────────────────────────────────────────────────────┐
│                           Data Layer                                 │
├────────────────┬────────────────┬─────────────────┬────────────────┤
│  PostgreSQL    │     Redis       │   Elasticsearch │   File Storage │
│  (Primary DB)  │    (Cache)      │    (Search)     │   (AWS S3)     │
└────────────────┴────────────────┴─────────────────┴────────────────┘
                                    │
                                    ▼
┌─────────────────────────────────────────────────────────────────────┐
│                      External Services Layer                         │
├──────────────┬──────────────┬──────────────┬───────────────────────┤
│    LDAP/AD   │Email Service │ SMS Gateway  │ Calendar APIs         │
└──────────────┴──────────────┴──────────────┴───────────────────────┘
```

#### Technology Stack

**Frontend:**
- React 18.x with TypeScript
- Redux Toolkit for state management
- Material-UI or Ant Design
- React Native for mobile
- D3.js/Recharts for analytics

**Backend:**
- Node.js 18.x with Express
- TypeScript for type safety
- Passport.js for authentication
- Socket.io for real-time
- Bull for job queues

**Database:**
- PostgreSQL 14.x (primary)
- Redis 7.x (cache & sessions)
- Elasticsearch 8.x (search)

**Infrastructure:**
- Docker containers
- Kubernetes orchestration
- Nginx reverse proxy
- AWS/Azure cloud hosting

### 5.2 Component Diagram

```
┌─────────────────────────────────────────────────────────────────────┐
│                         Component Architecture                       │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │                    Frontend Components                       │   │
│  ├─────────────────┬──────────────────┬───────────────────────┤   │
│  │  <<component>>  │  <<component>>   │   <<component>>       │   │
│  │  AuthModule     │  BookingModule   │   ReportModule        │   │
│  │  ├─ LoginForm   │  ├─ RoomSearch   │   ├─ Dashboard       │   │
│  │  ├─ Register    │  ├─ BookingForm  │   ├─ Analytics       │   │
│  │  └─ Profile     │  └─ Calendar     │   └─ Export          │   │
│  └─────────────────┴──────────────────┴───────────────────────┘   │
│                              │                                      │
│                              ▼                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │                    Service Components                        │   │
│  ├─────────────────────────────────────────────────────────────┤   │
│  │                                                              │   │
│  │  ┌────────────────┐      ┌────────────────┐                │   │
│  │  │ <<service>>    │      │ <<service>>    │                │   │
│  │  │ AuthService    │      │ BookingService │                │   │
│  │  │                │      │                │                │   │
│  │  │ + login()      │      │ + create()     │                │   │
│  │  │ + logout()     │      │ + update()     │                │   │
│  │  │ + validate()   │      │ + cancel()     │                │   │
│  │  │ + refresh()    │      │ + search()     │                │   │
│  │  └────────────────┘      └────────────────┘                │   │
│  │                                                              │   │
│  │  ┌────────────────┐      ┌────────────────┐                │   │
│  │  │ <<service>>    │      │ <<service>>    │                │   │
│  │  │ RoomService    │      │ NotifyService  │                │   │
│  │  │                │      │                │                │   │
│  │  │ + list()       │      │ + sendEmail()  │                │   │
│  │  │ + getDetails() │      │ + sendSMS()    │                │   │
│  │  │ + checkAvail() │      │ + sendPush()   │                │   │
│  │  └────────────────┘      └────────────────┘                │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                              │                                      │
│                              ▼                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │                    Data Access Layer                         │   │
│  ├─────────────────────────────────────────────────────────────┤   │
│  │  ┌────────────────┐      ┌────────────────┐                │   │
│  │  │ <<repository>> │      │ <<repository>> │                │   │
│  │  │ UserRepository │      │ RoomRepository │                │   │
│  │  │                │      │                │                │   │
│  │  │ + findById()   │      │ + findAvail()  │                │   │
│  │  │ + save()       │      │ + save()       │                │   │
│  │  │ + update()     │      │ + update()     │                │   │
│  │  └────────────────┘      └────────────────┘                │   │
│  └─────────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────────┘
```

### 5.3 Database Design

#### Entity Relationship Diagram

```
┌─────────────────┐         ┌─────────────────┐         ┌─────────────────┐
│     Users       │         │    Bookings     │         │     Rooms       │
├─────────────────┤         ├─────────────────┤         ├─────────────────┤
│ PK user_id      │ 1     * │ PK booking_id   │ *     1 │ PK room_id      │
│    email        ├─────────┤ FK user_id      ├─────────┤    name         │
│    password     │         │ FK room_id      │         │    capacity     │
│    first_name   │         │    start_time   │         │    floor        │
│    last_name    │         │    end_time     │         │    building     │
│    phone        │         │    title        │         │    status       │
│    department   │         │    attendees    │         │    created_at   │
│ FK role_id      │         │    status       │         │    updated_at   │
│    created_at   │         │    created_at   │         └─────────────────┘
│    updated_at   │         │    updated_at   │                 │ 1
└─────────────────┘         └─────────────────┘                 │
         │ *                         │ 1                         │ *
         │                           │                           │
         │ 1                         ▼ *                         ▼
┌─────────────────┐         ┌─────────────────┐         ┌─────────────────┐
│     Roles       │         │  Notifications  │         │RoomEquipment    │
├─────────────────┤         ├─────────────────┤         ├─────────────────┤
│ PK role_id      │         │ PK notif_id     │         │ PK equip_id     │
│    role_name    │         │ FK booking_id   │         │ FK room_id      │
│    permissions  │         │ FK user_id      │         │    type         │
│    created_at   │         │    type         │         │    quantity     │
└─────────────────┘         │    channel      │         │    description  │
                            │    status       │         └─────────────────┘
                            │    sent_at      │
                            └─────────────────┘
```

#### Key Tables Schema

**users table:**
```sql
CREATE TABLE users (
    user_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    email VARCHAR(255) UNIQUE NOT NULL,
    password_hash VARCHAR(255),
    first_name VARCHAR(100) NOT NULL,
    last_name VARCHAR(100) NOT NULL,
    phone VARCHAR(20),
    department VARCHAR(100),
    role_id INTEGER REFERENCES roles(role_id),
    is_active BOOLEAN DEFAULT true,
    last_login TIMESTAMP,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

**rooms table:**
```sql
CREATE TABLE rooms (
    room_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    name VARCHAR(100) NOT NULL,
    capacity INTEGER NOT NULL,
    floor INTEGER,
    building VARCHAR(50),
    description TEXT,
    status VARCHAR(20) DEFAULT 'available',
    amenities JSONB,
    photos TEXT[],
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE INDEX idx_rooms_capacity ON rooms(capacity);
CREATE INDEX idx_rooms_status ON rooms(status);
```

**bookings table:**
```sql
CREATE TABLE bookings (
    booking_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    user_id UUID REFERENCES users(user_id),
    room_id UUID REFERENCES rooms(room_id),
    title VARCHAR(255) NOT NULL,
    description TEXT,
    start_time TIMESTAMP NOT NULL,
    end_time TIMESTAMP NOT NULL,
    attendees INTEGER,
    status VARCHAR(20) DEFAULT 'confirmed',
    recurring_id UUID,
    equipment_request JSONB,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    CONSTRAINT no_overlap EXCLUDE USING gist (
        room_id WITH =,
        tsrange(start_time, end_time) WITH &&
    ) WHERE (status = 'confirmed')
);

CREATE INDEX idx_bookings_user ON bookings(user_id);
CREATE INDEX idx_bookings_room ON bookings(room_id);
CREATE INDEX idx_bookings_time ON bookings(start_time, end_time);
```

---

## 6. Validation and Verification

### 6.1 Test Strategy

#### Testing Levels

**1. Unit Testing**
- Coverage target: 80%+
- Tools: Jest, React Testing Library
- Focus: Business logic, utilities
- Automation: Run on every commit

**2. Integration Testing**
- API endpoint testing
- Database integration
- External service mocking
- Tools: Supertest, Postman

**3. System Testing**
- End-to-end scenarios
- Cross-browser testing
- Performance testing
- Security testing

**4. User Acceptance Testing**
- Beta testing with 20 users
- Feedback collection
- Usability testing
- A/B testing for UI

#### Test Environments

| Environment | Purpose | Data | Access |
|-------------|---------|------|--------|
| Development | Developer testing | Mock data | Developers |
| Testing | QA testing | Test data | QA Team |
| Staging | UAT, Performance | Prod-like | Selected users |
| Production | Live system | Real data | All users |

### 6.2 Acceptance Criteria

#### Functional Acceptance

Each functional requirement must pass:
1. All defined test cases (100%)
2. No critical bugs
3. < 5 minor bugs
4. User story acceptance
5. Cross-browser compatibility

#### Non-functional Acceptance

**Performance:**
- Load time < defined thresholds
- Concurrent user support verified
- Stress test passed (2x normal load)

**Security:**
- Penetration test passed
- OWASP top 10 addressed
- Security audit completed

**Usability:**
- Task success rate > 95%
- User satisfaction > 4.5/5
- Accessibility audit passed

### 6.3 Traceability Matrix

| Requirement | Design | Code Module | Test Case | Status |
|-------------|--------|-------------|-----------|--------|
| REQ-F001 | AUTH-01 | auth.service.ts | TC-001 to TC-010 | ✓ |
| REQ-F002 | SRCH-01 | search.service.ts | TC-011 to TC-020 | ✓ |
| REQ-F003 | BOOK-01 | booking.service.ts | TC-021 to TC-035 | ✓ |
| REQ-F004 | NOTF-01 | notify.service.ts | TC-036 to TC-045 | ✓ |
| REQ-F005 | REPT-01 | report.service.ts | TC-046 to TC-055 | ✓ |
| REQ-F006 | PROF-01 | profile.service.ts | TC-056 to TC-060 | ✓ |
| REQ-F007 | ROOM-01 | room.service.ts | TC-061 to TC-070 | ✓ |
| REQ-F008 | RBAC-01 | rbac.service.ts | TC-071 to TC-080 | ✓ |
| REQ-F009 | CAL-01 | calendar.service.ts | TC-081 to TC-085 | ✓ |
| REQ-F010 | MOB-01 | mobile.app | TC-086 to TC-095 | ✓ |
| REQ-F011 | AUD-01 | audit.service.ts | TC-096 to TC-100 | ✓ |

---

## 7. Project Management

### 7.1 Development Timeline (18 Weeks)

#### Phase 1: Foundation (Weeks 1-4)

**Week 1-2: Project Setup & Planning**
- Team onboarding
- Development environment setup
- Architecture finalization
- Tool selection and setup
- Git repository and CI/CD pipeline

**Week 3-4: Core Infrastructure**
- Database design and setup
- Authentication service (REQ-F001)
- Basic API gateway
- Frontend project scaffolding
- Testing framework setup

**Deliverables:**
- Development environment ready
- Basic auth working
- Database schema implemented
- CI/CD pipeline operational

#### Phase 2: Core Features (Weeks 5-10)

**Week 5-6: Room Management**
- Room service implementation (REQ-F007)
- Search functionality (REQ-F002)
- Room availability algorithm
- Admin room management UI

**Week 7-8: Booking System**
- Booking service (REQ-F003)
- Conflict detection
- Booking UI components
- Real-time updates setup

**Week 9-10: Notifications**
- Notification service (REQ-F004)
- Email integration
- SMS integration
- Notification preferences

**Deliverables:**
- Complete booking flow
- Working notifications
- Search and filter functionality
- Basic admin panel

#### Phase 3: Advanced Features (Weeks 11-14)

**Week 11: Reporting & Analytics**
- Analytics service (REQ-F005)
- Report generation
- Dashboard development
- Data visualization

**Week 12: User Features**
- Profile management (REQ-F006)
- Access control (REQ-F008)
- Calendar integration (REQ-F009)

**Week 13: Mobile Development**
- Mobile app development (REQ-F010)
- Push notifications
- Responsive web optimization

**Week 14: Security & Compliance**
- Security hardening
- Audit trail (REQ-F011)
- Performance optimization
- Load testing

**Deliverables:**
- All features implemented
- Mobile app beta
- Security audit passed
- Performance benchmarks met

#### Phase 4: Testing & Deployment (Weeks 15-18)

**Week 15-16: Testing Phase**
- System integration testing
- User acceptance testing
- Bug fixes and refinements
- Performance tuning

**Week 17: Deployment Preparation**
- Production environment setup
- Data migration planning
- User training materials
- Documentation completion

**Week 18: Go-Live**
- Production deployment
- User training sessions
- Monitoring setup
- Post-launch support

**Deliverables:**
- Production system live
- All tests passed
- Users trained
- Documentation complete

### 7.2 Risk Management

#### Risk Register

| Risk | Probability | Impact | Mitigation | Owner |
|------|-------------|--------|------------|-------|
| LDAP integration delays | Medium | High | Early prototype, have backup auth | Tech Lead |
| Performance issues | Medium | High | Early load testing, scalable architecture | Architect |
| Scope creep | High | Medium | Strict change control, clear requirements | PM |
| Resource availability | Low | High | Cross-training, documentation | PM |
| Third-party service failure | Low | Medium | Multiple providers, fallback options | Tech Lead |
| Security vulnerabilities | Medium | High | Regular audits, security testing | Security Lead |
| User adoption | Medium | Medium | User training, intuitive UI | UX Lead |

#### Risk Response Strategies

**Technical Risks:**
- Proof of concepts for integrations
- Performance testing from week 10
- Security testing throughout
- Redundancy for critical services

**Project Risks:**
- Weekly status meetings
- Clear escalation paths
- Change request process
- Regular stakeholder communication

**Business Risks:**
- Phased rollout option
- User feedback loops
- Training program
- Support desk ready

### 7.3 Resource Planning

#### Team Structure

**Core Team (8 people):**
1. **Project Manager** (1)
   - Overall project coordination
   - Stakeholder management
   - Risk management
   - Schedule tracking

2. **Technical Lead** (1)
   - Architecture decisions
   - Code reviews
   - Technical mentoring
   - Integration oversight

3. **Backend Developers** (2)
   - API development
   - Service implementation
   - Database development
   - Integration coding

4. **Frontend Developers** (2)
   - React development
   - UI implementation
   - Mobile app development
   - User experience

5. **QA Engineer** (1)
   - Test planning
   - Test automation
   - Bug tracking
   - UAT coordination

6. **DevOps Engineer** (1)
   - Infrastructure setup
   - CI/CD pipeline
   - Deployment automation
   - Monitoring setup

**Extended Team:**
- UX Designer (part-time)
- Security Consultant (2 weeks)
- Database Administrator (part-time)
- Business Analyst (first 4 weeks)

#### Resource Allocation

| Phase | PM | Tech Lead | Backend | Frontend | QA | DevOps |
|-------|-----|-----------|---------|----------|-----|---------|
| Phase 1 | 100% | 100% | 100% | 50% | 50% | 100% |
| Phase 2 | 100% | 100% | 100% | 100% | 75% | 50% |
| Phase 3 | 100% | 75% | 100% | 100% | 100% | 50% |
| Phase 4 | 100% | 50% | 50% | 50% | 100% | 100% |

#### Budget Allocation

**Total Budget: 3,000,000 THB**

| Category | Amount (THB) | Percentage |
|----------|-------------|------------|
| Personnel Costs | 1,800,000 | 60% |
| Infrastructure | 450,000 | 15% |
| Software Licenses | 300,000 | 10% |
| Third-party Services | 150,000 | 5% |
| Training & Documentation | 150,000 | 5% |
| Contingency | 150,000 | 5% |

---

## 8. Appendices

### 8.1 Glossary

| Term | Definition |
|------|------------|
| **Active Directory (AD)** | Microsoft's directory service for Windows domain networks |
| **API Gateway** | Single entry point for all client requests to microservices |
| **Booking Window** | Time period during which rooms can be booked in advance |
| **Capacity** | Maximum number of people a room can accommodate |
| **Conflict** | When two bookings overlap for the same resource |
| **Dashboard** | Main screen showing summary information and quick actions |
| **Double Booking** | Error condition where same room is booked twice for same time |
| **Equipment** | Additional resources available in rooms (projector, whiteboard, etc.) |
| **Failover** | Automatic switching to backup system when primary fails |
| **Heat Map** | Visual representation of data using colors to show patterns |
| **Integration** | Connection between MeetingRoom Pro and external systems |
| **JWT** | JSON Web Token used for secure authentication |
| **Load Balancing** | Distributing network traffic across multiple servers |
| **Microservices** | Architecture pattern where app is built as collection of services |
| **No-show** | When booker doesn't use reserved room without canceling |
| **Notification** | Alert sent to users about booking events |
| **OAuth** | Open standard for authorization |
| **Occupancy Rate** | Percentage of time rooms are actually used |
| **Push Notification** | Message sent to mobile device |
| **QR Code** | Quick Response code for scanning |
| **Rate Limiting** | Controlling number of requests user can make |
| **RBAC** | Role-Based Access Control |
| **Real-time** | Immediate update without page refresh |
| **Recurring Booking** | Booking that repeats on schedule |
| **REST** | Representational State Transfer API architecture |
| **SAML** | Security Assertion Markup Language for SSO |
| **Scalability** | Ability to handle increased load |
| **Session** | Period when user is logged in |
| **SSO** | Single Sign-On |
| **Throttling** | Limiting rate of requests |
| **Two-Factor Authentication** | Additional security layer beyond password |
| **Utilization Rate** | How efficiently rooms are being used |
| **WebSocket** | Protocol for real-time bidirectional communication |

### 8.2 Analysis Models

#### State Diagram - Booking Lifecycle

```
     ┌─────────┐
     │  Start  │
     └────┬────┘
          │
          ▼
    ┌──────────┐      Cancel        ┌────────────┐
    │ Creating ├───────────────────►│ Cancelled  │
    └────┬─────┘                    └────────────┘
         │                                 ▲
         │ Save                           │
         ▼                                │
   ┌───────────┐      Cancel             │
   │ Confirmed ├─────────────────────────┘
   └─────┬─────┘                          
         │                                
         │ Start Time                     
         ▼                                
   ┌───────────┐      Check-in      ┌────────────┐
   │  Active   ├───────────────────►│ In Progress│
   └─────┬─────┘                    └─────┬──────┘
         │                                 │
         │ No Check-in                    │ End Time
         ▼                                 ▼
   ┌───────────┐                    ┌────────────┐
   │  No-show  │                    │ Completed  │
   └───────────┘                    └────────────┘
```

#### Sequence Diagram - Booking Flow

```
User          UI           API          Booking       Room         Notification
 │            │            │           Service      Service        Service
 │            │            │              │            │              │
 ├─Search────►│            │              │            │              │
 │            ├─GET /search►              │            │              │
 │            │            ├─checkAvail──►│            │              │
 │            │            │              ├─getStatus─►│              │
 │            │            │              │◄──status───┤              │
 │            │            │◄─available────┤            │              │
 │            │◄───rooms────┤              │            │              │
 │◄──results──┤            │              │            │              │
 │            │            │              │            │              │
 ├─Book Room─►│            │              │            │              │
 │            ├─POST /book─►              │            │              │
 │            │            ├─validate────►│            │              │
 │            │            ├─reserve─────►│            │              │
 │            │            │              ├─lock──────►│              │
 │            │            │              │◄─locked────┤              │
 │            │            ├─create──────►│            │              │
 │            │            │◄─bookingId───┤            │              │
 │            │            ├─notify──────►│            ├─sendEmail───►│
 │            │            │              │            │◄─sent────────┤
 │            │◄─confirmed──┤              │            │              │
 │◄─success───┤            │              │            │              │
 │            │            │              │            │              │
```

#### Data Flow Diagram - Level 1

```
┌─────────────────────────────────────────────────────────────────┐
│                     MeetingRoom Pro System                      │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  External Entities          Processes              Data Stores  │
│                                                                 │
│   ┌────────┐           ┌─────────────┐          ┌────────────┐│
│   │  User  │──Login───►│1.0 Validate │          │   Users    ││
│   │        │◄─Token────│    User     │◄─────────│    DB      ││
│   └────────┘           └─────────────┘          └────────────┘│
│                                │                                │
│   ┌────────┐                  ▼                 ┌────────────┐│
│   │  User  │           ┌─────────────┐          │   Rooms    ││
│   │        │──Search──►│2.0 Search   │◄─────────│    DB      ││
│   │        │◄─Results──│    Rooms    │          └────────────┘│
│   └────────┘           └─────────────┘                         │
│                                │                                │
│   ┌────────┐                  ▼                 ┌────────────┐│
│   │  User  │           ┌─────────────┐          │ Bookings   ││
│   │        │──Book────►│3.0 Create   │─────────►│    DB      ││
│   │        │◄─Confirm──│   Booking   │          └────────────┘│
│   └────────┘           └─────────────┘                         │
│                                │                                │
│   ┌────────┐                  ▼                                │
│   │ Email  │           ┌─────────────┐          ┌────────────┐│
│   │Service │◄─Send─────│4.0 Send     │◄─────────│Notification││
│   │        │           │Notification │          │   Queue    ││
│   └────────┘           └─────────────┘          └────────────┘│
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 8.3 Supporting Information

#### API Documentation Example

**Endpoint: Create Booking**

```http
POST /api/v1/bookings
Authorization: Bearer {jwt_token}
Content-Type: application/json

{
  "room_id": "uuid",
  "title": "Project Review Meeting",
  "start_time": "2024-04-01T10:00:00Z",
  "end_time": "2024-04-01T12:00:00Z",
  "attendees": 8,
  "equipment": ["projector", "whiteboard"],
  "description": "Quarterly project review",
  "recurring": {
    "pattern": "weekly",
    "end_date": "2024-06-30"
  }
}
```

**Response:**

```json
{
  "success": true,
  "data": {
    "booking_id": "uuid",
    "confirmation_code": "BOOK-20240401-001",
    "room": {
      "id": "uuid",
      "name": "Conference Room A",
      "floor": 5,
      "building": "Main"
    },
    "status": "confirmed",
    "created_at": "2024-03-01T08:00:00Z"
  }
}
```

#### Error Codes

| Code | Message | Description |
|------|---------|-------------|
| 400 | Bad Request | Invalid input data |
| 401 | Unauthorized | Invalid or missing token |
| 403 | Forbidden | Insufficient permissions |
| 404 | Not Found | Resource not found |
| 409 | Conflict | Booking conflict |
| 422 | Unprocessable | Business rule violation |
| 429 | Too Many Requests | Rate limit exceeded |
| 500 | Server Error | Internal error |
| 503 | Service Unavailable | System maintenance |

#### Performance Benchmarks

**Load Test Results (Target):**

| Scenario | Users | Response Time | Success Rate |
|----------|-------|---------------|--------------|
| Normal Load | 200 | < 1s | 100% |
| Peak Load | 500 | < 3s | 99.5% |
| Stress Test | 1000 | < 5s | 95% |

**Database Performance:**

| Query Type | Expected Time | Index |
|------------|--------------|--------|
| User lookup | < 10ms | email |
| Room search | < 100ms | capacity, floor |
| Availability check | < 200ms | time range |
| Booking creation | < 500ms | transaction |

#### Security Checklist

- [ ] HTTPS enforced on all endpoints
- [ ] Input validation on all forms
- [ ] SQL injection prevention
- [ ] XSS protection headers
- [ ] CSRF tokens implemented
- [ ] Rate limiting configured
- [ ] Password policy enforced
- [ ] Session timeout implemented
- [ ] Audit logging active
- [ ] Data encryption at rest
- [ ] Secure key management
- [ ] Regular security scans
- [ ] Penetration test passed
- [ ] OWASP compliance verified
- [ ] PDPA compliance checked

---

## Conclusion

This Software Requirements Specification document provides a comprehensive blueprint for developing the MeetingRoom Pro system. With 11 SMART functional requirements, detailed non-functional requirements, complete use cases, and a realistic 18-week implementation timeline, this document serves as the definitive guide for all stakeholders involved in the project.

The system is designed to solve real business problems by reducing booking time by 87%, eliminating double bookings, and increasing room utilization by 30%. By following the specifications outlined in this document, the development team can deliver a robust, scalable, and user-friendly meeting room booking system that meets all stakeholder expectations.

**Document Status:** Complete and Ready for Approval

**Next Steps:**
1. Stakeholder review and approval
2. Development team kickoff
3. Sprint planning based on timeline
4. Begin Phase 1 implementation

---

*End of Document - Version 1.0*