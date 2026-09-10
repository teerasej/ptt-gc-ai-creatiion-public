# Module 2: Core Build - Vendor Comparison Assistant

Module นี้ใช้ Agent ชื่อ `PTT GC Vendor Comparison Assistant` เพื่อฝึก Core configuration, วิเคราะห์ใบเสนอราคาจำลอง, ตั้งค่า Suggested prompts และเพิ่ม reliability patterns โดย Agent มีหน้าที่ช่วยเปรียบเทียบ ไม่อนุมัติ vendor หรือการจัดซื้อแทนผู้มีอำนาจ

> **License:** ต้องมีสิทธิ์เข้าใช้ `Copilot Studio` และต้องตรวจสอบว่า tenant เปิด `File uploads` และความสามารถวิเคราะห์ structured data ก่อนเริ่มอบรม ความสามารถ chat-based code interpreter เป็น `Preview`; ใช้ไฟล์ CSV เป็น classroom fallback

## Support Files

- [Vendor quotations workbook](../../files/module-2/vendor-quotations-training.xlsx)
- [Vendor quotations CSV fallback](../../files/module-2/vendor-quotations-training.csv)
- [Mini-test log template](../../files/module-2/mini-test-log-template.xlsx)
- [Optional procurement references](../../files/module-2/README.md)

## Required Sequence

1. [Create and scope the Agent](./exercise-1-create-vendor-comparison-agent/README.md)
2. [Analyze vendor quotations](./exercise-2-analyze-vendor-quotations/README.md)
3. [Configure Suggested prompts](./exercise-3-suggested-prompts/README.md)
4. [Apply hardening and safe completion](./exercise-4-hardening-and-safe-completion/README.md)
5. [Run a mini-test and improve](./exercise-5-mini-test-and-improve/README.md)

## Learner Output

Agent ที่เปรียบเทียบราคา เงื่อนไขชำระเงิน ระยะเวลาส่งมอบ และข้อมูลที่ขาดได้ พร้อม Suggested prompts และหลักฐานการแก้ไขจาก mini-test

ขั้นตอนถัดไป → [Module 3: RAG with Operations Knowledge Assistant](../module-3/README.md)
