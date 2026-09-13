# แบบฝึกหัดที่ 1: สร้างและกำหนดขอบเขต Vendor Comparison Agent

เราจะสร้าง `PTT GC Vendor Comparison Assistant` เพื่อช่วยผู้ใช้เปรียบเทียบใบเสนอราคา

> **License:** ต้องมีสิทธิ์เข้าใช้ `Copilot Studio`

## Prerequisites

- บัญชีฝึกอบรมที่เข้า Environment ของที่เตรียมไว้ให้ได้

---

## Practice 1: สร้าง Agent และกำหนดงานหลัก

**Primary target:** สร้าง Agent ที่มีชื่อ คำอธิบาย และขอบเขตงานเปรียบเทียบ vendor ชัดเจน

1. เปิด [Copilot Studio](https://copilotstudio.microsoft.com) และเลือก Environment สำหรับการเรียน
2. เลือก `Agents` > `Create blank agent`
3. ตั้งชื่อว่า `PTT GC Vendor Comparison Assistant [ชื่อผู้เรียน]`
4. กด **Create**
5. รอจนระบบสร้าง Agent เสร็จ และแสดงแถบสีเขียวเพื่อยืนยันความพร้อมใช้งาน
6. ในหน้า `Overview` ให้กดปุ่ม edit และใส่ Description:

   ```text
   Compares vendor quotations using price, payment terms, delivery time, warranty, and stated risks.
   ```

### Checkpoint

- หน้า `Overview` แสดงชื่อและ Description ตรงกับ use case

---

## Practice 2: กำหนดบทบาทเริ่มต้นให้ Agent

**Primary target:** เพิ่ม Instruction เพียงบรรทัดเดียว แล้วสังเกตว่า Agent เข้าใจบทบาทได้กว้างเพียงใด

1. ที่ `Overview` เลือก `Instructions` > `Edit`
2. วาง Instruction บรรทัดแรกนี้ แล้วกด `Save`

   ```text
   You are PTT GC Vendor Comparison Assistant.
   ```

3. เปิด `Test your agent` และเริ่มบทสนทนาใหม่
4. ลองถามว่า Agent ช่วยทำอะไรได้บ้างด้วย Prompt นี้:

   ```text
   What can you help me compare in vendor quotations?
   ```

5. สังเกตว่า Agent อาจอธิบายความสามารถแบบกว้าง ๆ เพราะ Instructions ยังไม่ได้ระบุเกณฑ์และรูปแบบคำตอบ

### Checkpoint

- Agent รู้บทบาทว่าเกี่ยวข้องกับการเปรียบเทียบ Vendor แต่ยังไม่มีรายละเอียดการทำงานที่ชัดเจน

---

## Practice 3: เพิ่มรายละเอียดการเปรียบเทียบ

**Primary target:** เพิ่ม Instructions ที่กำหนดข้อมูลที่ต้องเปรียบเทียบและรูปแบบคำตอบ แล้วสังเกตความแตกต่างจากผลลัพธ์ก่อนหน้า

1. ที่ `Overview` เลือก `Instructions` > `Edit`
2. คงบรรทัดแรกไว้ แล้วเพิ่ม Instructions ที่เหลือดังนี้:

   ```text
   You are PTT GC Vendor Comparison Assistant.
   - Compare the vendor quotation documents supplied in the current conversation.
   - Evaluate price, payment terms, delivery time, warranty, and stated risks.
   - Summarize the quotation details and trade-offs.
   - Use a short comparison table when practical.
   ```

3. กด `Save` แล้วเริ่มบทสนทนาใหม่ใน `Test your agent`
4. ทดสอบด้วย Prompt เดิม:

   ```text
   What can you help me compare in vendor quotations?
   ```

5. เปรียบเทียบกับผลลัพธ์จาก Practice 2 และสังเกตว่า Agent ระบุเกณฑ์ได้ชัดเจนขึ้น เช่น ราคา เงื่อนไขชำระเงิน ระยะเวลาส่งมอบ การรับประกัน และความเสี่ยง

### Checkpoint

- Agent อธิบายเกณฑ์การเปรียบเทียบและรูปแบบคำตอบได้ตรงกับ Instructions ที่เพิ่มขึ้น

---

## Practice 4: กำหนดภาษาของคำตอบ

**Primary target:** เพิ่ม Instruction ด้านภาษาไว้บนสุด แล้วสังเกตว่า Agent ตอบเป็นภาษาไทยแม้ Prompt เป็นภาษาอังกฤษ

1. ที่ `Overview` เลือก `Instructions` > `Edit`
2. เพิ่ม Instruction นี้ไว้เป็นบรรทัดแรกเหนือ Instructions เดิม:

   ```text
   Respond in Thai only.
   ```

3. ตรวจว่า Instructions ทั้งหมดเป็นดังนี้ แล้วกด `Save`:

   ```text
   Respond in Thai only.
   You are PTT GC Vendor Comparison Assistant.
   - Compare the vendor quotation documents supplied in the current conversation.
   - Evaluate price, payment terms, delivery time, warranty, and stated risks.
   - Summarize the quotation details and trade-offs.
   - Use a short comparison table when practical.
   ```

4. เริ่มบทสนทนาใหม่ใน `Test your agent` แล้วทดสอบด้วย Prompt เดิม:

   ```text
   What can you help me compare in vendor quotations?
   ```

5. สังเกตว่า Agent ตอบเป็นภาษาไทย แม้ Prompt ที่ใช้ทดสอบจะเป็นภาษาอังกฤษ

### Checkpoint

- Agent ตอบเป็นภาษาไทยและยังอธิบายเกณฑ์การเปรียบเทียบได้ครบตาม Instructions

---

## Summary

คุณมี Agent ตั้งต้นที่พร้อมรับใบเสนอราคา PDF 3 ฉบับใน Exercise 2 ส่วน reliability rules จะเพิ่มและทดสอบทีละข้อใน Exercise 4

ขั้นตอนถัดไป → [วิเคราะห์และเปรียบเทียบใบเสนอราคา](../exercise-2-analyze-vendor-quotations/README.md)
