# Module 4: Topics, Prompt, Tools, and Agent Flow

Module นี้ใช้ `Financial Report Assistant` เพื่อฝึก workflow ที่รับข้อมูล วิเคราะห์ workbook ให้ผู้ใช้ review และส่งอีเมลผ่าน `Agent Flow` อย่างควบคุมได้

> **License:** ต้องมีสิทธิ์เข้าใช้ `Copilot Studio`, สร้างและ publish `Agent Flow`, ใช้ connection ของ `Office 365 Outlook`, และเรียก `Send an email (V2)` ความพร้อมของ `Prompt` file input ต้องตรวจสอบก่อนเริ่มอบรม

## Support Files

- [Financial workbook](../../files/module-4/PTT-Monthly-Financial-Report-May2026.xlsx)
- [Financial terminology](../../files/module-4/financial-report-technical-terms-knowledge.docx)
- [Distribution policy](../../files/module-4/financial-report-distribution-policy-knowledge.docx)

## Required Sequence

1. [Create the Financial Agent and intake Topic](./exercise-1-create-financial-agent-and-intake/README.md)
2. [Analyze one workbook through a Prompt](./exercise-2-analyze-financial-workbook/README.md)
3. [Review, revise, and confirm](./exercise-3-review-revise-confirm/README.md)
4. [Build the required Agent Flow email](./exercise-4-required-agent-flow-email/README.md)
5. [Test email paths](./exercise-5-test-email-paths/README.md)

## Optional Route

6. [Optional - Work IQ Mail MCP](./exercise-6-optional-work-iq-mail-mcp/README.md) เพื่อเปรียบเทียบ Preview MCP route กับ Agent Flow ไม่ใช่ prerequisite ของ Module 5

> **⚠️ Note:** ระหว่างทดสอบให้เปิดใช้งานเส้นทางส่งอีเมลเพียงเส้นทางเดียว เพื่อป้องกันการส่งซ้ำ

## Learner Output

Financial Report Assistant ที่รับ request, วิเคราะห์ workbook, รองรับ revision และส่งอีเมลหนึ่งครั้งหลังผู้ใช้ยืนยัน

ขั้นตอนถัดไป → [Optional Module 3.5 review](../module-3-5/README.md) หรือไปที่ [Module 5](../module-5/README.md)
