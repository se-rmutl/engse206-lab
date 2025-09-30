# Production Build Guide (สำหรับนักศึกษา)

## 1. ภาพรวมการ Build Production

การสอนให้นักศึกษาลอง build production เป็นความคิดที่ดี เพราะ:

**ข้อดี:**
- เข้าใจ process ตั้งแต่ development ถึง production
- ได้ลองใช้ electron-builder
- เห็นความแตกต่างระหว่าง dev และ prod mode
- ได้ installer จริงที่ใช้งานได้

**ข้อควรระวัง:**
- Build ใช้เวลานาน (5-15 นาที/platform)
- ใช้ RAM/CPU สูง (อาจค้างถ้าเครื่องแรงไม่พอ)
- Build cross-platform ต้องมี tools เฉพาะ
- File ขนาดใหญ่ (100-200 MB)

**คำแนะนำ:**
✅ ควรทำ: Build สำหรับ OS ของตัวเอง (Windows/Mac/Linux)
⚠️ ระวัง: Cross-platform build ซับซ้อนกว่า

---

## 2. Production Build - Step by Step

### Step 1: เตรียมโปรเจคสำหรับ Production

```bash
# 1. Clean install dependencies 
rm -rf node_modules package-lock.json
npm install

# 2. backup .env file to .env.dev
mv .env .env.dev

# 3. สร้าง production .env
cat > .env << EOF
REACT_APP_API_URL=http://localhost:3001/api
REACT_APP_SOCKET_URL=http://localhost:3001
NODE_ENV=production
ELECTRON_IS_DEV=false
EOF

# 4. ตรวจสอบ package.json version
# เปลี่ยนเป็นเวอร์ชันที่ต้องการ เช่น "3.2.0"
```

### Step 2: Build React Application

```bash
# Build React app เป็น static files
npm run build

# ผลลัพธ์: โฟลเดอร์ build/ ที่มี HTML, CSS, JS
# ใช้เวลา: 1-3 นาที

# ตรวจสอบ build สำเร็จ
ls -la build/
# ควรเห็น: index.html, static/, assets/
```

### Step 3: Test Production Build (Local)

```bash
# ทดสอบ production build ก่อน package
npm run electron

# ตรวจสอบ:
# - App เปิดได้
# - ไม่มี DevTools
# - โหลด static files จาก build/
# - ทำงานปกติ
```

---

## 3. Build สำหรับแต่ละ OS

### 🪟 Windows Build (ทำบน Windows)

```bash
# Build installer สำหรับ Windows
npm run dist:win

# Output:
# dist/
#   └── Agent Wallboard Setup 3.2.0.exe  (NSIS Installer)

# ขนาดไฟล์: ~150-200 MB
# เวลา: 5-10 นาที
```

**Features ที่ได้:**
- `.exe` installer แบบ NSIS
- Auto-update support (ถ้าตั้งค่า)
- Desktop shortcut
- Start menu entry
- Uninstaller

**การติดตั้ง:**
```
1. Double-click .exe file
2. เลือก installation folder
3. คลิก Install
4. เสร็จแล้วสามารถรันได้จาก Desktop หรือ Start Menu
```

---

### 🍎 macOS Build (ทำบน Mac)

```bash
# Build installer สำหรับ macOS
npm run dist:mac

# Output:
# dist/
#   └── Agent Wallboard-3.2.0.dmg  (DMG Installer)

# ขนาดไฟล์: ~120-180 MB
# เวลา: 5-10 นาที
```

**Features ที่ได้:**
- `.dmg` disk image
- Drag-and-drop installation
- Code signing (ถ้ามี certificate)
- Gatekeeper compatible

**การติดตั้ง:**
```
1. Open .dmg file
2. Drag app icon ไปที่ Applications folder
3. Eject disk image
4. เปิด app จาก Applications
```

**⚠️ หมายเหตุสำหรับ Mac:**
```bash
# ถ้าเจอ "App is damaged" error
# ลบ quarantine attribute:
xattr -cr "/Applications/Agent Wallboard.app"
```

---

### 🐧 Linux Build (ทำบน Linux)

```bash
# Build installer สำหรับ Linux
npm run dist:linux

# Output:
# dist/
#   ├── Agent-Wallboard-3.2.0.AppImage  (Portable)
#   └── agent-wallboard_3.2.0_amd64.deb (Debian/Ubuntu)

# ขนาดไฟล์: ~120-170 MB แต่ละไฟล์
# เวลา: 5-10 นาที
```

**Features ที่ได้:**
- `.AppImage` (portable, ใช้ได้ทุก distro)
- `.deb` (สำหรับ Debian/Ubuntu)

**การติดตั้ง AppImage:**
```bash
# 1. ให้สิทธิ์ execute
chmod +x Agent-Wallboard-3.2.0.AppImage

# 2. รัน
./Agent-Wallboard-3.2.0.AppImage
```

**การติดตั้ง .deb:**
```bash
# Ubuntu/Debian
sudo dpkg -i agent-wallboard_3.2.0_amd64.deb
sudo apt-get install -f  # แก้ dependencies

# รัน
agent-wallboard
```

---
