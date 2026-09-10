# Module 3: RAG - Operations Knowledge Assistant

Module นี้ใช้ `PTT GC Operations Knowledge Assistant` เพื่อเปรียบเทียบ RAG สองแบบ: Agent-level Knowledge สำหรับคำถามกว้าง และ Topic-level Generative answers สำหรับคำถามที่ต้องจำกัดแหล่งข้อมูล

> **License:** ต้องมีสิทธิ์เข้าใช้ `Copilot Studio` และความสามารถเพิ่มไฟล์เป็น `Knowledge`

> **⚠️ Note:** `Search only selected sources` ควบคุมแหล่งข้อมูลที่ node ใช้ค้นหา ไม่ใช่ระบบกำหนดสิทธิ์ผู้ใช้ ไฟล์ที่อัปโหลดตรงเข้า Agent ต้องเป็นข้อมูลจำลองหรือข้อมูลที่ผู้เรียนทุกคนมีสิทธิ์อ่าน

## Support Files

- [Operations overview](../../files/module-3/operations-overview.md)
- [Downtime reporting](../../files/module-3/downtime-reporting.md)
- [Maintenance escalation](../../files/module-3/maintenance-escalation.md)
- [Operations roles](../../files/module-3/operations-roles.md)

## Required Sequence

1. [Create and scope the Agent](./exercise-1-create-operations-knowledge-agent/README.md)
2. [Add Agent-level Knowledge](./exercise-2-agent-level-knowledge/README.md)
3. [Create Topics with questions, variables, and conditions](./exercise-3-topics-questions-variables-conditions/README.md)
4. [Add targeted Generative answers](./exercise-4-targeted-generative-answers/README.md)
5. [Compare broad and targeted retrieval](./exercise-5-compare-broad-targeted-retrieval/README.md)

## Learner Output

Operations Knowledge Agent ที่ตอบคำถามทั่วไปได้ และเลือกเส้นทางแบบเจาะจงสำหรับ downtime หรือ maintenance escalation พร้อม evaluation record ชุดเดียวกัน

ขั้นตอนถัดไป → [Module 4: Financial Report Assistant](../module-4/README.md)
