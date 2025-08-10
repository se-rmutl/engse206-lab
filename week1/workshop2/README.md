# Workshop Guide: User Stories และ Story Mapping
**ENGSE206 - สัปดาห์ที่ 1**

---

## Workshop 2: Story Mapping
### แอปพลิเคชันสั่งอาหารออนไลน์

---

## บริบทและสถานการณ์

### FoodieConnect - แอปสั่งอาหารออนไลน์

**Business Model:**
- เชื่อมต่อลูกค้ากับร้านอาหารท้องถิ่น
- รายได้จากค่าคอมมิชชั่นร้านค้า 15-20%
- ค่าบริการจัดส่ง 25-50 บาท
- Subscription model สำหรับ frequent users

**Target Market:**
- พื้นที่: กรุงเทพและปริมณฑล
- กลุ่มเป้าหมาย: วัยทำงาน 22-45 ปี
- เน้นอาหารไทยและเอเชีย
- รองรับทั้งมื้อเดี่ยวและสั่งหมู่

### Market Context
**คู่แข่งหลัก:** Grab Food, foodpanda, LINE MAN  
**Unique Value Proposition:**
- เน้นร้านอาหารท้องถิ่นและเมนูพิเศษ
- Community-driven reviews และ recommendations
- Flexible delivery options (pickup, delivery, scheduled)
- Better restaurant partner support

### Technical Context
**Platform:** iOS, Android, Web  
**Infrastructure:** Cloud-based, microservices  
**Payment:** Credit/Debit cards, mobile banking, cash  
**Location:** GPS tracking, address validation

---

## ข้อมูลธุรกิจและสถิติ

### การใช้งานปัจจุบัน
**ปริมาณการสั่ง:**
- สูงสุด: 12:00-13:00, 18:00-20:00
- เฉลี่ย: 1,500 orders/วัน
- Peak: 3,000 orders/วัน (วันศุกร์-อาทิตย์)

**ระยะเวลาจัดส่ง:**
- เป้าหมาย: 30-45 นาที
- ปัจจุบัน: 35-50 นาที
- Rush hour: 45-70 นาที

### คู่ค้าร้านอาหาร
**จำนวนร้าน:** 500 ร้าน  
**ประเภทร้าน:**
- ร้านอาหารตามสั่ง (40%)
- ร้านอาหารนั่งทาน (30%)
- ร้านอาหารฟาสต์ฟู้ด (20%)
- ร้านเบเกอรี่/เครื่องดื่ม (10%)

---

## 4 Primary Personas

### 1. Alex - Young Professional (นักศึกษา/พนักงานใหม่)
**Demographics:**
- อายุ 22-28 ปี
- รายได้ 15,000-25,000 บาท/เดือน
- อาศัยใกล้ออฟฟิศ/มหาวิทยาลัย
- ใช้มือถือ 95% ของเวลา

**Behaviors:**
- สั่งอาหาร 8-12 ครั้ง/เดือน
- งบอาหาร 80-150 บาท/มื้อ
- ชอบโปรโมชั่นและส่วนลด
- Share รีวิวบน social media

**Pain Points:**
- งบจำกัด แต่อยากกินของอร่อย
- เวลาจำกัดในการรอ
- ไม่แน่ใจในคุณภาพร้านใหม่
- ค่าจัดส่งที่สูง

**Goals:**
- หาอาหารอร่อยราคาดี
- ประหยัดเวลาและเงิน
- ค้นพบร้านใหม่ๆ
- แชร์ประสบการณ์กับเพื่อน

### 2. Maria - Busy Parent (พ่อแม่วัยทำงาน)
**Demographics:**
- อายุ 32-42 ปี
- รายได้ 40,000-80,000 บาท/เดือน
- มีลูก 1-3 คน
- ใช้ทั้งมือถือและคอมพิวเตอร์

**Behaviors:**
- สั่งอาหาร 15-20 ครั้ง/เดือน
- งบอาหาร 200-500 บาท/มื้อ (สำหรับครอบครัว)
- เน้นความสะดวกและประหยัดเวลา
- วางแผนการสั่งล่วงหน้า

**Pain Points:**
- ต้องหาอาหารที่เด็กชอบ
- เวลาไม่พอในการทำอาหาร
- ต้องการอาหารที่มีคุณภาพและสะอาด
- จัดการคำสั่งซื้อหลายมื้อ

**Goals:**
- ประหยัดเวลาในการเตรียมอาหาร
- หาอาหารที่ทั้งครอบครัวชอบ
- ได้อาหารคุณภาพดีในราคาสมเหตุสมผล
- วางแผนมื้ือประจำวัน

### 3. James - Food Enthusiast (คนรักอาหาร)
**Demographics:**
- อายุ 28-38 ปี
- รายได้ 30,000-60,000 บาท/เดือน
- ชอบลองอาหารใหม่ๆ
- มี social media following เรื่องอาหาร

**Behaviors:**
- สั่งอาหาร 20-25 ครั้ง/เดือน
- งบอาหาร 150-400 บาท/มื้อ
- ชอบลองร้านใหม่และเมนูพิเศษ
- เขียนรีวิวอย่างละเอียด

**Pain Points:**
- ยากที่จะค้นพบร้านใหม่ที่น่าสนใจ
- รีวิวที่มีอยู่ไม่ละเอียดพอ
- ไม่มีระบบแนะนำที่ตรงกับรสนิยม
- ข้อมูลเมนูไม่ครบถ้วน

**Goals:**
- ค้นพบอาหารและร้านใหม่ๆ
- ได้รับการแนะนำที่ตรงกับรสนิยม
- แชร์ประสบการณ์และช่วยเหลือคนอื่น
- สร้างเครือข่ายคนรักอาหาร

### 4. Linda - Senior User (ผู้ใช้วัยผู้ใหญ่)
**Demographics:**
- อายุ 45-60 ปี
- รายได้ 40,000-100,000 บาท/เดือน
- ไม่ค่อยคุ้นเคยกับเทคโนโลยี
- ชอบอาหารคุณภาพและบริการดี

**Behaviors:**
- สั่งอาหาร 5-10 ครั้ง/เดือน
- งบอาหาร 200-600 บาท/มื้อ
- เน้นความมั่นใจและการบริการ
- ชอบสั่งซ้ำจากร้านที่ถูกใจ

**Pain Points:**
- แอปซับซ้อนและยากใช้
- ไม่มั่นใจในการชำระเงินออนไลน์
- ต้องการคำแนะนำจากคนจริง
- กังวลเรื่องความปลอดภัยอาหาร

**Goals:**
- ใช้แอปได้ง่ายและมั่นใจ
- ได้อาหารคุณภาพดีและสะอาด
- มีช่องทางติดต่อเมื่อมีปัญหา
- ความสะดวกในการสั่งซ้ำ

---

## กิจกรรม Workshop 2: Story Mapping

### ขั้นตอนที่ 1: User Journey Overview (20 นาที)

**กิจกรรม:** วาด high-level user journey
**เป้าหมาย:** เข้าใจกระบวนการหลักของการสั่งอาหาร

**Main User Activities (Backbone):**
```
[Discover] → [Browse] → [Select] → [Customize] → [Order] → [Pay] → [Track] → [Receive] → [Review]
```

**คำถามสำหรับการอภิปราย:**
- User เริ่มต้นจากการรู้สึกหิวหรือการวางแผน?
- มีจุดไหนที่ user อาจจะออกจากระบบ?
- แต่ละ persona มี journey ที่แตกต่างกันอย่างไร?

### ขั้นตอนที่ 2: Task Breakdown (30 นาที)

**กิจกรรม:** แบ่งย่อยแต่ละ activity เป็น tasks
**วิธีการ:** ใช้ sticky notes สีต่างกันสำหรับแต่ละ activity

#### Discover Tasks:
- Open app/website
- See personalized recommendations
- Search by cuisine type
- Search by location
- Filter by dietary preferences
- Browse trending restaurants
- Check promotions/deals

#### Browse Tasks:
- View restaurant list
- Read restaurant reviews
- Check delivery time estimates
- View restaurant photos
- Check minimum order amount
- Sort by rating/price/distance
- Save favorite restaurants

#### Select Tasks:
- View restaurant menu
- Read menu item descriptions
- Check item availability
- View nutritional information
- See item photos and reviews
- Compare prices
- Add items to favorites

#### Customize Tasks:
- Select portion size
- Choose spice level
- Add special instructions
- Select add-ons/extras
- Remove ingredients
- Create custom combos
- Save customization preferences

#### Order Tasks:
- Add items to cart
- Review cart contents
- Apply discount codes
- Select delivery address
- Choose delivery time
- Add delivery instructions
- Confirm order details

#### Pay Tasks:
- Select payment method
- Enter payment details
- Apply loyalty points
- Choose tip amount
- Complete payment
- Receive order confirmation
- Get estimated delivery time

#### Track Tasks:
- View order status
- Track delivery driver
- Receive status updates
- Contact driver if needed
- Prepare for delivery
- Rate delivery experience

#### Receive Tasks:
- Confirm delivery
- Check order completeness
- Report missing items
- Contact customer service
- Take delivery photo
- Update delivery preferences

#### Review Tasks:
- Rate overall experience
- Review individual items
- Upload food photos
- Write detailed review
- Tag friends in reviews
- Share on social media
- Suggest improvements

### ขั้นตอนที่ 3: User Story Creation (45 นาที)

**กิจกรรม:** เปลี่ยน tasks เป็น detailed user stories
**เป้าหมาย:** สร้าง comprehensive backlog

**แนวทางการเขียน:**
- เลือก persona ที่เหมาะสมสำหรับแต่ละ story
- เน้น value proposition ที่ชัดเจน
- คำนึงถึง edge cases และ error scenarios
- รวม non-functional requirements

### ขั้นตอนที่ 4: Prioritization และ Release Planning (25 นาที)

**กิจกรรม:** จัดลำดับความสำคัญและวางแผน releases
**เครื่องมือ:** MoSCoW method และ Value vs Effort matrix

**Release Strategy:**
- **MVP (Release 1):** Core ordering functionality
- **Release 2:** Enhanced user experience
- **Release 3:** Advanced features และ personalization

---

## ตัวอย่างผลลัพธ์ที่ถูกต้อง - Workshop 2

### Story Map Structure

#### Level 1: User Activities (Backbone)
```
[Discover] [Browse] [Select] [Customize] [Order] [Pay] [Track] [Receive] [Review]
```

#### Level 2: User Tasks (Walking Skeleton)
```
Discover:
- Open app → Browse restaurants → Select restaurant → Add to cart → Checkout → Pay → Track → Receive → Rate

Browse:
- View list → Filter results → Read reviews → Check delivery time → Select restaurant

Select:  
- View menu → Check prices → Read descriptions → Add items → Customize options

...และอื่นๆ
```

#### Level 3: User Stories (Detailed Requirements)

### MVP Release (Release 1) - Core Functionality

#### Epic 1: Restaurant Discovery

##### Story 1.1: Location-Based Search
```
As Alex, a busy young professional,
I want to find restaurants that deliver to my location
So that I can order food during my short lunch break

Acceptance Criteria:
Given I open the app for the first time
When the app requests location permission
Then I should understand why location is needed and feel safe granting it
And I should see restaurants within delivery range immediately
And restaurants should be sorted by estimated delivery time

Given I want to order to a different address
When I enter a new delivery address
Then I should see restaurants available for that location
And I should be able to save multiple addresses for future use
And the app should validate that the address is deliverable

Story Points: 8
Priority: Must Have
Dependencies: Location services, restaurant database
```

##### Story 1.2: Basic Restaurant Filtering
```
As Maria, a busy parent,
I want to filter restaurants by cuisine type and dietary requirements
So that I can quickly find food that my whole family will enjoy

Acceptance Criteria:
Given I am browsing restaurants
When I apply cuisine filters (Thai, Chinese, Western, etc.)
Then I should see only restaurants serving that cuisine type
And the filter should show the number of available restaurants
And I should be able to apply multiple filters simultaneously

Given my family has dietary restrictions
When I filter by dietary requirements (vegetarian, halal, gluten-free)
Then I should see only restaurants with suitable options
And menu items should be clearly marked with dietary information
And I should be able to save my dietary preferences for future searches

Story Points: 5
Priority: Must Have
Dependencies: Restaurant categorization, menu data structure
```

##### Story 1.3: Restaurant List Display
```
As any hungry user,
I want to see essential restaurant information at a glance
So that I can quickly compare options and make decisions

Acceptance Criteria:
Given I am viewing the restaurant list
When I scroll through available options
Then each restaurant should display: name, cuisine type, rating, delivery time, delivery fee
And I should see attractive food photos that represent the restaurant
And promoted/featured restaurants should be clearly marked as such

Given I want more information about a restaurant
When I tap on a restaurant card
Then I should see expanded details: full description, opening hours, minimum order
And I should see recent customer reviews and photos
And I should be able to view the full menu without losing my place in the list

Story Points: 3
Priority: Must Have
Dependencies: Restaurant data, photo storage, review system
```

#### Epic 2: Menu and Ordering

##### Story 2.1: Menu Navigation
```
As James, a food enthusiast,
I want to easily browse and understand a restaurant's menu
So that I can discover new dishes and make informed choices

Acceptance Criteria:
Given I am viewing a restaurant's menu
When I browse through categories (appetizers, mains, desserts, drinks)
Then each item should show: name, description, price, photo, dietary indicators
And I should see item ratings and review counts from other customers
And popular or recommended items should be highlighted

Given I want detailed information about a dish
When I tap on a menu item
Then I should see full description, ingredients, nutritional info, allergen warnings
And I should see customer photos and reviews for that specific item
And I should see suggested pairings or similar items

Story Points: 8
Priority: Must Have
Dependencies: Menu data structure, photo storage, review system
```

##### Story 2.2: Cart Management
```
As Maria, ordering for my family,
I want to easily manage multiple items in my cart
So that I can organize our family meal efficiently

Acceptance Criteria:
Given I am adding items to my cart
When I select quantity and customizations
Then items should be added with clear pricing breakdown
And I should see running total with taxes and fees
And I should be able to add notes for the entire order

Given I need to modify my cart
When I want to change quantities or remove items
Then I should be able to edit items without going back to the menu
And I should see how changes affect the total price and minimum order requirements
And the cart should save automatically if I leave and return

Story Points: 5
Priority: Must Have
Dependencies: Shopping cart system, pricing calculation
```

##### Story 2.3: Item Customization
```
As Alex, who has specific preferences,
I want to customize menu items to my liking
So that I get exactly what I want without having to call the restaurant

Acceptance Criteria:
Given I am ordering an item with customization options
When I select modifications (spice level, size, add-ons, removals)
Then I should see how each modification affects the price
And I should see which modifications are free vs. paid
And I should be able to save my preferences for future orders

Given the restaurant has special preparation options
When I want to add cooking instructions or special requests
Then I should have a text field for additional notes
And the system should warn me if my request might delay the order
And I should be able to mark certain preferences as "always apply"

Story Points: 8
Priority: Should Have
Dependencies: Menu customization system, pricing engine
```

#### Epic 3: Checkout and Payment

##### Story 3.1: Address Management
```
As Linda, who orders for different occasions,
I want to manage multiple delivery addresses
So that I can easily order to home, office, or other locations

Acceptance Criteria:
Given I am placing an order
When I select delivery address
Then I should see my saved addresses with clear labels (Home, Office, etc.)
And I should be able to add new addresses with address validation
And I should see delivery fees and estimated times for each address

Given I want to set delivery preferences
When I save an address
Then I should be able to add delivery instructions (gate code, floor, landmarks)
And I should be able to set default addresses for different times of day
And I should be able to share addresses with family members

Story Points: 5
Priority: Must Have
Dependencies: Address validation service, user profile system
```

##### Story 3.2: Payment Processing
```
As any user making a purchase,
I want secure and convenient payment options
So that I can complete my order with confidence

Acceptance Criteria:
Given I am ready to pay
When I select payment method
Then I should see all available options (cards, mobile banking, cash, wallet)
And payment should process quickly with clear confirmation
And I should be able to save payment methods for future use

Given I am concerned about security
When I enter payment information
Then I should see clear security indicators and encryption notices
And I should never see my full card numbers in the app after saving
And I should be able to easily remove saved payment methods

Story Points: 13
Priority: Must Have
Dependencies: Payment gateway integration, security compliance
```

##### Story 3.3: Order Confirmation
```
As Maria, coordinating family meals,
I want clear confirmation of my order details
So that I can ensure everything is correct and plan accordingly

Acceptance Criteria:
Given I have completed payment
When my order is confirmed
Then I should receive immediate confirmation with order number and details
And I should see estimated preparation and delivery times
And I should receive confirmation via my preferred communication method

Given I need to track my order
When I view my order confirmation
Then I should see order status and tracking information
And I should have easy access to contact information for the restaurant and delivery
And I should be able to share order details with others who are waiting

Story Points: 3
Priority: Must Have
Dependencies: Order management system, notification system
```

#### Epic 4: Order Tracking

##### Story 4.1: Real-time Order Status
```
As Alex, managing my lunch break timing,
I want real-time updates on my order progress
So that I can plan when to expect delivery and avoid waiting

Acceptance Criteria:
Given I have placed an order
When the restaurant confirms and starts preparing
Then I should receive push notifications at key status changes
And I should see estimated times that update based on actual progress
And I should see if there are any delays with explanations

Given my order is ready for delivery
When the driver picks up my order
Then I should see driver information and contact details
And I should see real-time location tracking on a map
And I should see updated delivery time estimates

Story Points: 13
Priority: Must Have
Dependencies: Real-time tracking system, driver app integration
```

##### Story 4.2: Delivery Communication
```
As Linda, who may not be familiar with delivery apps,
I want clear communication about my delivery
So that I feel confident and prepared for the food arrival

Acceptance Criteria:
Given my order is out for delivery
When the driver is approaching
Then I should receive a notification with arrival time estimate
And I should be able to contact the driver easily if needed
And I should see delivery instructions I provided to help the driver

Given the driver has arrived
When delivery is being completed
Then I should receive notification that delivery is complete
And I should be able to confirm receipt and report any issues immediately
And I should see an option to rate and tip the delivery experience

Story Points: 8
Priority: Must Have
Dependencies: Driver communication system, notification service
```

### Release 2 - Enhanced Experience

#### Epic 5: Personalization

##### Story 5.1: Recommendation Engine
```
As James, always looking for new food experiences,
I want personalized restaurant and dish recommendations
So that I can discover amazing food that matches my taste preferences

Acceptance Criteria:
Given I have order history in the app
When I open the home screen
Then I should see restaurants recommended based on my previous orders
And I should see new dishes similar to ones I've enjoyed
And recommendations should consider time of day and day of week patterns

Given I want to discover new cuisines
When I browse recommendations
Then I should see explanations for why items are recommended to me
And I should be able to indicate if recommendations are helpful
And I should see seasonal or trending items that match my preferences

Story Points: 21 (Epic - requires machine learning implementation)
Priority: Should Have
Dependencies: Order history, ML recommendation system
```

##### Story 5.2: Favorites and Reordering
```
As Maria, with established family preferences,
I want to easily reorder meals we've enjoyed
So that I can quickly handle regular meal planning

Acceptance Criteria:
Given I have ordered before
When I want to reorder a previous meal
Then I should see my order history with easy reorder options
And I should be able to reorder with one tap, with option to modify
And I should see if any items are no longer available with alternatives

Given I have favorite restaurants and dishes
When I mark items as favorites
Then I should have a dedicated favorites section for quick access
And I should be notified when favorite restaurants have promotions
And I should be able to organize favorites into categories (breakfast, lunch, etc.)

Story Points: 8
Priority: Should Have
Dependencies: User profile system, order history storage
```

#### Epic 6: Social Features

##### Story 6.1: Reviews and Ratings
```
As James, who values detailed food reviews,
I want to read and write comprehensive reviews
So that I can make informed decisions and help other food lovers

Acceptance Criteria:
Given I want to review my experience
When I complete an order
Then I should be able to rate the restaurant, individual items, and delivery
And I should be able to upload photos and write detailed reviews
And I should be able to tag specific aspects (taste, portion, packaging, etc.)

Given I am considering an order
When I read reviews from others
Then I should see verified reviews from actual customers
And I should be able to filter reviews by helpful, recent, or similar taste preferences
And I should see aggregate ratings that help me make quick decisions

Story Points: 13
Priority: Should Have
Dependencies: Review system, photo storage, verification system
```

### Release 3 - Advanced Features

#### Epic 7: Loyalty and Gamification

##### Story 7.1: Loyalty Program
```
As Alex, a frequent orderer on a budget,
I want to earn rewards for my regular orders
So that I can save money and feel valued as a loyal customer

Acceptance Criteria:
Given I regularly order through the app
When I complete orders
Then I should earn points based on order value and frequency
And I should see my points balance and how to redeem them
And I should receive bonus points for trying new restaurants or dishes

Given I have accumulated loyalty points
When I want to use my rewards
Then I should be able to apply points for discounts or free items
And I should see exactly how much I'm saving with my loyalty status
And I should get special offers and early access to promotions

Story Points: 13
Priority: Could Have
Dependencies: Loyalty point system, promotion engine
```

### Non-Functional Requirements Stories

#### Performance Requirements
```
Story: App Performance
As any user in a hurry,
I want the app to load and respond quickly
So that I can place orders efficiently without frustration

Acceptance Criteria:
- App launch time under 3 seconds on standard devices
- Restaurant list loads within 2 seconds
- Search results appear within 1 second of typing
- Cart updates instantly when items are added/removed
- Payment processing completes within 10 seconds
```

#### Reliability Requirements
```
Story: System Reliability
As Maria, planning family meals,
I want the app to work consistently when I need it
So that I can rely on it for regular meal planning

Acceptance Criteria:
- App uptime of 99.5% during business hours
- Graceful degradation when services are temporarily unavailable
- Offline mode for browsing previously viewed restaurants
- Automatic retry for failed network requests
- Clear error messages with suggested solutions
```

#### Security Requirements
```
Story: Data Security
As Linda, concerned about online security,
I want my personal and payment information to be protected
So that I can use the app without worry about fraud or privacy breaches

Acceptance Criteria:
- All data transmission encrypted with TLS 1.3
- Payment information processed through PCI-compliant systems
- Personal data stored according to PDPA compliance
- Session timeout after 30 minutes of inactivity
- Two-factor authentication option for account access
```

#### Usability Requirements
```
Story: Accessibility
As Linda, who is not tech-savvy,
I want the app interface to be simple and accessible
So that I can use it confidently without assistance

Acceptance Criteria:
- Interface complies with accessibility guidelines
- Font sizes adjustable for older users
- Voice input option for search
- Simple navigation with clear labels
- Help and tutorial available at any time
```

---

## Release Planning Matrix

### MVP (Release 1) - 8 weeks
**Theme:** Basic Ordering Functionality
**Story Points:** 85-100 points

**Must Have Features:**
- Restaurant discovery and search (20 points)
- Menu browsing and item selection (25 points)  
- Cart management and checkout (20 points)
- Payment processing (15 points)
- Basic order tracking (25 points)

**Success Criteria:**
- Users can complete full order flow
- Payment processing works reliably
- Basic tracking provides confidence
- 90% of core user journeys successful

### Release 2 (Enhancement) - 6 weeks
**Theme:** Improved User Experience
**Story Points:** 65-80 points

**Should Have Features:**
- Personalized recommendations (25 points)
- Favorites and reordering (15 points)
- Enhanced order tracking (15 points)
- Review and rating system (20 points)
- Push notifications (10 points)

**Success Criteria:**
- User retention improves by 30%
- Order frequency increases
- User satisfaction score > 4.0
- Review participation > 40%

### Release 3 (Advanced) - 8 weeks
**Theme:** Engagement and Loyalty
**Story Points:** 80-100 points

**Could Have Features:**
- Loyalty program (25 points)
- Social sharing features (20 points)
- Advanced personalization (30 points)
- Subscription services (25 points)
- Analytics dashboard (15 points)

**Success Criteria:**
- User lifetime value increases
- Social engagement metrics improve
- Premium feature adoption > 15%
- Monthly active users grow 50%

---

## Workshop Assessment Criteria

### รูปแบบการประเมิน Workshop


#### Workshop 2: Story Mapping (40 คะแนน)
**Story Map Structure (15 คะแนน):**
- User journey ที่สมบูรณ์และเป็นตรรกะ (8 คะแนน)
- การแบ่งระดับ activities, tasks, stories ชัดเจน (7 คะแนน)

**Prioritization (15 คะแนน):**
- การจัดลำดับความสำคัญสมเหตุสมผล (8 คะแนน)
- Release planning ที่เป็นไปได้จริง (7 คะแนน)

**Comprehensive Coverage (10 คะแนน):**
- ครอบคลุมทุก personas (5 คะแนน)
- รวม functional และ non-functional requirements (5 คะแนน)

#### การทำงานเป็นทีม (20 คะแนน)
**Collaboration (10 คะแนน):**
- การมีส่วนร่วมของสมาชิกทุกคน (5 คะแนน)
- การสื่อสารและประสานงานที่ดี (5 คะแนน)

**Presentation (10 คะแนน):**
- การนำเสนอที่ชัดเจนและมั่นใจ (5 คะแนน)
- การตอบคำถามและรับข้อเสนอแนะ (5 คะแนน)

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