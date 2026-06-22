# Git Workflow และการส่งงาน

## หลักการ

แต่ละกลุ่มสร้าง repository ของตนเองจาก `student-repo-starter/` แล้วส่ง URL ตามช่องทางที่อาจารย์กำหนด โดย repository ต้องมีประวัติการแก้ไขชิ้นงานจริง

## โครงสร้าง repo นักศึกษา

```text
ENGSE206-GroupXX-ProjectName/
├── README.md
├── docs/
├── design/
├── evidence/
├── feedback/
├── final/
└── CHANGELOG.md
```

## macOS (iMac M1)

เปิด **Terminal** แล้วใช้คำสั่งหลังได้รับ URL จากอาจารย์

```bash
git clone <URL_FROM_INSTRUCTOR>
cd ENGSE206-GroupXX-ProjectName
git checkout -b week01-problem-brief
git add .
git commit -m "docs: complete problem brief v0.1"
git push -u origin week01-problem-brief
```

## Windows notebook

ใช้ **PowerShell**, Git Bash หรือ Terminal ใน VS Code โดยใช้คำสั่งเดียวกัน

```powershell
git clone <URL_FROM_INSTRUCTOR>
cd ENGSE206-GroupXX-ProjectName
git checkout -b week01-problem-brief
git add .
git commit -m "docs: complete problem brief v0.1"
git push -u origin week01-problem-brief
```

ผู้เรียนอาจใช้ GitHub Desktop, VS Code Source Control หรือ web editor ได้ แต่ต้องรักษา revision history และโครงสร้างไฟล์ที่กำหนด

## สิ่งที่ส่งแต่ละสัปดาห์

1. ไฟล์ Markdown/เอกสารต้นฉบับที่แก้ไขได้
2. PDF export เมื่อผู้สอนกำหนด
3. หลักฐาน เช่น screenshot, photo, interview notes, board export หรือ link ที่เข้าถึงได้
4. Commit history ที่แสดงการมีส่วนร่วม
5. Branch หรือ pull request ตามที่ผู้สอนกำหนด

## ข้อควรระวัง

- ห้าม commit password, token, ข้อมูลส่วนบุคคล หรือข้อมูลจริงที่ไม่ได้รับอนุญาต
- หากใช้ AI ให้เปิดเผยว่าใช้ช่วยเรื่องใดและทีมตรวจทาน/แก้ไขอะไรเอง
- ตรวจ [Submission Checklist](../weeks/week-01-problem-brief/submission-checklist.md) ก่อนส่ง
