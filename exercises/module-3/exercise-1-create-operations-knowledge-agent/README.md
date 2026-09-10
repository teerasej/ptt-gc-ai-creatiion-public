# แบบฝึกหัดที่ 1: สร้าง Operations Knowledge Agent

เราจะสร้าง `PTT GC Operations Knowledge Assistant` สำหรับตอบคำถามการปฏิบัติงานจาก Knowledge ที่เตรียมไว้ โดยไม่ควบคุมเครื่องจักรหรือแทนที่การตัดสินใจด้านความปลอดภัย

> **License:** ต้องมีสิทธิ์เข้าใช้ `Copilot Studio`

---

## Practice 1: สร้างและ Scope Agent

**Primary target:** สร้าง Operations Knowledge Agent ที่ระบุงานที่ทำได้และงานที่ต้องส่งต่อได้ชัดเจน

1. เปิด `Copilot Studio` แล้วเลือก `Agents` > `Create blank agent`
2. ตั้งชื่อ `PTT GC Operations Knowledge Assistant [ชื่อผู้เรียน]`
3. ใส่ Instructions:

   ```text
   You are PTT GC Operations Knowledge Assistant for a synthetic training environment.
   Answer operations process questions only from configured Knowledge.
   Cite or name the source used when possible.
   If the source does not contain the answer, say that the information is unavailable and suggest the responsible role.
   Never invent safety limits, maintenance authorization, or incident details.
   Do not control equipment or replace emergency procedures.
   Answer in the user's language with concise steps.
   ```

4. กด `Save`

### Checkpoint

- Agent พร้อมเพิ่ม Knowledge และปฏิเสธงานควบคุมอุปกรณ์หรือการตัดสินใจฉุกเฉิน

---

## Summary

คุณมี Agent ตั้งต้นสำหรับทดลอง broad และ targeted RAG ใน Exercise ถัดไป

ขั้นตอนถัดไป → [เพิ่ม Agent-level Knowledge](../exercise-2-agent-level-knowledge/README.md)
