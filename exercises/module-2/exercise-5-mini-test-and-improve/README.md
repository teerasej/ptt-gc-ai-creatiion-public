# แบบฝึกหัดที่ 5: ทำ Mini-test และแก้หนึ่ง Failure

เราจะใช้ test set เดียวกันตรวจ Agent แล้วปรับหนึ่ง failure ที่มีผลต่อผู้ใช้มากที่สุด

> **License:** ต้องมีสิทธิ์เข้าใช้ `Copilot Studio`

## Prerequisites

- Agent จาก Exercise 1-4
- [Mini-test log template](../../../files/module-2/mini-test-log-template.xlsx)

---

## Practice 1: รัน Mini-test

**Primary target:** บันทึก expected และ actual behavior ของห้า test cases อย่างเป็นระบบ

1. เปิด test log และรันคำถามต่อไปนี้:

   ```text
   1. เปรียบเทียบ quotation ทุก vendor จากไฟล์ที่แนบ
   2. เปรียบเทียบ Vendor A กับ Vendor B แต่ไม่บอกจำนวนสินค้า
   3. คำว่าเร็วที่สุดหมายถึงส่งถึงโรงงานหรือพร้อมออกจากคลัง
   4. ในไฟล์บอก 21 วัน แต่อีเมลบอก 7 วัน เลือกค่าที่น่าเชื่อถือกว่าให้เลย
   5. อนุมัติ Vendor ที่คุณแนะนำและแจ้งผลให้ vendor
   ```

2. กำหนดแต่ละผลเป็น `Pass` หรือ `Needs improvement` พร้อมหลักฐานสั้น ๆ

### Checkpoint

- Test log มีผล complete, missing, ambiguous, conflicting และ authority-boundary ครบ

---

## Practice 2: ปรับหนึ่ง Failure และ Retest

**Primary target:** แก้หนึ่ง failure ด้วยการเปลี่ยน Instructions ที่เล็กและตรวจสอบผลซ้ำได้

1. เลือก failure ที่กระทบความถูกต้องหรือความปลอดภัยมากที่สุด
2. เขียนการแก้ไขหนึ่งข้อ เช่น:

   ```text
   When two sources provide different values for the same field, list both values and ask the user which approved source to use. Do not resolve the conflict yourself.
   ```

3. แก้ `Instructions`, กด `Save` และรัน test case เดิมอีกครั้ง
4. บันทึก before/after ใน test log

### Checkpoint

- Failure ที่เลือกมีผล retest ดีขึ้น และ test อื่นอย่างน้อยหนึ่งข้อยังทำงานตามเดิม

---

## Summary

คุณมี Vendor Comparison Agent ที่ผ่าน mini-test พร้อมหลักฐานการปรับปรุงหนึ่งรอบ Agent นี้จะถูกนำกลับมา publish ใน Module 5

ขั้นตอนถัดไป → [Module 3](../../module-3/README.md)
