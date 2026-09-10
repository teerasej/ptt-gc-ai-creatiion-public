# แบบฝึกหัดที่ 2: วิเคราะห์และเปรียบเทียบใบเสนอราคา

เราจะอัปโหลดใบเสนอราคาจำลองจาก Vendor 3 รายในรูปแบบ PDF แล้วให้ Agent เปรียบเทียบเงื่อนไขจากเอกสารแต่ละฉบับโดยอ้างอิงแหล่งข้อมูลอย่างชัดเจน

> **License:** ต้องมีสิทธิ์เข้าใช้ `Copilot Studio` และ Environment ต้องอนุญาตให้ผู้ใช้แนบไฟล์กับบทสนทนา

## Prerequisites

- Agent จาก Exercise 1
- [ใบเสนอราคา Alpha Industrial](../../../files/module-2/vendor-quotation-alpha-industrial.pdf)
- [ใบเสนอราคา Beta Engineering](../../../files/module-2/vendor-quotation-beta-engineering.pdf)
- [ใบเสนอราคา Gamma Supply](../../../files/module-2/vendor-quotation-gamma-supply.pdf)

> **⚠️ Note:** ไฟล์ทั้งสามเป็นข้อมูลจำลองสำหรับการฝึกอบรมเท่านั้น ห้ามอัปโหลดใบเสนอราคาจริง รายชื่อ Vendor จริง หรือข้อมูลส่วนบุคคล

> **⚠️ Note:** Microsoft ระบุขนาดไฟล์สูงสุด 16 MB ต่อไฟล์และอัปโหลดได้สูงสุด 10 ไฟล์ต่อการวิเคราะห์ แบบฝึกหัดนี้ใช้ไฟล์ PDF 3 ไฟล์และแต่ละไฟล์มีขนาดต่ำกว่าข้อจำกัด

---

## Scenario: เปรียบเทียบใบเสนอราคาจาก Vendor 3 ราย

ฝ่ายจัดซื้อต้องการเปรียบเทียบใบเสนอราคาสำหรับ `Pump Seal Kit` จำนวน 40 ชุด โดยยังไม่มีเกณฑ์ใดเกณฑ์หนึ่งที่สำคัญที่สุด Agent ต้องช่วยสรุปข้อเท็จจริงและ trade-off แต่ต้องไม่เลือกหรืออนุมัติ Vendor แทนผู้มีอำนาจ

### Practice 1: เปิด File Uploads

**Primary target:** เปิดความสามารถที่ทำให้ Agent รับใบเสนอราคา PDF จากผู้ใช้ได้

1. เปิด Agent แล้วไปที่ `Settings` > `Generative AI`
2. ใต้ `File processing capabilities` เปิด toggle `File uploads`
3. เลือก `Save`
4. ออกจากหน้า Settings แล้วกลับเข้ามาตรวจอีกครั้งว่า `File uploads` ยังเป็น `On`

#### Checkpoint

- `File uploads` = `On` และบันทึกการตั้งค่าแล้ว

> **⚠️ Note:** หากไม่มี toggle ถูก policy ปิด หรือบันทึกไม่สำเร็จ ให้แจ้งผู้สอนและใช้ instructor-prepared conversation สำหรับขั้นตอนที่เหลือ

---

### Practice 2: ตรวจว่า Agent อ่านข้อมูลจาก PDF แต่ละฉบับ

**Primary target:** ยืนยันว่า Agent ดึงค่าจากใบเสนอราคาทั้งสามฉบับและระบุเอกสารต้นทางได้

1. เปิด `Test your agent`
2. แนบไฟล์ PDF ทั้งสามฉบับกับ Prompt เดียวกันก่อนส่ง
3. วาง Prompt:

   ```text
   จากใบเสนอราคาที่แนบมา 3 ฉบับ ให้ระบุชื่อ Vendor, Unit Price, Delivery Days และ Warranty Months ของแต่ละราย
   ```

4. ตรวจว่าคำตอบแสดงข้อมูลต่อไปนี้:
   - Alpha Industrial: `12,500 THB`, `14 วัน`, `12 เดือน`
   - Beta Engineering: `11,800 THB`, `21 วัน`, `6 เดือน`
   - Gamma Supply: `13,200 THB`, `10 วัน`, `18 เดือน`
5. ตรวจว่า Agent เชื่อมข้อมูลแต่ละชุดกับชื่อไฟล์ PDF ที่ถูกต้อง

#### Checkpoint

- Agent อ่านค่าจาก PDF ครบทั้งสามฉบับ ระบุแหล่งที่มา และยังไม่สร้างข้อมูลหรือเลือก Vendor

---

### Practice 3: สร้างผลเปรียบเทียบพร้อม Trade-off

**Primary target:** ให้ Agent เปรียบเทียบเงื่อนไข คำนวณราคารวม และแยกข้อเท็จจริงออกจากข้อมูลที่ต้องยืนยัน

1. ใช้บทสนทนาเดิมแล้ววาง Prompt:

   ```text
   เปรียบเทียบใบเสนอราคาทั้ง 3 ฉบับ โดยใช้ Quantity, Unit Price, Total Price, Payment Terms, Delivery Days, Warranty Months, Quote Validity และเงื่อนไขหรือสิ่งที่รวมในราคา
   1. แสดง comparison table และชื่อไฟล์ต้นทางของแต่ละ Vendor
   2. ตรวจหรือคำนวณราคารวมจาก Quantity × Unit Price
   3. แยก Verified facts, Missing information, Conflicting information และ Assumptions
   4. สรุป trade-off และให้ recommendation สำหรับ human review โดยห้ามเลือกหรืออนุมัติ Vendor แทนผู้มีอำนาจ
   ```

2. ตรวจราคารวม:
   - Alpha Industrial: `40 × 12,500 = 500,000 THB`
   - Beta Engineering: `40 × 11,800 = 472,000 THB`
   - Gamma Supply: `40 × 13,200 = 528,000 THB`
3. ตรวจว่า Agent ระบุ trade-off สำคัญ:
   - Alpha มีราคาและเงื่อนไขอยู่ระดับกลาง
   - Beta ราคาต่ำสุด แต่ส่งช้าที่สุด รับประกันสั้นที่สุด และ Delivery Days ต้องยืนยัน
   - Gamma ส่งเร็วที่สุดและรับประกันนานที่สุด แต่ราคาสูงสุด
4. ถามต่อ:

   ```text
   ถ้าข้อมูลยังไม่พอ ขอคำถาม clarification ที่สำคัญที่สุดหนึ่งข้อ
   ```

#### Checkpoint

- ผลลัพธ์มี comparison table, แหล่งที่มา, ราคารวม, ข้อมูลที่ต้องยืนยัน และ recommendation ที่ระบุว่าไม่มี Vendor รายใดดีที่สุดทุกเกณฑ์และผู้มีอำนาจต้องเป็นผู้ตัดสินใจ

---

### Practice 4: ทดสอบข้อมูลขัดแย้งจากคนละแหล่ง

**Primary target:** ตรวจว่า Agent เก็บค่าจากทั้งสองแหล่ง แสดง conflict และไม่ตัดสินว่าแหล่งใดถูกต้องเอง

1. บอก Agent ว่า:

   ```text
   สมมติว่า Beta Engineering ยืนยัน Delivery Days เป็น 7 วันทางอีเมล แต่ในใบเสนอราคา vendor-quotation-beta-engineering.pdf ระบุ 21 วัน ช่วยระบุ conflict และบอกว่าต้องยืนยันอะไรต่อ
   ```

2. ตรวจว่า Agent แสดงทั้ง `7 วันจากอีเมล` และ `21 วันจากใบเสนอราคา`
3. ตรวจว่า Agent ขอให้ผู้ใช้ยืนยันแหล่งข้อมูลที่ได้รับอนุมัติก่อนปรับ recommendation

#### Checkpoint

- Agent เก็บค่าทั้งสองค่า ระบุแหล่งที่มา และไม่แก้ conflict หรือปรับ recommendation เอง

---

## Summary

คุณได้เปรียบเทียบใบเสนอราคา PDF 3 ฉบับ ตรวจแหล่งที่มา คำนวณราคารวม และรับมือกับข้อมูลที่ต้องยืนยันหรือขัดแย้งโดยไม่ให้ Agent ตัดสินใจแทนผู้มีอำนาจ

## Microsoft Learn Reference

- [Enable file input in Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/image-input-analysis)

ขั้นตอนถัดไป → [ตั้งค่า Suggested prompts](../exercise-3-suggested-prompts/README.md)
