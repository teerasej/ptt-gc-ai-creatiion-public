# Module 2: Core Build - Vendor Comparison Assistant

Module นี้พลจะพาเรามาสร้าง Agent ชื่อ `PTT GC Vendor Comparison Assistant` เพื่อเรียนรู้การปรับแต่งการตั้งค่า Core configuration, เปรียบเทียบใบเสนอราคา PDF จาก Vendor 3 ราย, ตั้งค่า Suggested prompts และเพิ่ม reliability patterns โดย Agent มีหน้าที่ช่วยเปรียบเทียบ ไม่อนุมัติ Vendor หรือการจัดซื้อแทนผู้มีอำนาจ

> **License:** ต้องมีสิทธิ์เข้าใช้ `Copilot Studio` และต้องตรวจสอบว่า Environment เปิด `File uploads` ก่อนเริ่มอบรม

## Sample Files

- [ดาวน์โหลดไฟล์ประกอบทั้งหมด (.zip)](https://raw.githubusercontent.com/teerasej/ptt-gc-ai-creatiion-public/main/files/module-2/module-2-support-files.zip)

ไฟล์แยกรายการ:

- [Alpha Industrial quotation](../../files/module-2/vendor-quotation-alpha-industrial.pdf)
- [Beta Engineering quotation](../../files/module-2/vendor-quotation-beta-engineering.pdf)
- [Gamma Supply quotation](../../files/module-2/vendor-quotation-gamma-supply.pdf)
- [Mini-test log template](../../files/module-2/mini-test-log-template.xlsx)
- [Optional procurement references](../../files/module-2/README.md)

## Required Sequence

1. [Create and scope the Agent](./exercise-1-create-vendor-comparison-agent/README.md)
2. [Analyze vendor quotations](./exercise-2-analyze-vendor-quotations/README.md)
3. [Configure Suggested prompts](./exercise-3-suggested-prompts/README.md)
4. [Apply hardening and safe completion](./exercise-4-hardening-and-safe-completion/README.md)
5. [Run a mini-test and improve](./exercise-5-mini-test-and-improve/README.md)

## Learner Output

Agent ที่เปรียบเทียบราคา เงื่อนไขชำระเงิน ระยะเวลาส่งมอบ การรับประกัน และข้อมูลที่ต้องยืนยันจาก PDF หลายฉบับได้ พร้อม Suggested prompts และหลักฐานการแก้ไขจาก mini-test

ขั้นตอนถัดไป → [Module 3: RAG with Operations Knowledge Assistant](../module-3/README.md)
