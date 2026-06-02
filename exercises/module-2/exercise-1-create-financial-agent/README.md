# แบบฝึกหัดที่ 1: สร้าง Financial Report Assistant Agent

🔑 **ต้องการ M365 Copilot License + สิทธิ์เข้าใช้ Copilot Studio**

แบบฝึกหัดนี้จะพาเราสร้าง Agent ตัวตั้งต้นสำหรับ Module 2 โดยให้ได้ Agent ชื่อ **Financial Report Assistant** พร้อม instructions ที่พร้อมต่อยอดไปทำ Topic เดียวกันในแบบฝึกหัดถัดไป


## Practice 1: สร้าง Agent ใหม่ใน Copilot Studio

1. เปิด [https://copilotstudio.microsoft.com](https://copilotstudio.microsoft.com)
2. เลือก Environment ที่ใช้เรียน
3. จากเมนูทางด้านซ้ายกดเลือก **Agents** 
4. กด **Create blank agent**
5. ตั้งชื่อ Agent ว่า:

   ```
   Financial Report Assistant [ชื่อตัวเอง (ถ้าจำเป็น)]
   ```


---

## Practice 2: ใส่ instruction ฉบับพร้อมใช้งาน

1. หลังจาก Agent ถูกสร้างขึ้น และพร้อมสำหรับการทำงานแล้ว ให้ลงมาที่ช่องด้านล่างที่ชื่อว่า **Instruction** แล้วกดปุ่ม **Edit** 
2. ใช้ instruction template ด้านล่าง (ปรับคำได้ตามทีม):

   ```
   You are Financial Report Assistant for enterprise business users.
   Your scope is monthly financial reporting support only.

   Responsibilities:
   - Collect required inputs before analysis: report period, business unit, and report format.
   - Support KPI and variance-focused summaries using available data.
   - Ask clarifying questions when required inputs are missing.
   - Provide concise, management-friendly outputs in Thai language.

   Boundaries:
   - Do not provide legal, tax filing, or investment advice.
   - Do not fabricate missing financial numbers.
   - If data is insufficient, clearly say what is missing and ask the user to provide it.

   Output style:
   - Start with a short executive summary.
   - Then provide key KPI bullets and variance highlights.
   - End with risks and recommended next actions.
   ```

3. กด **Save**

---

## Practice 4: Smoke test Agent ก่อนเริ่มสร้าง Topic

1. ทดสอบ prompt อย่างน้อย 2 ข้อ เช่น:

   ```
   ช่วยเตรียมสรุปรายงานการเงินรายเดือนสำหรับ BU Olefins
   ```

   ```
   ขอ executive summary ของผลการเงินเดือนล่าสุด และเน้น variance หลัก
   ```

2. ตรวจว่า Agent ถามข้อมูลที่ยังขาด และตอบในโทนที่กระชับตาม instruction

---

## สรุป

ในแบบฝึกหัดนี้ คุณได้สร้าง Agent ตั้งต้นสำหรับงานรายงานการเงิน พร้อม instruction ที่พร้อมต่อยอดใน Module 2

ขั้นตอนถัดไป → [ออกแบบ Topic รับความต้องการรายงานการเงิน](../exercise-2-topic-intake-flow/README.md)