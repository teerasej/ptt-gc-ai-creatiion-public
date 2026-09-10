# แบบฝึกหัดที่ 1: สร้างและกำหนดขอบเขต Vendor Comparison Agent

เราจะสร้าง `PTT GC Vendor Comparison Assistant` เพื่อช่วยผู้ใช้เปรียบเทียบใบเสนอราคาอย่างเป็นกลาง โดยแยกคำแนะนำออกจากอำนาจอนุมัติ

> **License:** ต้องมีสิทธิ์เข้าใช้ `Copilot Studio`

## Prerequisites

- บัญชีฝึกอบรมที่เข้า Environment ของชั้นเรียนได้
- ใช้ข้อมูลจำลองเท่านั้น

---

## Practice 1: สร้าง Agent และกำหนดงานหลัก

**Primary target:** สร้าง Agent ที่มีชื่อ คำอธิบาย และขอบเขตงานเปรียบเทียบ vendor ชัดเจน

1. เปิด [Copilot Studio](https://copilotstudio.microsoft.com) และเลือก Environment สำหรับการเรียน
2. เลือก `Agents` > `Create blank agent`
3. ตั้งชื่อว่า `PTT GC Vendor Comparison Assistant [ชื่อผู้เรียน]`
4. ใส่ Description:

   ```text
   Compares synthetic vendor quotations using price, payment terms, delivery time, warranty, and missing information. It provides analysis for human review and never approves a vendor or purchase.
   ```

5. กด `Save`

### Checkpoint

- หน้า `Overview` แสดงชื่อและ Description ตรงกับ use case และไม่มีข้อความว่า Agent สามารถอนุมัติได้

---

## Practice 2: เพิ่ม Instructions พร้อมขอบเขตอำนาจ

**Primary target:** ตั้ง Instructions ให้ Agent เปรียบเทียบจากข้อมูลที่ได้รับและหยุดถามเมื่อข้อมูลสำคัญยังขาด

1. ที่ `Overview` เลือก `Instructions` > `Edit`
2. วาง Instructions นี้ แล้วกด `Save`

   ```text
   You are PTT GC Vendor Comparison Assistant.
   Compare only the vendor quotation data supplied in the current conversation.
   Evaluate price, payment terms, delivery time, warranty, and stated risks.
   Separate facts, missing information, assumptions, and recommendation.
   If required data is missing, ambiguous, or conflicting, ask a concise clarification question before recommending.
   Never invent values. Never approve, reject, select, or commit to a vendor or purchase.
   State that the final decision belongs to the authorized procurement owner.
   Answer in the user's language and use a short comparison table when practical.
   ```

3. เปิด `Test your agent` และลองถาม:

   ```text
   ช่วยเลือก vendor ที่ดีที่สุดให้หน่อย
   ```

4. สังเกตว่า Agent ควรถามหาใบเสนอราคาหรือข้อมูลเกณฑ์ ไม่ควรสร้างตัวเลขหรืออนุมัติแทน

### Checkpoint

- Agent ขอข้อมูลที่จำเป็นและบอกขอบเขตการตัดสินใจของมนุษย์ได้

---

## Summary

คุณมี Agent ตั้งต้นที่พร้อมรับไฟล์ quotation ใน Exercise 2 และมี boundary ว่าให้คำแนะนำได้แต่อนุมัติไม่ได้

ขั้นตอนถัดไป → [วิเคราะห์และเปรียบเทียบใบเสนอราคา](../exercise-2-analyze-vendor-quotations/README.md)
