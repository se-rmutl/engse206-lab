# Workshop Guide: User Stories และ Story Mapping
**ENGSE206 - สัปดาห์ที่ 1**

---

## Workshop 1: เขียน User Story ()
### ระบบจองห้องประชุมออนไลน์สำหรับบริษัท

---

## บริบทและสถานการณ์

### บริษัท TechCorp Solutions
**ขนาดบริษัท:** 500 พนักงาน, 3 อาคาร, 45 ห้องประชุม  
**ปัญหาปัจจุบัน:**
- พนักงานต้องเดินไปดูว่าห้องว่างหรือไม่
- มีการจองซ้อนทับกันบ่อย
- ไม่ทราบว่าห้องมีอุปกรณ์อะไรบ้าง
- ไม่สามารถจองล่วงหน้าได้นาน
- ผู้จัดการไม่ทราบสถิติการใช้ห้อง

### ข้อมูลห้องประชุม
**ประเภทห้อง:**
1. **ห้องเล็ก (Small):** 2-4 คน, TV 43", Whiteboard
2. **ห้องกลาง (Medium):** 6-8 คน, Projector, Conference phone, Whiteboard
3. **ห้องใหญ่ (Large):** 10-15 คน, Smart TV 65", Video conference, Sound system
4. **ห้องบอร์ด (Boardroom):** 16-20 คน, Full AV setup, Catering space

**ตำแหน่งห้อง:**
- **อาคาร A:** ชั้น 2-5 (15 ห้อง)
- **อาคาร B:** ชั้น 3-7 (20 ห้อง)  
- **อาคาร C:** ชั้น 1-4 (10 ห้อง)

### ข้อมูลการใช้งาน
**เวลาทำการ:** จันทร์-ศุกร์ 8:00-18:00  
**ช่วงเวลายอดนิยม:** 9:00-11:00, 14:00-16:00  
**ระยะเวลาการจองล่วงหน้า:** สูงสุด 30 วัน  
**นโยบายการยกเลิก:** ต้องยกเลิกก่อน 2 ชั่วโมง

---

## ข้อกำหนดเชิงธุรกิจ

### Business Goals
1. **เพิ่มประสิทธิภาพ:** ลดเวลาการหาห้องประชุม 80%
2. **ลดความขัดแย้ง:** ไม่มีการจองซ้อน
3. **เพิ่มการใช้งาน:** เพิ่ม room utilization rate เป็น 70%
4. **ประหยัดต้นทุน:** ลดการใช้ห้องเปล่า 50%

### Success Metrics
- **Time to book:** < 3 นาที
- **Booking conflicts:** 0%
- **User satisfaction:** > 4.5/5
- **System uptime:** 99.5%

---

## 3 Personas หลัก

### 1. Maya - Office Employee (พนักงานทั่วไป)
**ข้อมูลส่วนตัว:**
- อายุ 28 ปี, Marketing Specialist
- ทำงานมา 2 ปี, มีประชุมเฉลี่ย 3-4 ครั้ง/สัปดาห์
- ใช้โทรศัพท์มือถือเป็นหลัก

**Pain Points:**
- เสียเวลาเดินหาห้องว่าง
- ไม่แน่ใจว่าห้องมีอุปกรณ์ที่ต้องการ
- ลืมยกเลิกการจองเมื่อไม่ใช้

**Goals:**
- จองห้องได้รวดเร็ว
- มั่นใจว่าห้องพร้อมใช้งาน
- ได้รับการแจ้งเตือนที่เหมาะสม

**Tech Savviness:** ปานกลาง (ใช้แอปพื้นฐานได้)

### 2. David - Team Lead (หัวหน้าทีม)
**ข้อมูลส่วนตัว:**
- อายุ 35 ปี, Senior Project Manager
- ทำงานมา 8 ปี, มีประชุมเฉลี่ย 6-8 ครั้ง/สัปดาห์
- ใช้ทั้งคอมพิวเตอร์และมือถือ

**Pain Points:**
- ต้องจองห้องให้ทีมบ่อยๆ
- ต้องการห้องที่มีอุปกรณ์ครบครัน
- ต้องวางแผนประชุมล่วงหน้า

**Goals:**
- จองห้องแบบเป็นซีรีส์ (recurring)
- ดูปฏิทินทีมและห้องพร้อมกัน
- ได้รายงานการใช้ห้องของทีม

**Tech Savviness:** สูง (ใช้เครื่องมือหลากหลาย)

### 3. Sarah - Admin/Facility Manager (ผู้ดูแลสิ่งอำนวยความสะดวก)
**ข้อมูลส่วนตัว:**
- อายุ 42 ปี, Facility Manager
- ทำงานมา 12 ปี, รับผิดชอบห้องประชุมทั้งหมด
- ใช้คอมพิวเตอร์เป็นหลัก

**Pain Points:**
- ไม่ทราบสถิติการใช้ห้อง
- ไม่สามารถจัดการการจองที่ขัดแย้งได้
- ยากต่อการวางแผนการบำรุงรักษา

**Goals:**
- ดูภาพรวมการใช้ห้องทั้งหมด
- สร้างรายงานเพื่อตัดสินใจ
- จัดการข้อมูลห้องและอุปกรณ์

**Tech Savviness:** ปานกลาง (คุ้นเคยกับระบบ office)

---

## กิจกรรม Workshop 1

### ขั้นตอนที่ 1: ทำความเข้าใจ Personas (15 นาที)
**กิจกรรม:**
- แต่ละกลุ่มอ่านข้อมูล personas ทั้ง 3
- อภิปรายเพื่อทำความเข้าใจ pain points และ goals
- ระบุ personas เพิ่มเติมที่อาจมี (เช่น IT Support, Executive)

### ขั้นตอนที่ 2: เขียน User Stories (45 นาที)
**เป้าหมาย:** เขียน 5 user stories สำหรับแต่ละ persona (รวม 15 stories)

**ข้อกำหนด:**
- ใช้รูปแบบ "As a... I want... So that..."
- ปฏิบัติตาม INVEST criteria
- ครอบคลุมทั้ง functional และ non-functional requirements

**แนวทางการคิด:**
1. **Core Functions:** จอง, ดู, ยกเลิก, แก้ไข
2. **Supporting Functions:** ค้นหา, แจ้งเตือน, รายงาน
3. **Administrative Functions:** จัดการห้อง, สิทธิ์ผู้ใช้

### ขั้นตอนที่ 3: สร้าง Acceptance Criteria (30 นาที)
**เป้าหมาย:** เลือก 3 stories ที่สำคัญที่สุดมาเขียน acceptance criteria

**รูปแบบที่ใช้:**
- Given-When-Then format
- อย่างน้อย 3 scenarios ต่อ story
- ครอบคลุม happy path และ edge cases

### ขั้นตอนที่ 4: Story Point Estimation (20 นาที)
**เป้าหมาย:** ประมาณ story points สำหรับ stories ทั้งหมด

**วิธีการ:**
- ใช้ Modified Fibonacci (1, 2, 3, 5, 8, 13, 21)
- Planning Poker แบบง่าย
- เปรียบเทียบ relative complexity

---

## ตัวอย่างผลลัพธ์ที่ถูกต้อง - Workshop 1

### Maya (Office Employee) - User Stories

#### Story 1: Quick Room Search
```
As a busy office employee,
I want to quickly find available meeting rooms for today
So that I can book a room immediately when I need one

Acceptance Criteria:
Given I open the room booking app
When I select "Find rooms now" 
Then I should see all available rooms for the next 2 hours
And the results should show room capacity and basic equipment
And the results should be sorted by proximity to my location

Given I select a specific time slot
When I view available rooms
Then I should see only rooms available for that exact time period
And I should see if there are conflicts with adjacent bookings

Given there are no available rooms
When I search for immediate booking
Then I should see the next available time slots for each room type
And I should have an option to join a waitlist
```

**Story Points:** 5

#### Story 2: Mobile-First Booking
```
As a mobile-first office employee,
I want to book a meeting room using just my smartphone
So that I can reserve spaces while walking between meetings

Acceptance Criteria:
Given I am using the mobile app
When I select a room and time slot
Then I should be able to complete booking in maximum 3 taps
And the interface should be optimized for one-handed use
And I should receive immediate confirmation

Given I have a slow internet connection
When I submit a booking request
Then the app should show a loading indicator
And the request should complete within 10 seconds
And I should get offline confirmation if network fails

Given I need to extend my current meeting
When I am in a booked room 15 minutes before end time
Then I should receive a push notification asking if I need to extend
And I should be able to extend in 15-minute increments if room is available
```

**Story Points:** 8

#### Story 3: Smart Notifications
```
As an office employee who often forgets appointments,
I want to receive smart reminders about my room bookings
So that I don't miss meetings or waste reserved rooms

Acceptance Criteria:
Given I have a room booked
When it's 15 minutes before my meeting time
Then I should receive a push notification reminder
And the notification should include room location and equipment info
And I should have quick actions to "Confirm", "Cancel", or "Extend"

Given I haven't checked into my booked room
When it's 5 minutes after my meeting start time
Then I should receive a "Are you coming?" notification
And the system should automatically release the room if I don't respond within 10 minutes
And other users should be notified that the room is available

Given I regularly book but don't show up
When my no-show rate exceeds 20%
Then I should receive an educational notification about proper booking etiquette
And the system should suggest I reduce booking time or use waitlists
```

**Story Points:** 8

#### Story 4: Equipment Visibility
```
As an office employee planning presentations,
I want to see detailed equipment information for each room
So that I can choose the right room for my meeting needs

Acceptance Criteria:
Given I am browsing available rooms
When I view room details
Then I should see a complete list of available equipment with photos
And I should see equipment status (working, maintenance, unavailable)
And I should see setup instructions for complex equipment

Given I need specific equipment
When I filter rooms by equipment type
Then I should see only rooms that have that equipment available
And I should see equipment booking conflicts (if equipment can be moved)
And I should be able to request additional equipment for my meeting

Given equipment is broken
When I try to book a room with faulty equipment
Then I should see a clear warning about the equipment status
And I should have alternative room suggestions
And I should be able to report additional equipment issues
```

**Story Points:** 5

#### Story 5: Calendar Integration
```
As an office employee using multiple calendar systems,
I want my room bookings to sync with my work calendar
So that I have a unified view of my schedule

Acceptance Criteria:
Given I book a room through the app
When the booking is confirmed
Then the meeting should automatically appear in my Outlook/Google Calendar
And the calendar event should include room location, dial-in info, and equipment list
And attendees should be able to see the room details

Given I create a meeting in my calendar first
When I need to add a room to an existing meeting
Then I should be able to search and book rooms from within the calendar integration
And the room booking should update the calendar event automatically
And conflicts should be prevented at the calendar level

Given I cancel a meeting in my calendar
When the meeting had a room booking
Then I should be prompted to cancel the room reservation as well
And the room should be automatically released if I confirm
And I should have an option to keep the room if others will still meet
```

**Story Points:** 13

### David (Team Lead) - User Stories

#### Story 6: Recurring Meetings
```
As a team lead with regular team meetings,
I want to book recurring room reservations
So that my team has a consistent meeting space

Acceptance Criteria:
Given I am setting up a recurring meeting
When I select repeat options (daily, weekly, monthly)
Then I should be able to book the same room for all instances where available
And I should see which dates have conflicts and need alternative rooms
And I should be able to book different rooms for conflict dates

Given I have a recurring booking established
When I need to modify one instance
Then I should be able to change just that single occurrence
And I should be able to modify all future occurrences
And team members should be notified of any changes

Given my recurring meeting series encounters a room conflict
When someone books over my recurring slot
Then I should be notified immediately of the conflict
And I should receive suggestions for alternative rooms or times
And I should have priority options if I'm a regular booker
```

**Story Points:** 13

#### Story 7: Team Calendar View
```
As a team lead coordinating multiple people,
I want to see my team's schedules and available rooms together
So that I can find optimal meeting times for everyone

Acceptance Criteria:
Given I am planning a team meeting
When I open the team scheduling view
Then I should see availability for all my team members and relevant rooms
And I should see conflicts highlighted in real-time
And I should be able to drag and drop to find optimal time slots

Given I select a potential meeting time
When I view the combined calendar
Then I should see partial availability clearly marked
And I should see room capacity vs. number of attendees
And I should get suggestions for alternative times with better availability

Given I need to schedule an urgent meeting
When I use the "Find next available slot" feature
Then I should see the earliest time when team + room are available
And I should be able to send calendar invites directly from the booking system
And invites should include room details and preparation instructions
```

**Story Points:** 21 (จะต้องแบ่งย่อยเป็น Epic)

#### Story 8: Advanced Filtering
```
As a team lead with specific meeting requirements,
I want to filter rooms by multiple criteria simultaneously
So that I can quickly find the perfect room for specialized meetings

Acceptance Criteria:
Given I am looking for a room for a client presentation
When I set filters for capacity, AV equipment, and building location
Then I should see only rooms meeting all criteria
And results should show room rankings based on how well they match my needs
And I should be able to save filter combinations as presets

Given I have saved filter presets
When I need to book similar meetings in the future
Then I should be able to apply saved filters with one click
And presets should include my preferred booking duration and notification settings
And I should be able to share useful presets with my team

Given no rooms match my exact criteria
When I search with strict filters
Then I should see near-matches with clear indicators of what's missing
And I should get suggestions for alternative times when ideal rooms are available
And I should be able to request equipment or setup changes for near-matches
```

**Story Points:** 8

#### Story 9: Delegation and Permissions
```
As a team lead managing multiple projects,
I want to delegate room booking responsibilities to my team members
So that they can book on behalf of the team while maintaining oversight

Acceptance Criteria:
Given I want to delegate booking permissions
When I assign team members as booking delegates
Then they should be able to book rooms using my booking privileges
And I should receive notifications of all bookings made on my behalf
And I should be able to set limits on delegation (time range, room types, etc.)

Given a team member books on my behalf
When the booking is confirmed
Then the booking should show both their name and mine as the responsible parties
And I should be able to modify or cancel delegated bookings
And the delegate should maintain ability to manage their own bookings

Given I need to revoke delegation privileges
When I remove a team member as a delegate
Then their ability to book on my behalf should be immediately removed
And existing bookings made by them should remain valid
And they should receive notification of the privilege change
```

**Story Points:** 8

#### Story 10: Usage Analytics
```
As a team lead responsible for resource optimization,
I want to see analytics about my team's room usage patterns
So that I can make better decisions about space allocation and meeting efficiency

Acceptance Criteria:
Given I access the team analytics dashboard
When I view our monthly room usage report
Then I should see utilization rates, most-used rooms, and peak booking times
And I should see team member booking patterns and no-show rates
And I should get recommendations for improving booking efficiency

Given I want to optimize our meeting culture
When I review usage analytics
Then I should see average meeting duration vs. booked time
And I should see room capacity utilization (actual attendees vs. room size)
And I should get insights about whether we're over-booking or under-utilizing spaces

Given I need to justify resource requests
When I generate reports for management
Then I should be able to export data showing our team's space needs
And reports should include cost analysis and efficiency metrics
And I should be able to compare our team's usage against company averages
```

**Story Points:** 13

### Sarah (Admin/Facility Manager) - User Stories

#### Story 11: System Administration
```
As a facility manager responsible for room operations,
I want comprehensive administrative controls over the booking system
So that I can maintain optimal resource allocation and resolve conflicts

Acceptance Criteria:
Given I need to manage room information
When I access the admin panel
Then I should be able to add, modify, or remove rooms and their equipment
And I should be able to set room availability schedules and maintenance windows
And changes should be reflected in real-time across all user interfaces

Given there are booking conflicts or emergencies
When I need to override user bookings
Then I should be able to cancel or move bookings with proper justification logging
And affected users should receive immediate notifications with explanations
And I should be able to provide alternative room suggestions

Given I need to manage user access
When I configure user permissions
Then I should be able to set booking limits, advance booking windows, and room access levels
And I should be able to create user groups with different privilege levels
And permission changes should be audit-logged for compliance
```

**Story Points:** 13

#### Story 12: Comprehensive Reporting
```
As a facility manager making strategic decisions,
I want detailed analytics and reporting capabilities
So that I can optimize space utilization and plan future resource needs

Acceptance Criteria:
Given I need to analyze space utilization
When I generate utilization reports
Then I should see detailed metrics by room, time period, and user department
And I should see trends over time with forecasting capabilities
And reports should identify underutilized spaces and peak demand periods

Given I need to prepare budget justifications
When I create financial impact reports
Then I should see cost analysis per room including utilities and maintenance costs
And I should see ROI calculations for the booking system implementation
And I should be able to model scenarios for space reallocation or expansion

Given I need to ensure system health
When I review operational reports
Then I should see system performance metrics, user satisfaction scores, and issue tracking
And I should see data quality metrics and booking accuracy rates
And I should get alerts for unusual patterns or potential system problems
```

**Story Points:** 13

#### Story 13: Maintenance Integration
```
As a facility manager coordinating building maintenance,
I want to integrate maintenance schedules with the room booking system
So that rooms are automatically unavailable during maintenance periods

Acceptance Criteria:
Given I need to schedule room maintenance
When I create maintenance windows in the system
Then affected rooms should be automatically blocked from booking during those periods
And existing bookings should be flagged for relocation with alternative suggestions
And maintenance staff should receive notifications about upcoming scheduled work

Given maintenance issues are reported
When users report equipment problems
Then I should receive immediate notifications with room and equipment details
And the affected equipment should be marked as unavailable in the booking system
And I should be able to escalate urgent issues to appropriate maintenance teams

Given maintenance is completed
When work orders are closed
Then rooms and equipment should be automatically returned to available status
And I should be able to verify functionality before full availability restoration
And users should be notified when previously problematic rooms/equipment are fixed
```

**Story Points:** 8

#### Story 14: Policy Enforcement
```
As a facility manager enforcing company booking policies,
I want automated policy enforcement within the booking system
So that company resources are used fairly and efficiently

Acceptance Criteria:
Given I need to enforce booking limits
When users attempt to exceed their booking allowances
Then the system should prevent over-booking and display clear policy explanations
And I should be able to grant temporary exceptions for special circumstances
And policy violations should be logged for pattern analysis

Given I need to manage no-show policies
When users consistently fail to show up for bookings
Then the system should automatically apply progressive restrictions
And I should be able to review and override automatic penalties when appropriate
And users should receive educational communications about proper booking etiquette

Given I need to ensure equitable access
When popular rooms have high demand
Then the system should enforce fair scheduling policies (maximum advance booking, duration limits)
And I should be able to implement priority systems for critical business meetings
And regular users should have guaranteed access to basic meeting spaces
```

**Story Points:** 13

#### Story 15: Emergency Management
```
As a facility manager handling building emergencies,
I want emergency override capabilities for the booking system
So that I can manage space allocation during crisis situations

Acceptance Criteria:
Given there is a building emergency
When I activate emergency mode
Then I should be able to immediately clear all bookings for affected areas
And I should be able to designate emergency gathering spaces and communication centers
And all users should receive emergency notifications with clear instructions

Given I need to manage evacuation or lockdown procedures
When emergency protocols are activated
Then the system should provide real-time occupancy information for each room
And I should be able to communicate directly with people in specific rooms
And emergency responders should have access to building and occupancy information

Given the emergency is resolved
When I deactivate emergency mode
Then the system should help reschedule displaced meetings
And I should be able to send all-clear communications to affected users
And incident reports should be automatically generated for post-emergency analysis
```

**Story Points:** 21 (Epic - จะต้องแบ่งย่อย)

---

## Non-Functional Requirements Examples

### Performance Requirements
```
Story: System Response Time
As any system user,
I want the booking system to respond quickly to my actions
So that I can complete bookings without frustration

Acceptance Criteria:
- Page loads complete within 2 seconds on standard office internet
- Search results appear within 1 second
- Booking confirmation processes within 3 seconds
- Mobile app responds to taps within 500ms
```

### Security Requirements  
```
Story: Data Protection
As a security-conscious employee,
I want my personal information and booking history to be protected
So that my privacy and company confidentiality are maintained

Acceptance Criteria:
- All data transmissions are encrypted using TLS 1.3
- User sessions expire after 4 hours of inactivity
- Failed login attempts are limited to 5 tries before account lockout
- Audit logs track all booking changes and administrative actions
```

### Usability Requirements
```
Story: Accessibility Compliance
As an employee with visual impairments,
I want the booking system to be fully accessible
So that I can use the system independently and effectively

Acceptance Criteria:
- Interface complies with WCAG 2.1 AA standards
- All functions are keyboard navigable
- Screen reader compatibility is tested and verified
- Color contrast ratios meet accessibility guidelines
```

## Workshop Assessment Criteria

### รูปแบบการประเมิน Workshop

#### Workshop 1: User Stories (40 คะแนน)
**Story Quality (20 คะแนน):**
- ปฏิบัติตาม INVEST criteria (8 คะแนน)
- เน้นคุณค่าของผู้ใช้ชัดเจน (6 คะแนน)
- ใช้ภาษาที่เข้าใจง่าย (6 คะแนน)

**Acceptance Criteria (10 คะแนน):**
- ครอบคลุม happy path และ edge cases (5 คะแนน)
- สามารถทดสอบได้จริง (5 คะแนน)

**Story Point Estimation (10 คะแนน):**
- ความสมเหตุสมผลของการประมาณ (5 คะแนน)
- การใช้ relative estimation อย่างถูกต้อง (5 คะแนน)

---

## สำหรับอาจารย์

### การอำนวยความสะดวก Workshop

**เตรียมการก่อน Workshop:**
- จัดเตรียมวัสดุ: sticky notes, ปากกา, flipchart paper
- ตั้งค่า timer สำหรับแต่ละ activity
- เตรียม template และ example

**ระหว่าง Workshop:**
- หมุนเวียนระหว่างกลุ่มเพื่อให้คำแนะนำ
- ช่วยแก้ไขปัญหาเมื่อกลุ่มติดขัด
- เตือนเวลาและ objectives

**หลัง Workshop:**
- จัด gallery walk ให้กลุ่มดูผลงานของกลุ่มอื่น
- สรุปบทเรียนที่ได้และ best practices
- เก็บผลงานเป็น case study สำหรับครั้งต่อไป

### คำถามสำหรับกระตุ้นการคิด

**สำหรับ User Stories:**
- "ทำไม persona นี้ถึงต้องการฟีเจอร์นี้?"
- "คุณค่าที่แท้จริงของ story นี้คืออะไร?"
- "มี edge case อะไรที่ยังไม่ได้พิจารณา?"

**สำหรับ Story Mapping:**
- "User journey นี้สมจริงไหม?"
- "มีขั้นตอนไหนที่ user อาจจะหยุดใช้งาน?"
- "Release แรกควรมีอะไรบ้างถึงจะใช้งานได้จริง?"

---

## ผลลัพธ์การเรียนรู้ที่คาดหวัง

### สิ่งที่นักศึกษาจะได้รับจาก Workshop

**ทักษะปฏิบัติ:**
- เขียน User Stories ที่มีคุณภาพได้
- ทำ Story Mapping เพื่อวางแผนผลิตภัณฑ์
- ประมาณ Story Points แบบ relative estimation
- ทำงานร่วมกันในการวิเคราะห์ความต้องการ

**ความเข้าใจแนวคิด:**
- ความสำคัญของ user-centered design
- การจัดลำดับความสำคัญตาม business value
- ความแตกต่างระหว่าง features และ user value
- การวางแผน release แบบ incremental

**ประสบการณ์จริง:**
- การทำงานกับ personas และ scenarios ที่ซับซ้อน
- การจัดการกับความต้องการที่ขัดแย้งกัน
- การสื่อสารกับ stakeholders ที่หลากหลาย
- การตัดสินใจภายใต้ข้อจำกัดของเวลาและทรัพยากร

**เตรียมความพร้อมสู่การเรียนต่อ:**
- พื้นฐานสำหรับการเรียน Requirements Analysis (สัปดาห์ 2)
- ความเข้าใจใน user needs สำหรับ Software Design
- ประสบการณ์การทำงานเป็นทีมสำหรับโปรเจคใหญ่
- ทักษะการนำเสนอและการให้เหตุผล
