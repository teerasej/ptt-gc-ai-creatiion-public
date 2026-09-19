# แบบฝึกหัดที่ 2: เพิ่ม Agent-level Knowledge

เราจะเพิ่มเอกสาร operations ทั้งสี่ไฟล์ที่ระดับตัว Agent แล้วทดสอบการทำงานของ knowledge ที่สามารถดึงข้อมูลจากหลายแหล่ง ตามชุดคำถามตัวอย่าง

> **License:** ต้องมีสิทธิ์เพิ่มไฟล์เป็น `Knowledge` ใน `Copilot Studio`

## Prerequisites

- [Module 3 Knowledge files](../../../files/module-3/README.md)

---

## Practice 1: เพิ่ม Knowledge ที่ระดับ Agent

**Primary target:** เชื่อมโยงเอกสาร operations ทั้งสี่เป็น Agent-level Knowledge ที่พร้อมค้นหา

1. เปิด Agent และไปที่ `Overview` > `Knowledge` > `Add knowledge`

   ![เปิด Add knowledge จากหน้า Agent](./images/click-add-knowledge.png)

2. เลือก `Upload file` แล้วอัปโหลดไฟล์จาก `files/module-3/` ทีละไฟล์ตามตารางนี้

   | File | Knowledge source name | Description |
   |---|---|---|
   | `operations-overview.md` | `Operations Overview` | ภาพรวมการจัดการเหตุการณ์ด้าน operations และขอบเขตการให้คำแนะนำ |
   | `downtime-reporting.md` | `Downtime Reporting` | ข้อมูลที่ต้องบันทึกและขั้นตอนรายงาน unplanned downtime |
   | `maintenance-escalation.md` | `Maintenance Escalation` | ระดับ escalation สำหรับงาน maintenance และผู้ที่ต้องติดต่อ |
   | `operations-roles.md` | `Operations Roles` | บทบาทและความรับผิดชอบของผู้เกี่ยวข้องในสถานการณ์ operations |

3. สำหรับแต่ละไฟล์ ให้กำหนด `Name` และ `Description` ตามตาราง แล้วกด `Add to agent`
4. กลับไปที่หน้า `Knowledge` และทำซ้ำจนมี Knowledge sources ครบทั้งสี่รายการ
5. รอจนสถานะของทุก source เปลี่ยนจาก `In progress` เป็น `Ready` และไม่มี error
6. กด `Save`

   ![ตรวจสถานะ Knowledge หลังอัปโหลด](./images/check-knowledge-status.png)

### Checkpoint

- หน้า `Knowledge` แสดง `Operations Overview`, `Downtime Reporting`, `Maintenance Escalation` และ `Operations Roles`
- Knowledge sources ทั้งสี่มีสถานะ `Ready` และไม่มี error

---

## Practice 2: ทดสอบ Broad Retrieval

**Primary target:** ยืนยันว่า Agent-level Knowledge ตอบคำถามภาพรวมจากหลายแหล่งได้

1. เปิด `Test your agent` แล้วถาม:

   ```text
   ถ้าเกิด unplanned downtime ใครควรทำอะไรบ้างตั้งแต่เริ่มพบเหตุจนถึงการ escalation
   ```

2. ถามต่อ:

   ```text
   สรุปคำตอบเป็นบทบาท ขั้นตอน และข้อมูลที่ต้องบันทึก พร้อมบอกชื่อเอกสารที่ใช้
   ```

3. ตรวจคำตอบกับไฟล์ต้นทาง

### Checkpoint

- คำตอบรวมข้อมูลจากเอกสารที่เกี่ยวข้องโดยไม่สร้างขั้นตอนหรือบทบาทใหม่

---

## Summary

Agent ตอบคำถาม broad retrieval ได้แล้ว ต่อไปเราจะสร้าง Topic เพื่อเก็บ intent และตัวแปรก่อนเลือกแหล่งข้อมูลเฉพาะ

ขั้นตอนถัดไป → [สร้าง Topics, Questions, Variables, and Conditions](../exercise-3-topics-questions-variables-conditions/README.md)
