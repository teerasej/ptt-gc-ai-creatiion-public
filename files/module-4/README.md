# Module 4 Support Files

ใช้ไฟล์เหล่านี้กับ `Financial Report Assistant` ใน [Module 4](../../exercises/module-4/README.md) ทุกไฟล์เป็นข้อมูลจำลองสำหรับการเรียน

- [PTT-Monthly-Financial-Report-May2026.xlsx](./PTT-Monthly-Financial-Report-May2026.xlsx) เป็น workbook จำลองสำหรับ Exercise 2
- [Module 4 test-results template](./module-4-test-results-template.md) ใช้ทำสำเนาเพื่อบันทึก readiness, route, ผล Tool, file count และ email count
- [Financial terminology Knowledge (.docx)](./financial-report-technical-terms-knowledge.docx) เป็น optional Knowledge ไม่จำเป็นในเส้นทางหลัก
- [Distribution policy Knowledge (.docx)](./financial-report-distribution-policy-knowledge.docx) เป็น optional Knowledge ไม่จำเป็นในเส้นทางหลัก

## Workbook Structure

1. `Summary` แสดง Revenue, Cost, Variance, Status และ Key Risk ตาม Business Unit
2. `Revenue` แสดงรายได้ตาม Product Category
3. `Costs` แสดงค่าใช้จ่ายเทียบ budget
4. `Variance_Analysis` แสดง Actual, Budget และ root cause จำลอง

## Numeric Checkpoints

| Cell | ค่าตาม workbook | หน่วย |
|---|---|---|
| `Summary!C2` | 448.49 | million THB — Olefins Revenue |
| `Summary!D2` | 379.26 | million THB — Olefins Cost |
| `Summary!E2` | 18.25 | reported percent — ไม่คูณ 100 ซ้ำ |

ข้อมูลจำลองแต่ละ sheet อาจไม่ reconcile กัน เช่น `Summary!C2` และ `Variance_Analysis!C2` ให้สรุปข้อขัดแย้งพร้อม cell references ไม่แก้ workbook ต้นฉบับ ไม่บวกยอดจาก overlapping sheets และไม่ถือว่า `GC` เป็นยอดรวมโดยไม่มีหลักฐาน

## File Input Readiness

1. ให้ผู้สอนยืนยัน `Code interpreter`, schema และ attachment mapping ผ่าน Agent ด้วยบัญชีผู้เรียนก่อนเริ่ม Exercise 2
2. เมื่อ agent-level File input ผ่าน rehearsal ให้แนบ workbook และคำขอสรุปใน message เดียวกันตาม Exercise 2
3. หาก capability, permission หรือ mapping ไม่พร้อม ให้บันทึก `Environment blocked` พร้อมหลักฐาน และหยุด Exercise 2–3 จนกว่าผู้สอนจะแก้ไขและทดสอบผ่าน ไม่ใช้ข้อมูลที่ copy จาก Excel หรือสรุปที่เตรียมไว้แทนผลวิเคราะห์ผ่าน Agent

> **⚠️ Note:** Prompt builder Test ผ่านไม่ได้ยืนยันว่า File input ผ่าน Agent ใช้งานได้ ต้องบันทึก `Pass` จากหลักฐาน Tool call และผลสรุปจริงเท่านั้น การตรวจ Markdown/ไฟล์ในเครื่องไม่ได้ยืนยัน tenant readiness
