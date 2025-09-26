# Agent Wallboard System - UML Diagrams Collection
## สำหรับ C4 Model Design (C1-C4) | ENGSE206 - RMUTL

---

## 1. C1 (Context Level) - System Context Diagram

**ใช้กับ:** การแสดงระบบในมุมมองภาพรวม, Stakeholders, External Systems

```xml
<mxfile host="app.diagrams.net">
  <diagram name="C1-Context-Diagram" id="context">
    <mxGraphModel dx="1422" dy="794" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="827" pageHeight="1169">
      <root>
        <mxCell id="0"/>
        <mxCell id="1" parent="0"/>
        
        <!-- Title -->
        <mxCell id="title-1" value="Agent Wallboard System - C1 Context Diagram" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontStyle=1;fontSize=16;" vertex="1" parent="1">
          <mxGeometry x="200" y="10" width="400" height="30" as="geometry"/>
        </mxCell>

        <!-- Central System -->
        <mxCell id="system-1" value="&#128187;&#xFE0F; Agent Wallboard System&#10;&#10;Real-time agent status monitoring&#10;and communication platform&#10;for call center operations" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;strokeWidth=3;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="300" y="300" width="250" height="120" as="geometry"/>
        </mxCell>

        <!-- Actors -->
        <mxCell id="agent-1" value="&#128100; Agent&#10;Call Center Staff" style="shape=umlActor;verticalLabelPosition=bottom;verticalAlign=top;html=1;outlineConnect=0;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="1">
          <mxGeometry x="80" y="180" width="30" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="supervisor-1" value="&#128104;&#x200D;&#128188; Supervisor&#10;Team Manager" style="shape=umlActor;verticalLabelPosition=bottom;verticalAlign=top;html=1;outlineConnect=0;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="1">
          <mxGeometry x="80" y="340" width="30" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="manager-1" value="&#128084; Operations Manager&#10;Department Head" style="shape=umlActor;verticalLabelPosition=bottom;verticalAlign=top;html=1;outlineConnect=0;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="1">
          <mxGeometry x="80" y="500" width="30" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="admin-1" value="⚙️ System Admin&#10;IT Personnel" style="shape=umlActor;verticalLabelPosition=bottom;verticalAlign=top;html=1;outlineConnect=0;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="1">
          <mxGeometry x="680" y="340" width="30" height="60" as="geometry"/>
        </mxCell>

        <!-- External Systems -->
        <mxCell id="fileshare-1" value="&#128193; File Share&#10;Network Storage&#10;Report Archive" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;" vertex="1" parent="1">
          <mxGeometry x="500" y="100" width="120" height="80" as="geometry"/>
        </mxCell>

        <mxCell id="backup-1" value="&#128190; Backup System&#10;Automated Database&#10;Backup Service" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;" vertex="1" parent="1">
          <mxGeometry x="500" y="500" width="120" height="80" as="geometry"/>
        </mxCell>

        <!-- Relationships -->
        <mxCell id="rel1" value="Uses desktop app&#10;Changes status&#10;Receives messages" style="endArrow=classic;html=1;entryX=0;entryY=0.25;" edge="1" parent="1" source="agent-1" target="system-1">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="rel2" value="Monitors team&#10;Sends messages&#10;Views dashboard" style="endArrow=classic;html=1;entryX=0;entryY=0.5;" edge="1" parent="1" source="supervisor-1" target="system-1">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="rel3" value="Reviews reports&#10;Analyzes performance&#10;Makes decisions" style="endArrow=classic;html=1;entryX=0;entryY=0.75;" edge="1" parent="1" source="manager-1" target="system-1">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="rel4" value="Manages system&#10;Configures settings&#10;Maintains users" style="endArrow=classic;html=1;entryX=1;entryY=0.5;" edge="1" parent="1" source="admin-1" target="system-1">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="rel5" value="Stores reports&#10;[SMB/File Copy]" style="endArrow=classic;html=1;exitX=0.5;exitY=0;" edge="1" parent="1" source="system-1" target="fileshare-1">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="rel6" value="Backup data&#10;[Database dumps]" style="endArrow=classic;html=1;exitX=0.5;exitY=1;" edge="1" parent="1" source="system-1" target="backup-1">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>
      </root>
    </mxGraphModel>
  </diagram>
</mxfile>
```

---

## 2. C2 (Container Level) - Container Architecture Diagram

**ใช้กับ:** การแสดง Technology Stack, Applications, และ Communication Protocols

```xml
<mxfile host="app.diagrams.net">
  <diagram name="C2-Container-Diagram" id="container">
    <mxGraphModel dx="1422" dy="1169" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="1169" pageHeight="827">
      <root>
        <mxCell id="0"/>
        <mxCell id="1" parent="0"/>
        
        <!-- Title -->
        <mxCell id="title-2" value="Agent Wallboard System - C2 Container Architecture Diagram" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontStyle=1;fontSize=16;" vertex="1" parent="1">
          <mxGeometry x="250" y="10" width="500" height="30" as="geometry"/>
        </mxCell>

        <!-- System Boundary -->
        <mxCell id="boundary-2" value="Agent Wallboard System" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f5f5f5;strokeColor=#666666;strokeWidth=2;dashed=1;verticalAlign=top;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="50" y="80" width="900" height="500" as="geometry"/>
        </mxCell>

        <!-- Frontend Containers -->
        <mxCell id="desktop-app-2" value="&#128187;&#xFE0F; Agent Desktop App&#10;---&#10;Technology: Electron + React&#10;Responsibilities:&#10;- Agent status management&#10;- Message receiving&#10;- Desktop notifications&#10;- Simple UI for agents" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="80" y="120" width="200" height="120" as="geometry"/>
        </mxCell>

        <mxCell id="web-dashboard-2" value="&#127760; Web Dashboard&#10;---&#10;Technology: React + Material-UI&#10;Responsibilities:&#10;- Team monitoring dashboard&#10;- Message sending interface&#10;- Performance analytics&#10;- Report generation" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="320" y="120" width="200" height="120" as="geometry"/>
        </mxCell>

        <mxCell id="admin-panel-2" value="⚙️ Admin Panel&#10;---&#10;Technology: React + Admin UI&#10;Responsibilities:&#10;- User management (CRUD)&#10;- System configuration&#10;- Basic system monitoring&#10;- Simple admin tools" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="560" y="120" width="200" height="120" as="geometry"/>
        </mxCell>

        <!-- Backend Containers -->
        <mxCell id="api-server-2" value="&#128295; API Server&#10;---&#10;Technology: Node.js + Express&#10;Responsibilities:&#10;- REST API endpoints&#10;- Business logic&#10;- Simple authentication (JWT)&#10;- Data validation" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="200" y="300" width="200" height="120" as="geometry"/>
        </mxCell>

        <mxCell id="websocket-server-2" value="⚡ WebSocket Server&#10;---&#10;Technology: Socket.io&#10;Responsibilities:&#10;- Real-time status updates&#10;- Message broadcasting&#10;- Live notifications&#10;- Connection management" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="440" y="300" width="200" height="120" as="geometry"/>
        </mxCell>

        <!-- Database Containers -->
        <mxCell id="sql-server-2" value="&#128451;&#xFE0F; SQL Server Database&#10;---&#10;Technology: Microsoft SQL Server&#10;Responsibilities:&#10;- User accounts &amp; teams&#10;- System configuration&#10;- Audit logs&#10;- Master data" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="130" y="480" width="200" height="80" as="geometry"/>
        </mxCell>

        <mxCell id="mongodb-2" value="&#128195; MongoDB Database&#10;---&#10;Technology: MongoDB&#10;Responsibilities:&#10;- Agent status &amp; history&#10;- Messages &amp; conversations&#10;- Performance metrics&#10;- Real-time data" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="500" y="480" width="200" height="80" as="geometry"/>
        </mxCell>

        <!-- External Users -->
        <mxCell id="user-agent-2" value="&#128100; Agent" style="shape=umlActor;verticalLabelPosition=bottom;verticalAlign=top;html=1;outlineConnect=0;" vertex="1" parent="1">
          <mxGeometry x="30" y="40" width="20" height="40" as="geometry"/>
        </mxCell>

        <mxCell id="user-supervisor-2" value="&#128104;&#x200D;&#128188; Supervisor" style="shape=umlActor;verticalLabelPosition=bottom;verticalAlign=top;html=1;outlineConnect=0;" vertex="1" parent="1">
          <mxGeometry x="270" y="40" width="20" height="40" as="geometry"/>
        </mxCell>

        <mxCell id="user-admin-2" value="⚙️ Admin" style="shape=umlActor;verticalLabelPosition=bottom;verticalAlign=top;html=1;outlineConnect=0;" vertex="1" parent="1">
          <mxGeometry x="550" y="40" width="20" height="40" as="geometry"/>
        </mxCell>

        <!-- External Systems -->
        <mxCell id="file-share-2" value="&#128193; File Share" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;" vertex="1" parent="1">
          <mxGeometry x="800" y="300" width="100" height="60" as="geometry"/>
        </mxCell>

        <!-- Connections -->
        <mxCell id="conn1-2" value="Desktop Application&#10;HTTP/WebSocket" style="endArrow=classic;html=1;" edge="1" parent="1" source="user-agent-2" target="desktop-app-2">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn2-2" value="Web Browser&#10;HTTPS/WebSocket" style="endArrow=classic;html=1;" edge="1" parent="1" source="user-supervisor-2" target="web-dashboard-2">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn3-2" value="Web Browser&#10;HTTPS" style="endArrow=classic;html=1;" edge="1" parent="1" source="user-admin-2" target="admin-panel-2">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn4-2" value="REST API&#10;HTTP/JSON" style="endArrow=classic;html=1;" edge="1" parent="1" source="desktop-app-2" target="api-server-2">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn5-2" value="Real-time Updates&#10;WebSocket" style="endArrow=classic;html=1;" edge="1" parent="1" source="desktop-app-2" target="websocket-server-2">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn6-2" value="REST API&#10;HTTP/JSON" style="endArrow=classic;html=1;" edge="1" parent="1" source="web-dashboard-2" target="api-server-2">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn7-2" value="Real-time Updates&#10;WebSocket" style="endArrow=classic;html=1;" edge="1" parent="1" source="web-dashboard-2" target="websocket-server-2">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn8-2" value="SQL Queries&#10;Connection Pool" style="endArrow=classic;html=1;" edge="1" parent="1" source="api-server-2" target="sql-server-2">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn9-2" value="Document Operations&#10;MongoDB Driver" style="endArrow=classic;html=1;" edge="1" parent="1" source="api-server-2" target="mongodb-2">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn10-2" value="Real-time Data&#10;MongoDB Driver" style="endArrow=classic;html=1;" edge="1" parent="1" source="websocket-server-2" target="mongodb-2">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn11-2" value="File Export&#10;Simple File Copy" style="endArrow=classic;html=1;" edge="1" parent="1" source="api-server-2" target="file-share-2">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>
      </root>
    </mxGraphModel>
  </diagram>
</mxfile>
```

---

## 3. C3 (Component Level) - Component Diagram

**ใช้กับ:** การแสดง Internal Components ภายใน Container และ Interface ระหว่าง Components

```xml
<mxfile host="app.diagrams.net">
  <diagram name="C3-Component-Diagram" id="component">
    <mxGraphModel dx="1422" dy="794" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="1169" pageHeight="827">
      <root>
        <mxCell id="0"/>
        <mxCell id="1" parent="0"/>
        
        <!-- Title -->
        <mxCell id="title-3" value="Agent Wallboard System - C3 Component Diagram (Backend Components)" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontStyle=1;fontSize=16;" vertex="1" parent="1">
          <mxGeometry x="200" y="10" width="600" height="30" as="geometry"/>
        </mxCell>

        <!-- API Server Container -->
        <mxCell id="api-container-3" value="API Server Container" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;strokeWidth=2;dashed=1;verticalAlign=top;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="50" y="70" width="450" height="350" as="geometry"/>
        </mxCell>

        <!-- Controllers Layer -->
        <mxCell id="controllers-layer-3" value="Controllers Layer" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;strokeWidth=1;dashed=1;verticalAlign=top;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="70" y="100" width="410" height="100" as="geometry"/>
        </mxCell>

        <mxCell id="auth-controller-3" value="AuthController&#10;&#128273; Authentication &amp; Login" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#e3f2fd;strokeColor=#1976d2;" vertex="1" parent="1">
          <mxGeometry x="90" y="130" width="110" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="agent-controller-3" value="AgentController&#10;&#128100; Agent Status Management" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#e3f2fd;strokeColor=#1976d2;" vertex="1" parent="1">
          <mxGeometry x="220" y="130" width="110" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="message-controller-3" value="MessageController&#10;&#128172; Message Handling" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#e3f2fd;strokeColor=#1976d2;" vertex="1" parent="1">
          <mxGeometry x="350" y="130" width="110" height="60" as="geometry"/>
        </mxCell>

        <!-- Services Layer -->
        <mxCell id="services-layer-3" value="Services Layer" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f3e5f5;strokeColor=#7b1fa2;strokeWidth=1;dashed=1;verticalAlign=top;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="70" y="220" width="250" height="100" as="geometry"/>
        </mxCell>

        <mxCell id="agent-service-3" value="AgentService&#10;&#128202; Business Logic" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f3e5f5;strokeColor=#7b1fa2;" vertex="1" parent="1">
          <mxGeometry x="90" y="250" width="100" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="message-service-3" value="MessageService&#10;&#128232; Message Processing" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f3e5f5;strokeColor=#7b1fa2;" vertex="1" parent="1">
          <mxGeometry x="200" y="250" width="100" height="60" as="geometry"/>
        </mxCell>

        <!-- Middleware -->
        <mxCell id="middleware-layer-3" value="Middleware" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fff3e0;strokeColor=#f57c00;strokeWidth=1;dashed=1;verticalAlign=top;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="340" y="220" width="140" height="100" as="geometry"/>
        </mxCell>

        <mxCell id="auth-middleware-3" value="AuthMiddleware&#10;&#128737;&#xFE0F; JWT Validation" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fff3e0;strokeColor=#f57c00;" vertex="1" parent="1">
          <mxGeometry x="350" y="240" width="120" height="35" as="geometry"/>
        </mxCell>

        <mxCell id="routes-3" value="Routes&#10;&#128739;&#xFE0F; API Endpoints" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fff3e0;strokeColor=#f57c00;" vertex="1" parent="1">
          <mxGeometry x="350" y="280" width="120" height="35" as="geometry"/>
        </mxCell>

        <!-- WebSocket Server Container -->
        <mxCell id="websocket-container-3" value="WebSocket Server Container" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#e8f5e8;strokeColor=#388e3c;strokeWidth=2;dashed=1;verticalAlign=top;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="550" y="70" width="350" height="350" as="geometry"/>
        </mxCell>

        <mxCell id="connection-handler-3" value="ConnectionHandler&#10;&#128268; Manage Connections" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#e8f5e8;strokeColor=#388e3c;" vertex="1" parent="1">
          <mxGeometry x="570" y="110" width="130" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="event-handlers-3" value="EventHandlers&#10;&#128225; Real-time Events" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#e8f5e8;strokeColor=#388e3c;" vertex="1" parent="1">
          <mxGeometry x="720" y="110" width="130" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="room-manager-3" value="RoomManager&#10;&#127968; Team Rooms" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#e8f5e8;strokeColor=#388e3c;" vertex="1" parent="1">
          <mxGeometry x="640" y="190" width="130" height="60" as="geometry"/>
        </mxCell>

        <!-- External Systems -->
        <mxCell id="frontend-3" value="Frontend Apps" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fce4ec;strokeColor=#c2185b;" vertex="1" parent="1">
          <mxGeometry x="200" y="20" width="120" height="40" as="geometry"/>
        </mxCell>

        <mxCell id="database-3" value="Databases" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fce4ec;strokeColor=#c2185b;" vertex="1" parent="1">
          <mxGeometry x="400" y="460" width="120" height="40" as="geometry"/>
        </mxCell>

        <!-- Connections -->
        <mxCell id="conn1-3" value="HTTP Requests" style="endArrow=classic;html=1;" edge="1" parent="1" source="frontend-3" target="routes-3">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn2-3" value="" style="endArrow=classic;html=1;" edge="1" parent="1" source="routes-3" target="auth-middleware-3">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn3-3" value="" style="endArrow=classic;html=1;" edge="1" parent="1" source="auth-middleware-3" target="auth-controller-3">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn4-3" value="" style="endArrow=classic;html=1;" edge="1" parent="1" source="auth-middleware-3" target="agent-controller-3">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn5-3" value="" style="endArrow=classic;html=1;" edge="1" parent="1" source="auth-middleware-3" target="message-controller-3">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn6-3" value="" style="endArrow=classic;html=1;" edge="1" parent="1" source="agent-controller-3" target="agent-service-3">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn7-3" value="" style="endArrow=classic;html=1;" edge="1" parent="1" source="message-controller-3" target="message-service-3">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn8-3" value="" style="endArrow=classic;html=1;" edge="1" parent="1" source="agent-service-3" target="database-3">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn9-3" value="" style="endArrow=classic;html=1;" edge="1" parent="1" source="message-service-3" target="database-3">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn10-3" value="WebSocket" style="endArrow=classic;html=1;" edge="1" parent="1" source="frontend-3" target="connection-handler-3">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn11-3" value="" style="endArrow=classic;html=1;" edge="1" parent="1" source="connection-handler-3" target="event-handlers-3">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn12-3" value="" style="endArrow=classic;html=1;" edge="1" parent="1" source="event-handlers-3" target="room-manager-3">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn13-3" value="" style="endArrow=classic;html=1;" edge="1" parent="1" source="event-handlers-3" target="database-3">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>
      </root>
    </mxGraphModel>
  </diagram>
</mxfile>
```

---

## 4. C4 (Code Level) - Class Diagram

**ใช้กับ:** การแสดง Class Structure, Methods, Properties, และ Relationships ในระดับ Implementation

```xml
<mxfile host="app.diagrams.net">
  <diagram name="C4-Class-Diagram" id="class">
    <mxGraphModel dx="1422" dy="794" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="1169" pageHeight="827">
      <root>
        <mxCell id="0"/>
        <mxCell id="1" parent="0"/>
        
        <!-- Title -->
        <mxCell id="title-4" value="Agent Wallboard System - C4 Class Diagram" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontStyle=1;fontSize=16;" vertex="1" parent="1">
          <mxGeometry x="300" y="10" width="400" height="30" as="geometry"/>
        </mxCell>

        <!-- AgentController Class -->
        <mxCell id="agent-controller-4" value="&lt;&lt;Controller&gt;&gt;&lt;br&gt;AgentController" style="swimlane;fontStyle=1;align=center;verticalAlign=top;childLayout=stackLayout;horizontal=1;startSize=40;horizontalStack=0;resizeParent=1;resizeParentMax=0;resizeLast=0;collapsible=1;marginBottom=0;fillColor=#e3f2fd;strokeColor=#1976d2;" vertex="1" parent="1">
          <mxGeometry x="50" y="70" width="220" height="200" as="geometry"/>
        </mxCell>
        <mxCell id="agent-controller-attributes-4" value="- agentService: AgentService&lt;br&gt;- authService: AuthService&lt;br&gt;- logger: Logger" style="text;strokeColor=none;fillColor=none;align=left;verticalAlign=top;spacingLeft=4;spacingRight=4;overflow=hidden;rotatable=0;points=[[0,0.5],[1,0.5]];portConstraint=eastwest;" vertex="1" parent="agent-controller-4">
          <mxGeometry y="40" width="220" height="60" as="geometry"/>
        </mxCell>
        <mxCell id="agent-controller-line-4" value="" style="line;strokeWidth=1;fillColor=none;align=left;verticalAlign=middle;spacingTop=-1;spacingLeft=3;spacingRight=3;rotatable=0;labelPosition=right;points=[];portConstraint=eastwest;" vertex="1" parent="agent-controller-4">
          <mxGeometry y="100" width="220" height="8" as="geometry"/>
        </mxCell>
        <mxCell id="agent-controller-methods-4" value="+ updateStatus(req, res): Promise&lt;void&gt;&lt;br&gt;+ getAgentStatus(req, res): Promise&lt;void&gt;&lt;br&gt;+ getStatusHistory(req, res): Promise&lt;void&gt;&lt;br&gt;- validateStatusTransition(): boolean&lt;br&gt;- handleError(error, res): void" style="text;strokeColor=none;fillColor=none;align=left;verticalAlign=top;spacingLeft=4;spacingRight=4;overflow=hidden;rotatable=0;points=[[0,0.5],[1,0.5]];portConstraint=eastwest;" vertex="1" parent="agent-controller-4">
          <mxGeometry y="108" width="220" height="92" as="geometry"/>
        </mxCell>

        <!-- AgentService Class -->
        <mxCell id="agent-service-4" value="&lt;&lt;Service&gt;&gt;&lt;br&gt;AgentService" style="swimlane;fontStyle=1;align=center;verticalAlign=top;childLayout=stackLayout;horizontal=1;startSize=40;horizontalStack=0;resizeParent=1;resizeParentMax=0;resizeLast=0;collapsible=1;marginBottom=0;fillColor=#f3e5f5;strokeColor=#7b1fa2;" vertex="1" parent="1">
          <mxGeometry x="320" y="70" width="250" height="220" as="geometry"/>
        </mxCell>
        <mxCell id="agent-service-attributes-4" value="- sqlRepository: SqlRepository&lt;br&gt;- mongoRepository: MongoRepository&lt;br&gt;- webSocketService: WebSocketService&lt;br&gt;- businessRules: BusinessRules" style="text;strokeColor=none;fillColor=none;align=left;verticalAlign=top;spacingLeft=4;spacingRight=4;overflow=hidden;rotatable=0;points=[[0,0.5],[1,0.5]];portConstraint=eastwest;" vertex="1" parent="agent-service-4">
          <mxGeometry y="40" width="250" height="70" as="geometry"/>
        </mxCell>
        <mxCell id="agent-service-line-4" value="" style="line;strokeWidth=1;fillColor=none;align=left;verticalAlign=middle;spacingTop=-1;spacingLeft=3;spacingRight=3;rotatable=0;labelPosition=right;points=[];portConstraint=eastwest;" vertex="1" parent="agent-service-4">
          <mxGeometry y="110" width="250" height="8" as="geometry"/>
        </mxCell>
        <mxCell id="agent-service-methods-4" value="+ updateAgentStatus(agentId, status): Promise&lt;AgentStatus&gt;&lt;br&gt;+ getAgentById(agentId): Promise&lt;Agent&gt;&lt;br&gt;+ getTeamAgents(teamId): Promise&lt;Agent[]&gt;&lt;br&gt;+ getStatusHistory(agentId, dateRange): Promise&lt;StatusHistory[]&gt;&lt;br&gt;- validateStatusChange(agent, newStatus): ValidationResult&lt;br&gt;- broadcastStatusUpdate(statusUpdate): Promise&lt;void&gt;&lt;br&gt;- logStatusChange(agentId, oldStatus, newStatus): Promise&lt;void&gt;" style="text;strokeColor=none;fillColor=none;align=left;verticalAlign=top;spacingLeft=4;spacingRight=4;overflow=hidden;rotatable=0;points=[[0,0.5],[1,0.5]];portConstraint=eastwest;" vertex="1" parent="agent-service-4">
          <mxGeometry y="118" width="250" height="102" as="geometry"/>
        </mxCell>

        <!-- Agent Model Class -->
        <mxCell id="agent-model-4" value="&lt;&lt;Model&gt;&gt;&lt;br&gt;Agent" style="swimlane;fontStyle=1;align=center;verticalAlign=top;childLayout=stackLayout;horizontal=1;startSize=40;horizontalStack=0;resizeParent=1;resizeParentMax=0;resizeLast=0;collapsible=1;marginBottom=0;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
          <mxGeometry x="620" y="70" width="200" height="180" as="geometry"/>
        </mxCell>
        <mxCell id="agent-model-attributes-4" value="+ agentId: string&lt;br&gt;+ agentCode: string&lt;br&gt;+ firstName: string&lt;br&gt;+ lastName: string&lt;br&gt;+ email: string&lt;br&gt;+ teamId: number&lt;br&gt;+ currentStatus: AgentStatus&lt;br&gt;+ loginTime: Date&lt;br&gt;+ lastActivityTime: Date" style="text;strokeColor=none;fillColor=none;align=left;verticalAlign=top;spacingLeft=4;spacingRight=4;overflow=hidden;rotatable=0;points=[[0,0.5],[1,0.5]];portConstraint=eastwest;" vertex="1" parent="agent-model-4">
          <mxGeometry y="40" width="200" height="130" as="geometry"/>
        </mxCell>
        <mxCell id="agent-model-line-4" value="" style="line;strokeWidth=1;fillColor=none;align=left;verticalAlign=middle;spacingTop=-1;spacingLeft=3;spacingRight=3;rotatable=0;labelPosition=right;points=[];portConstraint=eastwest;" vertex="1" parent="agent-model-4">
          <mxGeometry y="170" width="200" height="8" as="geometry"/>
        </mxCell>

        <!-- AgentStatus Model Class -->
        <mxCell id="agent-status-model-4" value="&lt;&lt;Model&gt;&gt;&lt;br&gt;AgentStatus" style="swimlane;fontStyle=1;align=center;verticalAlign=top;childLayout=stackLayout;horizontal=1;startSize=40;horizontalStack=0;resizeParent=1;resizeParentMax=0;resizeLast=0;collapsible=1;marginBottom=0;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
          <mxGeometry x="50" y="320" width="180" height="160" as="geometry"/>
        </mxCell>
        <mxCell id="agent-status-attributes-4" value="+ statusId: string&lt;br&gt;+ agentId: string&lt;br&gt;+ status: string&lt;br&gt;+ startTime: Date&lt;br&gt;+ duration: number&lt;br&gt;+ reason: string&lt;br&gt;+ isActive: boolean" style="text;strokeColor=none;fillColor=none;align=left;verticalAlign=top;spacingLeft=4;spacingRight=4;overflow=hidden;rotatable=0;points=[[0,0.5],[1,0.5]];portConstraint=eastwest;" vertex="1" parent="agent-status-model-4">
          <mxGeometry y="40" width="180" height="110" as="geometry"/>
        </mxCell>
        <mxCell id="agent-status-line-4" value="" style="line;strokeWidth=1;fillColor=none;align=left;verticalAlign=middle;spacingTop=-1;spacingLeft=3;spacingRight=3;rotatable=0;labelPosition=right;points=[];portConstraint=eastwest;" vertex="1" parent="agent-status-model-4">
          <mxGeometry y="150" width="180" height="8" as="geometry"/>
        </mxCell>

        <!-- WebSocketService Class -->
        <mxCell id="websocket-service-4" value="&lt;&lt;Service&gt;&gt;&lt;br&gt;WebSocketService" style="swimlane;fontStyle=1;align=center;verticalAlign=top;childLayout=stackLayout;horizontal=1;startSize=40;horizontalStack=0;resizeParent=1;resizeParentMax=0;resizeLast=0;collapsible=1;marginBottom=0;fillColor=#e8f5e8;strokeColor=#388e3c;" vertex="1" parent="1">
          <mxGeometry x="320" y="320" width="220" height="160" as="geometry"/>
        </mxCell>
        <mxCell id="websocket-service-attributes-4" value="- io: SocketIOServer&lt;br&gt;- connectedClients: Map&lt;br&gt;- roomManager: RoomManager" style="text;strokeColor=none;fillColor=none;align=left;verticalAlign=top;spacingLeft=4;spacingRight=4;overflow=hidden;rotatable=0;points=[[0,0.5],[1,0.5]];portConstraint=eastwest;" vertex="1" parent="websocket-service-4">
          <mxGeometry y="40" width="220" height="60" as="geometry"/>
        </mxCell>
        <mxCell id="websocket-service-line-4" value="" style="line;strokeWidth=1;fillColor=none;align=left;verticalAlign=middle;spacingTop=-1;spacingLeft=3;spacingRight=3;rotatable=0;labelPosition=right;points=[];portConstraint=eastwest;" vertex="1" parent="websocket-service-4">
          <mxGeometry y="100" width="220" height="8" as="geometry"/>
        </mxCell>
        <mxCell id="websocket-service-methods-4" value="+ broadcastStatusUpdate(statusUpdate): void&lt;br&gt;+ sendMessageToAgent(agentId, message): void&lt;br&gt;+ joinTeamRoom(socketId, teamId): void&lt;br&gt;+ leaveTeamRoom(socketId, teamId): void" style="text;strokeColor=none;fillColor=none;align=left;verticalAlign=top;spacingLeft=4;spacingRight=4;overflow=hidden;rotatable=0;points=[[0,0.5],[1,0.5]];portConstraint=eastwest;" vertex="1" parent="websocket-service-4">
          <mxGeometry y="108" width="220" height="52" as="geometry"/>
        </mxCell>

        <!-- DatabaseRepository Class -->
        <mxCell id="database-repository-4" value="&lt;&lt;Repository&gt;&gt;&lt;br&gt;DatabaseRepository" style="swimlane;fontStyle=1;align=center;verticalAlign=top;childLayout=stackLayout;horizontal=1;startSize=40;horizontalStack=0;resizeParent=1;resizeParentMax=0;resizeLast=0;collapsible=1;marginBottom=0;fillColor=#fce4ec;strokeColor=#c2185b;" vertex="1" parent="1">
          <mxGeometry x="620" y="320" width="200" height="160" as="geometry"/>
        </mxCell>
        <mxCell id="database-repository-attributes-4" value="- sqlConnection: Connection&lt;br&gt;- mongoConnection: MongoClient" style="text;strokeColor=none;fillColor=none;align=left;verticalAlign=top;spacingLeft=4;spacingRight=4;overflow=hidden;rotatable=0;points=[[0,0.5],[1,0.5]];portConstraint=eastwest;" vertex="1" parent="database-repository-4">
          <mxGeometry y="40" width="200" height="40" as="geometry"/>
        </mxCell>
        <mxCell id="database-repository-line-4" value="" style="line;strokeWidth=1;fillColor=none;align=left;verticalAlign=middle;spacingTop=-1;spacingLeft=3;spacingRight=3;rotatable=0;labelPosition=right;points=[];portConstraint=eastwest;" vertex="1" parent="database-repository-4">
          <mxGeometry y="80" width="200" height="8" as="geometry"/>
        </mxCell>
        <mxCell id="database-repository-methods-4" value="+ saveAgent(agent): Promise&lt;Agent&gt;&lt;br&gt;+ getAgentById(id): Promise&lt;Agent&gt;&lt;br&gt;+ saveAgentStatus(status): Promise&lt;AgentStatus&gt;&lt;br&gt;+ getStatusHistory(agentId): Promise&lt;AgentStatus[]&gt;" style="text;strokeColor=none;fillColor=none;align=left;verticalAlign=top;spacingLeft=4;spacingRight=4;overflow=hidden;rotatable=0;points=[[0,0.5],[1,0.5]];portConstraint=eastwest;" vertex="1" parent="database-repository-4">
          <mxGeometry y="88" width="200" height="72" as="geometry"/>
        </mxCell>

        <!-- Relationships -->
        <mxCell id="rel1-4" value="uses" style="endArrow=open;endFill=0;html=1;edge=1;dashed=1;" edge="1" parent="1" source="agent-controller-4" target="agent-service-4">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="rel2-4" value="creates" style="endArrow=open;endFill=0;html=1;edge=1;dashed=1;" edge="1" parent="1" source="agent-service-4" target="agent-model-4">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="rel3-4" value="manages" style="endArrow=open;endFill=0;html=1;edge=1;dashed=1;" edge="1" parent="1" source="agent-service-4" target="agent-status-model-4">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="rel4-4" value="broadcasts via" style="endArrow=open;endFill=0;html=1;edge=1;dashed=1;" edge="1" parent="1" source="agent-service-4" target="websocket-service-4">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="rel5-4" value="persists via" style="endArrow=open;endFill=0;html=1;edge=1;dashed=1;" edge="1" parent="1" source="agent-service-4" target="database-repository-4">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="rel6-4" value="1" style="endArrow=none;endFill=0;html=1;edge=1;" edge="1" parent="1" source="agent-model-4" target="agent-status-model-4">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="rel7-4" value="*" style="endArrow=none;endFill=0;html=1;edge=1;" edge="1" parent="1" source="agent-status-model-4" target="agent-model-4">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>
      </root>
    </mxGraphModel>
  </diagram>
</mxfile>
```

---

## 5. Sequence Diagram - Agent Status Update Flow

**ใช้กับ:** การแสดง Flow การทำงานของระบบ Step-by-Step สำหรับ Use Case เฉพาะ

```xml
<mxfile host="app.diagrams.net">
  <diagram name="Sequence-Diagram" id="sequence">
    <mxGraphModel dx="1422" dy="794" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="1169" pageHeight="827">
      <root>
        <mxCell id="0"/>
        <mxCell id="1" parent="0"/>
        
        <!-- Title -->
        <mxCell id="title-5" value="Agent Wallboard System - Sequence Diagram: Agent Status Update Flow" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontStyle=1;fontSize=16;" vertex="1" parent="1">
          <mxGeometry x="200" y="10" width="600" height="30" as="geometry"/>
        </mxCell>

        <!-- Actors/Objects -->
        <mxCell id="agent-user-5" value="&#128100; Agent" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="1">
          <mxGeometry x="50" y="70" width="80" height="40" as="geometry"/>
        </mxCell>
        
        <mxCell id="desktop-app-5" value="Desktop App" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#e3f2fd;strokeColor=#1976d2;" vertex="1" parent="1">
          <mxGeometry x="170" y="70" width="80" height="40" as="geometry"/>
        </mxCell>
        
        <mxCell id="api-server-5" value="API Server" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="1">
          <mxGeometry x="290" y="70" width="80" height="40" as="geometry"/>
        </mxCell>
        
        <mxCell id="agent-service-5" value="AgentService" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f3e5f5;strokeColor=#7b1fa2;" vertex="1" parent="1">
          <mxGeometry x="410" y="70" width="80" height="40" as="geometry"/>
        </mxCell>
        
        <mxCell id="database-5" value="Database" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
          <mxGeometry x="530" y="70" width="80" height="40" as="geometry"/>
        </mxCell>
        
        <mxCell id="websocket-5" value="WebSocket" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#e8f5e8;strokeColor=#388e3c;" vertex="1" parent="1">
          <mxGeometry x="650" y="70" width="80" height="40" as="geometry"/>
        </mxCell>
        
        <mxCell id="dashboard-5" value="Dashboard" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fce4ec;strokeColor=#c2185b;" vertex="1" parent="1">
          <mxGeometry x="770" y="70" width="80" height="40" as="geometry"/>
        </mxCell>

        <!-- Lifelines -->
        <mxCell id="lifeline1-5" value="" style="endArrow=none;dashed=1;html=1;" edge="1" parent="1">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="90" y="120" as="sourcePoint"/>
            <mxPoint x="90" y="600" as="targetPoint"/>
          </mxGeometry>
        </mxCell>
        
        <mxCell id="lifeline2-5" value="" style="endArrow=none;dashed=1;html=1;" edge="1" parent="1">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="210" y="120" as="sourcePoint"/>
            <mxPoint x="210" y="600" as="targetPoint"/>
          </mxGeometry>
        </mxCell>
        
        <mxCell id="lifeline3-5" value="" style="endArrow=none;dashed=1;html=1;" edge="1" parent="1">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="330" y="120" as="sourcePoint"/>
            <mxPoint x="330" y="600" as="targetPoint"/>
          </mxGeometry>
        </mxCell>
        
        <mxCell id="lifeline4-5" value="" style="endArrow=none;dashed=1;html=1;" edge="1" parent="1">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="450" y="120" as="sourcePoint"/>
            <mxPoint x="450" y="600" as="targetPoint"/>
          </mxGeometry>
        </mxCell>
        
        <mxCell id="lifeline5-5" value="" style="endArrow=none;dashed=1;html=1;" edge="1" parent="1">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="570" y="120" as="sourcePoint"/>
            <mxPoint x="570" y="600" as="targetPoint"/>
          </mxGeometry>
        </mxCell>
        
        <mxCell id="lifeline6-5" value="" style="endArrow=none;dashed=1;html=1;" edge="1" parent="1">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="690" y="120" as="sourcePoint"/>
            <mxPoint x="690" y="600" as="targetPoint"/>
          </mxGeometry>
        </mxCell>
        
        <mxCell id="lifeline7-5" value="" style="endArrow=none;dashed=1;html=1;" edge="1" parent="1">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="810" y="120" as="sourcePoint"/>
            <mxPoint x="810" y="600" as="targetPoint"/>
          </mxGeometry>
        </mxCell>

        <!-- Messages -->
        <mxCell id="msg1-5" value="1: Change status to 'Break'" style="endArrow=classic;html=1;" edge="1" parent="1">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="90" y="150" as="sourcePoint"/>
            <mxPoint x="210" y="150" as="targetPoint"/>
          </mxGeometry>
        </mxCell>
        
        <mxCell id="msg2-5" value="2: validateStatusChange()" style="endArrow=classic;html=1;" edge="1" parent="1">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="210" y="180" as="sourcePoint"/>
            <mxPoint x="210" y="200" as="targetPoint"/>
          </mxGeometry>
        </mxCell>
        
        <mxCell id="msg3-5" value="3: PUT /api/agents/{id}/status" style="endArrow=classic;html=1;" edge="1" parent="1">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="210" y="230" as="sourcePoint"/>
            <mxPoint x="330" y="230" as="targetPoint"/>
          </mxGeometry>
        </mxCell>
        
        <mxCell id="msg4-5" value="4: updateAgentStatus()" style="endArrow=classic;html=1;" edge="1" parent="1">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="330" y="260" as="sourcePoint"/>
            <mxPoint x="450" y="260" as="targetPoint"/>
          </mxGeometry>
        </mxCell>
        
        <mxCell id="msg5-5" value="5: Save status to DB" style="endArrow=classic;html=1;" edge="1" parent="1">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="450" y="290" as="sourcePoint"/>
            <mxPoint x="570" y="290" as="targetPoint"/>
          </mxGeometry>
        </mxCell>
        
        <mxCell id="msg6-5" value="6: Status saved successfully" style="endArrow=classic;html=1;dashed=1;" edge="1" parent="1">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="570" y="320" as="sourcePoint"/>
            <mxPoint x="450" y="320" as="targetPoint"/>
          </mxGeometry>
        </mxCell>
        
        <mxCell id="msg7-5" value="7: broadcastStatusUpdate()" style="endArrow=classic;html=1;" edge="1" parent="1">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="450" y="350" as="sourcePoint"/>
            <mxPoint x="690" y="350" as="targetPoint"/>
          </mxGeometry>
        </mxCell>
        
        <mxCell id="msg8-5" value="8: agent-status-updated event" style="endArrow=classic;html=1;" edge="1" parent="1">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="690" y="380" as="sourcePoint"/>
            <mxPoint x="810" y="380" as="targetPoint"/>
          </mxGeometry>
        </mxCell>
        
        <mxCell id="msg9-5" value="9: updateUI with new status" style="endArrow=classic;html=1;" edge="1" parent="1">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="810" y="410" as="sourcePoint"/>
            <mxPoint x="810" y="430" as="targetPoint"/>
          </mxGeometry>
        </mxCell>
        
        <mxCell id="msg10-5" value="10: Status updated confirmation" style="endArrow=classic;html=1;dashed=1;" edge="1" parent="1">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="330" y="460" as="sourcePoint"/>
            <mxPoint x="210" y="460" as="targetPoint"/>
          </mxGeometry>
        </mxCell>
        
        <mxCell id="msg11-5" value="11: Show success notification" style="endArrow=classic;html=1;dashed=1;" edge="1" parent="1">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="210" y="490" as="sourcePoint"/>
            <mxPoint x="90" y="490" as="targetPoint"/>
          </mxGeometry>
        </mxCell>

        <!-- Activation Bars -->
        <mxCell id="activation1-5" value="" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f8f8f8;" vertex="1" parent="1">
          <mxGeometry x="205" y="150" width="10" height="360" as="geometry"/>
        </mxCell>
        
        <mxCell id="activation2-5" value="" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f8f8f8;" vertex="1" parent="1">
          <mxGeometry x="325" y="230" width="10" height="250" as="geometry"/>
        </mxCell>
        
        <mxCell id="activation3-5" value="" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f8f8f8;" vertex="1" parent="1">
          <mxGeometry x="445" y="260" width="10" height="220" as="geometry"/>
        </mxCell>
        
        <mxCell id="activation4-5" value="" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f8f8f8;" vertex="1" parent="1">
          <mxGeometry x="685" y="350" width="10" height="80" as="geometry"/>
        </mxCell>

        <!-- Notes -->
        <mxCell id="note1-5" value="Validation occurs&#10;on client side first" style="shape=note;whiteSpace=wrap;html=1;backgroundOutline=1;darkOpacity=0.05;fillColor=#ffffcc;strokeColor=#d6b656;" vertex="1" parent="1">
          <mxGeometry x="30" y="200" width="80" height="50" as="geometry"/>
        </mxCell>
        
        <mxCell id="note2-5" value="Real-time broadcast&#10;to all supervisors" style="shape=note;whiteSpace=wrap;html=1;backgroundOutline=1;darkOpacity=0.05;fillColor=#ffffcc;strokeColor=#d6b656;" vertex="1" parent="1">
          <mxGeometry x="720" y="320" width="80" height="50" as="geometry"/>
        </mxCell>
      </root>
    </mxGraphModel>
  </diagram>
</mxfile>
```

---

## 6. Activity Diagram - Agent Login Process

**ใช้กับ:** การแสดง Business Process Flow และ Decision Points

```xml
<mxfile host="app.diagrams.net">
  <diagram name="Activity-Diagram" id="activity">
    <mxGraphModel dx="1422" dy="794" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="827" pageHeight="1169">
      <root>
        <mxCell id="0"/>
        <mxCell id="1" parent="0"/>
        
        <!-- Title -->
        <mxCell id="title-6" value="Agent Wallboard System - Activity Diagram: Agent Login Process" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontStyle=1;fontSize=16;" vertex="1" parent="1">
          <mxGeometry x="150" y="10" width="500" height="30" as="geometry"/>
        </mxCell>

        <!-- Start Node -->
        <mxCell id="start-6" value="" style="ellipse;whiteSpace=wrap;html=1;fillColor=#000000;" vertex="1" parent="1">
          <mxGeometry x="375" y="60" width="30" height="30" as="geometry"/>
        </mxCell>

        <!-- Activities -->
        <mxCell id="activity1-6" value="Agent opens&lt;br&gt;Desktop App" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="1">
          <mxGeometry x="320" y="120" width="140" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="activity2-6" value="Enter Agent Code&lt;br&gt;and Password" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="1">
          <mxGeometry x="320" y="210" width="140" height="60" as="geometry"/>
        </mxCell>

        <!-- Decision Diamond -->
        <mxCell id="decision1-6" value="Valid&lt;br&gt;Credentials?" style="rhombus;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
          <mxGeometry x="340" y="300" width="100" height="80" as="geometry"/>
        </mxCell>

        <!-- Error Path -->
        <mxCell id="activity3-6" value="Show Error&lt;br&gt;Message" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;" vertex="1" parent="1">
          <mxGeometry x="120" y="310" width="140" height="60" as="geometry"/>
        </mxCell>

        <!-- Success Path -->
        <mxCell id="activity4-6" value="Create User Session&lt;br&gt;&amp; Generate JWT Token" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="1">
          <mxGeometry x="520" y="310" width="140" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="activity5-6" value="Load Agent Profile&lt;br&gt;&amp; Team Information" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="1">
          <mxGeometry x="520" y="400" width="140" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="activity6-6" value="Establish WebSocket&lt;br&gt;Connection" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="1">
          <mxGeometry x="520" y="490" width="140" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="activity7-6" value="Set Initial Status&lt;br&gt;to 'Available'" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="1">
          <mxGeometry x="520" y="580" width="140" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="activity8-6" value="Display Main&lt;br&gt;Dashboard" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;" vertex="1" parent="1">
          <mxGeometry x="320" y="670" width="140" height="60" as="geometry"/>
        </mxCell>

        <!-- Decision Diamond 2 -->
        <mxCell id="decision2-6" value="Remember&lt;br&gt;Login?" style="rhombus;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
          <mxGeometry x="140" y="400" width="100" height="80" as="geometry"/>
        </mxCell>

        <mxCell id="activity9-6" value="Save Credentials&lt;br&gt;to Secure Storage" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="1">
          <mxGeometry x="30" y="520" width="140" height="60" as="geometry"/>
        </mxCell>

        <!-- End Node -->
        <mxCell id="end-6" value="" style="ellipse;whiteSpace=wrap;html=1;fillColor=#000000;" vertex="1" parent="1">
          <mxGeometry x="375" y="760" width="30" height="30" as="geometry"/>
        </mxCell>

        <!-- End Node Outer Ring -->
        <mxCell id="end-outer-6" value="" style="ellipse;whiteSpace=wrap;html=1;fillColor=none;strokeColor=#000000;strokeWidth=2;" vertex="1" parent="1">
          <mxGeometry x="370" y="755" width="40" height="40" as="geometry"/>
        </mxCell>

        <!-- Connections -->
        <mxCell id="conn1-6" value="" style="endArrow=classic;html=1;" edge="1" parent="1" source="start-6" target="activity1-6">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn2-6" value="" style="endArrow=classic;html=1;" edge="1" parent="1" source="activity1-6" target="activity2-6">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn3-6" value="" style="endArrow=classic;html=1;" edge="1" parent="1" source="activity2-6" target="decision1-6">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn4-6" value="No" style="endArrow=classic;html=1;" edge="1" parent="1" source="decision1-6" target="activity3-6">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn5-6" value="Yes" style="endArrow=classic;html=1;" edge="1" parent="1" source="decision1-6" target="activity4-6">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn6-6" value="" style="endArrow=classic;html=1;" edge="1" parent="1" source="activity4-6" target="activity5-6">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn7-6" value="" style="endArrow=classic;html=1;" edge="1" parent="1" source="activity5-6" target="activity6-6">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn8-6" value="" style="endArrow=classic;html=1;" edge="1" parent="1" source="activity6-6" target="activity7-6">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn9-6" value="" style="endArrow=classic;html=1;" edge="1" parent="1" source="activity7-6" target="activity8-6">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn10-6" value="" style="endArrow=classic;html=1;" edge="1" parent="1" source="activity8-6" target="end-6">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn11-6" value="" style="endArrow=classic;html=1;" edge="1" parent="1" source="activity3-6" target="decision2-6">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn12-6" value="Yes" style="endArrow=classic;html=1;" edge="1" parent="1" source="decision2-6" target="activity9-6">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="conn13-6" value="" style="endArrow=classic;html=1;dashed=1;" edge="1" parent="1" source="activity9-6" target="activity2-6">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="100" y="250"/>
            </Array>
          </mxGeometry>
        </mxCell>

        <mxCell id="conn14-6" value="No" style="endArrow=classic;html=1;dashed=1;" edge="1" parent="1" source="decision2-6" target="activity2-6">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="280" y="250"/>
            </Array>
          </mxGeometry>
        </mxCell>

        <!-- Swimlanes -->
        <mxCell id="swimlane1-6" value="Client Side" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;fillColor=#f5f5f5;strokeColor=#666666;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="40" y="50" width="60" height="240" as="geometry"/>
        </mxCell>

        <mxCell id="swimlane2-6" value="Server Side" style="swimlane;horizontal=0;whiteSpace=wrap;html=1;fillColor=#f5f5f5;strokeColor=#666666;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="40" y="300" width="60" height="350" as="geometry"/>
        </mxCell>

        <!-- Notes -->
        <mxCell id="note1-6" value="Login credentials&lt;br&gt;validated against&lt;br&gt;database" style="shape=note;whiteSpace=wrap;html=1;backgroundOutline=1;darkOpacity=0.05;fillColor=#ffffcc;strokeColor=#d6b656;" vertex="1" parent="1">
          <mxGeometry x="460" y="280" width="80" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="note2-6" value="Auto-save feature&lt;br&gt;for user convenience" style="shape=note;whiteSpace=wrap;html=1;backgroundOutline=1;darkOpacity=0.05;fillColor=#ffffcc;strokeColor=#d6b656;" vertex="1" parent="1">
          <mxGeometry x="20" y="600" width="80" height="50" as="geometry"/>
        </mxCell>
      </root>
    </mxGraphModel>
  </diagram>
</mxfile>
```

---

## 7. Use Case Diagram - System Overview

**ใช้กับ:** การแสดง Use Cases และ Actors สำหรับทำความเข้าใจ Requirements

```xml
<mxfile host="app.diagrams.net">
  <diagram name="Use-Case-Diagram" id="usecase">
    <mxGraphModel dx="1422" dy="794" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="1169" pageHeight="827">
      <root>
        <mxCell id="0"/>
        <mxCell id="1" parent="0"/>
        
        <!-- Title -->
        <mxCell id="title-7" value="Agent Wallboard System - Use Case Diagram" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontStyle=1;fontSize=16;" vertex="1" parent="1">
          <mxGeometry x="300" y="10" width="400" height="30" as="geometry"/>
        </mxCell>

        <!-- System Boundary -->
        <mxCell id="system-boundary-7" value="Agent Wallboard System" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f5f5f5;strokeColor=#666666;strokeWidth=2;dashed=1;verticalAlign=top;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="200" y="80" width="600" height="500" as="geometry"/>
        </mxCell>

        <!-- Actors -->
        <mxCell id="agent-actor-7" value="Agent" style="shape=umlActor;verticalLabelPosition=bottom;verticalAlign=top;html=1;outlineConnect=0;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="1">
          <mxGeometry x="80" y="150" width="30" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="supervisor-actor-7" value="Supervisor" style="shape=umlActor;verticalLabelPosition=bottom;verticalAlign=top;html=1;outlineConnect=0;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="1">
          <mxGeometry x="80" y="300" width="30" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="manager-actor-7" value="Operations&#10;Manager" style="shape=umlActor;verticalLabelPosition=bottom;verticalAlign=top;html=1;outlineConnect=0;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="1">
          <mxGeometry x="80" y="450" width="30" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="admin-actor-7" value="System&#10;Admin" style="shape=umlActor;verticalLabelPosition=bottom;verticalAlign=top;html=1;outlineConnect=0;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="1">
          <mxGeometry x="880" y="300" width="30" height="60" as="geometry"/>
        </mxCell>

        <!-- Use Cases -->
        <mxCell id="uc1-7" value="Login to System" style="ellipse;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
          <mxGeometry x="250" y="120" width="120" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="uc2-7" value="Update Agent Status" style="ellipse;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
          <mxGeometry x="250" y="200" width="120" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="uc3-7" value="Receive Messages" style="ellipse;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
          <mxGeometry x="250" y="280" width="120" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="uc4-7" value="Monitor Team Status" style="ellipse;whiteSpace=wrap;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;" vertex="1" parent="1">
          <mxGeometry x="420" y="200" width="120" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="uc5-7" value="Send Messages" style="ellipse;whiteSpace=wrap;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;" vertex="1" parent="1">
          <mxGeometry x="420" y="280" width="120" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="uc6-7" value="View Team Analytics" style="ellipse;whiteSpace=wrap;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;" vertex="1" parent="1">
          <mxGeometry x="420" y="360" width="120" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="uc7-7" value="Generate Reports" style="ellipse;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="1">
          <mxGeometry x="420" y="440" width="120" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="uc8-7" value="Manage Users" style="ellipse;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;" vertex="1" parent="1">
          <mxGeometry x="620" y="200" width="120" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="uc9-7" value="Configure System" style="ellipse;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;" vertex="1" parent="1">
          <mxGeometry x="620" y="280" width="120" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="uc10-7" value="View System Logs" style="ellipse;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;" vertex="1" parent="1">
          <mxGeometry x="620" y="360" width="120" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="uc11-7" value="Backup Data" style="ellipse;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;" vertex="1" parent="1">
          <mxGeometry x="620" y="440" width="120" height="60" as="geometry"/>
        </mxCell>

        <!-- Relationships -->
        <mxCell id="rel1-7" value="" style="endArrow=none;html=1;" edge="1" parent="1" source="agent-actor-7" target="uc1-7">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="rel2-7" value="" style="endArrow=none;html=1;" edge="1" parent="1" source="agent-actor-7" target="uc2-7">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="rel3-7" value="" style="endArrow=none;html=1;" edge="1" parent="1" source="agent-actor-7" target="uc3-7">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="rel4-7" value="" style="endArrow=none;html=1;" edge="1" parent="1" source="supervisor-actor-7" target="uc1-7">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="rel5-7" value="" style="endArrow=none;html=1;" edge="1" parent="1" source="supervisor-actor-7" target="uc4-7">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="rel6-7" value="" style="endArrow=none;html=1;" edge="1" parent="1" source="supervisor-actor-7" target="uc5-7">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="rel7-7" value="" style="endArrow=none;html=1;" edge="1" parent="1" source="supervisor-actor-7" target="uc6-7">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="rel8-7" value="" style="endArrow=none;html=1;" edge="1" parent="1" source="manager-actor-7" target="uc6-7">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="rel9-7" value="" style="endArrow=none;html=1;" edge="1" parent="1" source="manager-actor-7" target="uc7-7">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="rel10-7" value="" style="endArrow=none;html=1;" edge="1" parent="1" source="admin-actor-7" target="uc8-7">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="rel11-7" value="" style="endArrow=none;html=1;" edge="1" parent="1" source="admin-actor-7" target="uc9-7">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="rel12-7" value="" style="endArrow=none;html=1;" edge="1" parent="1" source="admin-actor-7" target="uc10-7">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="rel13-7" value="" style="endArrow=none;html=1;" edge="1" parent="1" source="admin-actor-7" target="uc11-7">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <!-- Include/Extend relationships -->
        <mxCell id="include1-7" value="&lt;&lt;include&gt;&gt;" style="endArrow=open;endFill=0;html=1;dashed=1;" edge="1" parent="1" source="uc2-7" target="uc1-7">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="include2-7" value="&lt;&lt;include&gt;&gt;" style="endArrow=open;endFill=0;html=1;dashed=1;" edge="1" parent="1" source="uc4-7" target="uc1-7">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="extend1-7" value="&lt;&lt;extend&gt;&gt;" style="endArrow=open;endFill=0;html=1;dashed=1;" edge="1" parent="1" source="uc7-7" target="uc6-7">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <!-- Legend -->
        <mxCell id="legend-7" value="Legend:&#10;Yellow: Agent Use Cases&#10;Purple: Supervisor Use Cases&#10;Green: Manager Use Cases&#10;Red: Admin Use Cases" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f5f5f5;strokeColor=#666666;align=left;verticalAlign=top;" vertex="1" parent="1">
          <mxGeometry x="30" y="600" width="200" height="100" as="geometry"/>
        </mxCell>
      </root>
    </mxGraphModel>
  </diagram>
</mxfile>
```

---

## 8. Database ERD (Entity Relationship Diagram)

**ใช้กับ:** การแสดง Database Schema และ Relationships สำหรับ C2-C3 Level

```xml
<mxfile host="app.diagrams.net">
  <diagram name="Database-ERD" id="erd">
    <mxGraphModel dx="1422" dy="794" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="1169" pageHeight="827">
      <root>
        <mxCell id="0"/>
        <mxCell id="1" parent="0"/>
        
        <!-- Title -->
        <mxCell id="title-8" value="Agent Wallboard System - Database ERD" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontStyle=1;fontSize=16;" vertex="1" parent="1">
          <mxGeometry x="350" y="10" width="400" height="30" as="geometry"/>
        </mxCell>

        <!-- SQL Server Tables -->
        <mxCell id="sql-section-8" value="SQL Server (Structured Data)" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;strokeWidth=2;dashed=1;verticalAlign=top;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="50" y="70" width="500" height="350" as="geometry"/>
        </mxCell>

        <!-- Users Table -->
        <mxCell id="users-table-8" value="Users" style="swimlane;fontStyle=1;align=center;verticalAlign=top;childLayout=stackLayout;horizontal=1;startSize=26;horizontalStack=0;resizeParent=1;resizeParentMax=0;resizeLast=0;collapsible=1;marginBottom=0;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
          <mxGeometry x="80" y="110" width="160" height="150" as="geometry"/>
        </mxCell>
        <mxCell id="users-attributes-8" value="+ UserID (PK)&#10;+ AgentCode (UNIQUE)&#10;+ FirstName&#10;+ LastName&#10;+ Email&#10;+ PasswordHash&#10;+ Role&#10;+ TeamID (FK)&#10;+ CreatedDate&#10;+ IsActive" style="text;strokeColor=none;fillColor=none;align=left;verticalAlign=top;spacingLeft=4;spacingRight=4;overflow=hidden;rotatable=0;points=[[0,0.5],[1,0.5]];portConstraint=eastwest;" vertex="1" parent="users-table-8">
          <mxGeometry y="26" width="160" height="124" as="geometry"/>
        </mxCell>

        <!-- Teams Table -->
        <mxCell id="teams-table-8" value="Teams" style="swimlane;fontStyle=1;align=center;verticalAlign=top;childLayout=stackLayout;horizontal=1;startSize=26;horizontalStack=0;resizeParent=1;resizeParentMax=0;resizeLast=0;collapsible=1;marginBottom=0;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
          <mxGeometry x="280" y="110" width="160" height="120" as="geometry"/>
        </mxCell>
        <mxCell id="teams-attributes-8" value="+ TeamID (PK)&#10;+ TeamName&#10;+ SupervisorID (FK)&#10;+ Description&#10;+ CreatedDate&#10;+ IsActive" style="text;strokeColor=none;fillColor=none;align=left;verticalAlign=top;spacingLeft=4;spacingRight=4;overflow=hidden;rotatable=0;points=[[0,0.5],[1,0.5]];portConstraint=eastwest;" vertex="1" parent="teams-table-8">
          <mxGeometry y="26" width="160" height="94" as="geometry"/>
        </mxCell>

        <!-- SystemConfig Table -->
        <mxCell id="config-table-8" value="SystemConfig" style="swimlane;fontStyle=1;align=center;verticalAlign=top;childLayout=stackLayout;horizontal=1;startSize=26;horizontalStack=0;resizeParent=1;resizeParentMax=0;resizeLast=0;collapsible=1;marginBottom=0;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
          <mxGeometry x="80" y="280" width="160" height="120" as="geometry"/>
        </mxCell>
        <mxCell id="config-attributes-8" value="+ ConfigID (PK)&#10;+ ConfigKey (UNIQUE)&#10;+ ConfigValue&#10;+ Description&#10;+ ModifiedDate&#10;+ ModifiedBy" style="text;strokeColor=none;fillColor=none;align=left;verticalAlign=top;spacingLeft=4;spacingRight=4;overflow=hidden;rotatable=0;points=[[0,0.5],[1,0.5]];portConstraint=eastwest;" vertex="1" parent="config-table-8">
          <mxGeometry y="26" width="160" height="94" as="geometry"/>
        </mxCell>

        <!-- AuditLogs Table -->
        <mxCell id="audit-table-8" value="AuditLogs" style="swimlane;fontStyle=1;align=center;verticalAlign=top;childLayout=stackLayout;horizontal=1;startSize=26;horizontalStack=0;resizeParent=1;resizeParentMax=0;resizeLast=0;collapsible=1;marginBottom=0;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
          <mxGeometry x="280" y="280" width="160" height="120" as="geometry"/>
        </mxCell>
        <mxCell id="audit-attributes-8" value="+ LogID (PK)&#10;+ UserID (FK)&#10;+ Action&#10;+ TableName&#10;+ RecordID&#10;+ Timestamp&#10;+ IPAddress" style="text;strokeColor=none;fillColor=none;align=left;verticalAlign=top;spacingLeft=4;spacingRight=4;overflow=hidden;rotatable=0;points=[[0,0.5],[1,0.5]];portConstraint=eastwest;" vertex="1" parent="audit-table-8">
          <mxGeometry y="26" width="160" height="94" as="geometry"/>
        </mxCell>

        <!-- MongoDB Collections -->
        <mxCell id="mongo-section-8" value="MongoDB (Real-time Data)" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;strokeWidth=2;dashed=1;verticalAlign=top;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="600" y="70" width="500" height="350" as="geometry"/>
        </mxCell>

        <!-- AgentStatus Collection -->
        <mxCell id="agent-status-8" value="AgentStatus Collection" style="swimlane;fontStyle=1;align=center;verticalAlign=top;childLayout=stackLayout;horizontal=1;startSize=26;horizontalStack=0;resizeParent=1;resizeParentMax=0;resizeLast=0;collapsible=1;marginBottom=0;fillColor=#f3e5f5;strokeColor=#7b1fa2;" vertex="1" parent="1">
          <mxGeometry x="630" y="110" width="180" height="130" as="geometry"/>
        </mxCell>
        <mxCell id="agent-status-attr-8" value="+ _id (ObjectId)&#10;+ agentId (string)&#10;+ status (string)&#10;+ startTime (Date)&#10;+ duration (number)&#10;+ reason (string)&#10;+ metadata (object)" style="text;strokeColor=none;fillColor=none;align=left;verticalAlign=top;spacingLeft=4;spacingRight=4;overflow=hidden;rotatable=0;points=[[0,0.5],[1,0.5]];portConstraint=eastwest;" vertex="1" parent="agent-status-8">
          <mxGeometry y="26" width="180" height="104" as="geometry"/>
        </mxCell>

        <!-- Messages Collection -->
        <mxCell id="messages-8" value="Messages Collection" style="swimlane;fontStyle=1;align=center;verticalAlign=top;childLayout=stackLayout;horizontal=1;startSize=26;horizontalStack=0;resizeParent=1;resizeParentMax=0;resizeLast=0;collapsible=1;marginBottom=0;fillColor=#f3e5f5;strokeColor=#7b1fa2;" vertex="1" parent="1">
          <mxGeometry x="850" y="110" width="180" height="150" as="geometry"/>
        </mxCell>
        <mxCell id="messages-attr-8" value="+ _id (ObjectId)&#10;+ senderId (string)&#10;+ recipientId (string)&#10;+ type (string)&#10;+ content (string)&#10;+ priority (string)&#10;+ sentAt (Date)&#10;+ readAt (Date)" style="text;strokeColor=none;fillColor=none;align=left;verticalAlign=top;spacingLeft=4;spacingRight=4;overflow=hidden;rotatable=0;points=[[0,0.5],[1,0.5]];portConstraint=eastwest;" vertex="1" parent="messages-8">
          <mxGeometry y="26" width="180" height="124" as="geometry"/>
        </mxCell>

        <!-- Performance Collection -->
        <mxCell id="performance-8" value="Performance Collection" style="swimlane;fontStyle=1;align=center;verticalAlign=top;childLayout=stackLayout;horizontal=1;startSize=26;horizontalStack=0;resizeParent=1;resizeParentMax=0;resizeLast=0;collapsible=1;marginBottom=0;fillColor=#f3e5f5;strokeColor=#7b1fa2;" vertex="1" parent="1">
          <mxGeometry x="630" y="280" width="200" height="120" as="geometry"/>
        </mxCell>
        <mxCell id="performance-attr-8" value="+ _id (ObjectId)&#10;+ teamId (number)&#10;+ date (Date)&#10;+ metrics (object)&#10;  - totalAgents (number)&#10;  - utilization (number)&#10;  - statusBreakdown (object)" style="text;strokeColor=none;fillColor=none;align=left;verticalAlign=top;spacingLeft=4;spacingRight=4;overflow=hidden;rotatable=0;points=[[0,0.5],[1,0.5]];portConstraint=eastwest;" vertex="1" parent="performance-8">
          <mxGeometry y="26" width="200" height="94" as="geometry"/>
        </mxCell>

        <!-- Relationships -->
        <mxCell id="rel1-8" value="1" style="endArrow=none;html=1;" edge="1" parent="1" source="teams-table-8" target="users-table-8">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="260" y="170" as="sourcePoint"/>
            <mxPoint x="260" y="170" as="targetPoint"/>
          </mxGeometry>
        </mxCell>

        <mxCell id="rel1-label-8" value="TeamID" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;" vertex="1" parent="1">
          <mxGeometry x="250" y="160" width="30" height="20" as="geometry"/>
        </mxCell>

        <mxCell id="rel2-8" value="*" style="endArrow=none;html=1;" edge="1" parent="1" source="users-table-8" target="teams-table-8">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="240" y="170" as="sourcePoint"/>
            <mxPoint x="280" y="170" as="targetPoint"/>
          </mxGeometry>
        </mxCell>

        <mxCell id="rel3-8" value="1" style="endArrow=none;html=1;" edge="1" parent="1" source="users-table-8" target="audit-table-8">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="160" y="260" as="sourcePoint"/>
            <mxPoint x="280" y="320" as="targetPoint"/>
          </mxGeometry>
        </mxCell>

        <mxCell id="rel4-8" value="*" style="endArrow=none;html=1;" edge="1" parent="1" source="audit-table-8" target="users-table-8">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="280" y="320" as="sourcePoint"/>
            <mxPoint x="240" y="260" as="targetPoint"/>
          </mxGeometry>
        </mxCell>

        <!-- Cross-database relationships -->
        <mxCell id="cross-rel1-8" value="References&#10;Users.AgentCode" style="endArrow=open;endFill=0;html=1;dashed=1;strokeColor=#666666;" edge="1" parent="1" source="agent-status-8" target="users-table-8">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="cross-rel2-8" value="References&#10;Users.AgentCode" style="endArrow=open;endFill=0;html=1;dashed=1;strokeColor=#666666;" edge="1" parent="1" source="messages-8" target="users-table-8">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="cross-rel3-8" value="References&#10;Teams.TeamID" style="endArrow=open;endFill=0;html=1;dashed=1;strokeColor=#666666;" edge="1" parent="1" source="performance-8" target="teams-table-8">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <!-- Indexes -->
        <mxCell id="indexes-8" value="Indexes:&#10;&#10;SQL Server:&#10;• IX_Users_AgentCode (UNIQUE)&#10;• IX_Users_TeamID&#10;• IX_AuditLogs_Timestamp&#10;&#10;MongoDB:&#10;• agentStatus: {agentId: 1, startTime: -1}&#10;• messages: {recipientId: 1, sentAt: -1}&#10;• performance: {teamId: 1, date: -1}" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f5f5f5;strokeColor=#666666;align=left;verticalAlign=top;" vertex="1" parent="1">
          <mxGeometry x="50" y="450" width="300" height="180" as="geometry"/>
        </mxCell>

        <!-- Data Flow -->
        <mxCell id="data-flow-8" value="Data Flow:&#10;&#10;1. User authentication → SQL Server&#10;2. Real-time status → MongoDB&#10;3. Message delivery → MongoDB&#10;4. Performance analytics → MongoDB&#10;5. Audit logging → SQL Server&#10;6. Cross-reference via AgentCode/TeamID" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;align=left;verticalAlign=top;" vertex="1" parent="1">
          <mxGeometry x="400" y="450" width="300" height="180" as="geometry"/>
        </mxCell>

        <!-- Business Rules -->
        <mxCell id="business-rules-8" value="Business Rules:&#10;&#10;• Agent can only have 1 active status&#10;• Messages expire after 30 days (TTL)&#10;• Status history kept for 90 days&#10;• Performance data aggregated daily&#10;• Audit logs retained for 1 year&#10;• Team assignment required for agents" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;align=left;verticalAlign=top;" vertex="1" parent="1">
          <mxGeometry x="750" y="450" width="300" height="180" as="geometry"/>
        </mxCell>
      </root>
    </mxGraphModel>
  </diagram>
</mxfile>
```

---

## 9. Deployment Diagram - Infrastructure Overview

**ใช้กับ:** การแสดง Infrastructure และ Deployment Architecture สำหรับ Production

```xml
<mxfile host="app.diagrams.net">
  <diagram name="Deployment-Diagram" id="deployment">
    <mxGraphModel dx="1422" dy="794" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="1169" pageHeight="827">
      <root>
        <mxCell id="0"/>
        <mxCell id="1" parent="0"/>
        
        <!-- Title -->
        <mxCell id="title-9" value="Agent Wallboard System - Deployment Diagram" style="text;html=1;strokeColor=none;fillColor=none;align=center;verticalAlign=middle;whiteSpace=wrap;rounded=0;fontStyle=1;fontSize=16;" vertex="1" parent="1">
          <mxGeometry x="300" y="10" width="400" height="30" as="geometry"/>
        </mxCell>

        <!-- Client Tier -->
        <mxCell id="client-tier-9" value="Client Tier" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;strokeWidth=2;dashed=1;verticalAlign=top;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="50" y="70" width="300" height="200" as="geometry"/>
        </mxCell>

        <mxCell id="desktop-9" value="&amp;lt;&amp;lt;device&amp;gt;&amp;gt;&lt;br&gt;Agent Workstation&lt;br&gt;---&lt;br&gt;Windows 10/11&lt;br&gt;Electron App&lt;br&gt;8GB RAM, i5 CPU" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#e3f2fd;strokeColor=#1976d2;" vertex="1" parent="1">
          <mxGeometry x="80" y="110" width="120" height="80" as="geometry"/>
        </mxCell>

        <mxCell id="browser-9" value="&amp;lt;&amp;lt;device&amp;gt;&amp;gt;&lt;br&gt;Supervisor Laptop&lt;br&gt;---&lt;br&gt;Chrome Browser&lt;br&gt;Web Dashboard&lt;br&gt;4GB RAM min" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#e3f2fd;strokeColor=#1976d2;" vertex="1" parent="1">
          <mxGeometry x="220" y="110" width="120" height="80" as="geometry"/>
        </mxCell>

        <mxCell id="mobile-9" value="&amp;lt;&amp;lt;device&amp;gt;&amp;gt;&lt;br&gt;Mobile Device&lt;br&gt;---&lt;br&gt;iOS/Android&lt;br&gt;Mobile Web&lt;br&gt;Responsive UI" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#e3f2fd;strokeColor=#1976d2;" vertex="1" parent="1">
          <mxGeometry x="150" y="210" width="120" height="50" as="geometry"/>
        </mxCell>

        <!-- Web Tier -->
        <mxCell id="web-tier-9" value="Web Tier (DMZ)" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;strokeWidth=2;dashed=1;verticalAlign=top;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="400" y="70" width="300" height="200" as="geometry"/>
        </mxCell>

        <mxCell id="load-balancer-9" value="&amp;lt;&amp;lt;device&amp;gt;&amp;gt;&lt;br&gt;Load Balancer&lt;br&gt;---&lt;br&gt;nginx&lt;br&gt;SSL Termination&lt;br&gt;Rate Limiting" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f3e5f5;strokeColor=#7b1fa2;" vertex="1" parent="1">
          <mxGeometry x="430" y="110" width="120" height="70" as="geometry"/>
        </mxCell>

        <mxCell id="web-server1-9" value="&amp;lt;&amp;lt;execution environment&amp;gt;&amp;gt;&lt;br&gt;Web Server 1&lt;br&gt;---&lt;br&gt;Node.js Runtime&lt;br&gt;Express.js App&lt;br&gt;Socket.io Server" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="1">
          <mxGeometry x="430" y="200" width="120" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="web-server2-9" value="&amp;lt;&amp;lt;execution environment&amp;gt;&amp;gt;&lt;br&gt;Web Server 2&lt;br&gt;---&lt;br&gt;Node.js Runtime&lt;br&gt;Express.js App&lt;br&gt;Socket.io Server" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;" vertex="1" parent="1">
          <mxGeometry x="570" y="200" width="120" height="60" as="geometry"/>
        </mxCell>

        <!-- Application Tier -->
        <mxCell id="app-tier-9" value="Application Tier (Internal Network)" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;strokeWidth=2;dashed=1;verticalAlign=top;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="750" y="70" width="350" height="200" as="geometry"/>
        </mxCell>

        <mxCell id="api-server-9" value="&amp;lt;&amp;lt;execution environment&amp;gt;&amp;gt;&lt;br&gt;API Server Cluster&lt;br&gt;---&lt;br&gt;Node.js + Express&lt;br&gt;Business Logic&lt;br&gt;Authentication Service" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
          <mxGeometry x="780" y="110" width="130" height="70" as="geometry"/>
        </mxCell>

        <mxCell id="websocket-server-9" value="&amp;lt;&amp;lt;execution environment&amp;gt;&amp;gt;&lt;br&gt;WebSocket Server&lt;br&gt;---&lt;br&gt;Socket.io Cluster&lt;br&gt;Redis Adapter&lt;br&gt;Real-time Events" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
          <mxGeometry x="940" y="110" width="130" height="70" as="geometry"/>
        </mxCell>

        <mxCell id="cache-server-9" value="&amp;lt;&amp;lt;device&amp;gt;&amp;gt;&lt;br&gt;Cache Server&lt;br&gt;---&lt;br&gt;Redis Cluster&lt;br&gt;Session Storage&lt;br&gt;Rate Limiting" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
          <mxGeometry x="860" y="200" width="130" height="60" as="geometry"/>
        </mxCell>

        <!-- Data Tier -->
        <mxCell id="data-tier-9" value="Data Tier (Secured Network)" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;strokeWidth=2;dashed=1;verticalAlign=top;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="200" y="320" width="600" height="200" as="geometry"/>
        </mxCell>

        <mxCell id="sql-server-9" value="&amp;lt;&amp;lt;device&amp;gt;&amp;gt;&lt;br&gt;SQL Server Cluster&lt;br&gt;---&lt;br&gt;Microsoft SQL Server 2019&lt;br&gt;Always On Availability&lt;br&gt;Master Data Storage" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;" vertex="1" parent="1">
          <mxGeometry x="230" y="360" width="150" height="80" as="geometry"/>
        </mxCell>

        <mxCell id="mongodb-9" value="&amp;lt;&amp;lt;device&amp;gt;&amp;gt;&lt;br&gt;MongoDB Cluster&lt;br&gt;---&lt;br&gt;MongoDB 5.0+&lt;br&gt;Replica Set (3 nodes)&lt;br&gt;Real-time Data Storage" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;" vertex="1" parent="1">
          <mxGeometry x="410" y="360" width="150" height="80" as="geometry"/>
        </mxCell>

        <mxCell id="backup-server-9" value="&amp;lt;&amp;lt;device&amp;gt;&amp;gt;&lt;br&gt;Backup Server&lt;br&gt;---&lt;br&gt;Automated Backups&lt;br&gt;Daily Full + Incremental&lt;br&gt;Disaster Recovery" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;" vertex="1" parent="1">
          <mxGeometry x="590" y="360" width="150" height="80" as="geometry"/>
        </mxCell>

        <mxCell id="file-server-9" value="&amp;lt;&amp;lt;device&amp;gt;&amp;gt;&lt;br&gt;File Server (NAS)&lt;br&gt;---&lt;br&gt;Network Storage&lt;br&gt;Report Repository&lt;br&gt;Log Archives" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;" vertex="1" parent="1">
          <mxGeometry x="320" y="460" width="150" height="50" as="geometry"/>
        </mxCell>

        <!-- External Services -->
        <mxCell id="external-9" value="External Services" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;strokeWidth=2;dashed=1;verticalAlign=top;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="50" y="320" width="120" height="200" as="geometry"/>
        </mxCell>

        <mxCell id="active-directory-9" value="&amp;lt;&amp;lt;external system&amp;gt;&amp;gt;&lt;br&gt;Active Directory&lt;br&gt;---&lt;br&gt;LDAP Authentication&lt;br&gt;Corporate SSO" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;" vertex="1" parent="1">
          <mxGeometry x="60" y="360" width="100" height="60" as="geometry"/>
        </mxCell>

        <mxCell id="email-server-9" value="&amp;lt;&amp;lt;external system&amp;gt;&amp;gt;&lt;br&gt;Email Server&lt;br&gt;---&lt;br&gt;SMTP Gateway&lt;br&gt;Notifications" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;" vertex="1" parent="1">
          <mxGeometry x="60" y="440" width="100" height="60" as="geometry"/>
        </mxCell>

        <!-- Network Connections -->
        <mxCell id="net1-9" value="HTTPS/WSS&lt;br&gt;443" style="endArrow=classic;html=1;" edge="1" parent="1" source="desktop-9" target="load-balancer-9">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="net2-9" value="HTTPS/WSS&lt;br&gt;443" style="endArrow=classic;html=1;" edge="1" parent="1" source="browser-9" target="load-balancer-9">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="net3-9" value="HTTP&lt;br&gt;8080" style="endArrow=classic;html=1;" edge="1" parent="1" source="load-balancer-9" target="web-server1-9">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="net4-9" value="HTTP&lt;br&gt;8080" style="endArrow=classic;html=1;" edge="1" parent="1" source="load-balancer-9" target="web-server2-9">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="net5-9" value="HTTP&lt;br&gt;3000" style="endArrow=classic;html=1;" edge="1" parent="1" source="web-server1-9" target="api-server-9">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="net6-9" value="WebSocket&lt;br&gt;3001" style="endArrow=classic;html=1;" edge="1" parent="1" source="web-server2-9" target="websocket-server-9">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="net7-9" value="TDS&lt;br&gt;1433" style="endArrow=classic;html=1;" edge="1" parent="1" source="api-server-9" target="sql-server-9">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="net8-9" value="MongoDB&lt;br&gt;27017" style="endArrow=classic;html=1;" edge="1" parent="1" source="websocket-server-9" target="mongodb-9">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="net9-9" value="Redis&lt;br&gt;6379" style="endArrow=classic;html=1;" edge="1" parent="1" source="api-server-9" target="cache-server-9">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <mxCell id="net10-9" value="LDAP&lt;br&gt;389" style="endArrow=classic;html=1;" edge="1" parent="1" source="api-server-9" target="active-directory-9">
          <mxGeometry relative="1" as="geometry"/>
        </mxCell>

        <!-- Information Boxes -->
        <mxCell id="deployment-notes-9" value="Deployment Configuration:&lt;br&gt;&lt;br&gt;• Load Balancer: nginx with SSL/TLS 1.3&lt;br&gt;• Web Servers: PM2 cluster mode (4 processes)&lt;br&gt;• API Servers: Horizontal scaling (2-4 instances)&lt;br&gt;• Databases: High availability with failover&lt;br&gt;• Monitoring: Prometheus + Grafana&lt;br&gt;• Logging: ELK Stack" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f5f5f5;strokeColor=#666666;align=left;verticalAlign=top;" vertex="1" parent="1">
          <mxGeometry x="50" y="550" width="350" height="120" as="geometry"/>
        </mxCell>

        <mxCell id="security-zones-9" value="Security Zones:&lt;br&gt;&lt;br&gt;• DMZ: Web tier with public access&lt;br&gt;• Internal Network: Application tier (restricted)&lt;br&gt;• Secured Network: Data tier (highly restricted)&lt;br&gt;• Firewall Rules: Port-specific access control&lt;br&gt;• VPN Required: Admin access to internal networks&lt;br&gt;• SSL/TLS: End-to-end encryption" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;align=left;verticalAlign=top;" vertex="1" parent="1">
          <mxGeometry x="450" y="550" width="300" height="120" as="geometry"/>
        </mxCell>

        <mxCell id="monitoring-9" value="Monitoring &amp; Logging:&lt;br&gt;&lt;br&gt;• Application Monitoring: New Relic/DataDog&lt;br&gt;• Infrastructure: Nagios/Zabbix&lt;br&gt;• Log Aggregation: ELK Stack&lt;br&gt;• Real-time Alerts: PagerDuty&lt;br&gt;• Performance Metrics: Custom dashboards&lt;br&gt;• Health Checks: Automated endpoint monitoring" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;align=left;verticalAlign=top;" vertex="1" parent="1">
          <mxGeometry x="800" y="550" width="300" height="120" as="geometry"/>
        </mxCell>
      </root>
    </mxGraphModel>
  </diagram>
</mxfile>
```

---

## การใช้งาน UML Diagrams แต่ละชนิดกับ C4 Model

### 📊 **C1 (Context Level)**
- **System Context Diagram** - แสดงภาพรวมระบบและความสัมพันธ์กับ external systems
- **Use Case Diagram** - แสดง actors และ use cases หลัก

### 🏗️ **C2 (Container Level)**
- **Container Architecture Diagram** - แสดง technology stack และ communication protocols
- **Deployment Diagram** - แสดง infrastructure และ production environment

### 🔧 **C3 (Component Level)**
- **Component Diagram** - แสดง internal components และ interfaces
- **Sequence Diagram** - แสดง interaction flows ระหว่าง components

### 💻 **C4 (Code Level)**
- **Class Diagram** - แสดง class structure และ relationships
- **Activity Diagram** - แสดง business process flows
- **Database ERD** - แสดง data model และ relationships

---

## 🚀 การใช้งาน Draw.io XML Codes

1. **Copy XML code** ทั้งหมดของ diagram ที่ต้องการ
2. **เปิด Draw.io** (draw.io หรือ app.diagrams.net)
3. ไปที่ **File → Import from → Text**
4. **Paste XML code** ลงในช่อง text input
5. กด **Import** - diagram จะปรากฏขึ้นพร้อมใช้งาน
6. **Edit และ customize** ตามความต้องการ

## ข้อแนะนำเพิ่มเติม:

### การปรับแต่ง Diagrams:
- เปลี่ยนสี: คลิกที่ shape แล้วเลือก fill color
- แก้ไขข้อความ: double-click บน text
- เพิ่ม/ลบ elements: ใช้ toolbar ด้านซ้าย
- ปรับ layout: drag & drop elements ไปตำแหน่งที่ต้องการ

### การจัดการไฟล์:
- **Save as .drawio** - สำหรับแก้ไขต่อ
- **Export as PNG/PDF** - สำหรับใส่ในเอกสาร
- **Share via link** - สำหรับความร่วมมือกับทีม

### Best Practices:
1. **เก็บไฟล์ต้นฉบับ** - บันทึกเป็น .drawio format
2. **ใช้ naming convention** - ตั้งชื่อไฟล์ให้เข้าใจง่าย
3. **Update เป็นระยะ** - แก้ไข diagram เมื่อระบบเปลี่ยนแปลง
4. **Version control** - เก็บ history การเปลี่ยนแปลง

Diagrams เหล่านี้ครอบคลุมตั้งแต่ระดับ high-level architecture จนถึง implementation details ซึ่งจะช่วยให้นักศึกษาเข้าใจ software design process อย่างเป็นระบบตาม C4 Model methodology ที่เป็นมาตรฐานในอุตสาหกรรม