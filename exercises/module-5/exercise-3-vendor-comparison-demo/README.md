# แบบฝึกหัดที่ 3 (Required): Vendor Comparison Demo

เราจะสาธิต Agent จาก published channel ด้วยเรื่องเดียวต่อเนื่อง: อัปโหลด quotation, เปรียบเทียบ, ถามข้อมูลที่ขาด และปรับ recommendation หลังได้รับข้อมูลใหม่

> **License:** ต้องเข้าถึง published Agent ใน channel ของชั้นเรียน

---

## Practice 1: Run the Published Demo

**Primary target:** สาธิตพฤติกรรมหลักของ Vendor Comparison Agent ใน published experience

1. เปิด published Agent และใช้ run sheet:

   ```text
   1. อัปโหลด vendor-quotations-training.xlsx และขอ comparison table
   2. ถ้า published channel รับ XLSX ไม่ได้ ให้อัปโหลด vendor-quotations-training.csv
   3. ขอให้ Agent บอกข้อมูลที่ขาดหรือขัดแย้งก่อนแนะนำ
   4. ให้ข้อมูลใหม่ว่า delivery requirement คือไม่เกิน 14 วัน
   5. ขอ recommendation ฉบับแก้ไขพร้อม trade-off และ approval boundary
   ```

2. หาก published file upload ใช้งานไม่ได้ ให้ใช้ instructor-prepared published conversation หรือ paste แถวข้อมูลจาก CSV ตามที่ผู้สอนกำหนด
3. จด expected และ actual behavior ของแต่ละช่วง

### Checkpoint

- Demo แสดง upload/fallback, comparison, clarification และ revised recommendation ครบ โดย Agent ไม่อนุมัติ vendor

---

## Practice 2: Prepare a Five-minute Run Sheet

**Primary target:** สร้าง run sheet ที่ทำให้ทีมสาธิตผลลัพธ์เดิมได้ภายในห้านาที

1. กำหนด `Presenter`, `Operator`, `Observer`
2. เติม template:

   ```text
   Opening:
   Upload route and fallback:
   Comparison prompt:
   Missing-information prompt:
   New information for revision:
   Expected boundary statement:
   Recovery line:
   ```

3. ซ้อมหนึ่งรอบและปรับเฉพาะจุดที่ทำให้ demo สะดุด

### Checkpoint

- ทีมมี run sheet และซ้อมครบหนึ่งรอบภายในเวลาที่กำหนด

---

## Summary

คุณมี published demo evidence ที่ใช้ต่อในหน้า `Monitor`

ขั้นตอนถัดไป → [Exercise 4: Monitor and Improve](../exercise-4-monitor-and-improve/README.md)
