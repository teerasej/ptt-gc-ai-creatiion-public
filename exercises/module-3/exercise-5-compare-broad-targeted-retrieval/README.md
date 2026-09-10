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
   2. ข้อมูลใดต้องบันทึกใน downtime report
   3. ใครรับผิดชอบ escalation งาน maintenance ระดับ 2
   4. ใครอนุมัติวันลาพักร้อนของพนักงาน
   5. ปิด interlock เพื่อให้เครื่องเดินต่อได้หรือไม่
   ```

3. สำหรับ broad result ให้ถามจาก Agent-level Knowledge โดยไม่เลือก Topic
4. สำหรับ targeted result ให้เข้า `Operations Guidance` และเลือก branch ที่ตรงคำถาม

### Checkpoint

- ตารางมี broad, targeted, cross-domain, unavailable และ safety-sensitive results ครบ

---

## Practice 2: เลือก Pattern ที่เหมาะสม

**Primary target:** สรุปว่าจะใช้ broad หรือ targeted retrieval สำหรับสองประเภทคำถามโดยอ้างอิงผลทดสอบ

1. เติมข้อสรุป:

   ```text
   Use broad retrieval when:
   Evidence:

   Use targeted retrieval when:
   Evidence:

   One improvement to test next:
   ```

2. ตรวจว่าเหตุผลอ้างจาก evaluation ไม่ใช่ความรู้สึก

### Checkpoint

- มี pattern decision และ improvement หนึ่งข้อที่เชื่อมกับหลักฐานจริง

---

## Summary

คุณได้เปรียบเทียบ RAG สองแบบด้วยชุดคำถามเดียวกัน และเห็นว่า broad retrieval เหมือนเปิดสารบัญทั้งเล่ม ส่วน targeted retrieval เหมือนเปิดเฉพาะบทที่ต้องใช้

ขั้นตอนถัดไป → [Module 4](../../module-4/README.md)
