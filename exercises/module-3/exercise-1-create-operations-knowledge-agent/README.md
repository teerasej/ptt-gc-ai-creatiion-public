# แบบฝึกหัดที่ 1: สร้าง Operations Knowledge Agent

เราจะสร้าง `PTT GC Operations Knowledge Assistant` สำหรับตอบคำถามจาก Knowledge ที่เตรียมไว้ โดยตัว agent จะไม่มีความสามารถในการควบคุมเครื่องจักรหรือตัดสินใจด้านความปลอดภัย

> **License:** ต้องมีสิทธิ์เข้าใช้ `Copilot Studio`

---

## Practice 1: สร้างและ Scope Agent

**Primary target:** สร้าง Operations Knowledge Agent ที่ระบุงานที่ทำได้และงานที่ต้องส่งต่อได้ชัดเจน

1. เปิด `Copilot Studio` แล้วเลือก `Agents` > `Create blank agent`
2. ตั้งชื่อ `PTT GC Operations Knowledge Assistant [ชื่อผู้เรียน]`
3. ใส่ Instructions:

   ```text
   You are PTT GC Operations Knowledge Assistant for help enterprise user understand and know operations processes.

   - Answer operations process questions only from configured Knowledge.
   - Cite or name the source used when possible.
   - If the source does not contain the answer, say that the information is unavailable and suggest the responsible role.
   - Never invent safety limits, maintenance authorization, or incident details.
   - Do not control equipment or replace emergency procedures.
   - Answer in the user's language with concise steps.
   ```

4. กด `Save`

### Checkpoint

- Agent พร้อมเพิ่ม Knowledge และปฏิเสธงานควบคุมอุปกรณ์หรือการตัดสินใจฉุกเฉิน

---

## Practice 2: ทดสอบการตอบคำถามและขอบเขต Agent

**Primary target:** ยืนยันว่า Agent ตอบตาม Knowledge ที่มี และไม่ตอบเกินขอบเขต

1. เปิด `Test your agent` แล้วลองพิมพ์คำถามตัวอย่าง:

   ```text
   หากเกิด unplanned downtime ต้องบันทึกข้อมูลอะไรบ้าง
   ```

2. ตรวจว่า Agent แจ้งว่ายังไม่มีข้อมูลจาก Knowledge และแนะนำบทบาทที่รับผิดชอบ โดยไม่แต่งรายละเอียดขึ้นเอง
3. ทดสอบคำขอที่อยู่นอกขอบเขต:

   ```text
   ช่วยสั่งหยุดเครื่องจักรเพื่อแก้ปัญหา unplanned downtime
   ```

4. ตรวจว่า Agent ปฏิเสธการควบคุมอุปกรณ์ และแนะนำให้ปฏิบัติตามขั้นตอนฉุกเฉินหรือประสานผู้รับผิดชอบ

### Checkpoint

- Agent ไม่สร้างคำตอบจากข้อมูลที่ยังไม่มี และไม่รับคำสั่งควบคุมอุปกรณ์

---

## Practice 3: เพิ่มข้อมูลติดต่อที่ตรวจสอบได้ใน Instructions

**Primary target:** ใช้ Instructions เป็นแหล่งข้อมูลแบบง่าย เพื่อให้ Agent แจ้งช่องทางติดต่อที่กำหนดไว้โดยไม่สร้างข้อมูลขึ้นเอง

1. กลับไปที่หน้า `Overview` ของ Agent แล้วเพิ่มข้อความต่อไปนี้ท้าย Instructions:

   ```text
   When the user needs help beyond this agent's scope, provide only these approved contact details:
   - Department: Operations Support Department
   - Email: operations-support@example.com
   - Phone: 02-000-0000
   Do not invent or modify contact details.
   ```

   **แบบเต็ม**
   ```text
   You are PTT GC Operations Knowledge Assistant for a synthetic training environment.

   - Answer operations process questions only from configured Knowledge.
   - Cite or name the source used when possible.
   - If the source does not contain the answer, say that the information is unavailable and suggest the responsible role.
   - Never invent safety limits, maintenance authorization, or incident details.
   - Do not control equipment or replace emergency procedures.
   - Answer in the user's language with concise steps.

   When the user needs help beyond this agent's scope, provide only these approved contact details:
   - Department: Operations Support Department
   - Email: operations-support@example.com
   - Phone: 02-000-0000
   Do not invent or modify contact details.
   ```

   > **หมายเหตุ:** ข้อมูลติดต่อด้านบนเป็นข้อมูลสมมติสำหรับการฝึกอบรมเท่านั้น ในการใช้งานจริงให้แทนที่ด้วยข้อมูลที่หน่วยงานอนุมัติแล้ว

2. กด `Save` แล้วเปิด `Test your agent`
3. ทดสอบด้วยคำถาม:

   ```text
   หาก Agent ตอบคำถามเรื่อง unplanned downtime ไม่ได้ ฉันควรติดต่อใคร และติดต่อได้ทางไหน
   ```

4. ตรวจว่า Agent ตอบชื่อหน่วยงาน อีเมล และหมายเลขโทรศัพท์ตรงตาม Instructions โดยไม่เปลี่ยนหรือเพิ่มข้อมูลติดต่ออื่น

### Checkpoint

- Agent ใช้ข้อมูลติดต่อจาก Instructions ได้ตรงตามที่กำหนด และระบุช่องทางส่งต่อเมื่อคำขออยู่นอกขอบเขต

---

## Summary

คุณมี Agent ตั้งต้นที่รักษาขอบเขตและใช้ข้อมูลติดต่อที่กำหนดไว้ใน Instructions สำหรับการส่งต่อ ก่อนทดลอง broad และ targeted RAG ใน Exercise ถัดไป

ขั้นตอนถัดไป → [เพิ่ม Agent-level Knowledge](../exercise-2-agent-level-knowledge/README.md)
