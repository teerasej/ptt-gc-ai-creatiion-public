# แบบฝึกหัดที่ 2 (Required): Readiness, Publish, Install, and Access

เราจะตรวจ minimum readiness ของ Vendor Comparison Agent แล้ว publish, install และยืนยันว่า user ที่กำหนดเข้าถึง Agent และเห็น Suggested prompts ได้ Exercise นี้ทำได้แม้ข้าม Exercise 1

> **License:** ต้องมีสิทธิ์เข้าใช้ `Copilot Studio`, publish และเพิ่ม Agent ไปยัง channel ที่องค์กรอนุญาต การติดตั้งหรือแชร์อาจต้องผ่าน admin policy

## Prerequisites

- `PTT GC Vendor Comparison Assistant` จาก Module 2
- [Vendor quotations CSV fallback](../../../files/module-2/vendor-quotations-training.csv)

---

## Practice 1: ทำ Minimum Readiness Check

**Primary target:** ยืนยันว่า Agent มีองค์ประกอบขั้นต่ำสำหรับ publish แม้ไม่ได้ทำ optional tune-up

1. เปิด Agent และตรวจ:
   - ชื่อและ Description ระบุว่าเปรียบเทียบ quotation
   - Instructions มี clarification, don't guess และ approval boundary
   - Suggested prompts มีอย่างน้อยสามรายการที่ `Overview`
   - CSV fallback พร้อมใช้งาน
   - complete และ missing-data tests ผ่าน
2. แก้เฉพาะรายการที่ยังไม่ครบก่อนดำเนินการ

### Checkpoint

- Readiness checklist ครบโดยไม่อ้างอิง Exercise 1 หรือ Module 4

---

## Practice 2: Publish และ Install

**Primary target:** Publish Agent และเพิ่มไปยัง approved channel ของชั้นเรียน

1. เลือก `Publish` และยืนยันการ publish
2. หาก publish ถูก block ให้บันทึกข้อความหรือ screenshot แล้วใช้ instructor-published Agent สำหรับขั้นตอนถัดไป
3. ไปที่ `Channels` และเลือก channel ที่ผู้สอนกำหนด เช่น `Microsoft Teams` หรือ `Microsoft 365 Copilot`
4. เพิ่มหรือติดตั้ง Agent ตาม policy ขององค์กร

### Checkpoint

- มี publish status หรือหลักฐาน publish blocked และทราบ published Agent ที่ใช้เป็น fallback

---

## Practice 3: Verify Access and Suggested Prompts

**Primary target:** ยืนยันจาก published experience ว่าผู้ใช้เข้าถึง Agent และเห็น Suggested prompts

1. เปิด Agent จาก channel ที่ publish แล้วด้วยบัญชีผู้เรียนทั่วไป
2. ตรวจชื่อ Agent และ Suggested prompts บน welcome experience
3. เลือก Suggested prompt หนึ่งรายการและยืนยันว่าเริ่ม conversation ได้
4. ถ้า prompt ยังไม่อัปเดต ให้ refresh หรือเปิด conversation ใหม่ตามคำแนะนำผู้สอน และบันทึก observation

### Checkpoint

- ผู้ใช้ทั่วไปเปิด Agent และเห็น Suggested prompts ใน published experience

---

## Summary

Vendor Comparison Agent พร้อมสำหรับ demo ไม่ว่าผู้เรียนจะทำ optional Exercise 1 หรือไม่

## Microsoft Learn Reference

- [Publish and add an agent to Microsoft Teams](https://learn.microsoft.com/en-us/microsoft-copilot-studio/publication-add-bot-to-microsoft-teams)
- [Configure suggested prompts](https://learn.microsoft.com/en-us/microsoft-copilot-studio/configure-starter-prompts)

ขั้นตอนถัดไป → [Exercise 3: Vendor Comparison Demo](../exercise-3-vendor-comparison-demo/README.md)
