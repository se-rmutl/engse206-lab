# 📄 Task#1: User Management System - Implementation Guide (Updated v1.2)

**Document ID:** TASK1-IMPL-GUIDE-001-v1.2  
**Version:** 1.2 (Updated)  
**Created:** October 2025  
**Last Updated:** October 2025  
**Course:** ENGSE206 - Software Requirements Specification and Design  
**ระยะเวลา:** 3 วัน  
**Code Coverage:** 70-80% (นักศึกษาเติม 20-30%)
**Changelog v1.2:**
- 🔧 ปรับชื่อ teams and users tables ให้เป็นตัวเล็ก
- 🔧 ปรับชื่อ การอ้าง FK ของตาราง users จาก id เป็น team_id
- 🔧 ปรับชื่อ การอ้าง จาก t.name เป็น t.team_name
- 🔧 ปรับ code ที่ให้ ในเอกสารให้อ้างถึง ตาราง teams and users ให้ถูกต้อง

---

## 📋 สารบัญ

1. [ภาพรวมและการเตรียมพร้อม](#1-ภาพรวมและการเตรียมพร้อม)
2. [ส่วนที่ 1: Database Setup](#2-ส่วนที่-1-database-setup)
3. [ส่วนที่ 2: Backend Extensions](#3-ส่วนที่-2-backend-extensions)
4. [ส่วนที่ 3: Frontend Admin Panel](#4-ส่วนที่-3-frontend-admin-panel)
5. [ส่วนที่ 4: Integration & Testing](#5-ส่วนที่-4-integration--testing)
6. [Troubleshooting & Tips](#6-troubleshooting--tips)

---

## 1. ภาพรวมและการเตรียมพร้อม

### 1.1 สิ่งที่มีอยู่แล้ว (จาก Project เดิม)

```
✅ Backend Server (Node.js + Express)
   ├── server.js (main entry point)
   ├── config/database.js (SQLite + MongoDB connections)
   ├── routes/ (auth, agents, messages)
   ├── models/ (Agent, Message, Status)
   └── socket/ (WebSocket handlers)

✅ SQLite Database
   ├── wallboard.db
   ├── agents table
   └── teams table

✅ MongoDB Database
   ├── messages collection
   └── statuses collection
```

### 1.2 สิ่งที่จะเพิ่มใหม่ (Task#1)

```
🆕 Backend Extensions
   ├── routes/users.js (User Management APIs)
   ├── controllers/userController.js
   ├── services/userService.js
   ├── repositories/userRepository.js
   └── middleware/validation.js (User validation)

🆕 Database Tables
   ├── users table (ใน SQLite)
   └── Sample users data

🆕 Frontend Admin Panel (React - Project ใหม่)
   ├── Admin dashboard
   ├── User management page
   ├── User CRUD operations
   └── Login without password
```

### 1.3 Project Structure (หลังเพิ่ม Task#1)

```
agent-wallboard-system/
├── backend-server/              # ⚠️ ใช้ Backend เดิม + เพิ่มไฟล์ใหม่
│   ├── server.js                # แก้ไข: เพิ่ม users route
│   ├── config/
│   │   └── database.js          # ใช้เดิม (no change)
│   ├── routes/
│   │   ├── auth.js              # แก้ไข: เพิ่ม login without password
│   │   ├── agents.js            # ใช้เดิม (no change)
│   │   ├── messages.js          # ใช้เดิม (no change)
│   │   └── users.js             # 🆕 ไฟล์ใหม่
│   ├── controllers/
│   │   └── userController.js    # 🆕 ไฟล์ใหม่
│   ├── services/
│   │   ├── authService.js       # แก้ไข: เพิ่ม loginWithoutPassword
│   │   └── userService.js       # 🆕 ไฟล์ใหม่
│   ├── repositories/
│   │   └── userRepository.js    # 🆕 ไฟล์ใหม่
│   ├── middleware/
│   │   ├── auth.js              # ใช้เดิม (no change)
│   │   └── validation.js        # 🆕 ไฟล์ใหม่
│   └── package.json             # แก้ไข: เพิ่ม express-validator
│
├── admin-panel/                 # 🆕 React Project ใหม่ทั้งหมด
│   ├── public/
│   ├── src/
│   │   ├── pages/
│   │   │   ├── LoginPage.js
│   │   │   └── UserManagementPage.js
│   │   ├── components/
│   │   │   ├── UserTable.js
│   │   │   ├── UserFormModal.js
│   │   │   └── UserActionButtons.js
│   │   ├── services/
│   │   │   ├── authAPI.js
│   │   │   └── userAPI.js
│   │   ├── styles/
│   │   │   ├── UserManagementPage.css
│   │   │   ├── UserTable.css
│   │   │   └── UserFormModal.css
│   │   ├── App.js
│   │   └── index.js
│   ├── package.json
│   └── .env
│
└── database/
    ├── sqlite/
    │   └── wallboard.db         # แก้ไข: เพิ่ม users table
    └── scripts/
        ├── 01-create-users-table.sql  # 🆕 SQL script
        └── 02-insert-sample-users.sql # 🆕 SQL script
```

---

## 2. ส่วนที่ 1: Database Setup

### 2.1 สร้าง users Table (ให้ครบ 100%)

**ไฟล์: `database/scripts/01-create-users-table.sql`**

```sql
-- ========================================
-- Task#1: User Management - users Table
-- Version: 1.2 (Updated with FK pragma)
-- ========================================

-- 🆕 IMPORTANT: เปิดใช้งาน Foreign Key constraints
PRAGMA foreign_keys = ON;

-- ลบตารางเดิมถ้ามี (สำหรับ development)
DROP TABLE IF EXISTS users;

-- สร้างตาราง users
CREATE TABLE users (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    username TEXT NOT NULL UNIQUE,
    fullName TEXT NOT NULL,
    role TEXT NOT NULL CHECK(role IN ('Agent', 'Supervisor', 'Admin')),
    teamId INTEGER,
    status TEXT NOT NULL DEFAULT 'Active' CHECK(status IN ('Active', 'Inactive')),
    createdAt DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
    updatedAt DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
    lastLoginAt DATETIME,
    deletedAt DATETIME,
    FOREIGN KEY (teamId) REFERENCES teams(team_id)
);

-- สร้าง indexes เพื่อ performance
CREATE INDEX idx_users_username ON users(username);
CREATE INDEX idx_users_role ON users(role);
CREATE INDEX idx_users_status ON users(status);
CREATE INDEX idx_users_teamId ON users(teamId);
CREATE INDEX idx_users_deletedAt ON users(deletedAt);

-- สร้าง trigger สำหรับ updatedAt
CREATE TRIGGER update_users_timestamp 
AFTER UPDATE ON users
FOR EACH ROW
BEGIN
    UPDATE users SET updatedAt = CURRENT_TIMESTAMP WHERE id = NEW.id;
END;
```

**วิธีรัน SQL Script:**
```bash
# ใน terminal ที่ database/sqlite/
sqlite3 wallboard.db < ../scripts/01-create-users-table.sql
```

### 2.2 Insert Sample Data (ให้ครบ 100%)

**ไฟล์: `database/scripts/02-insert-sample-users.sql`**

```sql
-- ========================================
-- Task#1: Sample users Data
-- ========================================

-- เปิดใช้งาน Foreign Key constraints
PRAGMA foreign_keys = ON;

-- ล้างข้อมูลเดิม (ถ้ามี)
DELETE FROM users;

-- Insert Admin users
INSERT INTO users (username, fullName, role, teamId, status) VALUES
('AD001', 'Admin One', 'Admin', NULL, 'Active'),
('AD002', 'Admin Two', 'Admin', NULL, 'Active');

-- Insert Supervisor users (assuming teams with team_id 1,2,3 exist)
INSERT INTO users (username, fullName, role, teamId, status) VALUES
('SP001', 'Supervisor Alpha', 'Supervisor', 1, 'Active'),
('SP002', 'Supervisor Beta', 'Supervisor', 2, 'Active'),
('SP003', 'Supervisor Gamma', 'Supervisor', 3, 'Active');

-- Insert Agent users
INSERT INTO users (username, fullName, role, teamId, status) VALUES
('AG001', 'Agent Smith', 'Agent', 1, 'Active'),
('AG002', 'Agent Johnson', 'Agent', 1, 'Active'),
('AG003', 'Agent Williams', 'Agent', 1, 'Active'),
('AG004', 'Agent Brown', 'Agent', 2, 'Active'),
('AG005', 'Agent Davis', 'Agent', 2, 'Active'),
('AG006', 'Agent Miller', 'Agent', 3, 'Active'),
('AG007', 'Agent Wilson', 'Agent', 3, 'Active'),
('AG008', 'Agent Moore', 'Agent', 3, 'Active');

-- Verify data
SELECT 
    id,
    username,
    fullName,
    role,
    teamId,
    status,
    createdAt
FROM users
ORDER BY role, username;
```

**วิธีรัน:**
```bash
sqlite3 wallboard.db < ../scripts/02-insert-sample-users.sql
```

### 2.3 ทดสอบ Database

**ไฟล์: `database/scripts/03-test-users-queries.sql`**

```sql
-- Test queries for users table

-- 1. Get all active users
SELECT * FROM users WHERE deletedAt IS NULL;

-- 2. Get users by role
SELECT * FROM users WHERE role = 'Agent' AND deletedAt IS NULL;

-- 3. Get user with team info
SELECT 
    u.id,
    u.username,
    u.fullName,
    u.role,
    t.team_name as teamName,
    u.status
FROM users u
LEFT JOIN teams t ON u.teamId = t.team_id
WHERE u.deletedAt IS NULL;

-- 4. Count users by role
SELECT role, COUNT(*) as count 
FROM users 
WHERE deletedAt IS NULL 
GROUP BY role;

-- 5. Find user by username
SELECT * FROM users 
WHERE username = 'AG001' AND deletedAt IS NULL;

-- 6. Test Foreign Key constraint
-- This should fail if team doesn't exist
-- INSERT INTO users (username, fullName, role, teamId, status) 
-- VALUES ('AG999', 'Test Agent', 'Agent', 999, 'Active');
```

---

## 3. ส่วนที่ 2: Backend Extensions

### 3.1 เพิ่ม Dependencies

**แก้ไขไฟล์: `backend-server/package.json`**

```json
{
  "dependencies": {
    "express": "^4.18.2",
    "socket.io": "^4.7.2",
    "sqlite3": "^5.1.6",
    "mongoose": "^7.5.0",
    "cors": "^2.8.5",
    "dotenv": "^16.3.1",
    "jsonwebtoken": "^9.0.2",
    "express-validator": "^7.0.1"  // 🆕 เพิ่มบรรทัดนี้
  }
}
```

**ติดตั้ง dependency ใหม่:**
```bash
cd backend-server
npm install express-validator
```

### 3.2 User Repository (Data Access Layer)

**ไฟล์ใหม่: `backend-server/repositories/userRepository.js` (ให้ 85%)**

```javascript
// repositories/userRepository.js
const sqlite3 = require('sqlite3').verbose();
const path = require('path');

// Database path (ใช้ database เดิม)
const dbPath = path.join(__dirname, '../../database/sqlite/wallboard.db');

/**
 * User Repository - Data Access Layer
 * ให้ 85% - นักศึกษาเพิ่ม update() method (15%)
 */
class UserRepository {
  constructor() {
    this.db = new sqlite3.Database(dbPath, (err) => {
      if (err) {
        console.error('Error connecting to database:', err);
      } else {
        console.log('✅ UserRepository connected to SQLite database');
        // 🆕 เปิดใช้งาน Foreign Key constraints
        this.db.run('PRAGMA foreign_keys = ON');
      }
    });
  }

  /**
   * Find all users with optional filters
   */
  async findAll(filters = {}) {
    return new Promise((resolve, reject) => {
      let query = `
        SELECT 
          u.id,
          u.username,
          u.fullName,
          u.role,
          u.teamId,
          t.team_name as teamName,
          u.status,
          u.createdAt,
          u.updatedAt,
          u.lastLoginAt
        FROM users u
        LEFT JOIN teams t ON u.teamId = t.team_id
        WHERE u.deletedAt IS NULL
      `;
      
      const params = [];
      
      // Add filters
      if (filters.role) {
        query += ' AND u.role = ?';
        params.push(filters.role);
      }
      
      if (filters.status) {
        query += ' AND u.status = ?';
        params.push(filters.status);
      }
      
      if (filters.teamId) {
        query += ' AND u.teamId = ?';
        params.push(filters.teamId);
      }
      
      query += ' ORDER BY u.createdAt DESC';
      
      this.db.all(query, params, (err, rows) => {
        if (err) reject(err);
        else resolve(rows);
      });
    });
  }

  /**
   * Find user by ID
   */
  async findById(userId) {
    return new Promise((resolve, reject) => {
      const query = `
        SELECT 
          u.id,
          u.username,
          u.fullName,
          u.role,
          u.teamId,
          t.team_name as teamName,
          u.status,
          u.createdAt,
          u.updatedAt,
          u.lastLoginAt
        FROM users u
        LEFT JOIN teams t ON u.teamId = t.team_id
        WHERE u.id = ? AND u.deletedAt IS NULL
      `;
      
      this.db.get(query, [userId], (err, row) => {
        if (err) reject(err);
        else resolve(row);
      });
    });
  }

  /**
   * Find user by username
   */
  async findByUsername(username) {
    return new Promise((resolve, reject) => {
      const query = `
        SELECT 
          u.id,
          u.username,
          u.fullName,
          u.role,
          u.teamId,
          t.team_name as teamName,
          u.status,
          u.createdAt,
          u.updatedAt,
          u.lastLoginAt
        FROM users u
        LEFT JOIN teams t ON u.teamId = t.team_id
        WHERE u.username = ? AND u.deletedAt IS NULL
      `;
      
      this.db.get(query, [username], (err, row) => {
        if (err) reject(err);
        else resolve(row);
      });
    });
  }

  /**
   * Create new user
   */
  async create(userData) {
    return new Promise((resolve, reject) => {
      const query = `
        INSERT INTO users (username, fullName, role, teamId, status)
        VALUES (?, ?, ?, ?, ?)
      `;
      
      const params = [
        userData.username,
        userData.fullName,
        userData.role,
        userData.teamId || null,
        userData.status || 'Active'
      ];
      
      this.db.run(query, params, function(err) {
        if (err) {
          reject(err);
        } else {
          // Return the created user
          const newUserId = this.lastID;
          resolve({ id: newUserId, ...userData });
        }
      });
    });
  }

  /**
   * Update user
   * TODO: นักศึกษาเขียน implementation (15%)
   * 
   * 📝 INSTRUCTIONS:
   * เป้าหมาย: สร้าง dynamic UPDATE query ที่สามารถอัพเดตเฉพาะ fields ที่ส่งมา
   * 
   * ขั้นตอนการทำ:
   * 1. สร้างตัวแปร setClause เริ่มต้นด้วย 'updatedAt = CURRENT_TIMESTAMP'
   * 2. สร้าง array params สำหรับเก็บค่าที่จะ bind
   * 3. ตรวจสอบแต่ละ field ใน userData:
   *    - ถ้า userData.fullName !== undefined:
   *        setClause += ', fullName = ?'
   *        params.push(userData.fullName)
   *    - ทำเหมือนกันกับ role, teamId, status
   * 4. เพิ่ม userId เป็น parameter สุดท้าย: params.push(userId)
   * 5. สร้าง query: UPDATE users SET ${setClause} WHERE id = ? AND deletedAt IS NULL
   * 6. รัน this.db.run(query, params, callback)
   * 7. ใน callback:
   *    - ถ้า err: reject(err)
   *    - ถ้า this.changes === 0: reject(new Error('User not found'))
   *    - ถ้าสำเร็จ: resolve({ id: userId, ...userData })
   * 
   * 💡 HINTS:
   * - ใช้ undefined แทน null เพื่อตรวจสอบว่า field ถูกส่งมาหรือไม่
   * - this.changes จะบอกจำนวน rows ที่ถูกอัพเดต
   * - ต้องมี AND deletedAt IS NULL เพื่อไม่ให้อัพเดต deleted users
   */
  async update(userId, userData) {
    return new Promise((resolve, reject) => {
      // TODO: เขียนตามขั้นตอนด้านบน
      // Step 1: สร้าง setClause
      let setClause = 'updatedAt = CURRENT_TIMESTAMP';
      const params = [];
      
      // Step 2-3: เพิ่ม fields ที่มีค่า
      if (userData.fullName !== undefined) {
        setClause += ', fullName = ?';
        params.push(userData.fullName);
      }
      
      // TODO: เพิ่ม role, teamId, status (ทำเหมือน fullName)
      
      // Step 4: เพิ่ม userId
      params.push(userId);
      
      // Step 5-7: สร้าง query และรัน
      const query = `
        UPDATE users 
        SET ${setClause}
        WHERE id = ? AND deletedAt IS NULL
      `;
      
      this.db.run(query, params, function(err) {
        if (err) {
          reject(err);
        } else if (this.changes === 0) {
          reject(new Error('User not found or already deleted'));
        } else {
          resolve({ id: userId, ...userData });
        }
      });
    });
  }

  /**
   * Soft delete user
   */
  async softDelete(userId) {
    return new Promise((resolve, reject) => {
      const query = `
        UPDATE users 
        SET status = 'Inactive', 
            deletedAt = CURRENT_TIMESTAMP,
            updatedAt = CURRENT_TIMESTAMP
        WHERE id = ? AND deletedAt IS NULL
      `;
      
      this.db.run(query, [userId], function(err) {
        if (err) {
          reject(err);
        } else if (this.changes === 0) {
          reject(new Error('User not found or already deleted'));
        } else {
          resolve({ success: true, changes: this.changes });
        }
      });
    });
  }

  /**
   * Update last login timestamp
   */
  async updateLastLogin(userId) {
    return new Promise((resolve, reject) => {
      const query = `
        UPDATE users 
        SET lastLoginAt = CURRENT_TIMESTAMP
        WHERE id = ?
      `;
      
      this.db.run(query, [userId], function(err) {
        if (err) {
          reject(err);
        } else {
          resolve({ success: true });
        }
      });
    });
  }

  /**
   * Check if username exists
   */
  async usernameExists(username) {
    return new Promise((resolve, reject) => {
      const query = `
        SELECT COUNT(*) as count 
        FROM users 
        WHERE username = ? AND deletedAt IS NULL
      `;
      
      this.db.get(query, [username], (err, row) => {
        if (err) reject(err);
        else resolve(row.count > 0);
      });
    });
  }
}

module.exports = new UserRepository();
```

### 3.3 User Service (Business Logic)

**ไฟล์ใหม่: `backend-server/services/userService.js` (ให้ 70%)**

```javascript
// services/userService.js
const userRepository = require('../repositories/userRepository');

/**
 * User Service - Business Logic Layer
 * ให้ 70% - นักศึกษาเพิ่ม validation และ updateUser, deleteUser methods (30%)
 */
const userService = {
  /**
   * Get all users with optional filtering
   */
  async getAllUsers(filters = {}) {
    try {
      const users = await userRepository.findAll(filters);
      return users;
    } catch (error) {
      console.error('Error in getAllUsers service:', error);
      throw error;
    }
  },

  /**
   * Get user by ID
   */
  async getUserById(userId) {
    try {
      const user = await userRepository.findById(userId);
      
      if (!user) {
        throw new Error('User not found');
      }

      return user;
    } catch (error) {
      console.error('Error in getUserById service:', error);
      throw error;
    }
  },

  /**
   * Create new user
   */
  async createUser(userData) {
    try {
      // 1. Validate username format
      const usernameRegex = /^(AG|SP|AD)(00[1-9]|0[1-9]\d|[1-9]\d{2})$/;
      if (!usernameRegex.test(userData.username)) {
        throw new Error('Invalid username format. Use AGxxx, SPxxx, or ADxxx (001-999)');
      }

      // 2. Check if username already exists
      const exists = await userRepository.usernameExists(userData.username);
      if (exists) {
        throw new Error(`Username "${userData.username}" already exists`);
      }

      // TODO: 3. Validate role-specific rules (นักศึกษาทำ 10%)
      // HINT: ถ้า role = 'Agent' หรือ 'Supervisor' ต้องมี teamId
      //       ถ้า role = 'Admin' ไม่ต้องมี teamId (หรือเป็น null ก็ได้)
      // Example:
      // if ((userData.role === 'Agent' || userData.role === 'Supervisor') && !userData.teamId) {
      //   throw new Error('Team ID is required for Agent and Supervisor roles');
      // }
      
      // 4. Create user
      const newUser = await userRepository.create(userData);
      
      return newUser;
    } catch (error) {
      console.error('Error in createUser service:', error);
      
      // 🆕 Improved error handling
      if (error.code === 'SQLITE_CONSTRAINT') {
        if (error.message.includes('UNIQUE')) {
          throw new Error(`Username "${userData.username}" already exists`);
        }
        if (error.message.includes('FOREIGN KEY')) {
          throw new Error(`Team ID ${userData.teamId} does not exist`);
        }
      }
      
      throw error;
    }
  },

  /**
   * Update existing user
   * TODO: นักศึกษาเขียน implementation (15%)
   * 
   * 📝 INSTRUCTIONS:
   * ขั้นตอนที่ต้องทำ:
   * 1. ตรวจสอบว่า user มีอยู่จริง
   *    - เรียก: const existingUser = await userRepository.findById(userId)
   *    - ถ้าไม่มี: throw new Error('User not found')
   * 
   * 2. ตรวจสอบว่าไม่มีการเปลี่ยน username
   *    - if (userData.username && userData.username !== existingUser.username)
   *    - throw new Error('Username cannot be changed')
   * 
   * 3. Validate role-specific rules (ถ้ามีการเปลี่ยน role หรือ teamId)
   *    - ถ้า role เปลี่ยนเป็น Agent/Supervisor และไม่มี teamId
   *    - throw error
   * 
   * 4. เรียก userRepository.update(userId, userData)
   * 
   * 5. Return updated user
   */
  async updateUser(userId, userData) {
    try {
      // TODO: เขียนตามขั้นตอนด้านบน
      
      throw new Error('Not implemented - TODO by student');
    } catch (error) {
      console.error('Error in updateUser service:', error);
      throw error;
    }
  },

  /**
   * Delete user (soft delete)
   * TODO: นักศึกษาเขียน implementation (5%)
   * 
   * 📝 INSTRUCTIONS:
   * ขั้นตอนที่ต้องทำ:
   * 1. ตรวจสอบว่า user มีอยู่จริง
   *    - const user = await userRepository.findById(userId)
   *    - ถ้าไม่มี: throw new Error('User not found')
   * 
   * 2. (Optional) ตรวจสอบว่าไม่ใช่ current user
   *    - ถ้าต้องการป้องกันการลบตัวเอง
   * 
   * 3. Soft delete
   *    - await userRepository.softDelete(userId)
   * 
   * 4. Return success message
   *    - return { success: true, message: 'User deleted successfully' }
   */
  async deleteUser(userId) {
    try {
      // TODO: เขียนตามขั้นตอนด้านบน
      
      throw new Error('Not implemented - TODO by student');
    } catch (error) {
      console.error('Error in deleteUser service:', error);
      throw error;
    }
  },

  /**
   * Validate username format
   */
  validateUsername(username) {
    const regex = /^(AG|SP|AD)(00[1-9]|0[1-9]\d|[1-9]\d{2})$/;
    return regex.test(username);
  },

  /**
   * Get role from username prefix
   */
  getRoleFromUsername(username) {
    if (username.startsWith('AG')) return 'Agent';
    if (username.startsWith('SP')) return 'Supervisor';
    if (username.startsWith('AD')) return 'Admin';
    return null;
  }
};

module.exports = userService;
```

### 3.4 Validation Middleware

**ไฟล์ใหม่: `backend-server/middleware/validation.js` (ให้ครบ 100%)**

```javascript
// middleware/validation.js
const { body, param, query, validationResult } = require('express-validator');

/**
 * Validation Middleware
 * ให้ครบ 100%
 */

// User creation validation
exports.validateCreateUser = [
  body('username')
    .notEmpty().withMessage('Username is required')
    .matches(/^(AG|SP|AD)(00[1-9]|0[1-9]\d|[1-9]\d{2})$/)
    .withMessage('Username must be in format: AGxxx, SPxxx, or ADxxx (001-999)'),
  
  body('fullName')
    .notEmpty().withMessage('Full name is required')
    .isLength({ min: 2, max: 100 }).withMessage('Full name must be 2-100 characters'),
  
  body('role')
    .notEmpty().withMessage('Role is required')
    .isIn(['Agent', 'Supervisor', 'Admin']).withMessage('Invalid role'),
  
  body('teamId')
    .optional()
    .isInt({ min: 1 }).withMessage('Team ID must be a positive integer'),
  
  body('status')
    .optional()
    .isIn(['Active', 'Inactive']).withMessage('Status must be Active or Inactive'),
  
  // Custom validation: Agent/Supervisor must have teamId
  body('teamId').custom((value, { req }) => {
    if ((req.body.role === 'Agent' || req.body.role === 'Supervisor') && !value) {
      throw new Error('Team ID is required for Agent and Supervisor roles');
    }
    return true;
  })
];

// User update validation
exports.validateUpdateUser = [
  param('id')
    .notEmpty().withMessage('User ID is required')
    .isInt({ min: 1 }).withMessage('Invalid user ID'),
  
  body('username')
    .optional()
    .custom(() => {
      throw new Error('Username cannot be changed');
    }),
  
  body('fullName')
    .optional()
    .isLength({ min: 2, max: 100 }).withMessage('Full name must be 2-100 characters'),
  
  body('role')
    .optional()
    .isIn(['Agent', 'Supervisor', 'Admin']).withMessage('Invalid role'),
  
  body('teamId')
    .optional()
    .isInt({ min: 1 }).withMessage('Team ID must be a positive integer'),
  
  body('status')
    .optional()
    .isIn(['Active', 'Inactive']).withMessage('Status must be Active or Inactive')
];

// User ID validation
exports.validateUserId = [
  param('id')
    .notEmpty().withMessage('User ID is required')
    .isInt({ min: 1 }).withMessage('Invalid user ID')
];

// Query filters validation
exports.validateUserFilters = [
  query('role')
    .optional()
    .isIn(['Agent', 'Supervisor', 'Admin']).withMessage('Invalid role filter'),
  
  query('status')
    .optional()
    .isIn(['Active', 'Inactive']).withMessage('Invalid status filter'),
  
  query('teamId')
    .optional()
    .isInt({ min: 1 }).withMessage('Invalid team ID filter')
];

// Validation error handler
exports.handleValidationErrors = (req, res, next) => {
  const errors = validationResult(req);
  if (!errors.isEmpty()) {
    return res.status(400).json({
      success: false,
      message: 'Validation failed',
      errors: errors.array().map(err => ({
        field: err.path,
        message: err.msg
      }))
    });
  }
  next();
};
```

### 3.5 User Controller

**ไฟล์ใหม่: `backend-server/controllers/userController.js` (ให้ 80%)**

```javascript
// controllers/userController.js
const userService = require('../services/userService');

/**
 * User Controller
 * จัดการ HTTP requests สำหรับ user management
 * ให้ 80% - นักศึกษาเพิ่ม updateUser และ deleteUser (20%)
 */
const userController = {
  /**
   * GET /api/users
   * Get all users
   */
  getAllUsers: async (req, res) => {
    try {
      const { role, status, teamId } = req.query;
      
      const users = await userService.getAllUsers({
        role,
        status,
        teamId
      });

      res.status(200).json({
        success: true,
        data: users,
        count: users.length
      });
    } catch (error) {
      console.error('Error in getAllUsers:', error);
      res.status(500).json({
        success: false,
        message: 'Failed to fetch users',
        error: error.message
      });
    }
  },

  /**
   * GET /api/users/:id
   * Get user by ID
   */
  getUserById: async (req, res) => {
    try {
      const { id } = req.params;
      
      const user = await userService.getUserById(id);

      res.status(200).json({
        success: true,
        data: user
      });
    } catch (error) {
      console.error('Error in getUserById:', error);
      const statusCode = error.message === 'User not found' ? 404 : 500;
      res.status(statusCode).json({
        success: false,
        message: error.message
      });
    }
  },

  /**
   * POST /api/users
   * Create new user
   */
  createUser: async (req, res) => {
    try {
      const userData = req.body;
      
      const newUser = await userService.createUser(userData);

      res.status(201).json({
        success: true,
        message: 'User created successfully',
        data: newUser
      });
    } catch (error) {
      console.error('Error in createUser:', error);
      
      // 🆕 Improved error status codes
      let statusCode = 500;
      if (error.message.includes('already exists')) {
        statusCode = 409; // Conflict
      } else if (error.message.includes('Invalid') || error.message.includes('required')) {
        statusCode = 400; // Bad Request
      } else if (error.message.includes('does not exist')) {
        statusCode = 404; // Not Found
      }
      
      res.status(statusCode).json({
        success: false,
        message: error.message
      });
    }
  },

  /**
   * PUT /api/users/:id
   * Update existing user
   * TODO: นักศึกษาเขียน implementation (10%)
   * 
   * 📝 INSTRUCTIONS:
   * 1. ดึง id จาก req.params
   * 2. ดึง updated data จาก req.body
   * 3. เรียก userService.updateUser(id, userData)
   * 4. Return response:
   *    - Success: status 200 + updated user data
   *    - Error: status 400/404/500 + error message
   * 
   * 💡 HINT: ดูตัวอย่างจาก createUser ด้านบน
   */
  updateUser: async (req, res) => {
    try {
      const { id } = req.params;
      const userData = req.body;
      
      // TODO: เรียก userService.updateUser(id, userData)
      // TODO: Return updated user
      
      res.status(501).json({
        success: false,
        message: 'Not implemented - TODO by student'
      });
    } catch (error) {
      console.error('Error in updateUser:', error);
      
      let statusCode = 500;
      if (error.message === 'User not found') {
        statusCode = 404;
      } else if (error.message.includes('cannot be changed') || error.message.includes('Invalid')) {
        statusCode = 400;
      }
      
      res.status(statusCode).json({
        success: false,
        message: error.message
      });
    }
  },

  /**
   * DELETE /api/users/:id
   * Delete user (soft delete)
   * TODO: นักศึกษาเขียน implementation (10%)
   * 
   * 📝 INSTRUCTIONS:
   * 1. ดึง id จาก req.params
   * 2. เรียก userService.deleteUser(id)
   * 3. Return response:
   *    - Success: status 200 + success message
   *    - Error: status 404/500 + error message
   */
  deleteUser: async (req, res) => {
    try {
      const { id } = req.params;
      
      // TODO: เรียก userService.deleteUser(id)
      // TODO: Return success message
      
      res.status(501).json({
        success: false,
        message: 'Not implemented - TODO by student'
      });
    } catch (error) {
      console.error('Error in deleteUser:', error);
      
      const statusCode = error.message === 'User not found' ? 404 : 500;
      
      res.status(statusCode).json({
        success: false,
        message: error.message
      });
    }
  }
};

module.exports = userController;
```

### 3.6 User Routes

**ไฟล์ใหม่: `backend-server/routes/users.js` (ให้ครบ 100%)**

```javascript
// routes/users.js
const express = require('express');
const router = express.Router();
const userController = require('../controllers/userController');
const validation = require('../middleware/validation');
// const auth = require('../middleware/auth'); // ถ้ามี auth middleware

/**
 * User Management Routes
 * ให้ครบ 100%
 */

// GET /api/users - Get all users
router.get('/',
  // auth.verifyToken,           // TODO: เปิดใช้งานถ้าต้องการ authentication
  // auth.requireAdmin,          // TODO: เปิดใช้งานถ้าต้องการ admin only
  validation.validateUserFilters,
  validation.handleValidationErrors,
  userController.getAllUsers
);

// GET /api/users/:id - Get user by ID
router.get('/:id',
  // auth.verifyToken,
  validation.validateUserId,
  validation.handleValidationErrors,
  userController.getUserById
);

// POST /api/users - Create new user
router.post('/',
  // auth.verifyToken,
  // auth.requireAdmin,
  validation.validateCreateUser,
  validation.handleValidationErrors,
  userController.createUser
);

// PUT /api/users/:id - Update user
router.put('/:id',
  // auth.verifyToken,
  // auth.requireAdmin,
  validation.validateUpdateUser,
  validation.handleValidationErrors,
  userController.updateUser
);

// DELETE /api/users/:id - Delete user (soft delete)
router.delete('/:id',
  // auth.verifyToken,
  // auth.requireAdmin,
  validation.validateUserId,
  validation.handleValidationErrors,
  userController.deleteUser
);

module.exports = router;
```

### 3.7 Update Auth Service (Login Without Password)

**แก้ไขไฟล์: `backend-server/services/authService.js`**

```javascript
// services/authService.js
const jwt = require('jsonwebtoken');
const userRepository = require('../repositories/userRepository');

const JWT_SECRET = process.env.JWT_SECRET || 'your-secret-key';
const JWT_EXPIRES_IN = '24h';

/**
 * Authentication Service
 * เพิ่ม loginWithoutPassword method
 */
const authService = {
  /**
   * 🆕 Login without password (using username only)
   * @param {string} username - User username/code
   * @returns {Promise<Object>} Auth result with token
   */
  loginWithoutPassword: async (username) => {
    try {
      // 1. Find user by username
      const user = await userRepository.findByUsername(username);
      
      if (!user) {
        throw new Error('Invalid username');
      }

      // 2. Check if user is active
      if (user.status !== 'Active') {
        throw new Error('User account is inactive');
      }

      // 3. Generate JWT token
      const token = jwt.sign(
        {
          userId: user.id,
          username: user.username,
          role: user.role
        },
        JWT_SECRET,
        { expiresIn: JWT_EXPIRES_IN }
      );

      // 4. Update last login timestamp
      await userRepository.updateLastLogin(user.id);

      // 5. Return user data และ token
      return {
        success: true,
        user: {
          id: user.id,
          username: user.username,
          fullName: user.fullName,
          role: user.role,
          teamId: user.teamId
        },
        token: token,
        expiresIn: JWT_EXPIRES_IN
      };
    } catch (error) {
      console.error('Error in loginWithoutPassword:', error);
      throw error;
    }
  },

  /**
   * Verify JWT token
   */
  verifyToken: (token) => {
    try {
      const decoded = jwt.verify(token, JWT_SECRET);
      return decoded;
    } catch (error) {
      throw new Error('Invalid or expired token');
    }
  }
};

module.exports = authService;
```

### 3.8 Update Auth Routes

**แก้ไขไฟล์: `backend-server/routes/auth.js`**

เพิ่ม route สำหรับ login without password:

```javascript
// routes/auth.js
const express = require('express');
const router = express.Router();
const authService = require('../services/authService');
const { body, validationResult } = require('express-validator');

/**
 * 🆕 POST /api/auth/login
 * Login without password
 */
router.post('/login',
  // Validation
  body('username')
    .notEmpty().withMessage('Username is required')
    .matches(/^(AG|SP|AD)(00[1-9]|0[1-9]\d|[1-9]\d{2})$/)
    .withMessage('Invalid username format'),
  
  // Handler
  async (req, res) => {
    try {
      // Check validation
      const errors = validationResult(req);
      if (!errors.isEmpty()) {
        return res.status(400).json({
          success: false,
          message: 'Validation failed',
          errors: errors.array()
        });
      }

      const { username } = req.body;
      
      // Login
      const result = await authService.loginWithoutPassword(username);

      res.status(200).json(result);
    } catch (error) {
      console.error('Login error:', error);
      
      let statusCode = 500;
      if (error.message === 'Invalid username') {
        statusCode = 401;
      } else if (error.message === 'User account is inactive') {
        statusCode = 403;
      }
      
      res.status(statusCode).json({
        success: false,
        message: error.message
      });
    }
  }
);

module.exports = router;
```

### 3.9 Update Server.js

**แก้ไขไฟล์: `backend-server/server.js`**

เพิ่ม users route:

```javascript
// server.js
// ... existing code ...

// Import routes
const authRoutes = require('./routes/auth');
const agentRoutes = require('./routes/agents');
const messageRoutes = require('./routes/messages');
const userRoutes = require('./routes/users'); // 🆕 เพิ่มบรรทัดนี้

// ... existing code ...

// API Routes
app.use('/api/auth', authRoutes);
app.use('/api/agents', agentRoutes);
app.use('/api/messages', messageRoutes);
app.use('/api/users', userRoutes); // 🆕 เพิ่มบรรทัดนี้

// ... rest of the code ...
```

### 3.10 ทดสอบ Backend APIs

**ใช้ Postman หรือ curl ทดสอบ:**

```bash
# 1. Get all users
curl http://localhost:3001/api/users

# 2. Get user by ID
curl http://localhost:3001/api/users/1

# 3. Create new user
curl -X POST http://localhost:3001/api/users \
  -H "Content-Type: application/json" \
  -d '{
    "username": "AG099",
    "fullName": "Test Agent",
    "role": "Agent",
    "teamId": 1,
    "status": "Active"
  }'

# 4. Update user (TODO: นักศึกษาทดสอบหลังเขียนเสร็จ)
curl -X PUT http://localhost:3001/api/users/1 \
  -H "Content-Type: application/json" \
  -d '{
    "fullName": "Updated Name",
    "status": "Inactive"
  }'

# 5. Delete user (TODO: นักศึกษาทดสอบหลังเขียนเสร็จ)
curl -X DELETE http://localhost:3001/api/users/1

# 6. Login without password
curl -X POST http://localhost:3001/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"username": "AD001"}'
```

---

## 4. ส่วนที่ 3: Frontend Admin Panel

### 4.1 สร้าง React Project ใหม่

```bash
# สร้าง React app ใหม่
npx create-react-app admin-panel
cd admin-panel

# ติดตั้ง dependencies
npm install

# ไม่ต้องติดตั้งอะไรเพิ่ม เพราะใช้ React เปล่าๆ
```

### 4.2 Environment Configuration

**ไฟล์: `admin-panel/.env`**

```env
REACT_APP_API_URL=http://localhost:3001/api
```

### 4.3 API Services

**ไฟล์: `src/services/authAPI.js` (ให้ครบ 100%)**

```javascript
// services/authAPI.js
const API_BASE_URL = process.env.REACT_APP_API_URL || 'http://localhost:3001/api';

/**
 * Authentication API Service
 * ให้ครบ 100%
 */
export const authAPI = {
  /**
   * Login without password
   * @param {string} username - User username
   * @returns {Promise<Object>} Login result with token
   */
  login: async (username) => {
    try {
      const response = await fetch(`${API_BASE_URL}/auth/login`, {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify({ username })
      });

      const data = await response.json();

      if (!response.ok) {
        throw new Error(data.message || 'Login failed');
      }

      // Store token in localStorage
      if (data.token) {
        localStorage.setItem('token', data.token);
        localStorage.setItem('user', JSON.stringify(data.user));
      }

      return data;
    } catch (error) {
      // 🆕 Better error handling
      if (error.message === 'Failed to fetch') {
        throw new Error('Network error. Please check your internet connection.');
      }
      console.error('Login error:', error);
      throw error;
    }
  },

  /**
   * Logout
   */
  logout: () => {
    localStorage.removeItem('token');
    localStorage.removeItem('user');
  },

  /**
   * Get current user from localStorage
   */
  getCurrentUser: () => {
    const userStr = localStorage.getItem('user');
    return userStr ? JSON.parse(userStr) : null;
  },

  /**
   * Check if user is logged in
   */
  isLoggedIn: () => {
    return localStorage.getItem('token') !== null;
  }
};
```

**ไฟล์: `src/services/userAPI.js` (ให้ 75%)**

```javascript
// services/userAPI.js
const API_BASE_URL = process.env.REACT_APP_API_URL || 'http://localhost:3001/api';

/**
 * 🆕 Helper function for error handling
 */
const handleAPIError = (error) => {
  if (error.message === 'Failed to fetch') {
    throw new Error('Network error. Please check your internet connection.');
  }
  throw error;
};

/**
 * User API Service
 * ให้ 75% - นักศึกษาเพิ่ม updateUser และ deleteUser (25%)
 */
export const userAPI = {
  /**
   * Get all users
   */
  getAllUsers: async () => {
    try {
      const response = await fetch(`${API_BASE_URL}/users`, {
        method: 'GET',
        headers: {
          'Content-Type': 'application/json',
          'Authorization': `Bearer ${localStorage.getItem('token')}`
        }
      });

      // 🆕 Handle authentication errors
      if (response.status === 401) {
        localStorage.removeItem('token');
        localStorage.removeItem('user');
        window.location.href = '/';
        throw new Error('Session expired. Please login again.');
      }

      if (!response.ok) {
        const errorData = await response.json();
        throw new Error(errorData.message || `HTTP error! status: ${response.status}`);
      }

      const data = await response.json();
      return data.data; // Return the users array
    } catch (error) {
      console.error('Error fetching users:', error);
      handleAPIError(error);
    }
  },

  /**
   * Get user by ID
   */
  getUserById: async (userId) => {
    try {
      const response = await fetch(`${API_BASE_URL}/users/${userId}`, {
        method: 'GET',
        headers: {
          'Content-Type': 'application/json',
          'Authorization': `Bearer ${localStorage.getItem('token')}`
        }
      });

      if (!response.ok) {
        const errorData = await response.json();
        throw new Error(errorData.message || `HTTP error! status: ${response.status}`);
      }

      const data = await response.json();
      return data.data;
    } catch (error) {
      console.error('Error fetching user:', error);
      handleAPIError(error);
    }
  },

  /**
   * Create new user
   */
  createUser: async (userData) => {
    try {
      const response = await fetch(`${API_BASE_URL}/users`, {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
          'Authorization': `Bearer ${localStorage.getItem('token')}`
        },
        body: JSON.stringify(userData)
      });

      if (!response.ok) {
        const errorData = await response.json();
        throw new Error(errorData.message || 'Failed to create user');
      }

      const data = await response.json();
      return data.data;
    } catch (error) {
      console.error('Error creating user:', error);
      handleAPIError(error);
    }
  },

  /**
   * Update user
   * TODO: นักศึกษาเขียน implementation (15%)
   * 
   * 📝 INSTRUCTIONS:
   * 1. ส่ง PUT request ไปที่ `${API_BASE_URL}/users/${userId}`
   * 2. Headers ต้องมี:
   *    - 'Content-Type': 'application/json'
   *    - 'Authorization': Bearer token
   * 3. Body: JSON.stringify(userData)
   * 4. Handle errors เหมือน createUser
   * 5. Return data.data
   * 
   * 💡 HINT: Copy จาก createUser แล้วเปลี่ยน method และ URL
   */
  updateUser: async (userId, userData) => {
    try {
      // TODO: ส่ง PUT request
      // TODO: ส่ง userData ใน body
      // TODO: ใส่ Authorization header
      // TODO: Handle response และ errors
      
      throw new Error('Not implemented - TODO by student');
    } catch (error) {
      console.error('Error updating user:', error);
      handleAPIError(error);
    }
  },

  /**
   * Delete user
   * TODO: นักศึกษาเขียน implementation (10%)
   * 
   * 📝 INSTRUCTIONS:
   * 1. ส่ง DELETE request ไปที่ `${API_BASE_URL}/users/${userId}`
   * 2. Headers ต้องมี Authorization
   * 3. ไม่ต้องมี body
   * 4. Handle errors
   * 5. Return success: true
   */
  deleteUser: async (userId) => {
    try {
      // TODO: ส่ง DELETE request
      // TODO: ใส่ Authorization header
      // TODO: Handle response
      
      throw new Error('Not implemented - TODO by student');
    } catch (error) {
      console.error('Error deleting user:', error);
      handleAPIError(error);
    }
  }
};
```

### 4.4 Login Page

**ไฟล์: `src/pages/LoginPage.js` (ให้ครบ 100%)**

```javascript
// pages/LoginPage.js
import React, { useState } from 'react';
import { authAPI } from '../services/authAPI';
import '../styles/LoginPage.css';

const LoginPage = ({ onLoginSuccess }) => {
  const [username, setUsername] = useState('');
  const [error, setError] = useState('');
  const [loading, setLoading] = useState(false);

  const handleSubmit = async (e) => {
    e.preventDefault();
    setError('');
    setLoading(true);

    try {
      // Validate username format
      const usernameRegex = /^(AG|SP|AD)(00[1-9]|0[1-9]\d|[1-9]\d{2})$/;
      if (!usernameRegex.test(username)) {
        setError('Invalid username format. Use AGxxx, SPxxx, or ADxxx');
        setLoading(false);
        return;
      }

      // Login
      const result = await authAPI.login(username);

      // Check if user is Admin
      if (result.user.role !== 'Admin') {
        setError('Access denied. Admin role required.');
        authAPI.logout();
        setLoading(false);
        return;
      }

      // Success - redirect to user management
      onLoginSuccess();
    } catch (err) {
      setError(err.message || 'Login failed');
    } finally {
      setLoading(false);
    }
  };

  return React.createElement('div', { className: 'login-container' },
    React.createElement('div', { className: 'login-box' },
      React.createElement('h1', { className: 'login-title' }, 
        '🔐 Admin Panel'
      ),
      React.createElement('p', { className: 'login-subtitle' },
        'User Management System'
      ),

      React.createElement('form', { onSubmit: handleSubmit, className: 'login-form' },
        React.createElement('div', { className: 'form-group' },
          React.createElement('label', { htmlFor: 'username' }, 'Admin Username'),
          React.createElement('input', {
            type: 'text',
            id: 'username',
            value: username,
            onChange: (e) => setUsername(e.target.value.toUpperCase()),
            placeholder: 'AD001',
            required: true,
            autoFocus: true,
            className: error ? 'error' : ''
          }),
          React.createElement('small', { className: 'hint' },
            'Format: AD001-AD999'
          )
        ),

        error && React.createElement('div', { className: 'alert alert-error' }, error),

        React.createElement('button', {
          type: 'submit',
          className: 'btn btn-primary',
          disabled: loading
        }, loading ? 'Logging in...' : 'Login')
      ),

      React.createElement('div', { className: 'login-footer' },
        React.createElement('p', null, '💡 Test Accounts:'),
        React.createElement('ul', null,
          React.createElement('li', null, 'AD001 - Admin One'),
          React.createElement('li', null, 'AD002 - Admin Two')
        )
      )
    )
  );
};

export default LoginPage;
```

**CSS: `src/styles/LoginPage.css` (ให้ครบ 100%)**

```css
/* styles/LoginPage.css */

.login-container {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  padding: 20px;
}

.login-box {
  background: white;
  border-radius: 12px;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
  padding: 40px;
  width: 100%;
  max-width: 400px;
  animation: slideUp 0.3s ease;
}

@keyframes slideUp {
  from {
    transform: translateY(20px);
    opacity: 0;
  }
  to {
    transform: translateY(0);
    opacity: 1;
  }
}

.login-title {
  font-size: 32px;
  font-weight: 700;
  text-align: center;
  margin: 0 0 8px 0;
  color: #1a1a1a;
}

.login-subtitle {
  text-align: center;
  color: #666;
  margin: 0 0 32px 0;
  font-size: 14px;
}

.login-form {
  margin-bottom: 24px;
}

.form-group {
  margin-bottom: 20px;
}

.form-group label {
  display: block;
  margin-bottom: 6px;
  font-weight: 500;
  font-size: 14px;
  color: #333;
}

.form-group input {
  width: 100%;
  padding: 12px;
  border: 2px solid #ddd;
  border-radius: 6px;
  font-size: 16px;
  transition: border-color 0.2s ease;
  box-sizing: border-box;
  text-transform: uppercase;
  font-family: 'Courier New', monospace;
  font-weight: 600;
}

.form-group input:focus {
  outline: none;
  border-color: #667eea;
  box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
}

.form-group input.error {
  border-color: #f44336;
}

.hint {
  display: block;
  margin-top: 4px;
  font-size: 12px;
  color: #666;
  font-style: italic;
}

.alert {
  padding: 12px;
  border-radius: 6px;
  margin-bottom: 16px;
  font-size: 14px;
}

.alert-error {
  background-color: #fee;
  border-left: 4px solid #f44336;
  color: #c62828;
}

.btn {
  width: 100%;
  padding: 12px;
  border: none;
  border-radius: 6px;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
}

.btn-primary {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
}

.btn-primary:hover:not(:disabled) {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(102, 126, 234, 0.4);
}

.btn-primary:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

.login-footer {
  text-align: center;
  padding-top: 20px;
  border-top: 1px solid #e0e0e0;
}

.login-footer p {
  margin: 0 0 8px 0;
  font-size: 13px;
  color: #666;
  font-weight: 600;
}

.login-footer ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.login-footer li {
  font-size: 12px;
  color: #999;
  font-family: 'Courier New', monospace;
  margin: 4px 0;
}
```

### 4.5 User Management Page

**ไฟล์: `src/pages/UserManagementPage.js` (ให้ 65%)**

```javascript
// pages/UserManagementPage.js
import React, { useState, useEffect } from 'react';
import UserTable from '../components/UserTable';
import UserFormModal from '../components/UserFormModal';
import { userAPI } from '../services/userAPI';
import { authAPI } from '../services/authAPI';
import '../styles/UserManagementPage.css';

const UserManagementPage = ({ onLogout }) => {
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState(null);
  const [selectedUser, setSelectedUser] = useState(null);
  const [isModalOpen, setIsModalOpen] = useState(false);
  const [successMessage, setSuccessMessage] = useState('');

  const currentUser = authAPI.getCurrentUser();

  // Load users on component mount
  useEffect(() => {
    loadUsers();
  }, []);

  // 🆕 Auto-clear success message after 3 seconds
  useEffect(() => {
    if (successMessage) {
      const timer = setTimeout(() => {
        setSuccessMessage('');
      }, 3000);
      
      return () => clearTimeout(timer);
    }
  }, [successMessage]);

  const loadUsers = async () => {
    setLoading(true);
    setError(null);
    try {
      const data = await userAPI.getAllUsers();
      setUsers(data);
    } catch (err) {
      setError(err.message);
    } finally {
      setLoading(false);
    }
  };

  const handleCreateUser = () => {
    setSelectedUser(null);
    setIsModalOpen(true);
  };

  const handleEditUser = (user) => {
    setSelectedUser(user);
    setIsModalOpen(true);
  };

  /**
   * TODO: นักศึกษาเขียน handleDeleteUser function (10%)
   * 
   * 📝 INSTRUCTIONS:
   * 1. แสดง confirmation dialog
   *    - ใช้ window.confirm(`Are you sure you want to delete user "${user.username}"?`)
   * 2. ถ้า user confirm (true):
   *    - try { ... } catch { ... }
   *    - เรียก await userAPI.deleteUser(userId)
   *    - setSuccessMessage('User deleted successfully')
   *    - await loadUsers() เพื่อ refresh list
   * 3. ถ้า error:
   *    - setError(err.message)
   */
  const handleDeleteUser = async (userId) => {
    // TODO: แสดง confirmation dialog
    // TODO: เรียก userAPI.deleteUser(userId)
    // TODO: refresh user list
    // TODO: แสดง success message
    
    console.log('Delete user:', userId, '- TODO by student');
  };

  const handleSaveUser = async (userData) => {
    try {
      if (selectedUser) {
        // Edit mode
        // TODO: นักศึกษาเรียก userAPI.updateUser(selectedUser.id, userData) (10%)
        console.log('Update user - TODO by student');
        setSuccessMessage('User updated successfully');
      } else {
        // Create mode
        await userAPI.createUser(userData);
        setSuccessMessage('User created successfully');
      }
      
      setIsModalOpen(false);
      await loadUsers();
    } catch (err) {
      setError(err.message);
    }
  };

  return React.createElement('div', { className: 'user-management-page' },
    // Header
    React.createElement('div', { className: 'page-header' },
      React.createElement('div', null,
        React.createElement('h1', null, '👥 User Management'),
        React.createElement('p', { className: 'page-subtitle' },
          `Logged in as: ${currentUser?.fullName} (${currentUser?.username})`
        )
      ),
      React.createElement('div', { className: 'header-actions' },
        React.createElement('button', {
          className: 'btn btn-primary',
          onClick: handleCreateUser
        }, '+ Add New User'),
        React.createElement('button', {
          className: 'btn btn-secondary',
          onClick: onLogout
        }, '🚪 Logout')
      )
    ),

    // Success message
    successMessage && React.createElement('div', { className: 'alert alert-success' },
      successMessage
    ),

    // Error message
    error && React.createElement('div', { className: 'alert alert-error' }, error),

    // Loading state
    loading ? 
      React.createElement('div', { className: 'loading' }, '⏳ Loading users...') :
      // User table
      React.createElement(UserTable, {
        users: users,
        onEdit: handleEditUser,
        onDelete: handleDeleteUser
      }),

    // User form modal
    isModalOpen && React.createElement(UserFormModal, {
      user: selectedUser,
      onClose: () => setIsModalOpen(false),
      onSave: handleSaveUser
    })
  );
};

export default UserManagementPage;
```

**CSS: `src/styles/UserManagementPage.css` (ให้ครบ 100%)**

```css
/* styles/UserManagementPage.css */

.user-management-page {
  padding: 24px;
  max-width: 1400px;
  margin: 0 auto;
  min-height: 100vh;
  background-color: #f5f5f5;
}

.page-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 24px;
  padding: 20px;
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.page-header h1 {
  font-size: 28px;
  font-weight: 600;
  color: #1a1a1a;
  margin: 0 0 4px 0;
}

.page-subtitle {
  font-size: 13px;
  color: #666;
  margin: 0;
}

.header-actions {
  display: flex;
  gap: 12px;
}

.btn {
  padding: 10px 20px;
  border: none;
  border-radius: 6px;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.3s ease;
}

.btn-primary {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(102, 126, 234, 0.4);
}

.btn-secondary {
  background-color: #f5f5f5;
  color: #333;
  border: 1px solid #ddd;
}

.btn-secondary:hover {
  background-color: #e0e0e0;
}

.alert {
  padding: 12px 16px;
  border-radius: 6px;
  margin-bottom: 20px;
  font-size: 14px;
  animation: slideIn 0.3s ease;
}

@keyframes slideIn {
  from {
    transform: translateY(-10px);
    opacity: 0;
  }
  to {
    transform: translateY(0);
    opacity: 1;
  }
}

.alert-success {
  background-color: #e8f5e8;
  border-left: 4px solid #4caf50;
  color: #2e7d32;
}

.alert-error {
  background-color: #fee;
  border-left: 4px solid #f44336;
  color: #c62828;
}

.loading {
  text-align: center;
  padding: 60px;
  font-size: 18px;
  color: #666;
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}
```

### 4.6 User Table Component

**ไฟล์: `src/components/UserTable.js` (ให้ครบ 100%)**

```javascript
// components/UserTable.js
import React from 'react';
import UserActionButtons from './UserActionButtons';
import '../styles/UserTable.css';

const UserTable = ({ users, onEdit, onDelete }) => {
  return React.createElement('div', { className: 'user-table-container' },
    React.createElement('table', { className: 'user-table' },
      // Table Header
      React.createElement('thead', null,
        React.createElement('tr', null,
          React.createElement('th', null, 'Username'),
          React.createElement('th', null, 'Full Name'),
          React.createElement('th', null, 'Role'),
          React.createElement('th', null, 'Team'),
          React.createElement('th', null, 'Status'),
          React.createElement('th', null, 'Created Date'),
          React.createElement('th', null, 'Actions')
        )
      ),
      // Table Body
      React.createElement('tbody', null,
        users.length === 0 ?
          React.createElement('tr', null,
            React.createElement('td', { colSpan: 7, className: 'no-data' },
              'No users found. Click "Add New User" to create one.'
            )
          ) :
          users.map(user =>
            React.createElement('tr', { key: user.id },
              React.createElement('td', null,
                React.createElement('span', { className: 'username' }, user.username)
              ),
              React.createElement('td', null, user.fullName),
              React.createElement('td', null,
                React.createElement('span', { 
                  className: `role-badge role-${user.role.toLowerCase()}` 
                }, user.role)
              ),
              React.createElement('td', null, user.teamName || '-'),
              React.createElement('td', null,
                React.createElement('span', {
                  className: `status-badge status-${user.status.toLowerCase()}`
                }, user.status)
              ),
              React.createElement('td', null,
                new Date(user.createdAt).toLocaleDateString('th-TH')
              ),
              React.createElement('td', null,
                React.createElement(UserActionButtons, {
                  user: user,
                  onEdit: () => onEdit(user),
                  onDelete: () => onDelete(user.id)
                })
              )
            )
          )
      )
    )
  );
};

export default UserTable;
```

**CSS: `src/styles/UserTable.css` (ให้ครบ 100%)**

```css
/* styles/UserTable.css */

.user-table-container {
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  overflow: hidden;
}

.user-table {
  width: 100%;
  border-collapse: collapse;
}

.user-table thead {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
}

.user-table th {
  padding: 14px 16px;
  text-align: left;
  font-weight: 600;
  font-size: 13px;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.user-table tbody tr {
  border-bottom: 1px solid #f0f0f0;
  transition: background-color 0.2s ease;
}

.user-table tbody tr:hover {
  background-color: #f8f9ff;
}

.user-table td {
  padding: 14px 16px;
  font-size: 14px;
  color: #333;
}

.username {
  font-family: 'Courier New', monospace;
  font-weight: 600;
  color: #667eea;
}

.role-badge {
  display: inline-block;
  padding: 4px 12px;
  border-radius: 12px;
  font-size: 12px;
  font-weight: 600;
  text-transform: uppercase;
}

.role-agent {
  background-color: #e3f2fd;
  color: #1976d2;
}

.role-supervisor {
  background-color: #fff3e0;
  color: #f57c00;
}

.role-admin {
  background-color: #fce4ec;
  color: #c2185b;
}

.status-badge {
  display: inline-block;
  padding: 4px 12px;
  border-radius: 12px;
  font-size: 12px;
  font-weight: 600;
}

.status-active {
  background-color: #e8f5e8;
  color: #2e7d32;
}

.status-inactive {
  background-color: #ffebee;
  color: #c62828;
}

.no-data {
  text-align: center;
  padding: 40px;
  color: #999;
  font-style: italic;
}
```

### 4.7 User Form Modal Component

**ไฟล์: `src/components/UserFormModal.js` (ให้ 60%)**

```javascript
// components/UserFormModal.js
import React, { useState, useEffect } from 'react';
import '../styles/UserFormModal.css';

const UserFormModal = ({ user, onClose, onSave }) => {
  // Initialize form data
  const [formData, setFormData] = useState({
    username: '',
    fullName: '',
    role: 'Agent',
    teamId: '',
    status: 'Active'
  });

  const [errors, setErrors] = useState({});

  // Load user data if editing
  useEffect(() => {
    if (user) {
      setFormData({
        username: user.username,
        fullName: user.fullName,
        role: user.role,
        teamId: user.teamId || '',
        status: user.status
      });
    }
  }, [user]);

  /**
   * TODO: นักศึกษาเขียน handleChange function (10%)
   * 
   * 📝 INSTRUCTIONS:
   * 1. ดึง name และ value จาก e.target
   * 2. อัพเดท formData state:
   *    setFormData(prev => ({ ...prev, [name]: value }))
   * 3. เคลียร์ error ของ field นั้น:
   *    if (errors[name]) {
   *      setErrors(prev => ({ ...prev, [name]: null }))
   *    }
   */
  const handleChange = (e) => {
    const { name, value } = e.target;
    
    // TODO: อัพเดท formData
    // TODO: เคลียร์ error
  };

  /**
   * TODO: นักศึกษาเขียน validateForm function (15%)
   * 
   * 📝 INSTRUCTIONS:
   * 1. สร้าง object newErrors = {}
   * 2. ตรวจสอบ username:
   *    - ถ้าว่าง: newErrors.username = 'Username is required'
   *    - ถ้า format ผิด: newErrors.username = 'Invalid username format'
   * 3. ตรวจสอบ fullName:
   *    - ถ้าว่างหรือสั้นกว่า 2 ตัวอักษร: newErrors.fullName = 'Full name must be at least 2 characters'
   * 4. ตรวจสอบ teamId (ถ้า role เป็น Agent หรือ Supervisor):
   *    - if ((formData.role === 'Agent' || formData.role === 'Supervisor') && !formData.teamId)
   *    - newErrors.teamId = 'Team is required for Agent and Supervisor'
   * 5. setErrors(newErrors)
   * 6. return Object.keys(newErrors).length === 0
   */
  const validateForm = () => {
    const newErrors = {};
    
    // TODO: Validate username
    // TODO: Validate fullName
    // TODO: Validate role-specific rules
    
    setErrors(newErrors);
    return Object.keys(newErrors).length === 0;
  };

  /**
   * TODO: นักศึกษาเขียน handleSubmit function (15%)
   * 
   * 📝 INSTRUCTIONS:
   * 1. e.preventDefault()
   * 2. ถ้า validateForm() === true:
   *    - เรียก onSave(formData)
   * 3. ถ้า validateForm() === false:
   *    - error messages จะแสดงอัตโนมัติจาก errors state
   */
  const handleSubmit = (e) => {
    e.preventDefault();
    
    // TODO: validate form
    // TODO: ถ้าผ่าน validation เรียก onSave(formData)
  };

  return React.createElement('div', { className: 'modal-overlay', onClick: onClose },
    React.createElement('div', {
      className: 'modal-content',
      onClick: (e) => e.stopPropagation()
    },
      // Modal Header
      React.createElement('div', { className: 'modal-header' },
        React.createElement('h2', null, user ? 'Edit User' : 'Add New User'),
        React.createElement('button', {
          className: 'btn-close',
          onClick: onClose
        }, '×')
      ),

      // Modal Body (Form)
      React.createElement('form', { onSubmit: handleSubmit, className: 'user-form' },
        // Username field
        React.createElement('div', { className: 'form-group' },
          React.createElement('label', { htmlFor: 'username' },
            'Username ',
            React.createElement('span', { className: 'required' }, '*')
          ),
          React.createElement('input', {
            type: 'text',
            id: 'username',
            name: 'username',
            value: formData.username,
            onChange: handleChange,
            placeholder: 'e.g., AG001, SP001, AD001',
            disabled: !!user, // disabled เมื่อแก้ไข
            className: errors.username ? 'error' : ''
          }),
          React.createElement('small', { className: 'hint' },
            'Format: AG001-AG999 (Agent), SP001-SP999 (Supervisor), AD001-AD999 (Admin)'
          ),
          errors.username && React.createElement('span', { className: 'error-message' },
            errors.username
          )
        ),

        // Full Name field
        React.createElement('div', { className: 'form-group' },
          React.createElement('label', { htmlFor: 'fullName' },
            'Full Name ',
            React.createElement('span', { className: 'required' }, '*')
          ),
          React.createElement('input', {
            type: 'text',
            id: 'fullName',
            name: 'fullName',
            value: formData.fullName,
            onChange: handleChange,
            placeholder: 'Enter full name',
            className: errors.fullName ? 'error' : ''
          }),
          errors.fullName && React.createElement('span', { className: 'error-message' },
            errors.fullName
          )
        ),

        // Role field
        React.createElement('div', { className: 'form-group' },
          React.createElement('label', { htmlFor: 'role' },
            'Role ',
            React.createElement('span', { className: 'required' }, '*')
          ),
          React.createElement('select', {
            id: 'role',
            name: 'role',
            value: formData.role,
            onChange: handleChange,
            className: errors.role ? 'error' : ''
          },
            React.createElement('option', { value: 'Agent' }, 'Agent'),
            React.createElement('option', { value: 'Supervisor' }, 'Supervisor'),
            React.createElement('option', { value: 'Admin' }, 'Admin')
          )
        ),

        // Team field (optional for Agent/Supervisor)
        React.createElement('div', { className: 'form-group' },
          React.createElement('label', { htmlFor: 'teamId' }, 'Team'),
          React.createElement('select', {
            id: 'teamId',
            name: 'teamId',
            value: formData.teamId,
            onChange: handleChange,
            className: errors.teamId ? 'error' : ''
          },
            React.createElement('option', { value: '' }, '-- Select Team --'),
            React.createElement('option', { value: '1' }, 'Team Alpha'),
            React.createElement('option', { value: '2' }, 'Team Beta'),
            React.createElement('option', { value: '3' }, 'Team Gamma')
          ),
          React.createElement('small', { className: 'hint' },
            'Required for Agent and Supervisor roles'
          ),
          errors.teamId && React.createElement('span', { className: 'error-message' },
            errors.teamId
          )
        ),

        // Status field
        React.createElement('div', { className: 'form-group' },
          React.createElement('label', { htmlFor: 'status' },
            'Status ',
            React.createElement('span', { className: 'required' }, '*')
          ),
          React.createElement('select', {
            id: 'status',
            name: 'status',
            value: formData.status,
            onChange: handleChange
          },
            React.createElement('option', { value: 'Active' }, 'Active'),
            React.createElement('option', { value: 'Inactive' }, 'Inactive')
          )
        ),

        // Form Actions
        React.createElement('div', { className: 'form-actions' },
          React.createElement('button', {
            type: 'button',
            className: 'btn btn-secondary',
            onClick: onClose
          }, 'Cancel'),
          React.createElement('button', {
            type: 'submit',
            className: 'btn btn-primary'
          }, user ? 'Update User' : 'Create User')
        )
      )
    )
  );
};

export default UserFormModal;
```

**CSS: `src/styles/UserFormModal.css` (ให้ครบ 100%)**

```css
/* styles/UserFormModal.css */

.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
  animation: fadeIn 0.2s ease;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

.modal-content {
  background: white;
  border-radius: 12px;
  width: 90%;
  max-width: 600px;
  max-height: 90vh;
  overflow-y: auto;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
  animation: slideUp 0.3s ease;
}

@keyframes slideUp {
  from {
    transform: translateY(20px);
    opacity: 0;
  }
  to {
    transform: translateY(0);
    opacity: 1;
  }
}

.modal-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 24px;
  border-bottom: 1px solid #e0e0e0;
}

.modal-header h2 {
  margin: 0;
  font-size: 22px;
  font-weight: 600;
  color: #1a1a1a;
}

.btn-close {
  background: none;
  border: none;
  font-size: 32px;
  color: #999;
  cursor: pointer;
  padding: 0;
  width: 32px;
  height: 32px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: color 0.2s ease;
}

.btn-close:hover {
  color: #333;
}

.user-form {
  padding: 24px;
}

.form-group {
  margin-bottom: 20px;
}

.form-group label {
  display: block;
  margin-bottom: 6px;
  font-weight: 500;
  font-size: 14px;
  color: #333;
}

.required {
  color: #f44336;
}

.form-group input,
.form-group select {
  width: 100%;
  padding: 10px 12px;
  border: 1px solid #ddd;
  border-radius: 6px;
  font-size: 14px;
  transition: border-color 0.2s ease;
  box-sizing: border-box;
}

.form-group input:focus,
.form-group select:focus {
  outline: none;
  border-color: #667eea;
  box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
}

.form-group input.error,
.form-group select.error {
  border-color: #f44336;
}

.form-group input:disabled {
  background-color: #f5f5f5;
  cursor: not-allowed;
}

.hint {
  display: block;
  margin-top: 4px;
  font-size: 12px;
  color: #666;
  font-style: italic;
}

.error-message {
  display: block;
  margin-top: 4px;
  font-size: 12px;
  color: #f44336;
}

.form-actions {
  display: flex;
  justify-content: flex-end;
  gap: 12px;
  margin-top: 24px;
  padding-top: 20px;
  border-top: 1px solid #e0e0e0;
}

.btn {
  padding: 10px 20px;
  border: none;
  border-radius: 6px;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.3s ease;
}

.btn-secondary {
  background-color: #f5f5f5;
  color: #333;
}

.btn-secondary:hover {
  background-color: #e0e0e0;
}

.btn-primary {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(102, 126, 234, 0.4);
}
```

### 4.8 User Action Buttons Component

**ไฟล์: `src/components/UserActionButtons.js` (ให้ครบ 100%)**

```javascript
// components/UserActionButtons.js
import React from 'react';
import '../styles/UserActionButtons.css';

const UserActionButtons = ({ user, onEdit, onDelete }) => {
  const handleDelete = () => {
    if (window.confirm(`Are you sure you want to delete user "${user.username}"?`)) {
      onDelete();
    }
  };

  return React.createElement('div', { className: 'action-buttons' },
    React.createElement('button', {
      className: 'btn-action btn-edit',
      onClick: onEdit,
      title: 'Edit user'
    }, '✏️ Edit'),
    React.createElement('button', {
      className: 'btn-action btn-delete',
      onClick: handleDelete,
      title: 'Delete user'
    }, '🗑️ Delete')
  );
};

export default UserActionButtons;
```

**CSS: `src/styles/UserActionButtons.css` (ให้ครบ 100%)**

```css
/* styles/UserActionButtons.css */

.action-buttons {
  display: flex;
  gap: 8px;
}

.btn-action {
  padding: 6px 12px;
  border: none;
  border-radius: 4px;
  font-size: 12px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.2s ease;
}

.btn-edit {
  background-color: #e3f2fd;
  color: #1976d2;
}

.btn-edit:hover {
  background-color: #1976d2;
  color: white;
  transform: translateY(-1px);
}

.btn-delete {
  background-color: #ffebee;
  color: #c62828;
}

.btn-delete:hover {
  background-color: #c62828;
  color: white;
  transform: translateY(-1px);
}
```

### 4.9 Main App Component

**ไฟล์: `src/App.js` (ให้ครบ 100%)**

```javascript
// App.js
import React, { useState } from 'react';
import LoginPage from './pages/LoginPage';
import UserManagementPage from './pages/UserManagementPage';
import { authAPI } from './services/authAPI';
import './App.css';

function App() {
  const [isLoggedIn, setIsLoggedIn] = useState(authAPI.isLoggedIn());

  const handleLoginSuccess = () => {
    setIsLoggedIn(true);
  };

  const handleLogout = () => {
    authAPI.logout();
    setIsLoggedIn(false);
  };

  return React.createElement('div', { className: 'App' },
    isLoggedIn ? 
      React.createElement(UserManagementPage, { onLogout: handleLogout }) :
      React.createElement(LoginPage, { onLoginSuccess: handleLoginSuccess })
  );
}

export default App;
```

**CSS: `src/App.css`**

```css
/* App.css */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen',
    'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans', 'Helvetica Neue',
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.App {
  min-height: 100vh;
  background-color: #f5f5f5;
}
```

---

## 5. ส่วนที่ 4: Integration & Testing

### 5.1 Environment Verification (🆕)

**ก่อนเริ่มทำงาน - ตรวจสอบความพร้อม:**

```bash
# ========================================
# ขั้นตอนการตรวจสอบ Environment
# ========================================

# 1. ตรวจสอบ Node.js version
node --version
# ควรเป็น v18.x หรือสูงกว่า

# 2. ตรวจสอบ npm version
npm --version
# ควรเป็น v9.x หรือสูงกว่า

# 3. ตรวจสอบ SQLite
sqlite3 --version
# ควรมี SQLite installed

# 4. ตรวจสอบ Backend dependencies
cd backend-server
npm list express express-validator sqlite3 jsonwebtoken
# ตรวจสอบว่า packages ติดตั้งครบ

# 5. ตรวจสอบ Database file
ls -lh database/sqlite/wallboard.db
# ควรเห็นไฟล์ wallboard.db

# 6. ตรวจสอบ .env files
test -f backend-server/.env && echo "✅ Backend .env exists" || echo "❌ Backend .env missing"
test -f admin-panel/.env && echo "✅ Frontend .env exists" || echo "❌ Frontend .env missing"

# 7. ตรวจสอบ users table
cd database/sqlite
sqlite3 wallboard.db "SELECT COUNT(*) as user_count FROM users;"
# ควรเห็นจำนวน users

# 8. ตรวจสอบ Foreign Keys
sqlite3 wallboard.db "PRAGMA foreign_keys;"
# ควรแสดง 1 (enabled)
```

### 5.2 วิธีรันทั้งระบบ

**Terminal 1: Backend Server**
```bash
cd backend-server
npm run dev
# หรือ npm start

# ควรเห็น output:
# ✅ UserRepository connected to SQLite database
# ✅ Server running on http://localhost:3001
```

**Terminal 2: Admin Panel**
```bash
cd admin-panel
npm start

# ควรเห็น output:
# Compiled successfully!
# React app running on http://localhost:3000
```

**Terminal 3: Manual Testing (Optional)**
```bash
# ทดสอบ API ด้วย curl
curl http://localhost:3001/api/users
```

### 5.3 Testing Checklist

#### **✅ Database Testing:**
```
[ ] รัน 01-create-users-table.sql สำเร็จ
[ ] รัน 02-insert-sample-users.sql สำเร็จ
[ ] ตรวจสอบข้อมูลใน users table ด้วย SQLite
[ ] Foreign Key constraints ทำงาน
[ ] Indexes ถูกสร้างครบ
[ ] Trigger updatedAt ทำงาน
```

#### **✅ Backend API Testing:**
```
[ ] GET /api/users - แสดงรายการ users ทั้งหมด
[ ] GET /api/users/:id - แสดง user ตาม ID
[ ] POST /api/users - สร้าง user ใหม่ได้
[ ] PUT /api/users/:id - อัพเดท user ได้ (TODO นักศึกษา)
[ ] DELETE /api/users/:id - ลบ user ได้ (TODO นักศึกษา)
[ ] POST /api/auth/login - Login without password ได้
[ ] Validation ทำงานถูกต้อง
[ ] Error responses มี proper status codes
```

#### **✅ Frontend Testing:**
```
Login Page:
[ ] แสดงหน้า login ถูกต้อง
[ ] Username validation ทำงาน
[ ] Login สำเร็จด้วย Admin account (AD001, AD002)
[ ] Error message แสดงเมื่อ username ผิด
[ ] Non-admin ไม่สามารถเข้าได้
[ ] Network error handling ทำงาน

User Management Page:
[ ] แสดง header พร้อมชื่อ admin ที่ login
[ ] แสดง user table ถูกต้อง
[ ] Loading state ทำงาน
[ ] Error messages แสดงถูกต้อง
[ ] Success messages แสดงและหายใน 3 วินาที
[ ] Logout button ทำงาน

User Table:
[ ] แสดง users ทั้งหมดในตาราง
[ ] Role badges แสดงสีถูกต้อง (Agent=blue, Supervisor=orange, Admin=pink)
[ ] Status badges แสดงสีถูกต้อง (Active=green, Inactive=red)
[ ] Team name แสดงถูกต้อง
[ ] Edit button เปิด modal ได้
[ ] Delete button แสดง confirmation

Create User:
[ ] คลิก "Add New User" เปิด modal
[ ] Form แสดงถูกต้อง
[ ] Validation ทำงาน (client-side)
[ ] สร้าง user สำเร็จ
[ ] Table refresh หลังสร้าง
[ ] Success message แสดง
[ ] Duplicate username ถูกป้องกัน
[ ] Agent/Supervisor ต้องเลือก team

Edit User (TODO นักศึกษา):
[ ] คลิก Edit เปิด modal พร้อมข้อมูล
[ ] Username ถูก disabled
[ ] แก้ไขข้อมูลได้
[ ] บันทึกสำเร็จ
[ ] Table refresh หลังแก้ไข
[ ] Success message แสดง

Delete User (TODO นักศึกษา):
[ ] คลิก Delete แสดง confirmation
[ ] Confirm แล้วลบสำเร็จ
[ ] User หายจาก table
[ ] Cancel ยกเลิกได้
[ ] Success message แสดง
[ ] Soft delete (user ยังอยู่ใน DB แต่ deletedAt ถูกเซ็ต)
```

### 5.4 Postman Collection

**ไฟล์: `Task1-API-Tests.postman_collection.json` (ให้ครบ 100%)**

```json
{
  "info": {
    "name": "Task#1: User Management API",
    "description": "API tests for User Management System",
    "schema": "https://schema.getpostman.com/json/collection/v2.1.0/collection.json"
  },
  "item": [
    {
      "name": "1. Login Without Password",
      "request": {
        "method": "POST",
        "header": [
          {
            "key": "Content-Type",
            "value": "application/json"
          }
        ],
        "body": {
          "mode": "raw",
          "raw": "{\n  \"username\": \"AD001\"\n}"
        },
        "url": {
          "raw": "http://localhost:3001/api/auth/login",
          "protocol": "http",
          "host": ["localhost"],
          "port": "3001",
          "path": ["api", "auth", "login"]
        }
      }
    },
    {
      "name": "2. Get All Users",
      "request": {
        "method": "GET",
        "header": [],
        "url": {
          "raw": "http://localhost:3001/api/users",
          "protocol": "http",
          "host": ["localhost"],
          "port": "3001",
          "path": ["api", "users"]
        }
      }
    },
    {
      "name": "3. Get User by ID",
      "request": {
        "method": "GET",
        "header": [],
        "url": {
          "raw": "http://localhost:3001/api/users/1",
          "protocol": "http",
          "host": ["localhost"],
          "port": "3001",
          "path": ["api", "users", "1"]
        }
      }
    },
    {
      "name": "4. Create User - Success",
      "request": {
        "method": "POST",
        "header": [
          {
            "key": "Content-Type",
            "value": "application/json"
          }
        ],
        "body": {
          "mode": "raw",
          "raw": "{\n  \"username\": \"AG099\",\n  \"fullName\": \"Test Agent\",\n  \"role\": \"Agent\",\n  \"teamId\": 1,\n  \"status\": \"Active\"\n}"
        },
        "url": {
          "raw": "http://localhost:3001/api/users",
          "protocol": "http",
          "host": ["localhost"],
          "port": "3001",
          "path": ["api", "users"]
        }
      }
    },
    {
      "name": "5. Create User - Invalid Username",
      "request": {
        "method": "POST",
        "header": [
          {
            "key": "Content-Type",
            "value": "application/json"
          }
        ],
        "body": {
          "mode": "raw",
          "raw": "{\n  \"username\": \"INVALID\",\n  \"fullName\": \"Test User\",\n  \"role\": \"Agent\",\n  \"teamId\": 1\n}"
        },
        "url": {
          "raw": "http://localhost:3001/api/users",
          "protocol": "http",
          "host": ["localhost"],
          "port": "3001",
          "path": ["api", "users"]
        }
      }
    },
    {
      "name": "6. Create User - Missing Team",
      "request": {
        "method": "POST",
        "header": [
          {
            "key": "Content-Type",
            "value": "application/json"
          }
        ],
        "body": {
          "mode": "raw",
          "raw": "{\n  \"username\": \"AG100\",\n  \"fullName\": \"Test Agent\",\n  \"role\": \"Agent\"\n}"
        },
        "url": {
          "raw": "http://localhost:3001/api/users",
          "protocol": "http",
          "host": ["localhost"],
          "port": "3001",
          "path": ["api", "users"]
        }
      }
    },
    {
      "name": "7. Update User (TODO)",
      "request": {
        "method": "PUT",
        "header": [
          {
            "key": "Content-Type",
            "value": "application/json"
          }
        ],
        "body": {
          "mode": "raw",
          "raw": "{\n  \"fullName\": \"Updated Name\",\n  \"status\": \"Inactive\"\n}"
        },
        "url": {
          "raw": "http://localhost:3001/api/users/1",
          "protocol": "http",
          "host": ["localhost"],
          "port": "3001",
          "path": ["api", "users", "1"]
        }
      }
    },
    {
      "name": "8. Delete User (TODO)",
      "request": {
        "method": "DELETE",
        "header": [],
        "url": {
          "raw": "http://localhost:3001/api/users/1",
          "protocol": "http",
          "host": ["localhost"],
          "port": "3001",
          "path": ["api", "users", "1"]
        }
      }
    },
    {
      "name": "9. Filter Users by Role",
      "request": {
        "method": "GET",
        "header": [],
        "url": {
          "raw": "http://localhost:3001/api/users?role=Agent",
          "protocol": "http",
          "host": ["localhost"],
          "port": "3001",
          "path": ["api", "users"],
          "query": [
            {
              "key": "role",
              "value": "Agent"
            }
          ]
        }
      }
    },
    {
      "name": "10. Filter Users by Status",
      "request": {
        "method": "GET",
        "header": [],
        "url": {
          "raw": "http://localhost:3001/api/users?status=Active",
          "protocol": "http",
          "host": ["localhost"],
          "port": "3001",
          "path": ["api", "users"],
          "query": [
            {
              "key": "status",
              "value": "Active"
            }
          ]
        }
      }
    }
  ]
}
```

### 5.5 Test Scenarios

**Test Case 1: Happy Path - Create User**
```
Steps:
1. Login as AD001
2. Click "Add New User"
3. Fill form:
   - Username: AG100
   - Full Name: Test Agent 100
   - Role: Agent
   - Team: Team Alpha (id=1)
   - Status: Active
4. Click "Create User"

Expected Result:
✅ User created successfully
✅ Success message shows and disappears after 3 seconds
✅ Table refreshes automatically
✅ New user appears in table with correct data
✅ Role badge is blue (Agent)
✅ Status badge is green (Active)
```

**Test Case 2: Validation - Invalid Username**
```
Steps:
1. Try to create user with username "TEST"

Expected Result:
❌ Validation error shows
❌ Error message: "Username must be in format AGxxx, SPxxx, or ADxxx"
❌ User not created
❌ Form stays open for correction
```

**Test Case 3: Business Rule - Agent Without Team**
```
Steps:
1. Try to create Agent without selecting team

Expected Result:
❌ Validation error shows
❌ Error message: "Team ID is required for Agent and Supervisor roles"
❌ User not created
```

**Test Case 4: Network Error Handling**
```
Steps:
1. Stop backend server
2. Try to load users or create user

Expected Result:
❌ Error message: "Network error. Please check your internet connection."
❌ User-friendly error (not technical error)
```

**Test Case 5: Update User (TODO นักศึกษาทดสอบ)**
```
Steps:
1. Click Edit on existing user
2. Change Full Name to "Updated Name"
3. Click "Update User"

Expected Result:
✅ User updated successfully
✅ Table shows new name
✅ Success message shows
✅ Username still disabled (cannot change)
```

**Test Case 6: Delete User (TODO นักศึกษาทดสอบ)**
```
Steps:
1. Click Delete on user AG008
2. Confirm deletion

Expected Result:
✅ Confirmation dialog shows
✅ User deleted (soft delete)
✅ User disappears from table
✅ Success message shows
✅ Check database: user still exists with deletedAt timestamp
✅ Check database: user status changed to 'Inactive'
```

---

## 6. Troubleshooting & Tips

### 6.1 Common Issues & Solutions

#### **Issue 1: Backend ไม่เริ่มต้น**

**Symptoms:**
```
Error: Cannot find module 'express-validator'
```

**Solution:**
```bash
cd backend-server
npm install express-validator
npm run dev
```

---

#### **Issue 2: Database table ไม่มีอยู่**

**Symptoms:**
```
Error: no such table: users
```

**Solution:**
```bash
cd database/sqlite
sqlite3 wallboard.db < ../scripts/01-create-users-table.sql
sqlite3 wallboard.db < ../scripts/02-insert-sample-users.sql

# ตรวจสอบ
sqlite3 wallboard.db "SELECT * FROM users;"
```

---

#### **Issue 3: Foreign Key constraint ไม่ทำงาน**

**Symptoms:**
```
สามารถ insert user ด้วย teamId ที่ไม่มีอยู่ได้
```

**Solution:**
```bash
# ตรวจสอบว่า PRAGMA foreign_keys เปิดอยู่หรือไม่
sqlite3 wallboard.db "PRAGMA foreign_keys;"
# ควรแสดง: 1

# ถ้าแสดง 0 แสดงว่าไม่ได้เปิด
# ต้องเพิ่ม PRAGMA foreign_keys = ON; ในทุก SQL script
```

---

#### **Issue 4: CORS Error ใน Frontend**

**Symptoms:**
```
Access to fetch at 'http://localhost:3001/api/users' 
from origin 'http://localhost:3000' has been blocked by CORS policy
```

**Solution:**

แก้ไข `backend-server/server.js`:
```javascript
const cors = require('cors');

// เพิ่ม CORS middleware
app.use(cors({
  origin: 'http://localhost:3000',
  credentials: true
}));
```

---

#### **Issue 5: React ไม่อ่าน environment variables**

**Symptoms:**
```
API_BASE_URL is undefined
```

**Solution:**
```bash
# 1. ตรวจสอบว่ามีไฟล์ .env
cat admin-panel/.env

# 2. ถ้าไม่มี ให้สร้าง
echo "REACT_APP_API_URL=http://localhost:3001/api" > admin-panel/.env

# 3. IMPORTANT: ต้อง restart React app
cd admin-panel
# Stop server (Ctrl+C)
npm start
```

---

#### **Issue 6: Success message ไม่หาย**

**Symptoms:**
- Success message แสดงแล้วไม่หายเอง

**Solution:**

ตรวจสอบว่ามี useEffect สำหรับ auto-clear:
```javascript
// ใน UserManagementPage.js
useEffect(() => {
  if (successMessage) {
    const timer = setTimeout(() => {
      setSuccessMessage('');
    }, 3000);
    
    return () => clearTimeout(timer); // ⬅️ IMPORTANT: cleanup
  }
}, [successMessage]);
```

---

#### **Issue 7: Modal ไม่ปิด**

**Symptoms:**
- คลิก Save แล้ว modal ไม่หาย

**Solution:**

ตรวจสอบว่า `handleSaveUser` เรียก `setIsModalOpen(false)`:
```javascript
const handleSaveUser = async (userData) => {
  try {
    await userAPI.createUser(userData);
    setIsModalOpen(false); // ⬅️ ต้องมีบรรทัดนี้
    await loadUsers();
    setSuccessMessage('User created successfully');
  } catch (err) {
    setError(err.message);
  }
};
```

---

#### **Issue 8: Validation ไม่ทำงาน**

**Symptoms:**
- ส่ง invalid data ไปได้

**Solution:**

1. **Backend:** ตรวจสอบว่า middleware validation ถูกเรียกใช้:
```javascript
router.post('/',
  validation.validateCreateUser,      // ⬅️ ต้องมี
  validation.handleValidationErrors,  // ⬅️ ต้องมี
  userController.createUser
);
```

2. **Frontend:** ตรวจสอบว่า `validateForm()` ถูกเรียก:
```javascript
const handleSubmit = (e) => {
  e.preventDefault();
  
  if (validateForm()) {  // ⬅️ ต้องมี
    onSave(formData);
  }
};
```

---

### 6.2 Debugging Tips

#### **1. ตรวจสอบ API Response**

**เปิด Browser Developer Tools (F12):**
```
Network tab:
- ดู request/response
- ตรวจสอบ status code (200, 201, 400, 404, 500)
- ดู response body
- ตรวจสอบ request headers

Console tab:
- ดู console.log outputs
- ตรวจสอบ JavaScript errors
- ดู network errors
```

---

#### **2. ตรวจสอบ Backend Logs**

```bash
# Terminal ที่รัน backend จะแสดง logs
✅ UserRepository connected to SQLite database
POST /api/users 201 - 45ms
GET /api/users 200 - 12ms
Error in createUser: Username already exists
```

---

#### **3. ทดสอบ API ด้วย curl**

```bash
# Test GET
curl http://localhost:3001/api/users

# Test POST
curl -X POST http://localhost:3001/api/users \
  -H "Content-Type: application/json" \
  -d '{"username":"AG100","fullName":"Test","role":"Agent","teamId":1}'

# Test with verbose output
curl -v http://localhost:3001/api/users

# Test error case
curl -X POST http://localhost:3001/api/users \
  -H "Content-Type: application/json" \
  -d '{"username":"INVALID"}'
```

---

#### **4. ตรวจสอบ Database**

```bash
cd database/sqlite

# เปิด SQLite
sqlite3 wallboard.db

# Commands ใน SQLite
.tables                    # แสดง tables ทั้งหมด
.schema users             # แสดง schema ของ users table
PRAGMA foreign_keys;      # ตรวจสอบ FK status
SELECT * FROM users;      # แสดงข้อมูลทั้งหมด
SELECT * FROM users WHERE deletedAt IS NULL;  # แสดงเฉพาะ active users
SELECT * FROM users WHERE deletedAt IS NOT NULL;  # แสดง deleted users
.exit                     # ออกจาก SQLite
```

---

#### **5. Reset Database**

```bash
# ถ้าต้องการเริ่มใหม่
cd database/sqlite
rm wallboard.db

# สร้างใหม่
sqlite3 wallboard.db < ../scripts/01-create-users-table.sql
sqlite3 wallboard.db < ../scripts/02-insert-sample-users.sql

# ตรวจสอบ
sqlite3 wallboard.db "SELECT COUNT(*) FROM users;"
```

---

### 6.3 Performance & Best Practices

#### **1. Database Indexes**

```sql
-- ✅ Good: มี indexes บน frequently queried columns
CREATE INDEX idx_users_username ON users(username);
CREATE INDEX idx_users_role ON users(role);

-- Query จะเร็วขึ้นมาก
SELECT * FROM users WHERE username = 'AG001';  -- ใช้ index
SELECT * FROM users WHERE role = 'Agent';      -- ใช้ index
```

---

#### **2. API Response Optimization**

```javascript
// ✅ Good: Return เฉพาะข้อมูลที่จำเป็น
const users = await userRepository.findAll();
// Already filtered: deletedAt IS NULL
// Already joined: team names included

// ❌ Bad: Return ทุกอย่างรวม sensitive data
return users;  // Might include passwords, tokens, etc.
```

---

#### **3. Frontend State Management**

```javascript
// ✅ Good: แยก state ตามหน้าที่
const [users, setUsers] = useState([]);
const [loading, setLoading] = useState(false);
const [error, setError] = useState(null);

// ❌ Bad: รวม state ทุกอย่าง
const [state, setState] = useState({ users: [], loading: false, error: null });
```

---

### 6.4 Code Quality Checklist

```
Clean Code:
[ ] Variable names สื่อความหมาย
[ ] Functions มีขนาดเหมาะสม (< 50 lines)
[ ] Comments อธิบาย business logic
[ ] No duplicate code
[ ] Consistent formatting

Error Handling:
[ ] Try-catch ครอบทุก async operations
[ ] User-friendly error messages
[ ] Proper HTTP status codes
[ ] Network errors handled
[ ] Validation errors displayed

Security:
[ ] SQL injection prevention (parameterized queries)
[ ] Input validation (frontend + backend)
[ ] No sensitive data in logs
[ ] CORS configured properly

Testing:
[ ] All happy paths tested
[ ] Edge cases tested
[ ] Error scenarios tested
[ ] Cross-browser tested (Chrome, Firefox, Safari)
```

---

## 7. สรุปและ Next Steps

### 7.1 สิ่งที่ได้จาก Implementation Guide

```
✅ Database Setup (100%)
├── users table พร้อม Foreign Keys
├── Indexes สำหรับ performance
├── Triggers สำหรับ auto-update
└── Sample data สำหรับทดสอบ

✅ Backend Extensions (75%)
├── User Repository (85% - TODO: complete update method)
├── User Service (70% - TODO: update, delete, validations)
├── User Controller (80% - TODO: update, delete handlers)
├── Validation Middleware (100%)
├── User Routes (100%)
└── Auth Service with login without password (100%)

✅ Frontend Admin Panel (65%)
├── Login Page (100%)
├── User Management Page (65% - TODO: delete, update handlers)
├── User Table (100%)
├── User Form Modal (60% - TODO: validation logic)
├── User Action Buttons (100%)
├── Auth API Service (100%)
└── User API Service (75% - TODO: update, delete methods)

✅ Testing & Documentation (100%)
├── Postman Collection (100%)
├── Test Scenarios (100%)
├── Troubleshooting Guide (100%)
└── Environment Verification (100%)
```

---

### 7.2 งานที่นักศึกษาต้องทำเพิ่มเติม (25-30%)

#### **Backend (15%):**
```
TODO #1: userRepository.update() - 5%
├── Build dynamic UPDATE query
├── Handle multiple fields
└── Return updated user

TODO #2: userService.updateUser() - 5%
├── Validate user exists
├── Check business rules
└── Role-specific validations

TODO #3: userService.deleteUser() - 2%
├── Check user exists
└── Soft delete implementation

TODO #4: userController.updateUser() - 2%
├── Handle request
└── Return proper responses

TODO #5: userController.deleteUser() - 1%
├── Handle request
└── Return success message
```

#### **Frontend (15%):**
```
TODO #1: UserFormModal validation - 10%
├── handleChange implementation
├── validateForm implementation
└── handleSubmit implementation

TODO #2: userAPI.updateUser() - 2%
├── Send PUT request
└── Handle response

TODO #3: userAPI.deleteUser() - 1%
├── Send DELETE request
└── Handle response

TODO #4: UserManagementPage handlers - 2%
├── handleDeleteUser with confirmation
└── Update handleSaveUser for edit mode
```

---

### 7.3 Timeline Suggestions (3 วัน / 24 ชั่วโมง)

**Day 1: Setup & Backend (8 ชม.)**
```
Morning (4 ชม.):
├── 1h: อ่านเอกสาร + verify environment
├── 1h: Database setup + ทดสอบ SQL
├── 1h: ทดสอบ backend APIs ที่มีให้ (GET, POST)
└── 1h: ทำความเข้าใจ code structure

Afternoon (4 ชม.):
├── 2h: เติม TODO ใน backend (update, delete)
│       - userRepository.update()
│       - userService methods
│       - userController methods
├── 1h: ทดสอบ APIs ที่เขียนเพิ่ม
└── 1h: Debug และ fix bugs

✅ Milestone: Backend CRUD complete
```

**Day 2: Frontend (8 ชม.)**
```
Morning (4 ชม.):
├── 1h: Setup React project + environment
├── 1h: ทดสอบ login + user list
├── 1h: เติม form validation logic
│       - handleChange
│       - validateForm
│       - handleSubmit
└── 1h: ทดสอบ create user

Afternoon (4 ชม.):
├── 2h: เติม update/delete handlers
│       - userAPI.updateUser()
│       - userAPI.deleteUser()
│       - handleDeleteUser with confirmation
│       - handleSaveUser for edit mode
├── 1h: เชื่อมต่อ frontend-backend
└── 1h: ทดสอบ CRUD operations ทั้งหมด

✅ Milestone: Frontend CRUD complete
```

**Day 3: Integration, Testing & Documentation (8 ชม.)**
```
Morning (4 ชม.):
├── 1h: Integration testing ทุก features
├── 1h: Fix bugs ที่เจอ
├── 1h: Improve UI/UX (error messages, loading states)
└── 1h: Add more error handling

Afternoon (4 ชม.):
├── 1h: Complete testing checklist
├── 1h: Documentation (README, comments)
├── 1h: Git commits + Trello update
│       - Meaningful commit messages
│       - Move cards to Done
└── 1h: Final review + submission prep

✅ Milestone: Project ready for submission
```

---

### 7.4 Grading Rubric

| Criteria | Weight | Description | Points |
|----------|--------|-------------|--------|
| **Functionality** | 40% | ทุก features ทำงานถูกต้อง | |
| - Create User | 10% | Form, validation, API integration | /10 |
| - Edit User | 10% | Modal, update API, validation | /10 |
| - Delete User | 10% | Confirmation, soft delete | /10 |
| - List & Filter | 10% | Table display, no bugs | /10 |
| **Code Quality** | 30% | คุณภาพของ code | |
| - Error Handling | 10% | Try-catch, user-friendly messages | /10 |
| - Validation | 10% | Client + server validation | /10 |
| - Code Organization | 10% | Clean, readable, maintainable | /10 |
| **Git & Trello** | 20% | การใช้เครื่องมือ | |
| - Commit History | 10% | 15+ commits, meaningful messages | /10 |
| - Task Management | 10% | Trello tracking, progress updates | /10 |
| **Testing** | 10% | การทดสอบ | |
| - API Testing | 5% | Postman tests, documented results | /5 |
| - UI Testing | 5% | Manual testing, bug fixes | /5 |
| **Total** | **100%** | | **/100** |

---

### 7.5 Submission Requirements

#### **1. Git Repository Structure**

```
repository/
├── backend-server/
│   ├── (modified files only)
│   └── package.json
├── admin-panel/
│   ├── (complete React project)
│   └── package.json
├── database/
│   └── scripts/
│       ├── 01-create-users-table.sql
│       └── 02-insert-sample-users.sql
├── docs/
│   ├── README.md
│   ├── API-DOCUMENTATION.md
│   └── TEST-RESULTS.md
└── Task1-API-Tests.postman_collection.json
```

#### **2. Required Documents**

**README.md:**
```markdown
# Task#1: User Management System

## Overview
Implementation of User Management system with login without password.

## Features Implemented
- ✅ Create new users
- ✅ Edit existing users
- ✅ Delete users (soft delete)
- ✅ List users with filtering
- ✅ Login without password (Admin only)
- ✅ Form validation (client + server)

## Setup Instructions

### Prerequisites
- Node.js v18+
- SQLite3
- npm

### Installation
1. Database setup:
   ```bash
   cd database/sqlite
   sqlite3 wallboard.db < ../scripts/01-create-users-table.sql
   sqlite3 wallboard.db < ../scripts/02-insert-sample-users.sql
   ```

2. Backend:
   ```bash
   cd backend-server
   npm install
   npm run dev
   ```

3. Frontend:
   ```bash
   cd admin-panel
   npm install
   npm start
   ```

### Test Accounts
- AD001 - Admin One
- AD002 - Admin Two

## API Endpoints
- GET /api/users - Get all users
- POST /api/users - Create user
- PUT /api/users/:id - Update user
- DELETE /api/users/:id - Delete user
- POST /api/auth/login - Login

## Testing
- Run Postman collection: `Task1-API-Tests.postman_collection.json`
- See TEST-RESULTS.md for detailed test results

## Known Issues
[List any known bugs or limitations]

## Future Improvements
[Suggestions for enhancements]
```

**TEST-RESULTS.md:**
```markdown
# Test Results - Task#1

## Test Environment
- Date: [date]
- Backend: Node.js v18.x
- Frontend: React 18.x
- Database: SQLite 3.x

## Backend API Tests

### GET /api/users
- ✅ Returns all active users
- ✅ Filters by role work correctly
- ✅ Filters by status work correctly
- ✅ Response time: < 100ms

### POST /api/users
- ✅ Creates user successfully
- ✅ Validates username format
- ✅ Prevents duplicate username
- ✅ Validates required fields
- ✅ Enforces role-specific rules

### PUT /api/users/:id
- ✅ Updates user successfully
- ✅ Prevents username change
- ✅ Validates update data
- ✅ Returns 404 for non-existent user

### DELETE /api/users/:id
- ✅ Soft deletes user
- ✅ Sets deletedAt timestamp
- ✅ Changes status to Inactive
- ✅ Returns 404 for non-existent user

### POST /api/auth/login
- ✅ Login with valid admin username
- ✅ Rejects invalid username format
- ✅ Rejects inactive users
- ✅ Generates JWT token
- ✅ Updates lastLoginAt

## Frontend UI Tests

### Login Page
- ✅ Form validation works
- ✅ Login with AD001 successful
- ✅ Login with AD002 successful
- ✅ Non-admin rejected
- ✅ Error messages display correctly

### User Management Page
- ✅ Lists all users in table
- ✅ Role badges colored correctly
- ✅ Status badges colored correctly
- ✅ Loading state displays
- ✅ Error messages display
- ✅ Success messages auto-clear

### Create User
- ✅ Modal opens correctly
- ✅ Form validation works
- ✅ Creates user successfully
- ✅ Table refreshes after create
- ✅ Success message displays

### Edit User
- ✅ Modal opens with data
- ✅ Username disabled
- ✅ Updates user successfully
- ✅ Table refreshes after update
- ✅ Success message displays

### Delete User
- ✅ Confirmation dialog shows
- ✅ Deletes user successfully
- ✅ Table refreshes after delete
- ✅ Success message displays

## Edge Cases Tested
- ✅ Network errors handled
- ✅ Session expiration handled
- ✅ Duplicate username prevented
- ✅ Foreign key constraints enforced
- ✅ Form validation comprehensive

## Performance
- Average API response time: 50ms
- Page load time: < 2s
- Table render time: < 500ms

## Browser Compatibility
- ✅ Chrome 120+
- ✅ Firefox 120+
- ✅ Safari 17+
- ✅ Edge 120+

## Issues Found & Fixed
1. Issue: Foreign keys not working
   - Fix: Added PRAGMA foreign_keys = ON

2. Issue: Success message not clearing
   - Fix: Added useEffect with setTimeout

3. Issue: Network errors not user-friendly
   - Fix: Added handleAPIError helper

## Conclusion
All features working as expected. Ready for production.
```

#### **3. Trello Board Export**

```bash
# Export Trello board
# Menu → More → Print and Export → Export as JSON
# บันทึกเป็น: task1-trello-board.json
```

#### **4. Git Workflow**

```bash
# 1. Create feature branch
git checkout -b feature/task1-user-management

# 2. Make commits throughout development
git add database/scripts/01-create-users-table.sql
git commit -m "feat: add users table schema with foreign keys"

git add backend-server/repositories/userRepository.js
git commit -m "feat: add UserRepository with CRUD operations"

git add backend-server/services/userService.js
git commit -m "feat: add UserService with business logic"

git add backend-server/controllers/userController.js
git commit -m "feat: add UserController for HTTP handlers"

git add backend-server/routes/users.js
git commit -m "feat: add user management routes"

git add admin-panel/
git commit -m "feat: add admin panel React application"

git add admin-panel/src/pages/LoginPage.js
git commit -m "feat: add login page with validation"

git add admin-panel/src/components/UserTable.js
git commit -m "feat: add user table component"

git add admin-panel/src/components/UserFormModal.js
git commit -m "feat: add user form modal for create/edit"

git add .
git commit -m "feat: implement update and delete functionality"

git add .
git commit -m "test: add comprehensive test cases"

git add .
git commit -m "docs: add README and test results"

git add .
git commit -m "fix: improve error handling and validation"

git add .
git commit -m "chore: final cleanup and optimization"

# 3. Push to remote
git push origin feature/task1-user-management

# 4. Create Pull Request
# - Title: [Task#1] User Management System Implementation
# - Description: Complete implementation with tests
# - Add screenshots
```

---

### 7.6 Submission Checklist

```
Code:
├── [ ] ทุก TODO ใน code ทำเสร็จแล้ว
├── [ ] ไม่มี console.log ใน production code (ยกเว้น error logs)
├── [ ] ไม่มี commented code ที่ไม่ใช้
├── [ ] Variable names เป็นภาษาอังกฤษและสื่อความหมาย
├── [ ] Indentation ถูกต้องสม่ำเสมอ
└── [ ] No syntax errors

Functionality:
├── [ ] สามารถ login ด้วย Admin account ได้
├── [ ] สามารถ create user ได้
├── [ ] สามารถ edit user ได้
├── [ ] สามารถ delete user ได้
├── [ ] สามารถ list และ filter users ได้
├── [ ] Validation ทำงานทั้ง frontend และ backend
├── [ ] Error messages แสดงถูกต้อง
└── [ ] Success messages auto-clear

Testing:
├── [ ] ทดสอบ happy path ทุก feature
├── [ ] ทดสอบ validation errors
├── [ ] ทดสอบ API errors (404, 500)
├── [ ] ทดสอบ network errors
├── [ ] ทดสอบ edge cases
└── [ ] ทดสอบใน browser อย่างน้อย 2 ตัว

Documentation:
├── [ ] README.md complete
├── [ ] TEST-RESULTS.md complete
├── [ ] API documentation complete
├── [ ] Comments ใน code ที่ซับซ้อน
└── [ ] Known issues documented

Git:
├── [ ] มี commits อย่างน้อย 15 commits
├── [ ] Commit messages ชัดเจนและมีความหมาย
├── [ ] ทุก changes committed
├── [ ] Push ไป remote repository แล้ว
├── [ ] Pull Request สร้างแล้ว
└── [ ] Tag final version

Trello:
├── [ ] ทุก tasks moved to Done
├── [ ] Progress comments เพิ่มแล้ว
├── [ ] Screenshots attached
└── [ ] Board exported

Submission:
├── [ ] ส่ง Git repository URL
├── [ ] ส่ง Trello board link  
├── [ ] ส่ง Postman collection
├── [ ] ส่ง README documentation
└── [ ] ส่ง TEST-RESULTS document
```

---

### 7.7 Evaluation Criteria Summary

**ตัวชี้วัดความสำเร็จ:**

**🟢 Excellent (90-100%):**
- ทุก features ทำงานสมบูรณ์
- Code quality ดีมาก (clean, organized, well-documented)
- Git commits สม่ำเสมอและมีความหมาย
- Testing ครบถ้วนทุก cases
- Documentation สมบูรณ์

**🟡 Good (75-89%):**
- Features หลักทำงานได้
- Code quality ดี แต่อาจมีส่วนที่ปรับปรุงได้
- Git commits ดี แต่อาจไม่สม่ำเสมอมาก
- Testing ครอบคลุม happy paths
- Documentation ครบพอใช้งาน

**🟠 Fair (60-74%):**
- Features พื้นฐานทำงาน แต่มี bugs บ้าง
- Code quality พอใช้ แต่ต้องปรับปรุง
- Git commits มีแต่ไม่ค่อยมีความหมาย
- Testing ไม่ครบทุก cases
- Documentation ไม่สมบูรณ์

**🔴 Poor (< 60%):**
- Features ไม่ทำงานหรือมี bugs เยอะ
- Code quality ต่ำ
- Git commits น้อยหรือไม่มีความหมาย
- Testing ไม่เพียงพอ
- Documentation ขาดหาย

---

## 🎉 Final Notes

### ข้อความจากอาจารย์

นักศึกษาทุกคน,

Task นี้ออกแบบมาให้เป็นประสบการณ์การทำงานจริง โดยให้คุณได้:

1. **ทำงานกับ codebase ที่มีอยู่แล้ว** - เหมือนในโลกจริง
2. **เชื่อมต่อ frontend และ backend** - เข้าใจ full-stack development
3. **จัดการ database** - ใช้ SQLite และ foreign keys
4. **ทำงานร่วมกับทีม** - ใช้ Git และ Trello
5. **เรียนรู้จากการทำจริง** - 70% ให้มา 30% ทำเอง

**Tips สำหรับความสำเร็จ:**
- อ่านเอกสารทั้งหมดก่อนเริ่มเขียน code
- ทำทีละขั้นตอน ไม่รีบ
- ทดสอบบ่อยๆ หลังแก้ไข
- ถามเมื่อติดปัญหา (Discussion forum, Office hours)
- Commit บ่อยๆ พร้อม meaningful messages
- อย่ากลัวที่จะ debug และ learn from mistakes

**หากมีปัญหา:**
1. ตรวจสอบ Troubleshooting section ในเอกสาร
2. ดู error messages ใน console/terminal
3. ใช้ browser DevTools (F12)
4. ถามใน Discussion forum
5. มา Office Hours (วันพุธ 13:00-15:00)

**Remember:**
- 70-80% ของงานให้มาแล้ว คุณแค่เติมให้สมบูรณ์
- TODO comments บอกชัดเจนว่าต้องทำอะไร
- มีตัวอย่าง code ให้ดูทุกที่
- 3 วันเพียงพอถ้าทำตามแผน

**Good luck และสนุกกับการเขียน code! 🚀**

---

**หากมีคำถาม:**
- 📧 Email: thanit@rmutl.ac.th
- 💬 LINE Group: ENGSE206-2025
- 🏢 Office Hours: วันศุกร์ 09:00-16:00 น.
- 💻 GitHub Discussions: [link]

---

**Document Version:** 1.2 (Updated)  
**Last Updated:** October 2025  
**Status:** Ready for Student Use ✅

**Changelog v1.2:**
- 🔧 Fixed teams and users tables

---

**End of Document** 🎓