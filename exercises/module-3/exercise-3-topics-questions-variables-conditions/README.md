# แบบฝึกหัดที่ 3: สร้าง Topics, Questions, Variables, and Conditions

เราจะสร้าง Topic ชื่อ `Operations Guidance` เพื่อถามประเภทคำขอและ route ผู้ใช้ไปยัง downtime หรือ maintenance branch

> **License:** ต้องมีสิทธิ์แก้ไข `Topics` ใน `Copilot Studio`

```mermaid
flowchart LR
    A[Operations question] --> B[Ask guidance type]
    B --> C[Save GuidanceType]
   C --> D[Ask full question]
   D --> E[Save GuidanceQuestion]
   E --> F{Condition}
   F -->|Downtime| G[Downtime branch]
   F -->|Maintenance| H[Maintenance branch]
   F -->|Other| I[Ask user to clarify]
```

---

## Practice 1: สร้าง Topic และเก็บตัวแปร

**Primary target:** สร้าง Topic ที่บันทึกประเภทคำขอใน `GuidanceType` และคำถามฉบับเต็มใน `GuidanceQuestion`

1. ไปที่ `Topics` > `Add a topic` > `From blank`
2. ตั้งชื่อ `Operations Guidance`
3. กำหนด Trigger description:

   ```text
   Use this topic when the user asks for operations guidance about downtime reporting or maintenance escalation.
   ```

4. เพิ่ม `Question` node:

   ```text
   ต้องการข้อมูลด้าน Downtime reporting หรือ Maintenance escalation ครับ
   ```

5. ใช้ multiple-choice options `Downtime reporting`, `Maintenance escalation`, `Other` และบันทึกเป็น `GuidanceType`
6. ใต้ Question แรก เพิ่ม `Question` node อีกหนึ่ง node แล้วใส่ข้อความ:

   ```text
   กรุณาระบุคำถามหรือเหตุการณ์ที่ต้องการทราบ
   ```

7. ตั้ง `Identify` เป็น `User's entire response` และบันทึกคำตอบเป็นตัวแปร `GuidanceQuestion`

### Checkpoint

- Topic รับคำตอบและบันทึกค่า `GuidanceType` ได้
- Topic บันทึกคำถามฉบับเต็มของผู้ใช้ใน `GuidanceQuestion` โดยไม่แทนที่ด้วยค่าจากตัวเลือก

---

## Practice 2: Route ด้วย Condition

**Primary target:** สร้าง Condition ที่แยกผู้ใช้ไปยังสาม branch ตาม `GuidanceType`

1. เพิ่ม `Condition` node ใต้ Question ที่บันทึก `GuidanceQuestion`
2. สร้าง branch สำหรับ `Downtime reporting` และ `Maintenance escalation`
3. ใน `All other conditions` เพิ่ม Message:

   ```text
   กรุณาบอกเหตุการณ์หรือขั้นตอนที่ต้องการทราบเพิ่มเติม
   ```

4. กด `Save` และทดสอบทั้งสามตัวเลือก โดยป้อนคำถามฉบับเต็มหลังเลือกประเภทคำขอ

### Checkpoint

- แต่ละตัวเลือกไปยัง branch ที่กำหนด
- ตัวแปร `GuidanceQuestion` แสดงคำถามฉบับเต็มที่ผู้ใช้ป้อน และไม่มี branch ใดตอบจาก Knowledge ที่ยังไม่ได้เลือก

---

## Summary

คุณสร้างโครง Topic ที่พร้อมเชื่อม targeted Generative answers ใน Exercise 4

ขั้นตอนถัดไป → [สร้าง Targeted Generative Answers](../exercise-4-targeted-generative-answers/README.md)
