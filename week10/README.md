# UML Diagram การสอน
## Agent Wallboard Management System Case Study
### ENGSE206: Software Requirements Specification and Design
### มหาวิทยาลัยเทคโนโลยีราชมงคลล้านนา (ดอยสะเก็ด)

---

## หน้า 1: วัตถุประสงค์การเรียนรู้

### 🎯 Learning Objectives
หลังจากเรียนจบบทเรียนนี้ นักศึกษาจะสามารถ:

1. **เข้าใจ** ความหมายและสัญลักษณ์ของ UML Diagram แต่ละประเภท
2. **อธิบาย** หลักการใช้งาน UML Diagram ในแต่ละช่วงของ SDLC
3. **วิเคราะห์** ความเหมาะสมของ Diagram แต่ละประเภทใน C1-C4 Model
4. **สร้าง** UML Diagram สำหรับระบบ Agent Wallboard Management
5. **ประยุกต์ใช้** UML Diagrams ในโครงการจริง

### 📋 Case Study: Agent Wallboard Management System
- ระบบ Real-time monitoring สำหรับ Call Center
- 4 ประเภทผู้ใช้งาน: Agent, Supervisor, Manager, Admin
- Architecture: 3-tier + WebSocket communication
- 13 Use Cases หลัก, 14 User Stories

---

## หน้า 2: ภาพรวม UML 2.5

### 📊 หมวดหมู่ของ UML Diagrams

#### **Structure Diagrams** (แผนภาพโครงสร้าง)
- **Class Diagram** - โครงสร้างและความสัมพันธ์ระหว่าง Classes
- **Component Diagram** - โครงสร้างของ Software Components  
- **Deployment Diagram** - การกระจายระบบบน Hardware
- **Package Diagram** - การจัดกลุ่มและการพึ่งพา

#### **Behavior Diagrams** (แผนภาพพฤติกรรม)
- **Use Case Diagram** - ปฏิสัมพันธ์ระหว่าง Actor และ System
- **Activity Diagram** - กระบวนการทำงานและ Workflow
- **State Machine Diagram** - การเปลี่ยนแปลงสถานะ
- **Sequence Diagram** - ลำดับการสื่อสารระหว่าง Objects

### 🎯 Diagrams ที่จะศึกษาในวันนี้
จะมุ่งเน้น **6 Diagrams หลัก** ที่เหมาะสมกับ Agent Wallboard System

---

## หน้า 3: UML กับ C4 Model Architecture

### 🏗️ การเชื่อมโยง C4 Model กับ UML Diagrams

| **C4 Level** | **UML Diagrams** | **Agent Wallboard ตัวอย่าง** | **เหตุผล** |
|-------------|------------------|------------------------------|------------|
| **C1: Context** | Use Case Diagram | แสดง Actor ทั้ง 4 ประเภทและ System boundary | แสดงขอบเขตระบบให้ Stakeholders เห้าใจ |
| **C2: Container** | Component + Deployment | Desktop App, Web API, Database containers | แสดงการแบ่งส่วนระบบตามเทคโนโลยี |
| **C3: Component** | Package + Class Diagram | โครงสร้าง internal ของ Desktop App | แสดงรายละเอียดการออกแบบ |
| **C4: Code** | Class + Sequence | Implementation classes และ method calls | แสดงรายละเอียดการ implement |

### 💡 หลักการเลือกใช้ Diagram
- **Requirements Phase**: Use Case + Activity (เข้าใจความต้องการ)
- **Analysis Phase**: Class + State Machine (วิเคราะห์ Domain)  
- **Design Phase**: Component + Sequence (ออกแบบโซลูชัน)
- **Implementation**: Deployment + detailed Class (การนำไปใช้)

---

## หน้า 4: Use Case Diagram - ทฤษฎีและสัญลักษณ์

### 🎭 Use Case Diagram คืออะไร?
แผนภาพที่แสดง **ปฏิสัมพันธ์** ระหว่าง **Actors** (ผู้ใช้งาน) กับ **System** (ระบบ)

### 📚 สัญลักษณ์หลักใน Use Case Diagram

#### 1. **Actor (นักแสดง)**
```
สัญลักษณ์: รูปคนหรือสี่เหลี่ยมผืนผ้า
ความหมาย: บุคคลหรือระบบภายนอกที่ใช้งานระบบ
ตัวอย่าง: Agent, Supervisor, Manager, Admin
```

#### 2. **Use Case (กรณีการใช้งาน)**  
```
สัญลักษณ์: วงรี (Oval)
ความหมาย: ฟังก์ชันหรือบริการที่ระบบให้กับ Actor
ตัวอย่าง: "Agent Authentication", "Status Management"
```

#### 3. **System Boundary (ขอบเขตระบบ)**
```
สัญลักษณ์: สี่เหลี่ยมผืนผ้าขนาดใหญ่
ความหมาย: กำหนดขอบเขตของระบบที่กำลังพัฒนา
ข้อควรระวัง: Use Cases อยู่ภายในขอบเขต, Actors อยู่ภายนอก
```

#### 4. **Association (ความสัมพันธ์)**
```
สัญลักษณ์: เส้นตรงเชื่อม Actor กับ Use Case
ความหมาย: Actor สามารถดำเนินการ Use Case นั้นได้
ชื่อ: ไม่จำเป็นต้องใส่ชื่อบนเส้น
```

### 📋 Use Case Relationships

#### 5. **Include Relationship**
```
สัญลักษณ์: เส้นประ + <<include>>
ความหมาย: Use Case หนึ่งรวม Use Case อื่นเสมอ
ตัวอย่าง: "Status Management" include "User Authentication"
```

#### 6. **Extend Relationship**
```
สัญลักษณ์: เส้นประ + <<extend>>
ความหมาย: Use Case หนึ่งขยาย Use Case อื่นเมื่อมีเงื่อนไข
ตัวอย่าง: "Emergency Alert" extend "Status Management"
```

### 🎯 เมื่อไหร่ใช้ Use Case Diagram?
- **C1 Context Level**: แสดงภาพรวมระบบ
- **Requirements Gathering**: สื่อสารกับ Stakeholders
- **Functional Requirements**: ระบุฟังก์ชันหลักของระบบ

---

## หน้า 5: Use Case Diagram - Agent Wallboard System

### 🎭 Use Case Diagram สำหรับ Agent Wallboard

#### **Actors ในระบบ:**
1. **Agent** - เจ้าหน้าที่รับสาย
2. **Supervisor** - หัวหน้าทีมควบคุม
3. **Manager** - ผู้จัดการดูรายงาน
4. **Admin** - ผู้ดูแลระบบ

#### **Use Cases หลัก:**
- **UC-01**: Agent Authentication
- **UC-02**: Status Management  
- **UC-03**: Real-time Monitoring
- **UC-04**: Message Communication
- **UC-05**: Team Performance
- **UC-06**: System Administration

### 📋 Draw.io Code สำหรับ Use Case Diagram

```xml
<mxGraphModel dx="1422" dy="794" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="827" pageHeight="1169">
  <root>
    <mxCell id="0"/>
    <mxCell id="1" parent="0"/>
    
    <!-- System Boundary -->
    <mxCell id="system" value="Agent Wallboard System" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;fontSize=16;fontStyle=1;verticalAlign=top;" vertex="1" parent="1">
      <mxGeometry x="200" y="80" width="400" height="480" as="geometry"/>
    </mxCell>
    
    <!-- Actors -->
    <mxCell id="agent" value="Agent" style="shape=umlActor;verticalLabelPosition=bottom;verticalAlign=top;html=1;outlineConnect=0;" vertex="1" parent="1">
      <mxGeometry x="50" y="150" width="30" height="60" as="geometry"/>
    </mxCell>
    
    <mxCell id="supervisor" value="Supervisor" style="shape=umlActor;verticalLabelPosition=bottom;verticalAlign=top;html=1;outlineConnect=0;" vertex="1" parent="1">
      <mxGeometry x="50" y="280" width="30" height="60" as="geometry"/>
    </mxCell>
    
    <mxCell id="manager" value="Manager" style="shape=umlActor;verticalLabelPosition=bottom;verticalAlign=top;html=1;outlineConnect=0;" vertex="1" parent="1">
      <mxGeometry x="680" y="200" width="30" height="60" as="geometry"/>
    </mxCell>
    
    <mxCell id="admin" value="Admin" style="shape=umlActor;verticalLabelPosition=bottom;verticalAlign=top;html=1;outlineConnect=0;" vertex="1" parent="1">
      <mxGeometry x="680" y="350" width="30" height="60" as="geometry"/>
    </mxCell>
    
    <!-- Use Cases -->
    <mxCell id="uc1" value="Agent&#xa;Authentication" style="ellipse;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="1">
      <mxGeometry x="240" y="120" width="120" height="60" as="geometry"/>
    </mxCell>
    
    <mxCell id="uc2" value="Status&#xa;Management" style="ellipse;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="1">
      <mxGeometry x="240" y="200" width="120" height="60" as="geometry"/>
    </mxCell>
    
    <mxCell id="uc3" value="Real-time&#xa;Monitoring" style="ellipse;whiteSpace=wrap;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;" vertex="1" parent="1">
      <mxGeometry x="420" y="200" width="120" height="60" as="geometry"/>
    </mxCell>
    
    <mxCell id="uc4" value="Message&#xa;Communication" style="ellipse;whiteSpace=wrap;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;" vertex="1" parent="1">
      <mxGeometry x="240" y="300" width="120" height="60" as="geometry"/>
    </mxCell>
    
    <mxCell id="uc5" value="Team&#xa;Performance" style="ellipse;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
      <mxGeometry x="420" y="300" width="120" height="60" as="geometry"/>
    </mxCell>
    
    <mxCell id="uc6" value="System&#xa;Administration" style="ellipse;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="1">
      <mxGeometry x="420" y="400" width="120" height="60" as="geometry"/>
    </mxCell>
    
    <!-- Include Relationship -->
    <mxCell id="include" value="&lt;&lt;include&gt;&gt;" style="endArrow=open;endSize=12;dashed=1;html=1;dashPattern=5 5;" edge="1" parent="1" source="uc2" target="uc1">
      <mxGeometry x="0.1" width="160" relative="1" as="geometry">
        <mxPoint as="offset"/>
      </mxGeometry>
    </mxCell>
    
    <!-- Associations -->
    <mxCell edge="1" parent="1" source="agent" target="uc1">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell edge="1" parent="1" source="agent" target="uc2">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell edge="1" parent="1" source="supervisor" target="uc3">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell edge="1" parent="1" source="supervisor" target="uc4">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell edge="1" parent="1" source="manager" target="uc5">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell edge="1" parent="1" source="admin" target="uc6">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
  </root>
</mxGraphModel>
```

### 💡 สีต่างๆ ในแผนภาพ
- **น้ำเงิน**: Use Cases ของ Agent
- **ม่วง**: Use Cases ของ Supervisor  
- **เหลือง**: Use Cases ของ Manager
- **เขียว**: Use Cases ของ Admin

---

## หน้า 6: Activity Diagram - ทฤษฎีและสัญลักษณ์

### 🔄 Activity Diagram คืออะไร?
แผนภาพที่แสดง **กระบวนการทำงาน** (Workflow) และ **ลำดับขั้นตอน** ของ Business Process หรือ Algorithm

### 📚 สัญลักษณ์หลักใน Activity Diagram

#### 1. **Start State (จุดเริ่มต้น)**
```
สัญลักษณ์: วงกลมทึบสีดำ (●)
ความหมาย: จุดเริ่มต้นของกิจกรรม
ข้อกำหนด: มีได้เพียง 1 จุดต่อ 1 Activity Diagram
```

#### 2. **End State (จุดสิ้นสุด)**
```
สัญลักษณ์: วงกลมทึบสีดำมีวงกลมขาวล้อม (◉)  
ความหมาย: จุดสิ้นสุดของกิจกรรม
ข้อกำหนด: อาจมีหลายจุดได้
```

#### 3. **Activity (กิจกรรม)**
```
สัญลักษณ์: สี่เหลี่ยมมุมโค้ง
ความหมาย: ขั้นตอนหรือกิจกรรมที่ต้องดำเนินการ
ตัวอย่าง: "Agent Login", "Update Status"
```

#### 4. **Decision Diamond (การตัดสินใจ)**
```
สัญลักษณ์: รูปข้าวหลามตัด (◆)
ความหมาย: จุดที่ต้องเลือกเส้นทางต่อไป
เงื่อนไข: ใส่เงื่อนไขบนเส้นลูกศร (Yes/No, True/False)
```

#### 5. **Fork (แยกสาย)**
```
สัญลักษณ์: เส้นตรงหนา (แนวนอนหรือแนวตั้ง)
ความหมาย: แยกกิจกรรมให้ทำพร้อมกัน (Parallel)
ใช้เมื่อ: กิจกรรมสามารถทำพร้อมกันได้
```

#### 6. **Join (รวมสาย)**
```
สัญลักษณ์: เส้นตรงหนา (เหมือน Fork)
ความหมาย: รอให้กิจกรรมทั้งหมดเสร็จก่อนดำเนินต่อ
ใช้เมื่อ: ต้องรอ Parallel activities เสร็จทั้งหมด
```

#### 7. **Swimlane (ช่องทาง)**
```
สัญลักษณ์: เส้นแบ่งพื้นที่แนวตั้งหรือแนวนอน
ความหมาย: แบ่งความรับผิดชอบตาม Actor
ตัวอย่าง: Agent Lane, Supervisor Lane, System Lane
```

### 🎯 เมื่อไหร่ใช้ Activity Diagram?
- **Requirements Phase**: ทำความเข้าใจ Business Process
- **Analysis Phase**: วิเคราะห์ Workflow ที่ซับซ้อน
- **Design Phase**: ออกแบบ Algorithm หรือ Method

---

## หน้า 7: Activity Diagram - Agent Status Management

### 🔄 Activity Diagram สำหรับ Agent Status Change Process

#### **กระบวนการ Agent Status Management:**
1. Agent เข้าสู่ระบบ
2. ตรวจสอบ Current Status
3. เลือก New Status  
4. Validate Status Transition Rules
5. อัปเดต Status ในระบบ
6. แจ้งเตือน Supervisor (พร้อมกัน)
7. บันทึก Status History (พร้อมกัน)

#### **Business Rules:**
- Status transition ต้องถูกต้องตามกฎ (Available → Busy ✓, Offline → Busy ✗)
- การแจ้งเตือนและบันทึกประวัติทำพร้อมกัน

### 📋 Draw.io Code สำหรับ Activity Diagram

```xml
<mxGraphModel dx="1422" dy="794" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="827" pageHeight="1169">
  <root>
    <mxCell id="0"/>
    <mxCell id="1" parent="0"/>
    
    <!-- Swimlanes -->
    <mxCell id="agentLane" value="Agent" style="swimlane;html=1;startSize=30;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="1">
      <mxGeometry x="80" y="40" width="200" height="680" as="geometry"/>
    </mxCell>
    
    <mxCell id="systemLane" value="System" style="swimlane;html=1;startSize=30;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
      <mxGeometry x="280" y="40" width="200" height="680" as="geometry"/>
    </mxCell>
    
    <mxCell id="supervisorLane" value="Supervisor" style="swimlane;html=1;startSize=30;fillColor=#e1d5e7;strokeColor=#9673a6;" vertex="1" parent="1">
      <mxGeometry x="480" y="40" width="200" height="680" as="geometry"/>
    </mxCell>
    
    <!-- Start -->
    <mxCell id="start" value="" style="ellipse;html=1;shape=startState;fillColor=#000000;strokeColor=#000000;" vertex="1" parent="agentLane">
      <mxGeometry x="85" y="50" width="30" height="30" as="geometry"/>
    </mxCell>
    
    <!-- Activities in Agent Lane -->
    <mxCell id="login" value="Agent Login" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="agentLane">
      <mxGeometry x="35" y="100" width="130" height="40" as="geometry"/>
    </mxCell>
    
    <mxCell id="selectStatus" value="Select New Status" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="agentLane">
      <mxGeometry x="35" y="240" width="130" height="40" as="geometry"/>
    </mxCell>
    
    <!-- Activities in System Lane -->
    <mxCell id="checkStatus" value="Check Current&#xa;Status" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="systemLane">
      <mxGeometry x="35" y="170" width="130" height="40" as="geometry"/>
    </mxCell>
    
    <!-- Decision -->
    <mxCell id="validate" value="Valid&#xa;Transition?" style="rhombus;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="systemLane">
      <mxGeometry x="50" y="310" width="100" height="60" as="geometry"/>
    </mxCell>
    
    <mxCell id="updateStatus" value="Update Status&#xa;in Database" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="systemLane">
      <mxGeometry x="35" y="410" width="130" height="40" as="geometry"/>
    </mxCell>
    
    <mxCell id="error" value="Show Error&#xa;Message" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;" vertex="1" parent="systemLane">
      <mxGeometry x="35" y="500" width="130" height="40" as="geometry"/>
    </mxCell>
    
    <!-- Fork -->
    <mxCell id="fork" value="" style="line;html=1;strokeWidth=6;fillColor=#000000;" vertex="1" parent="systemLane">
      <mxGeometry x="50" y="480" width="100" height="10" as="geometry"/>
    </mxCell>
    
    <!-- Parallel Activities -->
    <mxCell id="notifySupervisor" value="Send Notification&#xa;to Supervisor" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;" vertex="1" parent="supervisorLane">
      <mxGeometry x="35" y="520" width="130" height="50" as="geometry"/>
    </mxCell>
    
    <mxCell id="logHistory" value="Log Status&#xa;History" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="systemLane">
      <mxGeometry x="35" y="570" width="130" height="40" as="geometry"/>
    </mxCell>
    
    <!-- Join -->
    <mxCell id="join" value="" style="line;html=1;strokeWidth=6;fillColor=#000000;" vertex="1" parent="systemLane">
      <mxGeometry x="50" y="640" width="100" height="10" as="geometry"/>
    </mxCell>
    
    <!-- End -->
    <mxCell id="end" value="" style="ellipse;html=1;shape=endState;fillColor=#000000;strokeColor=#000000;" vertex="1" parent="systemLane">
      <mxGeometry x="85" y="680" width="30" height="30" as="geometry"/>
    </mxCell>
    
    <!-- Flow Arrows -->
    <mxCell edge="1" parent="1" source="start" target="login">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell edge="1" parent="1" source="login" target="checkStatus">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell edge="1" parent="1" source="checkStatus" target="selectStatus">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell edge="1" parent="1" source="selectStatus" target="validate">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell value="Yes" edge="1" parent="1" source="validate" target="updateStatus">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell value="No" edge="1" parent="1" source="validate" target="error">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell edge="1" parent="1" source="updateStatus" target="fork">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell edge="1" parent="1" source="fork" target="notifySupervisor">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell edge="1" parent="1" source="fork" target="logHistory">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell edge="1" parent="1" source="notifySupervisor" target="join">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell edge="1" parent="1" source="logHistory" target="join">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell edge="1" parent="1" source="join" target="end">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell edge="1" parent="1" source="error" target="selectStatus">
      <mxGeometry relative="1" as="geometry">
        <Array as="points">
          <mxPoint x="180" y="560"/>
          <mxPoint x="180" y="300"/>
        </Array>
      </mxGeometry>
    </mxCell>
  </root>
</mxGraphModel>
```

### 💡 จุดเด่นของแผนภาพนี้
- **Swimlanes**: แบ่งความรับผิดชอบชัดเจน
- **Decision Point**: แสดงการตรวจสอบกฎ Business
- **Fork/Join**: แสดงการทำงานพร้อมกัน
- **Error Handling**: แสดงการจัดการข้อผิดพลาด

---

## หน้า 8: Class Diagram - ทฤษฎีและสัญลักษณ์

### 🏛️ Class Diagram คืออะไร?
แผนภาพที่แสดง **โครงสร้างของ Classes** และ **ความสัมพันธ์** ระหว่างกัน ใช้สำหรับ Object-Oriented Design

### 📚 สัญลักษณ์หลักใน Class Diagram

#### 1. **Class (คลาส)**
```
รูปแบบ: สี่เหลี่ยมผืนผ้าแบ่งเป็น 3 ส่วน
┌─────────────────┐
│   ClassName     │ ← ชื่อ Class
├─────────────────┤
│ - attribute1    │ ← Attributes/Properties
│ + attribute2    │
├─────────────────┤
│ + method1()     │ ← Methods/Operations  
│ - method2()     │
└─────────────────┘
```

#### 2. **Visibility Modifiers (การเข้าถึง)**
```
+ Public    : เข้าถึงได้จากทุกที่
- Private   : เข้าถึงได้เฉพาะใน Class เดียวกัน
# Protected : เข้าถึงได้จาก Class และ Subclass
~ Package  : เข้าถึงได้จาก Package เดียวกัน
```

#### 3. **Data Types (ประเภทข้อมูล)**
```
รูปแบบ: attributeName : dataType
ตัวอย่าง:
- agentCode : String
- isOnline : Boolean  
- loginTime : DateTime
- statusCount : Integer
```

#### 4. **Method Signatures (รูปแบบ Method)**
```
รูปแบบ: methodName(parameter : type) : returnType
ตัวอย่าง:
+ login(agentCode : String) : Boolean
+ changeStatus(newStatus : AgentStatus) : void
+ getStatusHistory() : List<StatusLog>
```

### 🔗 ความสัมพันธ์ระหว่าง Classes (Relationships)

#### 5. **Association (ความสัมพันธ์)**
```
สัญลักษณ์: เส้นตรง
ความหมาย: Classes มีการเชื่อมโยงกัน
ตัวอย่าง: Agent ─── Team (Agent belongs to Team)
Multiplicity: 1, 0..1, 0..*, 1..*
```

#### 6. **Aggregation (การรวมกัน)**  
```
สัญลักษณ์: เส้นตรง + ข้าวหลามตัดขาว ◇─
ความหมาย: "has-a" relationship (Weak ownership)
ตัวอย่าง: Team ◇─── Agent (Team has Agents)
```

#### 7. **Composition (การประกอบ)**
```
สัญลักษณ์: เส้นตรง + ข้าวหลามตัดดำ ◆─
ความหมาย: "part-of" relationship (Strong ownership)
ตัวอย่าง: Agent ◆─── AgentStatus (Status เป็นส่วนหนึ่งของ Agent)
```

#### 8. **Inheritance (การสืบทอด)**
```
สัญลักษณ์: เส้นตรง + สามเหลี่ยมขาว ─△
ความหมาย: "is-a" relationship
ตัวอย่าง: Supervisor ─△ User (Supervisor is a User)
```

#### 9. **Dependency (การพึ่งพา)**
```
สัญลักษณ์: เส้นประ ┄┄►
ความหมาย: Class หนึ่งใช้ Class อื่น (loosely coupled)
ตัวอย่าง: MessageService ┄┄► NotificationAPI
```

### 🎯 เมื่อไหร่ใช้ Class Diagram?
- **C3/C4 Level**: แสดงโครงสร้าง internal ของ Components
- **Design Phase**: ออกแบบ Object-Oriented solution
- **Code Generation**: สร้าง skeleton code จาก diagram

---

## หน้า 9: Class Diagram - Agent Wallboard Domain Model

### 🏛️ Class Diagram สำหรับ Agent Wallboard System

#### **Core Domain Classes:**
- **User**: Base class สำหรับผู้ใช้ทุกประเภท
- **Agent**: Agent ที่รับสาย มี Status management
- **Supervisor**: หัวหน้าทีมที่ดูแล Agents  
- **Team**: กลุ่มของ Agents ที่อยู่ภายใต้ Supervisor
- **AgentStatus**: สถานะของ Agent และ transition rules
- **Message**: ข้อความระหว่าง Supervisor และ Agent
- **StatusLog**: ประวัติการเปลี่ยนสถานะ

### 📋 Draw.io Code สำหรับ Class Diagram

```xml
<mxGraphModel dx="1422" dy="794" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="827" pageHeight="1169">
  <root>
    <mxCell id="0"/>
    <mxCell id="1" parent="0"/>
    
    <!-- User Base Class -->
    <mxCell id="User" value="User&#xa;&#xa;- userId : String&#xa;- username : String&#xa;- email : String&#xa;- createdDate : DateTime&#xa;- isActive : Boolean&#xa;&#xa;+ login(username: String, password: String) : Boolean&#xa;+ logout() : void&#xa;+ updateProfile() : Boolean" style="swimlane;fontStyle=1;align=center;verticalAlign=top;childLayout=stackLayout;horizontal=1;startSize=26;horizontalStack=0;resizeParent=1;resizeParentMax=0;resizeLast=0;collapsible=1;marginBottom=0;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="1">
      <mxGeometry x="320" y="40" width="280" height="180" as="geometry"/>
    </mxCell>
    
    <!-- Agent Class -->
    <mxCell id="Agent" value="Agent&#xa;&#xa;- agentCode : String&#xa;- firstName : String&#xa;- lastName : String&#xa;- extension : String&#xa;- currentStatus : AgentStatus&#xa;- loginTime : DateTime&#xa;- teamId : String&#xa;&#xa;+ changeStatus(newStatus : AgentStatus) : Boolean&#xa;+ getStatusHistory() : List&lt;StatusLog&gt;&#xa;+ receiveMessage(message : Message) : void" style="swimlane;fontStyle=1;align=center;verticalAlign=top;childLayout=stackLayout;horizontal=1;startSize=26;horizontalStack=0;resizeParent=1;resizeParentMax=0;resizeLast=0;collapsible=1;marginBottom=0;fillColor=#e1d5e7;strokeColor=#9673a6;" vertex="1" parent="1">
      <mxGeometry x="80" y="280" width="280" height="200" as="geometry"/>
    </mxCell>
    
    <!-- Supervisor Class -->
    <mxCell id="Supervisor" value="Supervisor&#xa;&#xa;- supervisorId : String&#xa;- departmentCode : String&#xa;- managedTeams : List&lt;Team&gt;&#xa;&#xa;+ monitorAgentStatus() : List&lt;Agent&gt;&#xa;+ sendMessage(agentId : String, message : String) : Boolean&#xa;+ sendBroadcast(message : String) : Boolean&#xa;+ generateTeamReport() : TeamPerformanceReport" style="swimlane;fontStyle=1;align=center;verticalAlign=top;childLayout=stackLayout;horizontal=1;startSize=26;horizontalStack=0;resizeParent=1;resizeParentMax=0;resizeLast=0;collapsible=1;marginBottom=0;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
      <mxGeometry x="560" y="280" width="300" height="180" as="geometry"/>
    </mxCell>
    
    <!-- Team Class -->
    <mxCell id="Team" value="Team&#xa;&#xa;- teamId : String&#xa;- teamName : String&#xa;- supervisorId : String&#xa;- agents : List&lt;Agent&gt;&#xa;- maxCapacity : Integer&#xa;&#xa;+ addAgent(agent : Agent) : Boolean&#xa;+ removeAgent(agentId : String) : Boolean&#xa;+ getTeamStatus() : TeamStatusSummary&#xa;+ calculateUtilization() : Double" style="swimlane;fontStyle=1;align=center;verticalAlign=top;childLayout=stackLayout;horizontal=1;startSize=26;horizontalStack=0;resizeParent=1;resizeParentMax=0;resizeLast=0;collapsible=1;marginBottom=0;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="1">
      <mxGeometry x="80" y="520" width="280" height="180" as="geometry"/>
    </mxCell>
    
    <!-- AgentStatus Enum -->
    <mxCell id="AgentStatus" value="&lt;&lt;enumeration&gt;&gt;&#xa;AgentStatus&#xa;&#xa;+ AVAILABLE&#xa;+ BUSY&#xa;+ BREAK&#xa;+ OFFLINE&#xa;+ MEETING&#xa;+ TRAINING&#xa;&#xa;+ isValidTransition(from : AgentStatus, to : AgentStatus) : Boolean&#xa;+ getTransitionRules() : Map&lt;AgentStatus, List&lt;AgentStatus&gt;&gt;" style="swimlane;fontStyle=1;align=center;verticalAlign=top;childLayout=stackLayout;horizontal=1;startSize=26;horizontalStack=0;resizeParent=1;resizeParentMax=0;resizeLast=0;collapsible=1;marginBottom=0;fillColor=#f8cecc;strokeColor=#b85450;" vertex="1" parent="1">
      <mxGeometry x="400" y="520" width="350" height="180" as="geometry"/>
    </mxCell>
    
    <!-- Message Class -->
    <mxCell id="Message" value="Message&#xa;&#xa;- messageId : String&#xa;- fromUserId : String&#xa;- toUserId : String&#xa;- content : String&#xa;- timestamp : DateTime&#xa;- messageType : MessageType&#xa;- isRead : Boolean&#xa;&#xa;+ markAsRead() : void&#xa;+ formatForDisplay() : String" style="swimlane;fontStyle=1;align=center;verticalAlign=top;childLayout=stackLayout;horizontal=1;startSize=26;horizontalStack=0;resizeParent=1;resizeParentMax=0;resizeLast=0;collapsible=1;marginBottom=0;fillColor=#ffe6cc;strokeColor=#d79b00;" vertex="1" parent="1">
      <mxGeometry x="560" y="520" width="250" height="180" as="geometry"/>
    </mxCell>
    
    <!-- StatusLog Class -->
    <mxCell id="StatusLog" value="StatusLog&#xa;&#xa;- logId : String&#xa;- agentId : String&#xa;- previousStatus : AgentStatus&#xa;- newStatus : AgentStatus&#xa;- changeTimestamp : DateTime&#xa;- duration : Integer&#xa;&#xa;+ calculateDuration() : Integer&#xa;+ toAuditString() : String" style="swimlane;fontStyle=1;align=center;verticalAlign=top;childLayout=stackLayout;horizontal=1;startSize=26;horizontalStack=0;resizeParent=1;resizeParentMax=0;resizeLast=0;collapsible=1;marginBottom=0;fillColor=#e6f7ff;strokeColor=#1890ff;" vertex="1" parent="1">
      <mxGeometry x="80" y="750" width="250" height="160" as="geometry"/>
    </mxCell>
    
    <!-- Inheritance Relationships -->
    <mxCell edge="1" parent="1" source="Agent" target="User">
      <mxGeometry relative="1" as="geometry">
        <mxPoint x="220" y="280" as="sourcePoint"/>
        <mxPoint x="400" y="220" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    <mxCell value="extends" style="endArrow=block;endSize=16;endFill=0;html=1;" edge="1" parent="1">
      <mxGeometry width="160" relative="1" as="geometry">
        <mxPoint x="220" y="280" as="sourcePoint"/>
        <mxPoint x="400" y="220" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    
    <mxCell edge="1" parent="1" source="Supervisor" target="User">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell value="extends" style="endArrow=block;endSize=16;endFill=0;html=1;" edge="1" parent="1">
      <mxGeometry width="160" relative="1" as="geometry">
        <mxPoint x="680" y="280" as="sourcePoint"/>
        <mxPoint x="500" y="220" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    
    <!-- Composition Relationships -->
    <mxCell value="1" style="endArrow=none;html=1;endSize=12;startArrow=diamondThin;startSize=14;startFill=1;edgeStyle=orthogonalEdgeStyle;" edge="1" parent="1" source="Agent" target="AgentStatus">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- Association Relationships -->
    <mxCell value="1..*" style="endArrow=none;html=1;endSize=12;" edge="1" parent="1" source="Agent" target="Team">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell value="1" style="endArrow=none;html=1;endSize=12;" edge="1" parent="1">
      <mxGeometry relative="1" as="geometry">
        <mxPoint x="220" y="520" as="sourcePoint"/>
        <mxPoint x="220" y="480" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    
    <mxCell value="1" style="endArrow=none;html=1;endSize=12;" edge="1" parent="1" source="Team" target="Supervisor">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell value="1..*" style="endArrow=none;html=1;endSize=12;" edge="1" parent="1">
      <mxGeometry relative="1" as="geometry">
        <mxPoint x="560" y="400" as="sourcePoint"/>
        <mxPoint x="360" y="600" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    
    <!-- Dependency for StatusLog -->
    <mxCell value="creates" style="endArrow=open;endSize=12;dashed=1;html=1;dashPattern=5 5;" edge="1" parent="1" source="Agent" target="StatusLog">
      <mxGeometry width="160" relative="1" as="geometry"/>
    </mxCell>
    
    <!-- Association for Message -->
    <mxCell value="sends/receives" style="endArrow=none;html=1;endSize=12;" edge="1" parent="1" source="Supervisor" target="Message">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell value="*" style="endArrow=none;html=1;endSize=12;" edge="1" parent="1">
      <mxGeometry relative="1" as="geometry">
        <mxPoint x="685" y="520" as="sourcePoint"/>
        <mxPoint x="685" y="460" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
  </root>
</mxGraphModel>
```

### 💡 จุดเด่นของ Class Diagram นี้
- **สีต่างๆ**: แยกประเภท Classes ให้เข้าใจง่าย
- **Inheritance**: User เป็น base class ของ Agent และ Supervisor
- **Composition**: Agent มี AgentStatus เป็นส่วนประกอบ
- **Association**: แสดงความสัมพันธ์และ Multiplicity
- **Enumeration**: AgentStatus แสดงค่าคงที่และกฎการเปลี่ยนสถานะ

---

## หน้า 10: Sequence Diagram - ทฤษฎีและสัญลักษณ์

### 📞 Sequence Diagram คืออะไร?
แผนภาพที่แสดง **ลำดับการสื่อสาร** ระหว่าง Objects ในระบบตามช่วงเวลา เหมาะสำหรับ **Dynamic Behavior**

### 📚 สัญลักษณ์หลักใน Sequence Diagram

#### 1. **Actor/Object (ตัวแสดง/วัตถุ)**
```
สัญลักษณ์: สี่เหลี่ยมผืนผ้าที่ด้านบน
รูปแบบ: objectName : ClassName
ตัวอย่าง: agent1 : Agent, :StatusService
```

#### 2. **Lifeline (เส้นชีวิต)**
```
สัญลักษณ์: เส้นประแนวตั้งจาก Object
ความหมาย: แสดงอายุการมีอยู่ของ Object
การใช้งาน: ยาวตามเวลาการทำงาน
```

#### 3. **Activation Box (กล่องการทำงาน)**
```
สัญลักษณ์: สี่เหลี่ยมผืนผ้าบาง ๆ บน Lifeline
ความหมาย: Object กำลังทำงานอยู่
ความกว้าง: แสดงระยะเวลาการทำงาน
```

#### 4. **Message (ข้อความ)**
```
Synchronous Call: เส้นตรง + ลูกศรเต็ม →
Asynchronous Call: เส้นตรง + ลูกศรว่าง ⇾  
Return Message: เส้นประ + ลูกศร ┄►
Self Call: ลูกศรวนรอบตัวเอง ↻
```

#### 5. **Message Types ต่างๆ**
```
Create Message: <<create>> สร้าง Object ใหม่
Destroy Message: ×  ทำลาย Object
Found Message: เส้นจากจุดดำ (จากภายนอกระบบ)
Lost Message: เส้นไปจุดดำ (ไปภายนอกระบบ)
```

#### 6. **Combined Fragments (ส่วนรวม)**
```
alt: Alternative (เลือกเส้นทาง - if/else)
opt: Optional (เงื่อนไข - if)
loop: Loop (การทำซ้ำ - while/for)
par: Parallel (ทำงานพร้อมกัน)
break: Break (หยุดการทำงาน)
```

#### 7. **Guards (เงื่อนไข)**
```
รูปแบบ: [condition]
ตัวอย่าง: [status == AVAILABLE]
ตำแหน่ง: ใส่ข้างหน้าข้อความ
```

### 🎯 เมื่อไหร่ใช้ Sequence Diagram?
- **Design Phase**: ออกแบบ Method calls และ API interactions
- **C4 Level**: แสดงการสื่อสารภายใน Components  
- **Testing**: วิเคราะห์ Test scenarios
- **Documentation**: อธิบาย Complex workflows

---

## หน้า 11: Sequence Diagram - Real-time Status Update

### 📞 Sequence Diagram สำหรับ Real-time Status Update Process

#### **Scenario**: Agent เปลี่ยนสถานะและ Supervisor ได้รับการแจ้งเตือนแบบ Real-time

#### **Objects ที่เกี่ยวข้อง:**
- **agent1 : Agent** - Agent ที่เปลี่ยนสถานะ
- **desktopApp : DesktopApp** - แอปพลิเคชันของ Agent
- **webAPI : WebAPI** - API Server
- **statusService : StatusService** - บริการจัดการสถานะ
- **webSocket : WebSocketService** - บริการ Real-time communication
- **supervisorDashboard : SupervisorDashboard** - Dashboard ของ Supervisor

### 📋 Draw.io Code สำหรับ Sequence Diagram

```xml
<mxGraphModel dx="1422" dy="794" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="827" pageHeight="1169">
  <root>
    <mxCell id="0"/>
    <mxCell id="1" parent="0"/>
    
    <!-- Objects/Actors -->
    <mxCell id="agent" value="agent1 : Agent" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;" vertex="1" parent="1">
      <mxGeometry x="40" y="40" width="120" height="40" as="geometry"/>
    </mxCell>
    
    <mxCell id="desktop" value="desktopApp :&#xa;DesktopApp" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="1">
      <mxGeometry x="200" y="40" width="120" height="40" as="geometry"/>
    </mxCell>
    
    <mxCell id="webapi" value="webAPI :&#xa;WebAPI" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
      <mxGeometry x="360" y="40" width="120" height="40" as="geometry"/>
    </mxCell>
    
    <mxCell id="statusService" value="statusService :&#xa;StatusService" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="1">
      <mxGeometry x="520" y="40" width="120" height="40" as="geometry"/>
    </mxCell>
    
    <mxCell id="websocket" value="webSocket :&#xa;WebSocketService" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;" vertex="1" parent="1">
      <mxGeometry x="680" y="40" width="120" height="40" as="geometry"/>
    </mxCell>
    
    <mxCell id="supervisor" value="supervisorDashboard :&#xa;SupervisorDashboard" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#ffe6cc;strokeColor=#d79b00;" vertex="1" parent="1">
      <mxGeometry x="840" y="40" width="140" height="40" as="geometry"/>
    </mxCell>
    
    <!-- Lifelines -->
    <mxCell id="agentLifeline" value="" style="endArrow=none;dashed=1;html=1;strokeWidth=2;" edge="1" parent="1">
      <mxGeometry width="50" height="50" relative="1" as="geometry">
        <mxPoint x="100" y="80" as="sourcePoint"/>
        <mxPoint x="100" y="700" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    
    <mxCell id="desktopLifeline" value="" style="endArrow=none;dashed=1;html=1;strokeWidth=2;" edge="1" parent="1">
      <mxGeometry width="50" height="50" relative="1" as="geometry">
        <mxPoint x="260" y="80" as="sourcePoint"/>
        <mxPoint x="260" y="700" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    
    <mxCell id="webapiLifeline" value="" style="endArrow=none;dashed=1;html=1;strokeWidth=2;" edge="1" parent="1">
      <mxGeometry width="50" height="50" relative="1" as="geometry">
        <mxPoint x="420" y="80" as="sourcePoint"/>
        <mxPoint x="420" y="700" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    
    <mxCell id="statusLifeline" value="" style="endArrow=none;dashed=1;html=1;strokeWidth=2;" edge="1" parent="1">
      <mxGeometry width="50" height="50" relative="1" as="geometry">
        <mxPoint x="580" y="80" as="sourcePoint"/>
        <mxPoint x="580" y="700" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    
    <mxCell id="websocketLifeline" value="" style="endArrow=none;dashed=1;html=1;strokeWidth=2;" edge="1" parent="1">
      <mxGeometry width="50" height="50" relative="1" as="geometry">
        <mxPoint x="740" y="80" as="sourcePoint"/>
        <mxPoint x="740" y="700" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    
    <mxCell id="supervisorLifeline" value="" style="endArrow=none;dashed=1;html=1;strokeWidth=2;" edge="1" parent="1">
      <mxGeometry width="50" height="50" relative="1" as="geometry">
        <mxPoint x="910" y="80" as="sourcePoint"/>
        <mxPoint x="910" y="700" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    
    <!-- Activation Boxes -->
    <mxCell id="agentActivation" value="" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#000000;" vertex="1" parent="1">
      <mxGeometry x="95" y="120" width="10" height="60" as="geometry"/>
    </mxCell>
    
    <mxCell id="desktopActivation" value="" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#000000;" vertex="1" parent="1">
      <mxGeometry x="255" y="140" width="10" height="400" as="geometry"/>
    </mxCell>
    
    <mxCell id="webapiActivation" value="" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#000000;" vertex="1" parent="1">
      <mxGeometry x="415" y="180" width="10" height="300" as="geometry"/>
    </mxCell>
    
    <mxCell id="statusActivation" value="" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#000000;" vertex="1" parent="1">
      <mxGeometry x="575" y="220" width="10" height="200" as="geometry"/>
    </mxCell>
    
    <mxCell id="websocketActivation" value="" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#000000;" vertex="1" parent="1">
      <mxGeometry x="735" y="380" width="10" height="100" as="geometry"/>
    </mxCell>
    
    <mxCell id="supervisorActivation" value="" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#000000;" vertex="1" parent="1">
      <mxGeometry x="905" y="460" width="10" height="80" as="geometry"/>
    </mxCell>
    
    <!-- Messages -->
    <mxCell value="1: selectNewStatus(BUSY)" style="endArrow=block;html=1;fontColor=#000000;" edge="1" parent="1">
      <mxGeometry width="160" relative="1" as="geometry">
        <mxPoint x="105" y="140" as="sourcePoint"/>
        <mxPoint x="255" y="140" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    
    <mxCell value="2: validateTransition(AVAILABLE, BUSY)" style="endArrow=block;html=1;fontColor=#000000;" edge="1" parent="1">
      <mxGeometry width="160" relative="1" as="geometry">
        <mxPoint x="265" y="180" as="sourcePoint"/>
        <mxPoint x="415" y="180" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    
    <mxCell value="3: updateAgentStatus(agentId, BUSY)" style="endArrow=block;html=1;fontColor=#000000;" edge="1" parent="1">
      <mxGeometry width="160" relative="1" as="geometry">
        <mxPoint x="425" y="220" as="sourcePoint"/>
        <mxPoint x="575" y="220" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    
    <!-- Alt Fragment -->
    <mxCell id="altFrame" value="alt" style="shape=umlFrame;whiteSpace=wrap;html=1;fillColor=#f5f5f5;strokeColor=#666666;" vertex="1" parent="1">
      <mxGeometry x="570" y="250" width="380" height="150" as="geometry"/>
    </mxCell>
    
    <mxCell value="[validation successful]" style="text;html=1;align=center;verticalAlign=middle;resizable=0;points=[];autosize=1;strokeColor=none;fillColor=none;fontColor=#333333;" vertex="1" parent="1">
      <mxGeometry x="580" y="270" width="130" height="30" as="geometry"/>
    </mxCell>
    
    <mxCell value="4: logStatusChange()" style="endArrow=block;html=1;fontColor=#000000;" edge="1" parent="1">
      <mxGeometry width="160" relative="1" as="geometry">
        <mxPoint x="580" y="300" as="sourcePoint"/>
        <mxPoint x="580" y="320" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    
    <mxCell value="5: success" style="endArrow=open;html=1;dashed=1;fontColor=#000000;" edge="1" parent="1">
      <mxGeometry width="160" relative="1" as="geometry">
        <mxPoint x="575" y="340" as="sourcePoint"/>
        <mxPoint x="425" y="340" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    
    <mxCell value="6: broadcastStatusUpdate(agentId, newStatus)" style="endArrow=block;html=1;fontColor=#000000;" edge="1" parent="1">
      <mxGeometry width="160" relative="1" as="geometry">
        <mxPoint x="425" y="380" as="sourcePoint"/>
        <mxPoint x="735" y="380" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    
    <!-- Line separator in alt -->
    <mxCell value="" style="endArrow=none;html=1;strokeWidth=1;" edge="1" parent="1">
      <mxGeometry width="50" height="50" relative="1" as="geometry">
        <mxPoint x="570" y="410" as="sourcePoint"/>
        <mxPoint x="950" y="410" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    
    <mxCell value="[validation failed]" style="text;html=1;align=center;verticalAlign=middle;resizable=0;points=[];autosize=1;strokeColor=none;fillColor=none;fontColor=#333333;" vertex="1" parent="1">
      <mxGeometry x="580" y="415" width="110" height="30" as="geometry"/>
    </mxCell>
    
    <!-- Par Fragment -->
    <mxCell id="parFrame" value="par" style="shape=umlFrame;whiteSpace=wrap;html=1;fillColor=#f0f8ff;strokeColor=#0066cc;" vertex="1" parent="1">
      <mxGeometry x="730" y="450" width="220" height="120" as="geometry"/>
    </mxCell>
    
    <mxCell value="7: notifyAllSupervisors(statusUpdate)" style="endArrow=block;html=1;fontColor=#000000;" edge="1" parent="1">
      <mxGeometry width="160" relative="1" as="geometry">
        <mxPoint x="745" y="480" as="sourcePoint"/>
        <mxPoint x="905" y="480" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    
    <mxCell value="8: updateDashboard()" style="endArrow=block;html=1;fontColor=#000000;" edge="1" parent="1">
      <mxGeometry width="160" relative="1" as="geometry">
        <mxPoint x="910" y="500" as="sourcePoint"/>
        <mxPoint x="910" y="520" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    
    <!-- Parallel activity separator -->
    <mxCell value="" style="endArrow=none;html=1;strokeWidth=1;" edge="1" parent="1">
      <mxGeometry width="50" height="50" relative="1" as="geometry">
        <mxPoint x="730" y="530" as="sourcePoint"/>
        <mxPoint x="950" y="530" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    
    <mxCell value="9: logBroadcastActivity()" style="endArrow=block;html=1;fontColor=#000000;" edge="1" parent="1">
      <mxGeometry width="160" relative="1" as="geometry">
        <mxPoint x="740" y="550" as="sourcePoint"/>
        <mxPoint x="740" y="570" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    
    <!-- Return Messages -->
    <mxCell value="10: statusUpdated" style="endArrow=open;html=1;dashed=1;fontColor=#000000;" edge="1" parent="1">
      <mxGeometry width="160" relative="1" as="geometry">
        <mxPoint x="415" y="600" as="sourcePoint"/>
        <mxPoint x="265" y="600" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    
    <mxCell value="11: confirmationMessage" style="endArrow=open;html=1;dashed=1;fontColor=#000000;" edge="1" parent="1">
      <mxGeometry width="160" relative="1" as="geometry">
        <mxPoint x="255" y="640" as="sourcePoint"/>
        <mxPoint x="105" y="640" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    
    <!-- Notes -->
    <mxCell id="note1" value="Note: WebSocket ensures&#xa;real-time updates to all&#xa;connected supervisors" style="shape=note;whiteSpace=wrap;html=1;backgroundOutline=1;darkOpacity=0.05;fillColor=#fff2cc;strokeColor=#d6b656;size=20;" vertex="1" parent="1">
      <mxGeometry x="40" y="580" width="150" height="80" as="geometry"/>
    </mxCell>
    
  </root>
</mxGraphModel>
```

### 💡 จุดเด่นของ Sequence Diagram นี้
- **Combined Fragments**: ใช้ `alt` แสดงเงื่อนไข และ `par` แสดงการทำงานพร้อมกัน
- **Activation Boxes**: แสดงระยะเวลาการทำงานของแต่ละ Object
- **Message Types**: แยกระหว่าง Synchronous calls และ Return messages
- **Real-time Communication**: แสดงการใช้ WebSocket สำหรับ Live updates

---

## หน้า 12: State Machine Diagram - ทฤษฎีและสัญลักษณ์

### 🔄 State Machine Diagram คืออะไร?
แผนภาพที่แสดง **สถานะต่างๆ** ของ Object และ **การเปลี่ยนแปลงสถานะ** (State Transitions) ตามเหตุการณ์ที่เกิดขึ้น

### 📚 สัญลักษณ์หลักใน State Machine Diagram

#### 1. **State (สถานะ)**
```
สัญลักษณ์: สี่เหลี่ยมมุมโค้ง
รูปแบบ: 
┌──────────────┐
│  StateName   │
├──────────────┤  
│ entry/ action│  ← Entry Action (ทำเมื่อเข้าสถานะ)
│ do/ activity │  ← Do Activity (ทำขณะอยู่ในสถานะ)  
│ exit/ action │  ← Exit Action (ทำเมื่อออกจากสถานะ)
└──────────────┘
```

#### 2. **Initial State (สถานะเริ่มต้น)**
```
สัญลักษณ์: วงกลมทึบสีดำ (●)
ความหมาย: จุดเริ่มต้นของ State Machine
ข้อกำหนด: มีได้เพียง 1 จุดต่อ 1 State Machine
```

#### 3. **Final State (สถานะสิ้นสุด)**
```
สัญลักษณ์: วงกลมทึบสีดำมีวงกลมขาวล้อม (◉)
ความหมาย: สถานะสิ้นสุดการทำงาน
ข้อกำหนด: อาจมีหลายจุดได้
```

#### 4. **Transition (การเปลี่ยนสถานะ)**
```
สัญลักษณ์: ลูกศรเชื่อมระหว่างสถานะ
รูปแบบ: event [guard] / action
ตัวอย่าง: loginRequest [validCredentials] / authenticateUser
```

#### 5. **Transition Elements**
```
Event: เหตุการณ์ที่เกิดขึ้น (loginRequest, timeout)
Guard: เงื่อนไข [condition] ที่ต้องเป็นจริง
Action: การกระทำที่ทำเมื่อเปลี่ยนสถานะ
```

#### 6. **Self Transition**
```
สัญลักษณ์: ลูกศรวนกลับตัวเอง
ความหมาย: เหตุการณ์เกิดขึ้นแต่ไม่เปลี่ยนสถานะ
ตัวอย่าง: refreshData / updateDisplay
```

#### 7. **Composite State (สถานะย่อย)**
```
รูปแบบ: สถานะใหญ่ที่มีสถานะย่อยภายใน
ใช้เมื่อ: สถานะมีความซับซ้อนภายใน
ตัวอย่าง: "Working" state มี "Available", "Busy" ภายใน
```

#### 8. **History State**
```
สัญลักษณ์: วงกลมมี H ข้างใน
ความหมาย: จำสถานะย่อยที่เคยอยู่ล่าสุด
ประเภท: Shallow History (H) และ Deep History (H*)
```

### 🎯 เมื่อไหร่ใช้ State Machine Diagram?
- **Object Behavior**: แสดงการเปลี่ยนแปลงสถานะของ Object
- **Business Rules**: แสดงกฎการเปลี่ยนสถานะที่ซับซ้อน
- **Protocol Design**: แสดง Communication protocols
- **UI/UX Design**: แสดงสถานะของ User Interface

---

## หน้า 13: State Machine Diagram - Agent Status Management

### 🔄 State Machine Diagram สำหรับ Agent Status

#### **สถานะของ Agent ใน Wallboard System:**
- **Offline**: Agent ยังไม่ได้ login เข้าระบบ
- **Available**: Agent พร้อมรับงาน
- **Busy**: Agent กำลังรับสายหรือทำงาน
- **Break**: Agent พักระหว่างงาน
- **Meeting**: Agent เข้าประชุม
- **Training**: Agent เข้ารับการอบรม

#### **Business Rules สำหรับ Status Transition:**
- จาก Offline สามารถไปได้เฉพาะ Available เท่านั้น
- จาก Available สามารถไปได้ทุกสถานะ ยกเว้น Offline
- การกลับสู่ Offline ต้องผ่าน Available เสมอ
- Break และ Training มีการจำกัดเวลา (Timeout)

### 📋 Draw.io Code สำหรับ State Machine Diagram

```xml
<mxGraphModel dx="1422" dy="794" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="827" pageHeight="1169">
  <root>
    <mxCell id="0"/>
    <mxCell id="1" parent="0"/>
    
    <!-- Initial State -->
    <mxCell id="initial" value="" style="ellipse;html=1;shape=startState;fillColor=#000000;strokeColor=#000000;" vertex="1" parent="1">
      <mxGeometry x="400" y="40" width="30" height="30" as="geometry"/>
    </mxCell>
    
    <!-- States -->
    <mxCell id="offline" value="Offline&#xa;&#xa;entry/ resetSession()&#xa;do/ waitForLogin&#xa;exit/ initializeAgent()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;fontSize=12;" vertex="1" parent="1">
      <mxGeometry x="350" y="100" width="130" height="80" as="geometry"/>
    </mxCell>
    
    <mxCell id="available" value="Available&#xa;&#xa;entry/ updateStatus()&#xa;do/ waitForCall&#xa;exit/ logStatusChange()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;fontSize=12;" vertex="1" parent="1">
      <mxGeometry x="350" y="250" width="130" height="80" as="geometry"/>
    </mxCell>
    
    <mxCell id="busy" value="Busy&#xa;&#xa;entry/ startTimer()&#xa;do/ handleCall&#xa;exit/ stopTimer()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;fontSize=12;" vertex="1" parent="1">
      <mxGeometry x="150" y="400" width="130" height="80" as="geometry"/>
    </mxCell>
    
    <mxCell id="break" value="Break&#xa;&#xa;entry/ scheduleTimeout()&#xa;do/ onBreak&#xa;exit/ clearTimeout()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;fontSize=12;" vertex="1" parent="1">
      <mxGeometry x="550" y="400" width="130" height="80" as="geometry"/>
    </mxCell>
    
    <mxCell id="meeting" value="Meeting&#xa;&#xa;entry/ blockCalls()&#xa;do/ attendMeeting&#xa;exit/ unblockCalls()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;fontSize=12;" vertex="1" parent="1">
      <mxGeometry x="150" y="550" width="130" height="80" as="geometry"/>
    </mxCell>
    
    <mxCell id="training" value="Training&#xa;&#xa;entry/ enrollTraining()&#xa;do/ attendTraining&#xa;exit/ completeTraining()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#ffe6cc;strokeColor=#d79b00;fontSize=12;" vertex="1" parent="1">
      <mxGeometry x="550" y="550" width="130" height="80" as="geometry"/>
    </mxCell>
    
    <!-- Final State (optional) -->
    <mxCell id="final" value="" style="ellipse;html=1;shape=endState;fillColor=#000000;strokeColor=#000000;" vertex="1" parent="1">
      <mxGeometry x="400" y="700" width="30" height="30" as="geometry"/>
    </mxCell>
    
    <!-- Transitions -->
    <!-- From Initial to Offline -->
    <mxCell edge="1" parent="1" source="initial" target="offline">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- From Offline to Available -->
    <mxCell value="login [validCredentials] / authenticateAgent" style="endArrow=block;html=1;fontSize=10;" edge="1" parent="1" source="offline" target="available">
      <mxGeometry x="0.1" width="160" relative="1" as="geometry">
        <mxPoint as="offset"/>
      </mxGeometry>
    </mxCell>
    
    <!-- From Available to other states -->
    <mxCell value="callReceived / acceptCall" style="endArrow=block;html=1;fontSize=10;" edge="1" parent="1" source="available" target="busy">
      <mxGeometry x="0.1" width="160" relative="1" as="geometry">
        <mxPoint as="offset"/>
      </mxGeometry>
    </mxCell>
    
    <mxCell value="takeBreak [breakAllowed] / startBreakTimer" style="endArrow=block;html=1;fontSize=10;" edge="1" parent="1" source="available" target="break">
      <mxGeometry x="0.1" width="160" relative="1" as="geometry">
        <mxPoint as="offset"/>
      </mxGeometry>
    </mxCell>
    
    <mxCell value="joinMeeting / blockIncomingCalls" style="endArrow=block;html=1;fontSize=10;" edge="1" parent="1" source="available" target="meeting">
      <mxGeometry x="0.1" width="160" relative="1" as="geometry">
        <mxPoint as="offset"/>
        <Array as="points">
          <mxPoint x="350" y="350"/>
          <mxPoint x="280" y="500"/>
        </Array>
      </mxGeometry>
    </mxCell>
    
    <mxCell value="startTraining [trainingScheduled] / enterTrainingMode" style="endArrow=block;html=1;fontSize=10;" edge="1" parent="1" source="available" target="training">
      <mxGeometry x="0.1" width="160" relative="1" as="geometry">
        <mxPoint as="offset"/>
        <Array as="points">
          <mxPoint x="480" y="350"/>
          <mxPoint x="550" y="500"/>
        </Array>
      </mxGeometry>
    </mxCell>
    
    <!-- Return to Available -->
    <mxCell value="callCompleted / endCall" style="endArrow=block;html=1;fontSize=10;" edge="1" parent="1" source="busy" target="available">
      <mxGeometry x="0.1" width="160" relative="1" as="geometry">
        <mxPoint as="offset"/>
      </mxGeometry>
    </mxCell>
    
    <mxCell value="breakTimeout / autoReturn" style="endArrow=block;html=1;fontSize=10;" edge="1" parent="1" source="break" target="available">
      <mxGeometry x="0.1" width="160" relative="1" as="geometry">
        <mxPoint as="offset"/>
      </mxGeometry>
    </mxCell>
    
    <mxCell value="meetingEnded / resumeWork" style="endArrow=block;html=1;fontSize=10;" edge="1" parent="1" source="meeting" target="available">
      <mxGeometry x="0.1" width="160" relative="1" as="geometry">
        <mxPoint as="offset"/>
        <Array as="points">
          <mxPoint x="280" y="350"/>
        </Array>
      </mxGeometry>
    </mxCell>
    
    <mxCell value="trainingCompleted / resumeWork" style="endArrow=block;html=1;fontSize=10;" edge="1" parent="1" source="training" target="available">
      <mxGeometry x="0.1" width="160" relative="1" as="geometry">
        <mxPoint as="offset"/>
        <Array as="points">
          <mxPoint x="550" y="350"/>
        </Array>
      </mxGeometry>
    </mxCell>
    
    <!-- Return to Available or extend time -->
    <mxCell value="endBreak / returnToWork" style="endArrow=block;html=1;fontSize=10;curved=1;" edge="1" parent="1" source="break" target="available">
      <mxGeometry x="-0.1" width="160" relative="1" as="geometry">
        <mxPoint as="offset"/>
        <Array as="points">
          <mxPoint x="520" y="350"/>
        </Array>
      </mxGeometry>
    </mxCell>
    
    <!-- Self transitions -->
    <mxCell value="extendBreak [withinLimit] / resetTimer" style="endArrow=block;html=1;fontSize=10;curved=1;" edge="1" parent="1" source="break" target="break">
      <mxGeometry x="0.3" width="160" relative="1" as="geometry">
        <mxPoint as="offset"/>
        <Array as="points">
          <mxPoint x="720" y="440"/>
        </Array>
      </mxGeometry>
    </mxCell>
    
    <mxCell value="callWaiting / updateDisplay" style="endArrow=block;html=1;fontSize=10;curved=1;" edge="1" parent="1" source="available" target="available">
      <mxGeometry x="0.3" width="160" relative="1" as="geometry">
        <mxPoint as="offset"/>
        <Array as="points">
          <mxPoint x="520" y="280"/>
        </Array>
      </mxGeometry>
    </mxCell>
    
    <!-- Logout transitions -->
    <mxCell value="logout / clearSession" style="endArrow=block;html=1;fontSize=10;" edge="1" parent="1" source="available" target="offline">
      <mxGeometry x="-0.1" width="160" relative="1" as="geometry">
        <mxPoint as="offset"/>
        <Array as="points">
          <mxPoint x="320" y="290"/>
          <mxPoint x="320" y="140"/>
        </Array>
      </mxGeometry>
    </mxCell>
    
    <!-- Emergency logout -->
    <mxCell value="systemShutdown / forceLogout" style="endArrow=block;html=1;fontSize=10;" edge="1" parent="1" source="available" target="final">
      <mxGeometry x="0.1" width="160" relative="1" as="geometry">
        <mxPoint as="offset"/>
        <Array as="points">
          <mxPoint x="415" y="330"/>
          <mxPoint x="415" y="700"/>
        </Array>
      </mxGeometry>
    </mxCell>
    
    <!-- Notes -->
    <mxCell id="note" value="Business Rules:&#xa;- Break timeout: 15 minutes&#xa;- Training can be interrupted&#xa;- Logout only from Available&#xa;- Busy state prevents logout" style="shape=note;whiteSpace=wrap;html=1;backgroundOutline=1;darkOpacity=0.05;fillColor=#fff2cc;strokeColor=#d6b656;size=20;" vertex="1" parent="1">
      <mxGeometry x="40" y="100" width="200" height="120" as="geometry"/>
    </mxCell>
    
  </root>
</mxGraphModel>
```

### 💡 จุดเด่นของ State Machine Diagram นี้
- **Entry/Do/Exit Actions**: แสดงการกระทำในแต่ละช่วงของสถานะ
- **Guards**: เงื่อนไข [condition] ที่ต้องผ่านก่อนเปลี่ยนสถานะ
- **Self Transitions**: การจัดการเหตุการณ์ภายในสถานะ
- **Business Rules**: แสดงกฎการทำงานที่ซับซ้อน
- **Timeout Handling**: จัดการกับเวลาจำกัดใน Break state

---

## หน้า 14: Component Diagram - ทฤษฎีและสัญลักษณ์

### 🧩 Component Diagram คืออะไร?
แผนภาพที่แสดง **โครงสร้างของ Software Components** และ **ความสัมพันธ์** ระหว่างกัน เหมาะสำหรับ **C2: Container Level**

### 📚 สัญลักษณ์หลักใน Component Diagram

#### 1. **Component (คอมโพเนนต์)**
```
สัญลักษณ์: สี่เหลี่ยมผืนผ้า + ไอคอน <<component>>
รูปแบบ:
┌─────────────────┐
│ <<component>>   │
│ ComponentName   │
└─────────────────┘

หรือใช้รูป UML Component icon (สี่เหลี่ยมมีปุ่มข้างๆ)
```

#### 2. **Interface (อินเทอร์เฟซ)**
```
Provided Interface (ให้บริการ):
สัญลักษณ์: วงกลม ○ เชื่อมกับ Component
ความหมาย: บริการที่ Component ให้กับ Component อื่น

Required Interface (ต้องการบริการ):  
สัญลักษณ์: ครึ่งวงกลม ) เชื่อมกับ Component
ความหมาย: บริการที่ Component ต้องการจาก Component อื่น
```

#### 3. **Port (พอร์ต)**
```
สัญลักษณ์: สี่เหลี่ยมเล็กบนขอบของ Component
ความหมาย: จุดเชื่อมต่อระหว่าง Component กับ Interface
ใช้เมื่อ: ต้องการแยกประเภทการเชื่อมต่อ
```

#### 4. **Assembly Connector (ตัวเชื่อม)**
```
สัญลักษณ์: เส้นตรงเชื่อม Provided กับ Required Interface  
รูปแบบ: Component A ○─── ) Component B
ความหมาย: Component B ใช้บริการจาก Component A
```

#### 5. **Delegation Connector**
```
สัญลักษณ์: เส้นประ
ความหมาย: เชื่อม Interface ภายนอกกับ Interface ภายใน
ใช้เมื่อ: Component ใหญ่มี Sub-components ภายใน
```

#### 6. **Dependency (การพึ่งพา)**
```
สัญลักษณ์: เส้นประ + ลูกศร ┄┄►
ความหมาย: Component หนึ่งพึ่งพา Component อื่น (loosely coupled)
ตัวอย่าง: Service ┄┄► Database Connection
```

### 🏗️ ระดับการใช้งาน Component Diagram

#### **C2: Container Level**
- แสดง Major technical building blocks
- Database, Web Server, Desktop Application
- External Systems และ API Services

#### **C3: Component Level**  
- แสดง Key components ภายใน Container
- Services, Controllers, Repositories
- Internal interfaces และ dependencies

### 🎯 เมื่อไหร่ใช้ Component Diagram?
- **System Architecture**: แสดงโครงสร้างระบบระดับสูง
- **Technology Mapping**: แสดงการแบ่ง components ตาม technology stack
- **Interface Design**: ออกแบบ API และ service interfaces
- **Deployment Planning**: วางแผนการ deploy แต่ละ component

---

## หน้า 15: Component Diagram - Agent Wallboard Architecture

### 🧩 Component Diagram สำหรับ Agent Wallboard System (C2: Container Level)

#### **Major Containers ในระบบ:**
- **Agent Desktop App**: Electron.js application สำหรับ Agent
- **Supervisor Web App**: Web-based dashboard สำหรับ Supervisor
- **WebAPI Server**: Node.js REST API server
- **WebSocket Service**: Real-time communication service  
- **MongoDB Database**: NoSQL database สำหรับ real-time data
- **MSSQL Database**: SQL database สำหรับ master data
- **Authentication Service**: JWT-based authentication
- **Notification Service**: Push notification service

### 📋 Draw.io Code สำหรับ Component Diagram

```xml
<mxGraphModel dx="1422" dy="794" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="827" pageHeight="1169">
  <root>
    <mxCell id="0"/>
    <mxCell id="1" parent="0"/>
    
    <!-- External Users -->
    <mxCell id="agent" value="Agent" style="shape=umlActor;verticalLabelPosition=bottom;verticalAlign=top;html=1;outlineConnect=0;" vertex="1" parent="1">
      <mxGeometry x="50" y="200" width="30" height="60" as="geometry"/>
    </mxCell>
    
    <mxCell id="supervisor" value="Supervisor" style="shape=umlActor;verticalLabelPosition=bottom;verticalAlign=top;html=1;outlineConnect=0;" vertex="1" parent="1">
      <mxGeometry x="50" y="400" width="30" height="60" as="geometry"/>
    </mxCell>
    
    <!-- Client Layer Components -->
    <mxCell id="desktopApp" value="&lt;&lt;component&gt;&gt;&#xa;Agent Desktop App&#xa;&#xa;(Electron.js)&#xa;- Agent Interface&#xa;- Status Management&#xa;- Message Display" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;fontSize=11;" vertex="1" parent="1">
      <mxGeometry x="150" y="180" width="160" height="100" as="geometry"/>
    </mxCell>
    
    <mxCell id="webApp" value="&lt;&lt;component&gt;&gt;&#xa;Supervisor Web App&#xa;&#xa;(React.js)&#xa;- Real-time Dashboard&#xa;- Team Management&#xa;- Reporting" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;fontSize=11;" vertex="1" parent="1">
      <mxGeometry x="150" y="380" width="160" height="100" as="geometry"/>
    </mxCell>
    
    <!-- API Layer Components -->
    <mxCell id="webAPI" value="&lt;&lt;component&gt;&gt;&#xa;WebAPI Server&#xa;&#xa;(Node.js + Express)&#xa;- REST Endpoints&#xa;- Business Logic&#xa;- Data Validation" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;fontSize=11;" vertex="1" parent="1">
      <mxGeometry x="400" y="280" width="160" height="100" as="geometry"/>
    </mxCell>
    
    <mxCell id="websocket" value="&lt;&lt;component&gt;&gt;&#xa;WebSocket Service&#xa;&#xa;(Socket.io)&#xa;- Real-time Updates&#xa;- Event Broadcasting&#xa;- Connection Management" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;fontSize=11;" vertex="1" parent="1">
      <mxGeometry x="600" y="180" width="160" height="100" as="geometry"/>
    </mxCell>
    
    <mxCell id="authService" value="&lt;&lt;component&gt;&gt;&#xa;Authentication Service&#xa;&#xa;(JWT + Passport)&#xa;- User Authentication&#xa;- Token Management&#xa;- Role Authorization" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;fontSize=11;" vertex="1" parent="1">
      <mxGeometry x="600" y="380" width="160" height="100" as="geometry"/>
    </mxCell>
    
    <mxCell id="notificationService" value="&lt;&lt;component&gt;&gt;&#xa;Notification Service&#xa;&#xa;(Node.js)&#xa;- Push Notifications&#xa;- Email Alerts&#xa;- SMS Gateway" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#ffe6cc;strokeColor=#d79b00;fontSize=11;" vertex="1" parent="1">
      <mxGeometry x="400" y="480" width="160" height="100" as="geometry"/>
    </mxCell>
    
    <!-- Database Layer -->
    <mxCell id="mongodb" value="&lt;&lt;database&gt;&gt;&#xa;MongoDB&#xa;&#xa;- Real-time Status Data&#xa;- Message Queue&#xa;- Session Storage&#xa;- WebSocket Events" style="shape=cylinder3;whiteSpace=wrap;html=1;boundedLbl=1;backgroundOutline=1;size=15;fillColor=#f0f8ff;strokeColor=#4169e1;fontSize=11;" vertex="1" parent="1">
      <mxGeometry x="800" y="200" width="140" height="100" as="geometry"/>
    </mxCell>
    
    <mxCell id="mssql" value="&lt;&lt;database&gt;&gt;&#xa;MSSQL Database&#xa;&#xa;- User Master Data&#xa;- Team Configuration&#xa;- Historical Reports&#xa;- Audit Logs" style="shape=cylinder3;whiteSpace=wrap;html=1;boundedLbl=1;backgroundOutline=1;size=15;fillColor=#fff0f5;strokeColor=#8b008b;fontSize=11;" vertex="1" parent="1">
      <mxGeometry x="800" y="400" width="140" height="100" as="geometry"/>
    </mxCell>
    
    <!-- External API -->
    <mxCell id="externalAPI" value="&lt;&lt;external&gt;&gt;&#xa;Call Center System&#xa;&#xa;- Agent Status Feed&#xa;- Call Information&#xa;- Performance Metrics" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f5f5f5;strokeColor=#666666;fontSize=11;dashed=1;" vertex="1" parent="1">
      <mxGeometry x="600" y="580" width="160" height="80" as="geometry"/>
    </mxCell>
    
    <!-- Interfaces (Provided) -->
    <!-- Agent Desktop App Interfaces -->
    <mxCell id="agentStatusIF" value="" style="ellipse;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;fontSize=8;" vertex="1" parent="1">
      <mxGeometry x="320" y="210" width="20" height="20" as="geometry"/>
    </mxCell>
    <mxCell value="AgentStatusAPI" style="text;html=1;align=center;verticalAlign=middle;resizable=0;points=[];autosize=1;strokeColor=none;fillColor=none;fontSize=9;" vertex="1" parent="1">
      <mxGeometry x="340" y="200" width="80" height="20" as="geometry"/>
    </mxCell>
    
    <mxCell id="messageIF" value="" style="ellipse;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="1">
      <mxGeometry x="320" y="240" width="20" height="20" as="geometry"/>
    </mxCell>
    <mxCell value="MessageAPI" style="text;html=1;align=center;verticalAlign=middle;resizable=0;points=[];autosize=1;strokeColor=none;fillColor=none;fontSize=9;" vertex="1" parent="1">
      <mxGeometry x="340" y="235" width="70" height="20" as="geometry"/>
    </mxCell>
    
    <!-- Web App Interfaces -->
    <mxCell id="dashboardIF" value="" style="ellipse;whiteSpace=wrap;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;" vertex="1" parent="1">
      <mxGeometry x="320" y="410" width="20" height="20" as="geometry"/>
    </mxCell>
    <mxCell value="DashboardAPI" style="text;html=1;align=center;verticalAlign=middle;resizable=0;points=[];autosize=1;strokeColor=none;fillColor=none;fontSize=9;" vertex="1" parent="1">
      <mxGeometry x="340" y="405" width="80" height="20" as="geometry"/>
    </mxCell>
    
    <!-- WebAPI Provided Interfaces -->
    <mxCell id="restIF" value="" style="ellipse;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
      <mxGeometry x="370" y="310" width="20" height="20" as="geometry"/>
    </mxCell>
    <mxCell value="REST API" style="text;html=1;align=center;verticalAlign=middle;resizable=0;points=[];autosize=1;strokeColor=none;fillColor=none;fontSize=9;" vertex="1" parent="1">
      <mxGeometry x="320" y="305" width="60" height="20" as="geometry"/>
    </mxCell>
    
    <!-- WebSocket Interfaces -->
    <mxCell id="realtimeIF" value="" style="ellipse;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;" vertex="1" parent="1">
      <mxGeometry x="570" y="210" width="20" height="20" as="geometry"/>
    </mxCell>
    <mxCell value="WebSocket" style="text;html=1;align=center;verticalAlign=middle;resizable=0;points=[];autosize=1;strokeColor=none;fillColor=none;fontSize=9;" vertex="1" parent="1">
      <mxGeometry x="500" y="205" width="70" height="20" as="geometry"/>
    </mxCell>
    
    <!-- Required Interfaces (half circles) -->
    <mxCell id="authRequired" value="" style="shape=arc;startAngle=90;endAngle=270;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="1">
      <mxGeometry x="570" y="320" width="20" height="20" as="geometry"/>
    </mxCell>
    <mxCell value="Auth Required" style="text;html=1;align=center;verticalAlign=middle;resizable=0;points=[];autosize=1;strokeColor=none;fillColor=none;fontSize=9;" vertex="1" parent="1">
      <mxGeometry x="595" y="315" width="80" height="20" as="geometry"/>
    </mxCell>
    
    <mxCell id="dbRequired" value="" style="shape=arc;startAngle=90;endAngle=270;html=1;fillColor=#f0f8ff;strokeColor=#4169e1;" vertex="1" parent="1">
      <mxGeometry x="570" y="350" width="20" height="20" as="geometry"/>
    </mxCell>
    <mxCell value="Database" style="text;html=1;align=center;verticalAlign=middle;resizable=0;points=[];autosize=1;strokeColor=none;fillColor=none;fontSize=9;" vertex="1" parent="1">
      <mxGeometry x="595" y="345" width="60" height="20" as="geometry"/>
    </mxCell>
    
    <!-- Assembly Connectors -->
    <!-- Agent to WebAPI -->
    <mxCell edge="1" parent="1" source="agentStatusIF" target="restIF">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell edge="1" parent="1" source="messageIF" target="restIF">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- Web App to WebAPI -->
    <mxCell edge="1" parent="1" source="dashboardIF" target="restIF">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- WebSocket Connections -->
    <mxCell edge="1" parent="1" source="desktopApp" target="realtimeIF">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell edge="1" parent="1" source="webApp" target="realtimeIF">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- API to Services -->
    <mxCell edge="1" parent="1" source="webAPI" target="authRequired">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- Services to Databases -->
    <mxCell edge="1" parent="1" source="websocket" target="mongodb">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell edge="1" parent="1" source="authService" target="mssql">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell edge="1" parent="1" source="webAPI" target="mongodb">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell edge="1" parent="1" source="webAPI" target="mssql">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- User Connections -->
    <mxCell edge="1" parent="1" source="agent" target="desktopApp">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    <mxCell edge="1" parent="1" source="supervisor" target="webApp">
      <mxGeometry relative="1" as="geometry"/>
    </mxCell>
    
    <!-- External API -->
    <mxCell value="<<uses>>" style="endArrow=open;endSize=12;dashed=1;html=1;dashPattern=5 5;" edge="1" parent="1" source="webAPI" target="externalAPI">
      <mxGeometry width="160" relative="1" as="geometry"/>
    </mxCell>
    
    <!-- Notification Dependencies -->
    <mxCell value="<<notifies>>" style="endArrow=open;endSize=12;dashed=1;html=1;dashPattern=5 5;" edge="1" parent="1" source="notificationService" target="desktopApp">
      <mxGeometry width="160" relative="1" as="geometry"/>
    </mxCell>
    
    <!-- Technology Notes -->
    <mxCell id="techNote" value="Technology Stack:&#xa;• Frontend: Electron.js, React.js&#xa;• Backend: Node.js, Express&#xa;• Real-time: Socket.io&#xa;• Databases: MongoDB, MSSQL&#xa;• Authentication: JWT + Passport" style="shape=note;whiteSpace=wrap;html=1;backgroundOutline=1;darkOpacity=0.05;fillColor=#fff2cc;strokeColor=#d6b656;size=20;" vertex="1" parent="1">
      <mxGeometry x="40" y="580" width="200" height="120" as="geometry"/>
    </mxCell>
    
  </root>
</mxGraphModel>
```

### 💡 จุดเด่นของ Component Diagram นี้
- **Layered Architecture**: แสดงการแบ่งชั้นของระบบ (Client, API, Database)
- **Interface Clarity**: แสดง Provided (○) และ Required ( ) interfaces ชัดเจน
- **Technology Mapping**: ระบุเทคโนโลยีที่ใช้แต่ละ component
- **External Dependencies**: แสดงการเชื่อมต่อกับระบบภายนอก
- **Real-time Architecture**: แสดง WebSocket สำหรับ real-time communication

---

## หน้า 16: Deployment Diagram - ทฤษฎีและสัญลักษณ์

### 🚀 Deployment Diagram คืออะไร?
แผนภาพที่แสดง **การติดตั้งและกระจาย** Software Components บน **Hardware Infrastructure** เหมาะสำหรับ **Production Deployment**

### 📚 สัญลักษณ์หลักใน Deployment Diagram

#### 1. **Node (โหนด)**
```
สัญลักษณ์: สี่เหลี่ยมสามมิติ (3D box)
ความหมาย: Hardware หรือ Execution environment
ประเภท:
- Device Node: อุปกรณ์ฟิสิคัล (Server, PC, Mobile)
- Execution Environment: สภาพแวดล้อมการทำงาน (JVM, Browser, Container)
```

#### 2. **Artifact (สิ่งประดิษฐ์)**
```
สัญลักษณ์: สี่เหลี่ยมผืนผ้า + <<artifact>>
ความหมาย: ไฟล์ที่สามารถ deploy ได้
ตัวอย่าง: .exe, .war, .jar, .dll, database
```

#### 3. **Component Instance**
```
สัญลักษณ์: สี่เหลี่ยมผืนผ้า + instanceName : ComponentName
ความหมาย: Instance ของ Component ที่ทำงานบน Node
ตัวอย่าง: webServer : WebAPI, database1 : MongoDB
```

#### 4. **Communication Path (เส้นทางการสื่อสาร)**
```
สัญลักษณ์: เส้นเชื่อมระหว่าง Nodes
ข้อมูลที่แสดง: Protocol, Bandwidth, Network type
ตัวอย่าง: HTTPS, TCP/IP, WebSocket
```

#### 5. **Deployment (การติดตั้ง)**
```
สัญลักษณ์: เส้นประ <<deploy>>
ความหมาย: Artifact ถูกติดตั้งบน Node
ตัวอย่าง: app.exe <<deploy>> ClientPC
```

#### 6. **Dependency (การพึ่งพา)**
```
สัญลักษณ์: เส้นประ <<use>>
ความหมาย: Component หนึ่งใช้บริการจาก Component อื่น
ตัวอย่าง: WebApp <<use>> WebAPI
```

#### 7. **Node Stereotypes**
```
<<device>>: อุปกรณ์ฟิสิคัล
<<execution environment>>: สภาพแวดล้อมการทำงาน
<<application server>>: Application server
<<database server>>: Database server
<<web server>>: Web server
<<client>>: Client machine
```

### 🏗️ การใช้งาน Deployment Diagram

#### **Physical Architecture**
- แสดงโครงสร้างฮาร์ดแวร์
- Network topology และ connections
- Server specifications และ capabilities

#### **Deployment Strategy**
- แสดงการกระจาย applications
- Load balancing และ redundancy
- Scalability และ performance considerations

### 🎯 เมื่อไหร่ใช้ Deployment Diagram?
- **Production Planning**: วางแผนการ deploy ระบบจริง
- **Infrastructure Design**: ออกแบบโครงสร้างฮาร์ดแวร์
- **Performance Analysis**: วิเคราะห์ bottlenecks และ scalability
- **Security Planning**: วางแผน network security

---

## หน้า 17: Deployment Diagram - Agent Wallboard Infrastructure

### 🚀 Deployment Diagram สำหรับ Agent Wallboard System

#### **Infrastructure Components:**
- **Client Tier**: Agent Desktop PCs + Supervisor Workstations
- **Web Tier**: Load Balancer + Web Servers
- **Application Tier**: API Servers + WebSocket Servers  
- **Database Tier**: MongoDB Cluster + MSSQL Server
- **Network**: Corporate LAN + DMZ + Internet connectivity

#### **Deployment Strategy:**
- High Availability สำหรับ critical components
- Load Balancing สำหรับ scalability
- Database replication สำหรับ data redundancy

### 📋 Draw.io Code สำหรับ Deployment Diagram

```xml
<mxGraphModel dx="1422" dy="794" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="827" pageHeight="1169">
  <root>
    <mxCell id="0"/>
    <mxCell id="1" parent="0"/>
    
    <!-- Client Tier -->
    <mxCell id="clientZone" value="Client Network Zone" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f0f8ff;strokeColor=#4169e1;fontSize=14;fontStyle=1;verticalAlign=top;" vertex="1" parent="1">
      <mxGeometry x="40" y="40" width="300" height="200" as="geometry"/>
    </mxCell>
    
    <mxCell id="agentPC" value="&lt;&lt;device&gt;&gt;&#xa;Agent Desktop PC&#xa;&#xa;Windows 10&#xa;8GB RAM, i5 CPU&#xa;Corporate Domain" style="shape=cube;whiteSpace=wrap;html=1;boundedLbl=1;backgroundOutline=1;darkOpacity=0.05;darkOpacity2=0.1;fillColor=#dae8fc;strokeColor=#6c8ebf;size=10;" vertex="1" parent="1">
      <mxGeometry x="60" y="80" width="120" height="60" as="geometry"/>
    </mxCell>
    
    <mxCell id="supervisorPC" value="&lt;&lt;device&gt;&gt;&#xa;Supervisor Workstation&#xa;&#xa;Windows 11&#xa;16GB RAM, i7 CPU&#xa;Dual Monitor" style="shape=cube;whiteSpace=wrap;html=1;boundedLbl=1;backgroundOutline=1;darkOpacity=0.05;darkOpacity2=0.1;fillColor=#e1d5e7;strokeColor=#9673a6;size=10;" vertex="1" parent="1">
      <mxGeometry x="200" y="80" width="120" height="60" as="geometry"/>
    </mxCell>
    
    <!-- Artifacts on Client -->
    <mxCell id="desktopApp" value="&lt;&lt;artifact&gt;&gt;&#xa;AgentWallboard.exe" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#ffffff;strokeColor=#666666;" vertex="1" parent="1">
      <mxGeometry x="70" y="160" width="100" height="30" as="geometry"/>
    </mxCell>
    
    <mxCell id="webBrowser" value="&lt;&lt;artifact&gt;&gt;&#xa;Chrome Browser" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#ffffff;strokeColor=#666666;" vertex="1" parent="1">
      <mxGeometry x="210" y="160" width="100" height="30" as="geometry"/>
    </mxCell>
    
    <!-- DMZ Zone -->
    <mxCell id="dmzZone" value="DMZ (Demilitarized Zone)" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;fontSize=14;fontStyle=1;verticalAlign=top;" vertex="1" parent="1">
      <mxGeometry x="400" y="40" width="400" height="200" as="geometry"/>
    </mxCell>
    
    <mxCell id="loadBalancer" value="&lt;&lt;device&gt;&gt;&#xa;Load Balancer&#xa;&#xa;NGINX&#xa;SSL Termination&#xa;High Availability" style="shape=cube;whiteSpace=wrap;html=1;boundedLbl=1;backgroundOutline=1;darkOpacity=0.05;darkOpacity2=0.1;fillColor=#f8cecc;strokeColor=#b85450;size=10;" vertex="1" parent="1">
      <mxGeometry x="420" y="80" width="120" height="60" as="geometry"/>
    </mxCell>
    
    <mxCell id="webServer1" value="&lt;&lt;execution environment&gt;&gt;&#xa;Web Server 1&#xa;&#xa;Node.js Runtime&#xa;Ubuntu 20.04&#xa;4GB RAM" style="shape=cube;whiteSpace=wrap;html=1;boundedLbl=1;backgroundOutline=1;darkOpacity=0.05;darkOpacity2=0.1;fillColor=#fff2cc;strokeColor=#d6b656;size=10;" vertex="1" parent="1">
      <mxGeometry x="560" y="80" width="110" height="60" as="geometry"/>
    </mxCell>
    
    <mxCell id="webServer2" value="&lt;&lt;execution environment&gt;&gt;&#xa;Web Server 2&#xa;&#xa;Node.js Runtime&#xa;Ubuntu 20.04&#xa;4GB RAM" style="shape=cube;whiteSpace=wrap;html=1;boundedLbl=1;backgroundOutline=1;darkOpacity=0.05;darkOpacity2=0.1;fillColor=#fff2cc;strokeColor=#d6b656;size=10;" vertex="1" parent="1">
      <mxGeometry x="680" y="80" width="110" height="60" as="geometry"/>
    </mxCell>
    
    <!-- Application Components -->
    <mxCell id="webAPI1" value="webAPI1 : WebAPI" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="1">
      <mxGeometry x="565" y="160" width="100" height="25" as="geometry"/>
    </mxCell>
    
    <mxCell id="websocket1" value="wsService1 : WebSocketService" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#ffe6cc;strokeColor=#d79b00;" vertex="1" parent="1">
      <mxGeometry x="560" y="190" width="110" height="25" as="geometry"/>
    </mxCell>
    
    <mxCell id="webAPI2" value="webAPI2 : WebAPI" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="1">
      <mxGeometry x="685" y="160" width="100" height="25" as="geometry"/>
    </mxCell>
    
    <mxCell id="websocket2" value="wsService2 : WebSocketService" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#ffe6cc;strokeColor=#d79b00;" vertex="1" parent="1">
      <mxGeometry x="680" y="190" width="110" height="25" as="geometry"/>
    </mxCell>
    
    <!-- Database Tier -->
    <mxCell id="dbZone" value="Database Tier (Private Network)" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f5f5f5;strokeColor=#666666;fontSize=14;fontStyle=1;verticalAlign=top;" vertex="1" parent="1">
      <mxGeometry x="40" y="300" width="760" height="180" as="geometry"/>
    </mxCell>
    
    <mxCell id="mongoCluster" value="&lt;&lt;database server&gt;&gt;&#xa;MongoDB Cluster&#xa;&#xa;Primary + 2 Secondaries&#xa;Replica Set&#xa;Auto Failover" style="shape=cylinder3;whiteSpace=wrap;html=1;boundedLbl=1;backgroundOutline=1;size=15;fillColor=#e1d5e7;strokeColor=#9673a6;" vertex="1" parent="1">
      <mxGeometry x="80" y="340" width="140" height="100" as="geometry"/>
    </mxCell>
    
    <mxCell id="mssqlServer" value="&lt;&lt;database server&gt;&gt;&#xa;MSSQL Server&#xa;&#xa;SQL Server 2019&#xa;Always On AG&#xa;Enterprise Edition" style="shape=cylinder3;whiteSpace=wrap;html=1;boundedLbl=1;backgroundOutline=1;size=15;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="1">
      <mxGeometry x="280" y="340" width="140" height="100" as="geometry"/>
    </mxCell>
    
    <mxCell id="redisCluster" value="&lt;&lt;cache server&gt;&gt;&#xa;Redis Cluster&#xa;&#xa;Session Store&#xa;Real-time Cache&#xa;3-Node Cluster" style="shape=cylinder3;whiteSpace=wrap;html=1;boundedLbl=1;backgroundOutline=1;size=15;fillColor=#f8cecc;strokeColor=#b85450;" vertex="1" parent="1">
      <mxGeometry x="480" y="340" width="140" height="100" as="geometry"/>
    </mxCell>
    
    <mxCell id="backupStorage" value="&lt;&lt;storage&gt;&gt;&#xa;Backup Storage&#xa;&#xa;Network Attached Storage&#xa;Daily Backups&#xa;7-Year Retention" style="shape=cylinder3;whiteSpace=wrap;html=1;boundedLbl=1;backgroundOutline=1;size=15;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
      <mxGeometry x="640" y="340" width="140" height="100" as="geometry"/>
    </mxCell>
    
    <!-- External Systems -->
    <mxCell id="callCenter" value="&lt;&lt;external system&gt;&gt;&#xa;Call Center System&#xa;&#xa;Legacy Avaya PBX&#xa;Agent Status Feed&#xa;REST API" style="shape=cube;whiteSpace=wrap;html=1;boundedLbl=1;backgroundOutline=1;darkOpacity=0.05;darkOpacity2=0.1;fillColor=#f5f5f5;strokeColor=#666666;size=10;dashed=1;" vertex="1" parent="1">
      <mxGeometry x="400" y="520" width="140" height="80" as="geometry"/>
    </mxCell>
    
    <mxCell id="activeDirectory" value="&lt;&lt;external system&gt;&gt;&#xa;Active Directory&#xa;&#xa;Windows Domain&#xa;LDAP Authentication&#xa;Group Policies" style="shape=cube;whiteSpace=wrap;html=1;boundedLbl=1;backgroundOutline=1;darkOpacity=0.05;darkOpacity2=0.1;fillColor=#f5f5f5;strokeColor=#666666;size=10;dashed=1;" vertex="1" parent="1">
      <mxGeometry x="560" y="520" width="140" height="80" as="geometry"/>
    </mxCell>
    
    <!-- Network Connections -->
    <!-- Client to Load Balancer -->
    <mxCell value="HTTPS&#xa;443" style="endArrow=none;html=1;strokeWidth=2;fillColor=#f8cecc;strokeColor=#b85450;" edge="1" parent="1" source="supervisorPC" target="loadBalancer">
      <mxGeometry width="50" height="50" relative="1" as="geometry">
        <mxPoint x="300" y="120" as="sourcePoint"/>
        <mxPoint x="350" y="70" as="targetPoint"/>
      </mxGeometry>
    </mxCell>
    
    <!-- Load Balancer to Web Servers -->
    <mxCell value="HTTP&#xa;3000" style="endArrow=none;html=1;strokeWidth=2;fillColor=#fff2cc;strokeColor=#d6b656;" edge="1" parent="1" source="loadBalancer" target="webServer1">
      <mxGeometry width="50" height="50" relative="1" as="geometry"/>
    </mxCell>
    
    <mxCell value="HTTP&#xa;3000" style="endArrow=none;html=1;strokeWidth=2;fillColor=#fff2cc;strokeColor=#d6b656;" edge="1" parent="1" source="loadBalancer" target="webServer2">
      <mxGeometry width="50" height="50" relative="1" as="geometry"/>
    </mxCell>
    
    <!-- Web Servers to Databases -->
    <mxCell value="TCP&#xa;27017" style="endArrow=none;html=1;strokeWidth=2;fillColor=#e1d5e7;strokeColor=#9673a6;" edge="1" parent="1" source="webServer1" target="mongoCluster">
      <mxGeometry width="50" height="50" relative="1" as="geometry"/>
    </mxCell>
    
    <mxCell value="TCP&#xa;1433" style="endArrow=none;html=1;strokeWidth=2;fillColor=#dae8fc;strokeColor=#6c8ebf;" edge="1" parent="1" source="webServer1" target="mssqlServer">
      <mxGeometry width="50" height="50" relative="1" as="geometry"/>
    </mxCell>
    
    <mxCell value="TCP&#xa;27017" style="endArrow=none;html=1;strokeWidth=2;fillColor=#e1d5e7;strokeColor=#9673a6;" edge="1" parent="1" source="webServer2" target="mongoCluster">
      <mxGeometry width="50" height="50" relative="1" as="geometry"/>
    </mxCell>
    
    <mxCell value="TCP&#xa;1433" style="endArrow=none;html=1;strokeWidth=2;fillColor=#dae8fc;strokeColor=#6c8ebf;" edge="1" parent="1" source="webServer2" target="mssqlServer">
      <mxGeometry width="50" height="50" relative="1" as="geometry"/>
    </mxCell>
    
    <!-- Redis Connections -->
    <mxCell value="TCP&#xa;6379" style="endArrow=none;html=1;strokeWidth=1;fillColor=#f8cecc;strokeColor=#b85450;" edge="1" parent="1" source="webServer1" target="redisCluster">
      <mxGeometry width="50" height="50" relative="1" as="geometry"/>
    </mxCell>
    
    <mxCell value="TCP&#xa;6379" style="endArrow=none;html=1;strokeWidth=1;fillColor=#f8cecc;strokeColor=#b85450;" edge="1" parent="1" source="webServer2" target="redisCluster">
      <mxGeometry width="50" height="50" relative="1" as="geometry"/>
    </mxCell>
    
    <!-- External System Connections -->
    <mxCell value="HTTPS&#xa;8443" style="endArrow=none;html=1;strokeWidth=1;dashed=1;fillColor=#666666;strokeColor=#666666;" edge="1" parent="1" source="webServer1" target="callCenter">
      <mxGeometry width="50" height="50" relative="1" as="geometry"/>
    </mxCell>
    
    <mxCell value="LDAPS&#xa;636" style="endArrow=none;html=1;strokeWidth=1;dashed=1;fillColor=#666666;strokeColor=#666666;" edge="1" parent="1" source="webServer2" target="activeDirectory">
      <mxGeometry width="50" height="50" relative="1" as="geometry"/>
    </mxCell>
    
    <!-- Backup Connections -->
    <mxCell value="Backup" style="endArrow=none;html=1;strokeWidth=1;dashed=1;fillColor=#fff2cc;strokeColor=#d6b656;" edge="1" parent="1" source="mongoCluster" target="backupStorage">
      <mxGeometry width="50" height="50" relative="1" as="geometry"/>
    </mxCell>
    
    <mxCell value="Backup" style="endArrow=none;html=1;strokeWidth=1;dashed=1;fillColor=#fff2cc;strokeColor=#d6b656;" edge="1" parent="1" source="mssqlServer" target="backupStorage">
      <mxGeometry width="50" height="50" relative="1" as="geometry"/>
    </mxCell>
    
    <!-- Deployment Relationships -->
    <mxCell value="&lt;&lt;deploy&gt;&gt;" style="endArrow=open;endSize=12;dashed=1;html=1;dashPattern=5 5;" edge="1" parent="1" source="desktopApp" target="agentPC">
      <mxGeometry width="160" relative="1" as="geometry"/>
    </mxCell>
    
    <mxCell value="&lt;&lt;deploy&gt;&gt;" style="endArrow=open;endSize=12;dashed=1;html=1;dashPattern=5 5;" edge="1" parent="1" source="webBrowser" target="supervisorPC">
      <mxGeometry width="160" relative="1" as="geometry"/>
    </mxCell>
    
    <!-- Performance and Availability Notes -->
    <mxCell id="perfNote" value="Performance &amp; Availability:&#xa;• Load Balancer: 99.9% uptime&#xa;• Web Servers: Auto-scaling (2-4 instances)&#xa;• MongoDB: Replica set with automatic failover&#xa;• Redis: 3-node cluster for session persistence&#xa;• Backup: Daily incremental, weekly full&#xa;• Network: Redundant connections" style="shape=note;whiteSpace=wrap;html=1;backgroundOutline=1;darkOpacity=0.05;fillColor=#e1d5e7;strokeColor=#9673a6;size=20;" vertex="1" parent="1">
      <mxGeometry x="40" y="620" width="280" height="140" as="geometry"/>
    </mxCell>
    
    <!-- Security Note -->
    <mxCell id="securityNote" value="Security Measures:&#xa;• SSL/TLS encryption (HTTPS)&#xa;• JWT token authentication&#xa;• Active Directory integration&#xa;• Network segmentation (DMZ)&#xa;• Database access controls&#xa;• Audit logging enabled&#xa;• Regular security patches" style="shape=note;whiteSpace=wrap;html=1;backgroundOutline=1;darkOpacity=0.05;fillColor=#f8cecc;strokeColor=#b85450;size=20;" vertex="1" parent="1">
      <mxGeometry x="350" y="620" width="250" height="140" as="geometry"/>
    </mxCell>
    
    <!-- Scalability Note -->
    <mxCell id="scalabilityNote" value="Scalability Features:&#xa;• Horizontal scaling: Web servers&#xa;• Database sharding: MongoDB&#xa;• Caching layer: Redis cluster&#xa;• CDN for static assets&#xa;• Connection pooling&#xa;• WebSocket connection management&#xa;• Auto-scaling policies" style="shape=note;whiteSpace=wrap;html=1;backgroundOutline=1;darkOpacity=0.05;fillColor=#d5e8d4;strokeColor=#82b366;size=20;" vertex="1" parent="1">
      <mxGeometry x="630" y="620" width="250" height="140" as="geometry"/>
    </mxCell>
    
  </root>
</mxGraphModel>
```

### 💡 จุดเด่นของ Deployment Diagram นี้
- **Network Zones**: แบ่งเครือข่ายตาม security zones (Client, DMZ, Database)
- **High Availability**: แสดง redundancy และ failover mechanisms
- **Technology Stack**: ระบุ OS, runtime environments, และ protocols
- **Security**: แสดงมาตรการรักษาความปลอดภัย
- **Scalability**: แสดงความสามารถในการขยายระบบ

---

## หน้า 18: Package Diagram - ทฤษฎีและสัญลักษณ์

### 📦 Package Diagram คืออะไร?
แผนภาพที่แสดง **การจัดกลุ่มและการจัดองค์กร** ของ Model elements เป็น **Packages** และแสดง **ความสัมพันธ์** ระหว่าง Packages

### 📚 สัญลักษณ์หลักใน Package Diagram

#### 1. **Package (แพ็คเกจ)**
```
สัญลักษณ์: สี่เหลี่ยมผืนผ้าที่มีแท็บด้านบน
รูปแบบ:
┌─────┐
│ tab │
├─────┴──────────┐
│ Package Name   │
│                │
│ +element1      │
│ +element2      │
│ -element3      │
└────────────────┘
```

#### 2. **Package Import (การนำเข้าแพ็คเกจ)**
```
<<import>> : นำเข้าเฉพาะ public elements
สัญลักษณ์: เส้นประ + <<import>>
ความหมาย: Package สามารถใช้ public elements จาก imported package
```

#### 3. **Package Access (การเข้าถึงแพ็คเกจ)**
```
<<access>> : เข้าถึงได้แต่ไม่เพิ่มเข้า namespace
สัญลักษณ์: เส้นประ + <<access>>  
ความหมาย: ต้องใช้ qualified name เสมอ
```

#### 4. **Package Merge (การรวมแพ็คเกจ)**
```
<<merge>> : รวมเนื้อหาของ package เข้าด้วยกัน
สัญลักษณ์: เส้นประ + <<merge>>
ความหมาย: Elements จาก merged package เป็นส่วนหนึ่งของ receiving package
```

#### 5. **Nested Package (แพ็คเกจซ้อน)**
```
รูปแบบ: Package ภายใน Package อื่น
ความหมาย: Package hierarchy และ logical organization
ตัวอย่าง: com.company.project.module
```

#### 6. **Visibility (การมองเห็น)**
```
+ Public: เข้าถึงได้จากภายนอก package
- Private: เข้าถึงได้เฉพาะภายใน package  
# Protected: เข้าถึงได้จาก package และ sub-packages
~ Package: เข้าถึงได้จาก package เดียวกัน
```

### 🏗️ การใช้งาน Package Diagram

#### **Code Organization**
- จัดกลุ่ม Classes ตาม functionality
- แยก Layers ในระบบ (Presentation, Business, Data)
- จัดการ Dependencies ระหว่าง modules

#### **System Architecture**
- แสดง Architectural layers
- แยก Core business logic จาก Infrastructure
- แสดง Reusable components

### 🎯 เมื่อไหร่ใช้ Package Diagram?
- **C3: Component Level**: แสดงการจัดกลุ่มภายใน Components
- **Code Structure**: วางแผน package structure ของโค้ด
- **Dependency Management**: แสดงและจัดการ dependencies
- **Team Organization**: แบ่งงานตาม package boundaries

---

## หน้า 19: Package Diagram - Agent Wallboard Code Structure

### 📦 Package Diagram สำหรับ Agent Wallboard System

#### **Package Organization Strategy:**
- **Layered Architecture**: แบ่งตาม architectural layers
- **Feature-based**: จัดกลุ่มตาม business features  
- **Shared Components**: แยก reusable components
- **External Dependencies**: แยก third-party packages

#### **Main Packages:**
- **presentation**: UI และ User interaction layers
- **business**: Core business logic และ domain models
- **data**: Data access และ persistence layers
- **infrastructure**: Cross-cutting concerns
- **shared**: Shared utilities และ common components

### 📋 Draw.io Code สำหรับ Package Diagram

```xml
<mxGraphModel dx="1422" dy="794" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="827" pageHeight="1169">
  <root>
    <mxCell id="0"/>
    <mxCell id="1" parent="0"/>
    
    <!-- Main Application Package -->
    <mxCell id="agentWallboard" value="agentWallboard" style="shape=folder;fontStyle=1;spacingTop=10;tabWidth=40;tabHeight=14;tabPosition=left;html=1;fillColor=#f8cecc;strokeColor=#b85450;fontSize=14;" vertex="1" parent="1">
      <mxGeometry x="200" y="40" width="500" height="600" as="geometry"/>
    </mxCell>
    
    <!-- Presentation Layer -->
    <mxCell id="presentation" value="presentation" style="shape=folder;fontStyle=1;spacingTop=10;tabWidth=60;tabHeight=14;tabPosition=left;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="1">
      <mxGeometry x="220" y="80" width="200" height="140" as="geometry"/>
    </mxCell>
    
    <!-- Presentation Sub-packages -->
    <mxCell id="desktop" value="desktop&#xa;&#xa;+AgentDesktopApp&#xa;+StatusController&#xa;+MessageView&#xa;+NotificationManager" style="shape=folder;fontStyle=0;spacingTop=10;tabWidth=50;tabHeight=14;tabPosition=left;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;fontSize=10;" vertex="1" parent="1">
      <mxGeometry x="230" y="110" width="80" height="80" as="geometry"/>
    </mxCell>
    
    <mxCell id="web" value="web&#xa;&#xa;+SupervisorDashboard&#xa;+RealtimeMonitor&#xa;+TeamManagement&#xa;+ReportingView" style="shape=folder;fontStyle=0;spacingTop=10;tabWidth=40;tabHeight=14;tabPosition=left;html=1;fillColor=#fff2cc;strokeColor=#d6b656;fontSize=10;" vertex="1" parent="1">
      <mxGeometry x="320" y="110" width="80" height="80" as="geometry"/>
    </mxCell>
    
    <!-- Business Layer -->
    <mxCell id="business" value="business" style="shape=folder;fontStyle=1;spacingTop=10;tabWidth=60;tabHeight=14;tabPosition=left;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="1">
      <mxGeometry x="450" y="80" width="200" height="180" as="geometry"/>
    </mxCell>
    
    <!-- Business Sub-packages -->
    <mxCell id="domain" value="domain&#xa;&#xa;+Agent&#xa;+Supervisor&#xa;+Team&#xa;+AgentStatus&#xa;+Message" style="shape=folder;fontStyle=0;spacingTop=10;tabWidth=50;tabHeight=14;tabPosition=left;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;fontSize=10;" vertex="1" parent="1">
      <mxGeometry x="460" y="110" width="80" height="70" as="geometry"/>
    </mxCell>
    
    <mxCell id="services" value="services&#xa;&#xa;+AuthService&#xa;+StatusService&#xa;+MessageService&#xa;+NotificationService&#xa;+TeamService" style="shape=folder;fontStyle=0;spacingTop=10;tabWidth=50;tabHeight=14;tabPosition=left;html=1;fillColor=#ffe6cc;strokeColor=#d79b00;fontSize=10;" vertex="1" parent="1">
      <mxGeometry x="550" y="110" width="80" height="70" as="geometry"/>
    </mxCell>
    
    <mxCell id="workflows" value="workflows&#xa;&#xa;+StatusChangeWorkflow&#xa;+MessageWorkflow&#xa;+AuthWorkflow&#xa;+ReportingWorkflow" style="shape=folder;fontStyle=0;spacingTop=10;tabWidth=55;tabHeight=14;tabPosition=left;html=1;fillColor=#f0f8ff;strokeColor=#4169e1;fontSize=10;" vertex="1" parent="1">
      <mxGeometry x="460" y="190" width="80" height="60" as="geometry"/>
    </mxCell>
    
    <mxCell id="validators" value="validators&#xa;&#xa;+AgentValidator&#xa;+StatusValidator&#xa;+MessageValidator&#xa;+BusinessRules" style="shape=folder;fontStyle=0;spacingTop=10;tabWidth=55;tabHeight=14;tabPosition=left;html=1;fillColor=#fff2cc;strokeColor=#d6b656;fontSize=10;" vertex="1" parent="1">
      <mxGeometry x="550" y="190" width="80" height="60" as="geometry"/>
    </mxCell>
    
    <!-- Data Layer -->
    <mxCell id="data" value="data" style="shape=folder;fontStyle=1;spacingTop=10;tabWidth=60;tabHeight=14;tabPosition=left;html=1;fillColor=#f8cecc;strokeColor=#b85450;" vertex="1" parent="1">
      <mxGeometry x="220" y="280" width="200" height="140" as="geometry"/>
    </mxCell>
    
    <!-- Data Sub-packages -->
    <mxCell id="repositories" value="repositories&#xa;&#xa;+AgentRepository&#xa;+TeamRepository&#xa;+MessageRepository&#xa;+StatusLogRepository" style="shape=folder;fontStyle=0;spacingTop=10;tabWidth=70;tabHeight=14;tabPosition=left;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;fontSize=10;" vertex="1" parent="1">
      <mxGeometry x="230" y="310" width="80" height="70" as="geometry"/>
    </mxCell>
    
    <mxCell id="datasources" value="datasources&#xa;&#xa;+MongoConnection&#xa;+MSSQLConnection&#xa;+RedisConnection&#xa;+ConnectionPool" style="shape=folder;fontStyle=0;spacingTop=10;tabWidth=70;tabHeight=14;tabPosition=left;html=1;fillColor=#ffe6cc;strokeColor=#d79b00;fontSize=10;" vertex="1" parent="1">
      <mxGeometry x="320" y="310" width="80" height="70" as="geometry"/>
    </mxCell>
    
    <mxCell id="mappers" value="mappers&#xa;&#xa;+AgentMapper&#xa;+StatusMapper&#xa;+MessageMapper&#xa;+DTOMappers" style="shape=folder;fontStyle=0;spacingTop=10;tabWidth=55;tabHeight=14;tabPosition=left;html=1;fillColor=#f0f8ff;strokeColor=#4169e1;fontSize=10;" vertex="1" parent="1">
      <mxGeometry x="230" y="390" width="80" height="60" as="geometry"/>
    </mxCell>
    
    <mxCell id="migrations" value="migrations&#xa;&#xa;+DatabaseSetup&#xa;+SchemaUpdates&#xa;+SeedData&#xa;+VersionControl" style="shape=folder;fontStyle=0;spacingTop=10;tabWidth=55;tabHeight=14;tabPosition=left;html=1;fillColor=#fff2cc;strokeColor=#d6b656;fontSize=10;" vertex="1" parent="1">
      <mxGeometry x="320" y="390" width="80" height="60" as="geometry"/>
    </mxCell>
    
    <!-- Infrastructure Layer -->
    <mxCell id="infrastructure" value="infrastructure" style="shape=folder;fontStyle=1;spacingTop=10;tabWidth=80;tabHeight=14;tabPosition=left;html=1;fillColor=#ffe6cc;strokeColor=#d79b00;" vertex="1" parent="1">
      <mxGeometry x="450" y="280" width="200" height="140" as="geometry"/>
    </mxCell>
    
    <!-- Infrastructure Sub-packages -->
    <mxCell id="communication" value="communication&#xa;&#xa;+WebSocketManager&#xa;+HTTPClient&#xa;+MessageQueue&#xa;+EventBus" style="shape=folder;fontStyle=0;spacingTop=10;tabWidth=80;tabHeight=14;tabPosition=left;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;fontSize=10;" vertex="1" parent="1">
      <mxGeometry x="460" y="310" width="80" height="60" as="geometry"/>
    </mxCell>
    
    <mxCell id="security" value="security&#xa;&#xa;+JWTManager&#xa;+PasswordHash&#xa;+RoleManager&#xa;+AuthMiddleware" style="shape=folder;fontStyle=0;spacingTop=10;tabWidth=55;tabHeight=14;tabPosition=left;html=1;fillColor=#f8cecc;strokeColor=#b85450;fontSize=10;" vertex="1" parent="1">
      <mxGeometry x="550" y="310" width="80" height="60" as="geometry"/>
    </mxCell>
    
    <mxCell id="logging" value="logging&#xa;&#xa;+Logger&#xa;+AuditLogger&#xa;+PerformanceMonitor&#xa;+ErrorHandler" style="shape=folder;fontStyle=0;spacingTop=10;tabWidth=50;tabHeight=14;tabPosition=left;html=1;fillColor=#d5e8d4;strokeColor=#82b366;fontSize=10;" vertex="1" parent="1">
      <mxGeometry x="460" y="380" width="80" height="60" as="geometry"/>
    </mxCell>
    
    <mxCell id="config" value="config&#xa;&#xa;+AppSettings&#xa;+DatabaseConfig&#xa;+EnvironmentConfig&#xa;+Constants" style="shape=folder;fontStyle=0;spacingTop=10;tabWidth=45;tabHeight=14;tabPosition=left;html=1;fillColor=#fff2cc;strokeColor=#d6b656;fontSize=10;" vertex="1" parent="1">
      <mxGeometry x="550" y="380" width="80" height="60" as="geometry"/>
    </mxCell>
    
    <!-- Shared Components -->
    <mxCell id="shared" value="shared" style="shape=folder;fontStyle=1;spacingTop=10;tabWidth=50;tabHeight=14;tabPosition=left;html=1;fillColor=#f0f8ff;strokeColor=#4169e1;" vertex="1" parent="1">
      <mxGeometry x="220" y="460" width="430" height="120" as="geometry"/>
    </mxCell>
    
    <mxCell id="utils" value="utils&#xa;&#xa;+DateHelper&#xa;+StringUtils&#xa;+ValidationUtils&#xa;+Crypto" style="shape=folder;fontStyle=0;spacingTop=10;tabWidth=40;tabHeight=14;tabPosition=left;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;fontSize=10;" vertex="1" parent="1">
      <mxGeometry x="230" y="490" width="70" height="60" as="geometry"/>
    </mxCell>
    
    <mxCell id="constants" value="constants&#xa;&#xa;+StatusConstants&#xa;+MessageTypes&#xa;+ErrorCodes&#xa;+URLs" style="shape=folder;fontStyle=0;spacingTop=10;tabWidth=55;tabHeight=14;tabPosition=left;html=1;fillColor=#ffe6cc;strokeColor=#d79b00;fontSize=10;" vertex="1" parent="1">
      <mxGeometry x="310" y="490" width="70" height="60" as="geometry"/>
    </mxCell>
    
    <mxCell id="types" value="types&#xa;&#xa;+Interfaces&#xa;+DTOs&#xa;+Enums&#xa;+ValueObjects" style="shape=folder;fontStyle=0;spacingTop=10;tabWidth=40;tabHeight=14;tabPosition=left;html=1;fillColor=#f8cecc;strokeColor=#b85450;fontSize=10;" vertex="1" parent="1">
      <mxGeometry x="390" y="490" width="70" height="60" as="geometry"/>
    </mxCell>
    
    <mxCell id="exceptions" value="exceptions&#xa;&#xa;+BusinessException&#xa;+ValidationException&#xa;+DataException&#xa;+SystemException" style="shape=folder;fontStyle=0;spacingTop=10;tabWidth=65;tabHeight=14;tabPosition=left;html=1;fillColor=#d5e8d4;strokeColor=#82b366;fontSize=10;" vertex="1" parent="1">
      <mxGeometry x="470" y="490" width="80" height="60" as="geometry"/>
    </mxCell>
    
    <mxCell id="testUtils" value="testUtils&#xa;&#xa;+MockData&#xa;+TestHelpers&#xa;+Fixtures&#xa;+Builders" style="shape=folder;fontStyle=0;spacingTop=10;tabWidth=55;tabHeight=14;tabPosition=left;html=1;fillColor=#fff2cc;strokeColor=#d6b656;fontSize=10;" vertex="1" parent="1">
      <mxGeometry x="560" y="490" width="70" height="60" as="geometry"/>
    </mxCell>
    
    <!-- External Dependencies -->
    <mxCell id="external" value="&lt;&lt;external&gt;&gt;" style="shape=folder;fontStyle=1;spacingTop=10;tabWidth=60;tabHeight=14;tabPosition=left;html=1;fillColor=#f5f5f5;strokeColor=#666666;dashed=1;" vertex="1" parent="1">
      <mxGeometry x="40" y="200" width="120" height="300" as="geometry"/>
    </mxCell>
    
    <mxCell id="electron" value="electron&#xa;&#xa;Desktop App&#xa;Framework" style="shape=folder;fontStyle=0;spacingTop=10;tabWidth=50;tabHeight=14;tabPosition=left;html=1;fillColor=#f5f5f5;strokeColor=#666666;fontSize=10;dashed=1;" vertex="1" parent="1">
      <mxGeometry x="50" y="230" width="60" height="40" as="geometry"/>
    </mxCell>
    
    <mxCell id="react" value="react&#xa;&#xa;Web UI&#xa;Framework" style="shape=folder;fontStyle=0;spacingTop=10;tabWidth=40;tabHeight=14;tabPosition=left;html=1;fillColor=#f5f5f5;strokeColor=#666666;fontSize=10;dashed=1;" vertex="1" parent="1">
      <mxGeometry x="50" y="280" width="60" height="40" as="geometry"/>
    </mxCell>
    
    <mxCell id="express" value="express&#xa;&#xa;Web Server&#xa;Framework" style="shape=folder;fontStyle=0;spacingTop=10;tabWidth=50;tabHeight=14;tabPosition=left;html=1;fillColor=#f5f5f5;strokeColor=#666666;fontSize=10;dashed=1;" vertex="1" parent="1">
      <mxGeometry x="50" y="330" width="60" height="40" as="geometry"/>
    </mxCell>
    
    <mxCell id="socketio" value="socket.io&#xa;&#xa;WebSocket&#xa;Library" style="shape=folder;fontStyle=0;spacingTop=10;tabWidth=55;tabHeight=14;tabPosition=left;html=1;fillColor=#f5f5f5;strokeColor=#666666;fontSize=10;dashed=1;" vertex="1" parent="1">
      <mxGeometry x="50" y="380" width="60" height="40" as="geometry"/>
    </mxCell>
    
    <mxCell id="mongoose" value="mongoose&#xa;&#xa;MongoDB&#xa;ODM" style="shape=folder;fontStyle=0;spacingTop=10;tabWidth=55;tabHeight=14;tabPosition=left;html=1;fillColor=#f5f5f5;strokeColor=#666666;fontSize=10;dashed=1;" vertex="1" parent="1">
      <mxGeometry x="50" y="430" width="60" height="40" as="geometry"/>
    </mxCell>
    
    <!-- Package Dependencies -->
    <!-- Presentation -> Business -->
    <mxCell value="&lt;&lt;import&gt;&gt;" style="endArrow=open;endSize=12;dashed=1;html=1;dashPattern=5 5;" edge="1" parent="1" source="presentation" target="business">
      <mxGeometry width="160" relative="1" as="geometry"/>
    </mxCell>
    
    <!-- Business -> Data -->
    <mxCell value="&lt;&lt;import&gt;&gt;" style="endArrow=open;endSize=12;dashed=1;html=1;dashPattern=5 5;" edge="1" parent="1" source="business" target="data">
      <mxGeometry width="160" relative="1" as="geometry"/>
    </mxCell>
    
    <!-- Business -> Infrastructure -->
    <mxCell value="&lt;&lt;import&gt;&gt;" style="endArrow=open;endSize=12;dashed=1;html=1;dashPattern=5 5;" edge="1" parent="1" source="business" target="infrastructure">
      <mxGeometry width="160" relative="1" as="geometry"/>
    </mxCell>
    
    <!-- All layers -> Shared -->
    <mxCell value="&lt;&lt;import&gt;&gt;" style="endArrow=open;endSize=12;dashed=1;html=1;dashPattern=5 5;" edge="1" parent="1" source="presentation" target="shared">
      <mxGeometry width="160" relative="1" as="geometry"/>
    </mxCell>
    
    <mxCell value="&lt;&lt;import&gt;&gt;" style="endArrow=open;endSize=12;dashed=1;html=1;dashPattern=5 5;" edge="1" parent="1" source="data" target="shared">
      <mxGeometry width="160" relative="1" as="geometry"/>
    </mxCell>
    
    <mxCell value="&lt;&lt;import&gt;&gt;" style="endArrow=open;endSize=12;dashed=1;html=1;dashPattern=5 5;" edge="1" parent="1" source="infrastructure" target="shared">
      <mxGeometry width="160" relative="1" as="geometry"/>
    </mxCell>
    
    <!-- External Dependencies -->
    <mxCell value="&lt;&lt;access&gt;&gt;" style="endArrow=open;endSize=12;dashed=1;html=1;dashPattern=5 5;" edge="1" parent="1" source="desktop" target="electron">
      <mxGeometry width="160" relative="1" as="geometry"/>
    </mxCell>
    
    <mxCell value="&lt;&lt;access&gt;&gt;" style="endArrow=open;endSize=12;dashed=1;html=1;dashPattern=5 5;" edge="1" parent="1" source="web" target="react">
      <mxGeometry width="160" relative="1" as="geometry"/>
    </mxCell>
    
    <mxCell value="&lt;&lt;access&gt;&gt;" style="endArrow=open;endSize=12;dashed=1;html=1;dashPattern=5 5;" edge="1" parent="1" source="communication" target="socketio">
      <mxGeometry width="160" relative="1" as="geometry"/>
    </mxCell>
    
    <mxCell value="&lt;&lt;access&gt;&gt;" style="endArrow=open;endSize=12;dashed=1;html=1;dashPattern=5 5;" edge="1" parent="1" source="datasources" target="mongoose">
      <mxGeometry width="160" relative="1" as="geometry"/>
    </mxCell>
    
  </root>
</mxGraphModel>
```

### 💡 จุดเด่นของ Package Diagram นี้
- **Layered Architecture**: แบ่งชั้นชัดเจนตาม architectural patterns
- **Separation of Concerns**: แยกหน้าที่ของแต่ละ package
- **Dependency Direction**: แสดงทิศทางการพึ่งพาที่ถูกต้อง
- **Shared Components**: แยก reusable components ให้ชัดเจน
- **External Dependencies**: แสดงการพึ่งพา third-party libraries

---

## หน้า 20: สรุปและแนวทางการประยุกต์ใช้

### 🎯 สรุป UML Diagrams ทั้ง 6 ประเภท

| **Diagram** | **จุดประสงค์หลัก** | **C4 Level** | **SDLC Phase** | **ผู้ใช้หลัก** |
|------------|-----------------|-------------|---------------|-------------|
| **Use Case** | แสดงฟังก์ชันระบบและ Actors | C1 Context | Requirements | BA, Stakeholders |
| **Activity** | แสดง Business Process Flow | All Levels | Requirements/Design | BA, Developers |
| **Class** | แสดงโครงสร้าง Objects | C3/C4 | Design/Implementation | Developers, Architects |
| **Sequence** | แสดงลำดับการสื่อสาร | C3/C4 | Design/Testing | Developers, Testers |
| **State Machine** | แสดงการเปลี่ยนสถานะ | C4 | Design/Implementation | Developers |
| **Component** | แสดงโครงสร้างระบบ | C2/C3 | Architecture/Design | Architects |
| **Deployment** | แสดงการติดตั้งระบบ | Infrastructure | Deployment | DevOps, Architects |
| **Package** | แสดงการจัดองค์กร | C3/C4 | Design/Implementation | Developers, Architects |

### 🔄 Workflow การใช้ UML Diagrams

#### **Phase 1: Requirements Analysis**
1. **Use Case Diagram** - ระบุ Actors และฟังก์ชันหลัก
2. **Activity Diagram** - วิเคราะห์ Business Process
3. **Validation** - ตรวจสอบความถูกต้องกับ Stakeholders

#### **Phase 2: System Design**
1. **Component Diagram** - ออกแบบ Architecture ระดับสูง
2. **Package Diagram** - จัดองค์กร Code structure  
3. **Class Diagram** - ออกแบบ Domain model
4. **State Machine** - ออกแบบ Complex state behaviors

#### **Phase 3: Detailed Design**
1. **Sequence Diagram** - ออกแบบ Method interactions
2. **Refined Class Diagram** - เพิ่มรายละเอียด Methods และ Attributes
3. **Component Interfaces** - ระบุ APIs และ Contracts

#### **Phase 4: Implementation & Deployment**
1. **Code Generation** - จาก Class และ Component diagrams
2. **Deployment Diagram** - วางแผนการติดตั้งระบบจริง
3. **Testing** - ใช้ Sequence diagrams สำหรับ Test scenarios

### 🚀 Best Practices สำหรับการใช้ UML

#### **1. เลือก Diagram ที่เหมาะสม**
- ไม่ต้องใช้ทุก Diagram ในทุกโครงการ
- เลือกตาม complexity และ requirements ของโครงการ
- มุ่งเน้น value ที่จะได้รับ ไม่ใช่การวาด Diagram ให้สวย

#### **2. Keep It Simple**
- เริ่มจาก high-level แล้วค่อยลงรายละเอียด
- หลีกเลี่ยงการใส่รายละเอียดมากเกินไปในภาพเดียว
- ใช้ abstraction ให้เหมาะสมกับผู้ดู

#### **3. Maintain Consistency**
- ใช้ naming conventions เดียวกันทั้งโครงการ
- ใช้สีและรูปแบบให้สอดคล้องกัน
- Update diagrams เมื่อมีการเปลี่ยนแปลง requirements

#### **4. Focus on Communication**
- Diagram ต้องช่วยให้ทีมเข้าใจระบบได้ง่ายขึ้น
- เพิ่ม notes และ descriptions เมื่อจำเป็น
- ทำ diagram review กับทีมอย่างสม่ำเสมอ

### 🛠️ Tools และ Resources

#### **Recommended Tools:**
- **Draw.io (diagrams.net)**: ฟรี, browser-based, รองรับ UML symbols
- **Lucidchart**: Professional diagramming tool
- **PlantUML**: Text-based UML generation
- **Enterprise Architect**: Professional UML modeling tool
- **Visual Paradigm**: Complete CASE tool

#### **Learning Resources:**
- UML 2.5 Specification (OMG)
- "UML Distilled" by Martin Fowler
- "Applying UML and Patterns" by Craig Larman
- Online UML tutorials และ documentation

### 📝 แนวทางการประเมินผล

#### **การประเมิน UML Diagrams:**
1. **Correctness** - ความถูกต้องของสัญลักษณ์และ syntax
2. **Completeness** - ความครบถ้วนของข้อมูลที่จำเป็น
3. **Consistency** - ความสอดคล้องระหว่าง diagrams
4. **Clarity** - ความชัดเจนในการสื่อสาร
5. **Traceability** - การเชื่อมโยงระหว่าง requirements และ design

#### **เกณฑ์การให้คะแนน:**
- **Excellent (A)**: ใช้ UML ได้ถูกต้อง มีการวิเคราะห์เชิงลึก
- **Good (B)**: ใช้ UML ได้ถูกต้อง แต่ยังขาดรายละเอียดบางส่วน
- **Satisfactory (C)**: ใช้ UML ได้พอใช้ แต่มีข้อผิดพลาดบ้าง
- **Needs Improvement (D)**: มีข้อผิดพลาดหลายจุด ต้องปรับปรุง

### 🎊 บทสรุป

การใช้ UML Diagrams อย่างมีประสิทธิภาพช่วยให้:
- **สื่อสารได้ชัดเจน** ระหว่างทีมพัฒนา
- **ลดความเสี่ยง** จากการเข้าใจผิด requirements
- **เพิ่มคุณภาพ** ของการออกแบบระบบ
- **ประหยัดเวลา** ในการพัฒนาและ maintenance
- **สร้าง documentation** ที่มีคุณภาพ

Agent Wallboard Management System เป็น case study ที่ดีสำหรับการเรียนรู้ UML เนื่องจาก:
- มี **ความซับซ้อนที่พอเหมาะ** สำหรับการศึกษา
- ครอบคลุม **หลาก use cases** และ user types
- เป็น **ระบบจริง** ที่ใช้ในองค์กรจริง
- แสดง **modern architecture** และ technology stack

**สำหรับนักศึกษา**: ให้นำความรู้ที่ได้ไปประยุกต์ใช้ในโครงการจริง โดยเริ่มจากการวิเคราะห์ requirements ด้วย Use Case Diagram แล้วค่อยลงรายละเอียดตาม SDLC phases

**ขอให้นักศึกษาประสบความสำเร็จในการเรียนรู้และการพัฒนา Software Engineering skills! 🚀**

---

