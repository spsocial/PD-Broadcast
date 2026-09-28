# PD Broadcast — อัปเดต & รีลีส

repo นี้ใช้เก็บ **ข้อมูลเวอร์ชัน (`version.json`)** และ **ไฟล์ติดตั้ง (Release assets)** ของส่วนขยาย PD Broadcast เท่านั้น
ตัวส่วนขยายจะเช็ค `version.json` อัตโนมัติเมื่อเปิดใช้งาน แล้วแจ้งเตือนเมื่อมีเวอร์ชันใหม่

> ⚠️ ไม่มีซอร์สโค้ดในนี้ — เก็บเฉพาะไฟล์แจกจ่าย (โค้ดถูกเข้ารหัสกันคัดลอก)

## วิธีออกเวอร์ชันใหม่ (ทุกครั้งที่ ship)
1. ในโปรเจกต์: bump version → `node build.js` → zip (ตามกฎ ship)
2. อัป zip โปรเทกต์เป็น **Release asset** ที่ tag `v<เวอร์ชัน>`
   ```
   gh release create v1.3.2 "PD-Broadcast-v1.3.2-protected.zip" --repo spsocial/PD-Broadcast --title "v1.3.2" --notes "รายละเอียด..."
   ```
3. แก้ `version.json` (`latest` + เพิ่ม entry ใน `versions[]` + `downloadUrl`) แล้ว push ขึ้น `main`
4. ลูกค้าที่เปิดแอปจะเห็นป้าย "🆕 อัปเดต" ภายในไม่กี่วินาที

## โครงสร้าง version.json
- `latest` — เวอร์ชันล่าสุด (แอปเทียบกับ manifest ของตัวเอง)
- `downloadUrl` — ลิงก์ Release asset ของเวอร์ชันล่าสุด
- `changelog` — สรุปสิ่งที่เปลี่ยน (แสดงในป๊อปอัพ)
- `versions[]` — ประวัติทุกเวอร์ชัน (แสดงย้อนหลัง)
