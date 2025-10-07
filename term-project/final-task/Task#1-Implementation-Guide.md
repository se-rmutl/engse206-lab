# 📄 Task#1: User Management System - Implementation Guide

**Document ID:** TASK1-IMPL-GUIDE-001  
**Version:** 1.0  
**Created:** October 2025  
**Course:** ENGSE206 - Software Requirements Specification and Design  
**สำหรับ:** กลุ่มเลขคี่ (Odd Groups)  
**ระยะเวลา:** 3 วัน  
**Code Coverage:** 70-80% (นักศึกษาเติม 20-30%)

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
   ├── Agents table
   └── Teams table

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
   ├── Users table (ใน SQLite)
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
    │   └── wallboard.db         # แก้ไข: เพิ่ม Users table
    └── scripts/
        ├── 01-create-users-table.sql  # 🆕 SQL script
        └── 02-insert-sample-users.sql # 🆕 SQL script
```

---

## 2. ส่วนที่ 1: Database Setup

### 2.1 สร้าง Users Table (ให้ครบ 100%)

**ไฟล์: `database/scripts/01-create-users-table.sql`**

```sql
-- ========================================
-- Task#1: User Management - Users Table
-- ========================================

-- ลบตารางเดิมถ้ามี (สำหรับ development)
DROP TABLE IF EXISTS Users;

-- สร้างตาราง Users
CREATE TABLE Users (
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
    FOREIGN KEY (teamId) REFERENCES Teams(id)
);

-- สร้าง indexes เพื่อ performance
CREATE INDEX idx_users_username ON Users(username);
CREATE INDEX idx_users_role ON Users(role);
CREATE INDEX idx_users_status ON Users(status);
CREATE INDEX idx_users_teamId ON Users(teamId);
CREATE INDEX idx_users_deletedAt ON Users(deletedAt);

-- สร้าง trigger สำหรับ updatedAt
CREATE TRIGGER update_users_timestamp 
AFTER UPDATE ON Users
BEGIN
    UPDATE Users SET updatedAt = CURRENT_TIMESTAMP WHERE id = NEW.id;
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
-- Task#1: Sample Users Data
-- ========================================

-- ล้างข้อมูลเดิม (ถ้ามี)
DELETE FROM Users;

-- Insert Admin users
INSERT INTO Users (username, fullName, role, teamId, status) VALUES
('AD001', 'Admin One', 'Admin', NULL, 'Active'),
('AD002', 'Admin Two', 'Admin', NULL, 'Active');

-- Insert Supervisor users (assuming Teams with id 1,2,3 exist)
INSERT INTO Users (username, fullName, role, teamId, status) VALUES
('SP001', 'Supervisor Alpha', 'Supervisor', 1, 'Active'),
('SP002', 'Supervisor Beta', 'Supervisor', 2, 'Active'),
('SP003', 'Supervisor Gamma', 'Supervisor', 3, 'Active');

-- Insert Agent users
INSERT INTO Users (username, fullName, role, teamId, status) VALUES
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
FROM Users
ORDER BY role, username;
```

**วิธีรัน:**
```bash
sqlite3 wallboard.db < ../scripts/02-insert-sample-users.sql
```

### 2.3 ทดสอบ Database

**ไฟล์: `database/scripts/03-test-users-queries.sql`**

```sql
-- Test queries for Users table

-- 1. Get all active users
SELECT * FROM Users WHERE deletedAt IS NULL;

-- 2. Get users by role
SELECT * FROM Users WHERE role = 'Agent' AND deletedAt IS NULL;

-- 3. Get user with team info
SELECT 
    u.id,
    u.username,
    u.fullName,
    u.role,
    t.name as teamName,
    u.status
FROM Users u
LEFT JOIN Teams t ON u.teamId = t.id
WHERE u.deletedAt IS NULL;

-- 4. Count users by role
SELECT role, COUNT(*) as count 
FROM Users 
WHERE deletedAt IS NULL 
GROUP BY role;

-- 5. Find user by username
SELECT * FROM Users 
WHERE username = 'AG001' AND deletedAt IS NULL;
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

**ไฟล์ใหม่: `backend-server/repositories/userRepository.js` (ให้ 90%)**

```javascript
// repositories/userRepository.js
const sqlite3 = require('sqlite3').verbose();
const path = require('path');

// Database path (ใช้ database เดิม)
const dbPath = path.join(__dirname, '../../database/sqlite/wallboard.db');

/**
 * User Repository - Data Access Layer
 * ให้ 90% - นักศึกษาเพิ่ม update() method
 */
class UserRepository {
  constructor() {
    this.db = new sqlite3.Database(dbPath, (err) => {
      if (err) {
        console.error('Error connecting to database:', err);
      } else {
        console.log('✅ UserRepository connected to SQLite database');
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
          t.name as teamName,
          u.status,
          u.createdAt,
          u.updatedAt,
          u.lastLoginAt
        FROM Users u
        LEFT JOIN Teams t ON u.teamId = t.id
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
          t.name as teamName,
          u.status,
          u.createdAt,
          u.updatedAt,
          u.lastLoginAt
        FROM Users u
        LEFT JOIN Teams t ON u.teamId = t.id
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
          t.name as teamName,
          u.status,
          u.createdAt,
          u.updatedAt,
          u.lastLoginAt
        FROM Users u
        LEFT JOIN Teams t ON u.teamId = t.id
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
        INSERT INTO Users (username, fullName, role, teamId, status)
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
   * TODO: นักศึกษาเขียน implementation (20%)
   */
  async update(userId, userData) {
    return new Promise((resolve, reject) => {
      // TODO: Build dynamic UPDATE query
      // Hint: UPDATE Users SET fullName = ?, role = ?, teamId = ?, status = ?, updatedAt = CURRENT_TIMESTAMP
      // Hint: WHERE id = ? AND deletedAt IS NULL
      
      // Example structure:
      let query = 'UPDATE Users SET updatedAt = CURRENT_TIMESTAMP';
      const params = [];
      
      if (userData.fullName !== undefined) {
        query += ', fullName = ?';
        params.push(userData.fullName);
      }
      
      // TODO: Add other fields (role, teamId, status)
      
      query += ' WHERE id = ? AND deletedAt IS NULL';
      params.push(userId);
      
      this.db.run(query, params, function(err) {
        if (err) {
          reject(err);
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
        UPDATE Users 
        SET status = 'Inactive', 
            deletedAt = CURRENT_TIMESTAMP,
            updatedAt = CURRENT_TIMESTAMP
        WHERE id = ? AND deletedAt IS NULL
      `;
      
      this.db.run(query, [userId], function(err) {
        if (err) {
          reject(err);
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
        UPDATE Users 
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
        FROM Users 
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
 * ให้ 70% - นักศึกษาเพิ่ม validation และ business rules
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
      // TODO: นักศึกษาเพิ่ม validations (30%)
      // 1. Validate username format (AGxxx, SPxxx, ADxxx)
      const usernameRegex = /^(AG|SP|AD)(00[1-9]|0[1-9]\d|[1-9]\d{2})$/;
      if (!usernameRegex.test(userData.username)) {
        throw new Error('Invalid username format. Use AGxxx, SPxxx, or ADxxx');
      }

      // 2. Check if username already exists
      const exists = await userRepository.usernameExists(userData.username);
      if (exists) {
        throw new Error('Username already exists');
      }

      // TODO: 3. Validate role-specific rules
      // - ถ้า role = 'Agent' หรือ 'Supervisor' ต้องมี teamId
      // - ถ้า role = 'Admin' ไม่ต้องมี teamId
      
      // 4. Create user
      const newUser = await userRepository.create(userData);
      
      return newUser;
    } catch (error) {
      console.error('Error in createUser service:', error);
      throw error;
    }
  },

  /**
   * Update existing user
   * TODO: นักศึกษาเขียน implementation (30%)
   */
  async updateUser(userId, userData) {
    try {
      // TODO: 1. ตรวจสอบว่า user มีอยู่จริง
      const existingUser = await userRepository.findById(userId);
      if (!existingUser) {
        throw new Error('User not found');
      }

      // TODO: 2. ตรวจสอบว่าไม่มีการเปลี่ยน username
      if (userData.username && userData.username !== existingUser.username) {
        throw new Error('Username cannot be changed');
      }

      // TODO: 3. Validate updated data
      // TODO: 4. เรียก userRepository.update()
      // TODO: 5. Return updated user
      
      throw new Error('Not implemented - TODO by student');
    } catch (error) {
      console.error('Error in updateUser service:', error);
      throw error;
    }
  },

  /**
   * Delete user (soft delete)
   * TODO: นักศึกษาเขียน implementation (30%)
   */
  async deleteUser(userId) {
    try {
      // TODO: 1. ตรวจสอบว่า user มีอยู่จริง
      // TODO: 2. ตรวจสอบว่าไม่ใช่ current user (optional)
      // TODO: 3. Soft delete: เรียก userRepository.softDelete()
      
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
 * ให้ 80% - นักศึกษาเพิ่ม updateUser และ deleteUser
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
      
      // Handle specific errors
      const statusCode = error.message.includes('already exists') ? 409 : 
                        error.message.includes('Invalid') ? 400 : 500;
      
      res.status(statusCode).json({
        success: false,
        message: error.message
      });
    }
  },

  /**
   * PUT /api/users/:id
   * Update existing user
   * TODO: นักศึกษาเขียน implementation (20%)
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
      res.status(500).json({
        success: false,
        message: 'Failed to update user',
        error: error.message
      });
    }
  },

  /**
   * DELETE /api/users/:id
   * Delete user (soft delete)
   * TODO: นักศึกษาเขียน implementation (20%)
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
      res.status(500).json({
        success: false,
        message: 'Failed to delete user',
        error: error.message
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

### 3.8 Update Server.js

**แก้ไขไฟล์: `backend-server/server.js`**

เพิ่มบรรทัดเหล่านี้ในส่วน routes:

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

### 3.9 ทดสอบ Backend APIs

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
  -d '{"username": "AG001"}'
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

### 4.3 Project Structure

```
admin-panel/
├── public/
│   └── index.html
├── src/
│   ├── pages/
│   │   ├── LoginPage.js
│   │   └── UserManagementPage.js
│   ├── components/
│   │   ├── UserTable.js
│   │   ├── UserFormModal.js
│   │   └── UserActionButtons.js
│   ├── services/
│   │   ├── authAPI.js
│   │   └── userAPI.js
│   ├── styles/
│   │   ├── LoginPage.css
│   │   ├── UserManagementPage.css
│   │   ├── UserTable.css
│   │   └── UserFormModal.css
│   ├── App.js
│   ├── App.css
│   └── index.js
├── package.json
└── .env
```

### 4.4 API Services

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

**ไฟล์: `src/services/userAPI.js` (ให้ 80%)**

```javascript
// services/userAPI.js
const API_BASE_URL = process.env.REACT_APP_API_URL || 'http://localhost:3001/api';

/**
 * User API Service
 * ให้ 80% - นักศึกษาเพิ่ม updateUser และ deleteUser
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

      if (response.status === 401) {
        localStorage.removeItem('token');
        window.location.href = '/login';
        throw new Error('Session expired. Please login again.');
      }

      if (!response.ok) {
        throw new Error(`HTTP error! status: ${response.status}`);
      }

      const data = await response.json();
      return data.data; // Return the users array
    } catch (error) {
      console.error('Error fetching users:', error);
      throw error;
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
        throw new Error(`HTTP error! status: ${response.status}`);
      }

      const data = await response.json();
      return data.data;
    } catch (error) {
      console.error('Error fetching user:', error);
      throw error;
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
      throw error;
    }
  },

  /**
   * Update user
   * TODO: นักศึกษาเขียน implementation (20%)
   */
  updateUser: async (userId, userData) => {
    try {
      // TODO: ส่ง PUT request ไปที่ /api/users/:userId
      // TODO: ส่ง userData ใน body
      // TODO: ใส่ Authorization header
      // TODO: Handle response และ errors
      
      throw new Error('Not implemented - TODO by student');
    } catch (error) {
      console.error('Error updating user:', error);
      throw error;
    }
  },

  /**
   * Delete user
   * TODO: นักศึกษาเขียน implementation (20%)
   */
  deleteUser: async (userId) => {
    try {
      // TODO: ส่ง DELETE request ไปที่ /api/users/:userId
      // TODO: ใส่ Authorization header
      // TODO: Handle response
      
      throw new Error('Not implemented - TODO by student');
    } catch (error) {
      console.error('Error deleting user:', error);
      throw error;
    }
  }
};
```

### 4.5 Login Page

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

### 4.6 User Management Page

**ไฟล์: `src/pages/UserManagementPage.js` (ให้ 70%)**

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

  // TODO: นักศึกษาเพิ่ม useEffect สำหรับ clear success message หลัง 3 วินาที

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

  // TODO: นักศึกษาเขียน handleDeleteUser function
  const handleDeleteUser = async (userId) => {
    // TODO: แสดง confirmation dialog
    // TODO: เรียก userAPI.deleteUser(userId)
    // TODO: refresh user list
    // TODO: แสดง success message
  };

  const handleSaveUser = async (userData) => {
    try {
      if (selectedUser) {
        // Edit mode
        // TODO: เรียก userAPI.updateUser(selectedUser.id, userData)
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

**CSS จาก C3 Design document ที่ให้ไว้แล้ว - copy มาใช้เลย**

### 4.7 User Table Component

**Copy จาก C3 Design document - ให้ครบ 100% แล้ว**

### 4.8 User Form Modal Component

**Copy จาก C3 Design document - ให้ HTML/CSS ครบ 100% แล้ว**

**นักศึกษาต้องเพิ่ม:**
- `handleChange` function
- `validateForm` function
- `handleSubmit` function

### 4.9 User Action Buttons Component

**Copy จาก C3 Design document - ให้ครบ 100% แล้ว**

### 4.10 Main App Component

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
}
```

---

## 5. ส่วนที่ 4: Integration & Testing

### 5.1 วิธีรันทั้งระบบ

**Terminal 1: Backend Server**
```bash
cd backend-server
npm run dev
# Server running on http://localhost:3001
```

**Terminal 2: Admin Panel**
```bash
cd admin-panel
npm start
# React app running on http://localhost:3000
```

### 5.2 Testing Checklist

#### **Backend Testing:**
```
✅ Database Setup
├── [ ] รัน 01-create-users-table.sql สำเร็จ
├── [ ] รัน 02-insert-sample-users.sql สำเร็จ
└── [ ] ตรวจสอบข้อมูลใน Users table ด้วย SQLite

✅ API Endpoints
├── [ ] GET /api/users - แสดงรายการ users ทั้งหมด
├── [ ] GET /api/users/:id - แสดง user ตาม ID
├── [ ] POST /api/users - สร้าง user ใหม่ได้
├── [ ] PUT /api/users/:id - อัพเดท user ได้ (TODO นักศึกษา)
├── [ ] DELETE /api/users/:id - ลบ user ได้ (TODO นักศึกษา)
└── [ ] POST /api/auth/login - Login without password ได้

✅ Validation
├── [ ] Username format validation ทำงาน
├── [ ] Required fields validation ทำงาน
├── [ ] Role-specific validation ทำงาน (Agent/Supervisor ต้องมี teamId)
└── [ ] Duplicate username ตรวจสอบได้

✅ Business Logic
├── [ ] Soft delete ทำงาน (set deletedAt)
├── [ ] Username ไม่สามารถเปลี่ยนได้
├── [ ] lastLoginAt อัพเดทเมื่อ login
└── [ ] Active users only สามารถ login ได้
```

#### **Frontend Testing:**
```
✅ Login Page
├── [ ] แสดงหน้า login ถูกต้อง
├── [ ] Username validation ทำงาน
├── [ ] Login สำเร็จด้วย Admin account
├── [ ] Error message แสดงเมื่อ login ล้มเหลว
└── [ ] Non-admin ไม่สามารถเข้าได้

✅ User Management Page
├── [ ] แสดง header พร้อมชื่อ admin ที่ login
├── [ ] แสดง user table ถูกต้อง
├── [ ] Loading state ทำงาน
├── [ ] Error messages แสดงถูกต้อง
└── [ ] Logout button ทำงาน

✅ User Table
├── [ ] แสดง users ทั้งหมดในตาราง
├── [ ] Role badges แสดงสีถูกต้อง
├── [ ] Status badges แสดงสีถูกต้อง
├── [ ] Team name แสดงถูกต้อง
├── [ ] Edit button เปิด modal ได้
└── [ ] Delete button แสดง confirmation

✅ Create User
├── [ ] คลิก "Add New User" เปิด modal
├── [ ] Form แสดงถูกต้อง
├── [ ] Validation ทำงาน (client-side)
├── [ ] สร้าง user สำเร็จ
├── [ ] Table refresh หลังสร้าง
└── [ ] Success message แสดง

✅ Edit User (TODO นักศึกษา)
├── [ ] คลิก Edit เปิด modal พร้อมข้อมูล
├── [ ] Username ถูก disabled
├── [ ] แก้ไขข้อมูลได้
├── [ ] บันทึกสำเร็จ
├── [ ] Table refresh หลังแก้ไข
└── [ ] Success message แสดง

✅ Delete User (TODO นักศึกษา)
├── [ ] คลิก Delete แสดง confirmation
├── [ ] Confirm แล้วลบสำเร็จ
├── [ ] User หายจาก table
├── [ ] Cancel ยกเลิกได้
└── [ ] Success message แสดง
```

### 5.3 Postman Collection

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
      "name": "4. Create User",
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
      "name": "5. Update User (TODO)",
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
      "name": "6. Delete User (TODO)",
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
      "name": "7. Filter Users by Role",
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
      "name": "8. Filter Users by Status",
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
    },
    {
      "name": "9. Validation Test - Invalid Username",
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
      "name": "10. Validation Test - Missing Required Fields",
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
          "raw": "{\n  \"username\": \"AG100\"\n}"
        },
        "url": {
          "raw": "http://localhost:3001/api/users",
          "protocol": "http",
          "host": ["localhost"],
          "port": "3001",
          "path": ["api", "users"]
        }
      }
    }
  ]
}
```

### 5.4 Test Scenarios

**Test Case 1: Happy Path - Create User**
```
Steps:
1. Login as AD001
2. Click "Add New User"
3. Fill form:
   - Username: AG100
   - Full Name: Test Agent 100
   - Role: Agent
   - Team: Team Alpha
   - Status: Active
4. Click "Create User"

Expected Result:
✅ User created successfully
✅ Success message shows
✅ Table refreshes
✅ New user appears in table
```

**Test Case 2: Validation - Invalid Username**
```
Steps:
1. Try to create user with username "TEST"

Expected Result:
❌ Validation error shows
❌ Error message: "Username must be in format AGxxx, SPxxx, or ADxxx"
❌ User not created
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

**Test Case 4: Update User (TODO นักศึกษาทดสอบ)**
```
Steps:
1. Click Edit on existing user
2. Change Full Name
3. Click "Update User"

Expected Result:
✅ User updated successfully
✅ Table shows new name
✅ Success message shows
```

**Test Case 5: Delete User (TODO นักศึกษาทดสอบ)**
```
Steps:
1. Click Delete on user
2. Confirm deletion

Expected Result:
✅ User deleted (soft delete)
✅ User disappears from table
✅ Success message shows
✅ User still exists in database with deletedAt timestamp
```

---

## 6. Troubleshooting & Tips

### 6.1 Common Issues

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
Error: no such table: Users
```

**Solution:**
```bash
cd database/sqlite
sqlite3 wallboard.db < ../scripts/01-create-users-table.sql
sqlite3 wallboard.db < ../scripts/02-insert-sample-users.sql

# ตรวจสอบ
sqlite3 wallboard.db "SELECT * FROM Users;"
```

---

#### **Issue 3: CORS Error ใน Frontend**

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

#### **Issue 4: React ไม่อ่าน environment variables**

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

# 3. Restart React app
cd admin-panel
npm start
```

---

#### **Issue 5: Modal ไม่ปิด**

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
  } catch (err) {
    setError(err.message);
  }
};
```

---

#### **Issue 6: Validation ไม่ทำงาน**

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
```javascript
// Network tab
- ดู request/response
- ตรวจสอบ status code
- ดู error messages

// Console tab
- ดู console.log outputs
- ตรวจสอบ JavaScript errors
```

---

#### **2. ตรวจสอบ Backend Logs**

```bash
# Terminal ที่รัน backend จะแสดง logs
✅ UserRepository connected to SQLite database
POST /api/users 201 - 45ms
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
```

---

#### **4. ตรวจสอบ Database**

```bash
cd database/sqlite

# เปิด SQLite
sqlite3 wallboard.db

# Commands
.tables                    # แสดง tables ทั้งหมด
.schema Users             # แสดง schema ของ Users table
SELECT * FROM Users;      # แสดงข้อมูลทั้งหมด
SELECT * FROM Users WHERE deletedAt IS NULL;  # แสดงเฉพาะ active users
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
```

---

### 6.3 Code Quality Tips

#### **1. Clean Code Practices**

```javascript
// ✅ Good: Descriptive variable names
const activeUsers = users.filter(u => u.status === 'Active');

// ❌ Bad: Unclear variable names
const x = users.filter(u => u.s === 'Active');

// ✅ Good: Extract complex logic to functions
const isValidUsername = (username) => {
  return /^(AG|SP|AD)\d{3}$/.test(username);
};

// ❌ Bad: Complex logic inline
if (/^(AG|SP|AD)\d{3}$/.test(formData.username)) { ... }
```

---

#### **2. Error Handling**

```javascript
// ✅ Good: Proper error handling
try {
  const user = await userAPI.createUser(userData);
  console.log('User created:', user);
} catch (error) {
  console.error('Failed to create user:', error.message);
  setError(error.message);
}

// ❌ Bad: Silent errors
try {
  await userAPI.createUser(userData);
} catch (error) {
  // Do nothing
}
```

---

#### **3. State Management**

```javascript
// ✅ Good: Separate state for different purposes
const [users, setUsers] = useState([]);
const [loading, setLoading] = useState(false);
const [error, setError] = useState(null);

// ❌ Bad: Mixed state
const [state, setState] = useState({
  users: [],
  loading: false,
  error: null
});
```

---

### 6.4 Performance Tips

#### **1. Avoid Unnecessary Re-renders**

```javascript
// ✅ Good: Memoize callbacks
const handleEdit = React.useCallback((user) => {
  setSelectedUser(user);
  setIsModalOpen(true);
}, []);

// ❌ Bad: Create new function every render
const handleEdit = (user) => {
  setSelectedUser(user);
  setIsModalOpen(true);
};
```

---

#### **2. Optimize Database Queries**

```sql
-- ✅ Good: Use indexes
CREATE INDEX idx_users_username ON Users(username);
SELECT * FROM Users WHERE username = 'AG001';

-- ❌ Bad: No index on frequently queried columns
SELECT * FROM Users WHERE username = 'AG001';  -- Slow without index
```

---

### 6.5 Git Best Practices

#### **Commit Message Format**

```bash
# Feature
git commit -m "feat: add user creation form with validation"

# Bug fix
git commit -m "fix: resolve duplicate username error"

# Refactor
git commit -m "refactor: extract validation logic to separate function"

# Documentation
git commit -m "docs: update API documentation"

# Style
git commit -m "style: format code and fix indentation"
```

---

#### **Git Workflow**

```bash
# 1. Create feature branch
git checkout -b feature/task1-user-management

# 2. Make changes and commit regularly
git add .
git commit -m "feat: add user repository"

git add .
git commit -m "feat: add user service with validation"

# 3. Push to remote
git push origin feature/task1-user-management

# 4. Create Pull Request
# Go to GitHub/GitLab and create PR

# 5. After review and approval, merge
git checkout main
git pull origin main
git merge feature/task1-user-management
```

---

### 6.6 Quick Reference

#### **File Locations**

```
Backend Files (เพิ่มใหม่):
├── repositories/userRepository.js
├── services/userService.js
├── controllers/userController.js
├── routes/users.js
└── middleware/validation.js

Frontend Files (ทั้งหมดใหม่):
├── src/pages/LoginPage.js
├── src/pages/UserManagementPage.js
├── src/components/UserTable.js
├── src/components/UserFormModal.js
├── src/components/UserActionButtons.js
├── src/services/authAPI.js
├── src/services/userAPI.js
└── src/styles/*.css

Database Files (ใหม่):
├── database/scripts/01-create-users-table.sql
├── database/scripts/02-insert-sample-users.sql
└── database/scripts/03-test-users-queries.sql
```

---

#### **Important URLs**

```
Backend API:     http://localhost:3001/api
Frontend App:    http://localhost:3000

API Endpoints:
GET    /api/users              - Get all users
GET    /api/users/:id          - Get user by ID
POST   /api/users              - Create user
PUT    /api/users/:id          - Update user
DELETE /api/users/:id          - Delete user
POST   /api/auth/login         - Login without password
```

---

#### **Test Accounts**

```
Admins:
- AD001: Admin One
- AD002: Admin Two

Supervisors:
- SP001: Supervisor Alpha (Team 1)
- SP002: Supervisor Beta (Team 2)
- SP003: Supervisor Gamma (Team 3)

Agents:
- AG001-AG003: Team Alpha
- AG004-AG005: Team Beta
- AG006-AG008: Team Gamma
```

---

## 7. สรุปและ Next Steps

### 7.1 สิ่งที่ได้จาก Implementation Guide นี้

```
✅ Database Setup (100%)
├── Users table พร้อม indexes
├── Sample data สำหรับทดสอบ
└── Test queries

✅ Backend Extensions (70-80%)
├── User Repository (90% - TODO: update method)
├── User Service (70% - TODO: update, delete methods)
├── User Controller (80% - TODO: update, delete methods)
├── Validation Middleware (100%)
├── User Routes (100%)
└── Auth Service with login without password (100%)

✅ Frontend Admin Panel (70-80%)
├── Login Page (100%)
├── User Management Page (70% - TODO: delete, edit handlers)
├── User Table (100%)
├── User Form Modal (HTML/CSS 100%, Logic 70%)
├── User Action Buttons (100%)
├── Auth API Service (100%)
└── User API Service (80% - TODO: update, delete)
```

---

### 7.2 งานที่นักศึกษาต้องทำเพิ่มเติม (20-30%)

#### **Backend (20%):**
```
TODO #1: userRepository.update()
- Build dynamic UPDATE query
- Handle multiple fields
- Return updated user

TODO #2: userService.updateUser()
- Validate user exists
- Check business rules
- Call repository

TODO #3: userService.deleteUser()
- Validate user exists
- Soft delete implementation
- Handle constraints

TODO #4: userController.updateUser()
- Handle request
- Call service
- Return response

TODO #5: userController.deleteUser()
- Handle request
- Call service
- Return response
```

---

#### **Frontend (20-30%):**
```
TODO #1: UserFormModal - Form Logic
- handleChange implementation
- validateForm implementation
- handleSubmit implementation

TODO #2: UserManagementPage - Delete Handler
- Show confirmation dialog
- Call deleteUser API
- Refresh list
- Show success message

TODO #3: UserManagementPage - Edit Handler
- Open modal with user data
- Handle save
- Refresh list

TODO #4: userAPI.updateUser()
- Send PUT request
- Handle response
- Error handling

TODO #5: userAPI.deleteUser()
- Send DELETE request
- Handle response
- Error handling
```

---

### 7.3 การส่งงาน

#### **Git Repository:**
```bash
# 1. สร้าง branch ใหม่
git checkout -b feature/task1-user-management

# 2. Commit changes
git add .
git commit -m "feat: complete Task#1 User Management System"

# 3. Push to remote
git push origin feature/task1-user-management

# 4. Create Pull Request
# รอ review จากอาจารย์
```

---

#### **Trello Board:**
```
📋 TODO → 🔄 In Progress → ✅ Testing → 🎉 Done

Cards to create:
├── Backend: User Repository
├── Backend: User Service
├── Backend: User Controller
├── Backend: Routes Setup
├── Frontend: Login Page
├── Frontend: User Management Page
├── Frontend: User Form Modal
├── Frontend: API Services
├── Database: Setup Tables
├── Testing: API Endpoints
└── Testing: UI Workflows
```

---

#### **Documentation:**
```
Required Documents:
├── README.md (setup instructions)
├── API-Documentation.md (endpoints list)
├── TEST-RESULTS.md (test cases results)
└── KNOWN-ISSUES.md (bugs found)
```

---

### 7.4 Grading Rubric

| Criteria | Weight | Description |
|----------|--------|-------------|
| **Functionality** | 40% | ทุก features ทำงานถูกต้อง |
| - Create User | 10% | สร้าง user ได้สมบูรณ์ |
| - Edit User | 10% | แก้ไข user ได้ถูกต้อง |
| - Delete User | 10% | ลบ user ได้ (soft delete) |
| - List & Filter | 10% | แสดงและกรองข้อมูลได้ |
| **Code Quality** | 30% | คุณภาพของ code |
| - Error Handling | 10% | จัดการ errors ครบถ้วน |
| - Validation | 10% | Validation ทั้งสองฝั่ง |
| - Code Organization | 10% | Code เป็นระเบียบ |
| **Git & Trello** | 20% | การใช้เครื่องมือ |
| - Commit History | 10% | Commits สม่ำเสมอ |
| - Task Management | 10% | Trello tracking ดี |
| **Testing** | 10% | การทดสอบ |
| - API Testing | 5% | ทดสอบ APIs ครบ |
| - UI Testing | 5% | ทดสอบ UI ครบ |

---

### 7.5 เวลาที่แนะนำ (3 วัน)

**Day 1: Setup & Backend (8 ชม.)**
```
Morning (4 ชม.):
├── 1h: อ่านเอกสาร + setup environment
├── 1h: Database setup + sample data
├── 1h: ทดสอบ backend APIs ที่มีให้
└── 1h: ทำความเข้าใจ code structure

Afternoon (4 ชม.):
├── 2h: เติม TODO ใน backend (update, delete)
├── 1h: ทดสอบ APIs ที่เขียนเอง
└── 1h: Debug และ fix bugs
```

**Day 2: Frontend (8 ชม.)**
```
Morning (4 ชม.):
├── 1h: Setup React project
├── 1h: ทำความเข้าใจ components
├── 1h: เติม form validation logic
└── 1h: ทดสอบ login + user list

Afternoon (4 ชม.):
├── 2h: เติม create/edit/delete handlers
├── 1h: เชื่อมต่อ frontend-backend
└── 1h: ทดสอบ CRUD operations
```

**Day 3: Integration & Testing (8 ชม.)**
```
Morning (4 ชม.):
├── 1h: Integration testing
├── 1h: Fix bugs
├── 1h: Improve UI/UX
└── 1h: Add error handling

Afternoon (4 ชม.):
├── 1h: Complete testing
├── 1h: Documentation
├── 1h: Git commits + Trello update
└── 1h: Final review + submission
```

---

### 7.6 Resources

**Documentation:**
- Task#1-C3-User-Management-Design.md (Design document)
- 6.6.2-Backend-Server-Code-Guide.md (Backend reference)
- React Documentation: https://react.dev

**Tools:**
- Postman: API testing
- SQLite Browser: Database viewer
- VS Code: Code editor
- Git: Version control

**Help:**
- GitHub Discussions
- Office Hours: วันพุธ 13:00-15:00
- LINE Group: ENGSE206-2025

---

## 🎉 สรุป

เอกสารนี้ให้ **code สำเร็จ 70-80%** พร้อม:

✅ Database scripts ที่รันได้เลย
✅ Backend code ที่ทำงานได้ส่วนใหญ่
✅ Frontend components พร้อม HTML/CSS
✅ API services structure
✅ Testing tools และ examples
✅ Troubleshooting guide

นักศึกษาต้อง**เติมเฉพาะ logic 20-30%** ที่มี TODO comments บอกไว้ชัดเจน

**Good luck with your implementation! 🚀**

---

**Document End**