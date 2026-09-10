# แบบฝึกหัดที่ 5: ทดสอบ Email Paths

เราจะทดสอบเส้นทางสำเร็จ การแก้ไข การยกเลิก ข้อมูลผู้รับหาย connection failure และ send failure โดยยืนยันว่าแต่ละคำขอส่งไม่เกินหนึ่งอีเมล

> **License:** ต้องมีสิทธิ์ทดสอบ Agent และ Agent Flow ด้วยบัญชีฝึกอบรม

---

## Practice 1: ทดสอบ Functional Paths

**Primary target:** บันทึกผล happy, revision, cancellation และ missing-recipient paths โดยไม่เกิดการส่งซ้ำ

1. สร้างตาราง `Scenario`, `Expected`, `Actual`, `Email count`, `Result`
2. ทดสอบ:
   - Happy path: confirm และระบุอีเมลถูกต้อง
   - Revision: revise หนึ่งครั้งแล้ว confirm
   - Cancellation: cancel ก่อน `Send now`
   - Missing recipient: เว้นอีเมลว่างหรือใส่ข้อความไม่ใช่อีเมล
3. ตรวจ mailbox หลังแต่ละ scenario และบันทึกจำนวนอีเมล

### Checkpoint

- Happy และ revision ส่ง scenario ละหนึ่งอีเมล; cancellation และ missing recipient ส่งศูนย์ฉบับ

---

## Practice 2: ทดสอบ Failure Paths

**Primary target:** ยืนยันว่า connection หรือ send failure แสดง failure response โดยไม่อ้างว่าส่งสำเร็จ

1. ใช้ connection ที่ผู้สอนเตรียมให้สำหรับจำลอง failure หรือ review prepared run history หากไม่อนุญาตให้เปลี่ยน connection
2. รัน connection failure และ send failure แยกกัน
3. ตรวจ `Run history` และข้อความที่ Agent แสดง
4. กลับมาเปิด connection ปกติหลังทดสอบ

### Checkpoint

- ทั้งสอง failure paths ไม่แสดง success confirmation และมี next step ให้ผู้ใช้

---

## Practice 3: ตรวจ Exactly-one-send Rule

**Primary target:** ตรวจ Topic และ Tool configuration ว่ามีเส้นทางส่งอีเมล active เพียงหนึ่งเส้นทางต่อ test

1. ตรวจว่า `Send now` branch เรียก Agent Flow เพียง node เดียว
2. ตรวจว่า optional Work IQ Mail MCP ยังไม่ถูกเพิ่มหรือถูกปิดระหว่าง required test
3. รัน confirmed request อีกหนึ่งครั้งและนับอีเมล

### Checkpoint

- Confirmed request สุดท้ายส่งอีเมลหนึ่งฉบับ ไม่เป็นศูนย์และไม่ซ้ำ

---

## Summary

คุณตรวจ required Agent Flow ครบทั้ง success และ failure paths แล้ว Exercise 6 เป็นทางเลือกสำหรับเปรียบเทียบเท่านั้น

ขั้นตอนถัดไป → [Optional Work IQ Mail MCP](../exercise-6-optional-work-iq-mail-mcp/README.md) หรือ [Module 5](../../module-5/README.md)
