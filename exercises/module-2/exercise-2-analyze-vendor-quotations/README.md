# แบบฝึกหัดที่ 2: วิเคราะห์และเปรียบเทียบใบเสนอราคา

เราจะอัปโหลดข้อมูลใบเสนอราคาจำลองในแชต แล้วให้ Agent เปรียบเทียบข้อมูลที่ตรวจสอบได้ พร้อมใช้ CSV fallback เมื่อเส้นทาง XLSX ไม่พร้อม

> **License:** ต้องมีสิทธิ์เข้าใช้ `Copilot Studio` และ premium generative AI capabilities ตาม licensing ขององค์กร ความสามารถ chat-based structured-data code interpreter เป็น `Preview` และรองรับ public cloud แต่ยังไม่รองรับ sovereign cloud

## Prerequisites

- Agent จาก Exercise 1
- [vendor-quotations-training.xlsx](../../../files/module-2/vendor-quotations-training.xlsx)
- [vendor-quotations-training.csv](../../../files/module-2/vendor-quotations-training.csv)

> **⚠️ Note:** Microsoft ระบุขนาดไฟล์สูงสุด 16 MB ต่อไฟล์และอัปโหลดได้สูงสุด 10 ไฟล์ต่อการวิเคราะห์ ไฟล์ฝึกนี้ใช้เพียงหนึ่งไฟล์และมีขนาดต่ำกว่าข้อจำกัด

> **⚠️ Note:** หากเปิดทั้งสอง toggles ได้ แต่ `.xlsx` วิเคราะห์ไม่สำเร็จ ให้ใช้ไฟล์ `.csv` ที่มีข้อมูลตรงกัน การสลับไฟล์เหมือนเปลี่ยนจากกล่องเอกสารเป็นซองใส ข้อมูลเดิมแต่ระบบอ่านได้ง่ายกว่า หาก `Code interpreter` ไม่มีให้ใช้หรือเปิดไม่ได้ CSV จะไม่แก้ข้อจำกัดนี้ ให้บันทึกว่า environment ถูก block และใช้ prepared analysis result จากผู้สอน

---

## Practice 1: เปิด File Upload และ Code Interpreter

**Primary target:** เปิด file processing capabilities สองรายการที่ Agent ต้องใช้สำหรับวิเคราะห์ structured data ที่ผู้ใช้อัปโหลด

1. เปิด Agent แล้วไปที่ `Settings` > `Generative AI`
2. ใต้ `File processing capabilities` เปิด toggle `File uploads`
3. ใต้ `File processing capabilities` เปิด toggle `Code interpreter`
4. เลือก `Save`
5. ออกจากหน้า Settings แล้วกลับเข้ามาตรวจอีกครั้งว่าทั้งสอง toggles ยังเป็น `On`

### Checkpoint

- `File uploads` = `On`, `Code interpreter` = `On` และบันทึกการตั้งค่าแล้ว

> **⚠️ Note:** ถ้า toggle ใดไม่มีให้เลือก ถูก policy ปิด หรือกด `Save` ไม่สำเร็จ ให้หยุดเส้นทาง live analysis และแจ้งผู้สอน อย่าข้ามไปโดยสมมติว่า Code interpreter ทำงานอยู่

---

## Practice 2: ยืนยันว่า Code Interpreter คำนวณจากไฟล์ได้

**Primary target:** ยืนยันว่า Agent ใช้ข้อมูลในไฟล์ที่แนบเพื่อคำนวณคำตอบ ไม่ได้อ่านเพียงชื่อไฟล์หรือคาดเดาค่า

1. เปิด `Test your agent`
2. พิมพ์ Prompt ด้านล่างและแนบ `vendor-quotations-training.xlsx` ไปกับ Prompt เดียวกันก่อนส่ง

   ```text
   จากไฟล์ที่แนบมา ให้คำนวณมูลค่ารวมของ Vendor V001 โดยใช้ Quantity × UnitPriceTHB แสดงสูตร ตัวเลขที่ใช้ และผลลัพธ์ โดยยังไม่ต้องแนะนำ vendor
   ```

3. ตรวจว่าคำตอบใช้ `40 × 12,500` และได้ผลลัพธ์ `500,000 THB`
4. ถ้าแนบ XLSX ไม่ได้หรือคำตอบไม่ใช้ข้อมูลในไฟล์ ให้เริ่ม conversation ใหม่ แนบ `vendor-quotations-training.csv` กับ Prompt เดิม แล้วทดสอบอีกครั้ง
5. หากทั้ง XLSX และ CSV ไม่ทำงานทั้งที่ toggles เปิดอยู่ ให้บันทึกผลเป็น `Environment blocked` และใช้ prepared analysis result ของผู้สอน

### Checkpoint

- Agent แสดง calculation `40 × 12,500 = 500,000 THB` จากไฟล์ที่แนบ หรือมีหลักฐาน `Environment blocked` และเลือก classroom fallback แล้ว

---

## Practice 3: สร้างผลเปรียบเทียบจากข้อมูลในไฟล์

**Primary target:** ให้ Agent สร้าง comparison ที่แยกข้อเท็จจริง ข้อมูลที่ขาด และคำแนะนำสำหรับ human review

1. ใช้ conversation เดิมแล้ววาง Prompt:

   ```text
   เปรียบเทียบ quotation ทุก vendor จากไฟล์นี้ โดยใช้ Unit Price, Quantity, Payment Terms, Delivery Days และ Warranty Months
   1. แสดง comparison table
   2. คำนวณราคารวมต่อ vendor จากข้อมูลที่มี
   3. แยก Missing information และ Conflicting information
   4. ให้ recommendation พร้อมเหตุผล แต่ห้ามอนุมัติหรือเลือก vendor แทนผู้มีอำนาจ
   ```

2. ตรวจตัวเลขรวมกับ workbook หรือ CSV อย่างน้อยหนึ่ง vendor
3. ถามต่อ:

   ```text
   ถ้าข้อมูลยังไม่พอ ขอคำถาม clarification ที่สำคัญที่สุดเพียงหนึ่งข้อ
   ```

### Checkpoint

- ผลลัพธ์มี comparison table, ราคารวม, missing/conflicting information และ recommendation ที่ระบุว่าต้องให้ผู้มีอำนาจตัดสินใจ

---

## Practice 4: ทดสอบข้อมูลผิดปกติ

**Primary target:** ตรวจว่า Agent หยุดถามเมื่อพบข้อมูลสำคัญที่คลุมเครือหรือขัดแย้ง

1. บอก Agent ว่า:

   ```text
   สมมติว่า Vendor B ยืนยัน Delivery Days เป็น 7 วันทางอีเมล แต่ในไฟล์ระบุ 21 วัน ช่วยสรุปผลทันที
   ```

2. ตรวจว่า Agent ระบุ conflict และไม่เลือกค่าหนึ่งเอง

### Checkpoint

- Agent ขอให้ยืนยัน Delivery Days ก่อนปรับ recommendation

---

## Summary

คุณได้ทดลอง complete, missing, ambiguous และ conflicting quotation data พร้อม fallback ที่ใช้ข้อมูลชุดเดียวกัน

## Microsoft Learn Reference

- [Use code interpreter for analysis of a user-uploaded structured data file](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-code-interpreter-structured-data#use-code-interpreter-for-analysis-of-a-user-uploaded-structured-data-file)
- [Enable file input in Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/image-input-analysis)

ขั้นตอนถัดไป → [ตั้งค่า Suggested prompts](../exercise-3-suggested-prompts/README.md)
