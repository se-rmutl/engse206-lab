# Activity W05-B — Requirement Type Card Sorting

> **เป้าหมาย:** แยก Requirement Candidate เป็น Functional, NFR, Business Rule, Constraint หรือ Issue

## Card Sorting Rule

ให้อ่าน card ทีละใบและถามว่า “ข้อความนี้กำลังบอกอะไร”

| Type | คำถามตัดสิน |
|---|---|
| Functional | ระบบต้องทำ action หรือ behavior อะไร |
| NFR | ระบบต้องมีคุณภาพหรือเงื่อนไขคุณภาพแบบใด |
| Business Rule | domain มีกฎการทำงานอะไร |
| Constraint | มีข้อจำกัดภายนอก บริบท นโยบาย หรือ platform ใดบังคับ |
| Issue | ยังไม่รู้ ยังไม่มี evidence หรือยังต้องถามต่อ |

## Worksheet

| Card / RC-ID | ประโยค Candidate | Type ที่เลือก | เหตุผล | ต้อง split หรือไม่ |
|---|---|---|---|---|
| RC-xx | [ข้อความ] | Functional/NFR/BR/Constraint/Issue | [เหตุผล] | Yes/No |

## Common Split Cases

- ประโยคเดียวมีทั้ง function และ business rule
- ประโยคเดียวมีทั้ง function และ NFR
- ประโยคมี solution เช่น LINE, QR, photo, database แต่ need ยังไม่ชัด
- ประโยคมี policy ที่ยังไม่มีผู้ยืนยัน

