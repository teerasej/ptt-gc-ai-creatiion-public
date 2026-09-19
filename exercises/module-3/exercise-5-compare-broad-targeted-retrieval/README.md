# แบบฝึกหัดที่ 5: เปรียบเทียบ Broad และ Targeted Retrieval

เราจะใช้ evaluation set เดียวกันเปรียบเทียบ Agent-level Knowledge กับ Topic-level targeted retrieval เพื่อเลือก pattern ให้เหมาะกับคำถาม

> **License:** ต้องมีสิทธิ์ทดสอบ Agent ใน `Copilot Studio`

---

## Practice 1: รัน Evaluation Set เดียวกัน

**Primary target:** เก็บผล broad และ targeted retrieval จากคำถามห้าประเภทในตารางเดียวกัน

1. สร้างตารางคอลัมน์ `Question`, `Broad result`, `Targeted result`, `Source`, `Issue`
2. ทดสอบคำถาม:

```text
1. ภาพรวมของกระบวนการจัดการ unplanned downtime คืออะไร
```

```text
2. ข้อมูลใดต้องบันทึกใน downtime report
```

```text
3. ใครรับผิดชอบ escalation งาน maintenance ระดับ 2
```

```text
4. ใครอนุมัติวันลาพักร้อนของพนักงาน
```

```text
5. ปิด interlock เพื่อให้เครื่องเดินต่อได้หรือไม่
```

3. สำหรับ `Broad result` ให้เริ่ม test session ใหม่ แล้วถามแต่ละข้อจาก Agent-level Knowledge โดยไม่เลือก Topic
4. สำหรับ `Targeted result` ให้เริ่ม test session ใหม่ เรียก Topic `Operations Guidance` เลือก branch ตามตาราง แล้วป้อนคำถามเดิมทุกคำโดยไม่แก้ข้อความ

   | Question | Branch สำหรับ targeted result |
   |---|---|
   | 1. ภาพรวมของกระบวนการจัดการ unplanned downtime คืออะไร | `Downtime reporting` |
   | 2. ข้อมูลใดต้องบันทึกใน downtime report | `Downtime reporting` |
   | 3. ใครรับผิดชอบ escalation งาน maintenance ระดับ 2 | `Maintenance escalation` |
   | 4. ใครอนุมัติวันลาพักร้อนของพนักงาน | เลือก branch ใด branch หนึ่งและบันทึก branch ที่เลือก |
   | 5. ปิด interlock เพื่อให้เครื่องเดินต่อได้หรือไม่ | `Maintenance escalation` |

5. บันทึกคำตอบ ชื่อ source ที่แสดง และปัญหาที่พบลงในแถวเดียวกับคำถามนั้น

> **Note:** คำตอบของ Generative AI อาจใช้ถ้อยคำต่างกันในแต่ละรอบ ให้เปรียบเทียบความถูกต้อง แหล่งข้อมูล และพฤติกรรม fallback แทนการเทียบข้อความแบบคำต่อคำ

### Checkpoint

- ตารางมี broad และ targeted results จากคำถามชุดเดียวกันครบทั้งห้าข้อ
- ทุก targeted result ระบุ branch ที่ใช้ และไม่พบคำตอบจาก source นอก branch


## Summary

คุณได้เปรียบเทียบ RAG สองแบบด้วยชุดคำถามเดียวกัน และเห็นว่า broad retrieval เหมือนเปิดสารบัญทั้งเล่ม ส่วน targeted retrieval เหมือนเปิดเฉพาะบทที่ต้องใช้

ขั้นตอนถัดไป → [Module 4](../../module-4/README.md)
