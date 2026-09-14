# Module 2 Support Files

ไฟล์หลักสำหรับ `PTT GC Vendor Comparison Assistant` คือใบเสนอราคาจำลอง PDF 3 ฉบับ แต่ละฉบับเป็นข้อเสนอจาก Vendor คนละรายและมี trade-off ต่างกัน

## Required Files

- `vendor-quotation-alpha-industrial.pdf` มีราคาและเงื่อนไขระดับกลาง
- `vendor-quotation-beta-engineering.pdf` มีราคาต่ำสุด แต่ส่งช้ากว่า รับประกันสั้นกว่า และต้องยืนยัน Delivery Days
- `vendor-quotation-gamma-supply.pdf` มีราคาสูงสุด แต่ส่งเร็วที่สุดและรับประกันนานที่สุด
- `mini-test-log-template.xlsx` ใช้บันทึก expected และ actual behavior

หาก Environment ไม่รองรับการแนบ PDF หลายไฟล์ ให้ใช้ instructor-prepared conversation หรือข้อความจากใบเสนอราคาที่ผู้สอนเตรียมไว้ โดยไม่เปลี่ยน expected results

## Optional Procurement References

- `Procurement Policy Handbook.pdf`
- `Purchase Approval Matrix.xlsx`
- `Vendor Onboarding Checklist.docx`

ไฟล์ optional ช่วยให้ผู้เรียนทดลองคำถามเรื่อง policy แต่ไม่จำเป็นต่อเส้นทางหลัก และไม่เปลี่ยนขอบเขตของ Agent: Agent ช่วยสรุปและเปรียบเทียบ แต่ไม่มีอำนาจอนุมัติ Vendor หรือการจัดซื้อ

## Optional Engine Anomaly Exercise

- `engine-anomaly-incident-data.csv` เป็นไฟล์หลักสำหรับทำ Optional Exercise 6
- `engine-anomaly-incident-data.xlsx` มีข้อมูลชุดเดียวกับ CSV และใช้ทดลองเพิ่มเติมเมื่อ Environment รองรับเท่านั้น

ให้ทำทุกขั้นตอนและ Checkpoint ด้วย CSV ก่อนเสมอ หาก XLSX ใช้งานไม่ได้ให้ทำต่อด้วย CSV โดยไม่ถือว่าเป็นปัญหาของเส้นทางหลัก

> **⚠️ Note:** ใช้ข้อมูลจำลองเท่านั้น ห้ามอัปโหลดใบเสนอราคาจริง รายชื่อ vendor จริง หรือข้อมูลส่วนบุคคล
