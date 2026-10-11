# Module 4: From Email Tools to Financial Report Workflows

เราจะสร้าง `Financial Report Assistant` หนึ่งตัว แล้วค่อย ๆ เพิ่มความสามารถจากการส่งอีเมล ไปสู่การสรุป Excel และการบันทึกสรุปพร้อมส่ง notification ด้วย `Agent Flow`

ใช้ **Standard harness** และ **generative orchestration**  โดยเพิ่ม Tools ที่ระดับ Agent ไม่ต้องสร้าง custom Topic ใหม่

> **License:** ต้องมีสิทธิ์ใช้ `Copilot Studio` แบบ standalone หรือสิทธิ์องค์กรที่รองรับการเรียนนี้ พร้อม Outlook mailbox, `OneDrive for Business` และสิทธิ์สร้าง/publish `Agent Flow` ความสามารถ `Prompt` และ `Code interpreter` อาจใช้ Copilot Credits ตาม entitlement ของ environment ต้องตรวจสอบก่อนเรียน ไม่ใช่กิจกรรมที่รับรองว่าฟรีทุกบัญชี


## Before You Begin

- ใช้บัญชีฝึกอบรมของตนเองและข้อมูลจำลองเท่านั้น ทดสอบส่งอีเมลถึง mailbox ฝึกอบรมของตนเอง
- เข้า classic experience สำหรับ **Standard harness** 
- ใช้ Agent ตัวใหม่ของ Module นี้ ไม่เพิ่ม Tools ลง Agent จาก Module 2 หรือ Module 3
- ต้องมี connection ของ `Office 365 Outlook` และ `OneDrive for Business` ที่ใช้บัญชีของผู้เรียนเอง
- Exercise 2 ใช้ File input เท่านั้น ต้องผ่าน rehearsal ของ `Code interpreter` และ attachment mapping ผ่าน Agent หากติดข้อจำกัด ให้บันทึก `Environment blocked` และหยุด Exercise 2–3 จนกว่าผู้สอนจะแก้ไขและทดสอบผ่าน

## Main Sequence

1. [สร้าง Agent และส่งอีเมลด้วย Outlook Tool](./exercise-1-create-agent-and-send-email/README.md)
2. [สรุป Excel ด้วย Prompt Tool](./exercise-2-summarize-excel-with-prompt-tool/README.md)
3. [บันทึกสรุปและส่ง Notification ด้วย Agent Flow](./exercise-3-archive-summary-and-notify/README.md)

> **💡 Tip:** Tool ช่วงเช้าเหมือนฝากผู้ช่วยไปส่งจดหมายหนึ่งฉบับ ส่วน Flow ช่วงบ่ายเหมือนให้ checklist ว่า “เก็บรายงานเข้าตู้ → ส่งข้อความแจ้ง → บอกผลกลับ” `Dynamic content` คือข้อมูลที่ส่งต่อจากช่องหนึ่งไปยังอีกขั้นตอน โดยไม่ต้องพิมพ์ค่าซ้ำ

## Support Files

- [Financial workbook](../../files/module-4/PTT-Monthly-Financial-Report-May2026.xlsx)
- [Test-results template](../../files/module-4/module-4-test-results-template.md)
- [Support guide](../../files/module-4/README.md)

## Optional Advanced Topic Route

[เปิดเส้นทางเดิมสำหรับฝึก Topics, variables และ review loop](./optional-topic-route/README.md) เส้นทางนี้เริ่มจาก Agent อีกตัว มี prerequisites ของตนเอง และไม่จำเป็นต้องทำก่อน Exercise 1–3 ของเส้นทางหลัก

กิจกรรม [Optional Work IQ Mail MCP](./exercise-6-optional-work-iq-mail-mcp/README.md) เป็นเนื้อหาเสริมเดิม ต้องตรวจ harness และ Preview availability แยกต่างหาก ไม่ใช่ส่วนหนึ่งของเส้นทางหลักหรือ prerequisite ของ Module 5

## Learner Output

`Financial Report Assistant` ที่ส่งอีเมลแบบ review ก่อนส่ง สรุป workbook ที่แนบผ่าน File input และใช้ Flow บันทึกข้อความที่ยืนยันแล้วพร้อมส่ง notification โดยมี test record แสดงผลที่สังเกตได้จริง

ผล static checks ของเอกสารไม่ใช่หลักฐานว่า connection, Prompt file input หรือ Flow ทำงานใน tenant แล้ว ต้อง rehearsal แยกก่อนใช้ในห้องเรียน

## Summary

คุณจะได้ฝึกความต่างของ Connector Tool, Prompt Tool และ Agent Flow โดยใช้สถานการณ์รายงานการเงินเดียวกัน

ขั้นตอนถัดไป → [Module 5](../module-5/README.md) ซึ่งกลับไปใช้ Vendor Comparison Agent จาก Module 2 ตามเส้นทางเดิม
