# แบบฝึกหัดที่ 1 (Optional): Trustworthy Answers and UX Tune-up

กิจกรรมเสริมนี้ใช้ `PTT GC Vendor Comparison Assistant` จาก Module 2 เพื่อปรับ opening message, response structure และ boundary wording ก่อน publish

> **License:** ต้องมีสิทธิ์แก้ไข Agent ใน `Copilot Studio`

> **⚠️ Note:** Exercise นี้ไม่ใช่ prerequisite ผู้เรียนสามารถเริ่ม required path ที่ Exercise 2 ได้ทันที

---

## Practice 1: ปรับ UX โดยไม่เปลี่ยน Scope

**Primary target:** ปรับ response structure ให้ผู้ใช้เห็น facts, gaps และ decision boundary ง่ายขึ้น

1. เปิด Agent จาก Module 2 และสำรอง Instructions เดิมไว้ในบันทึกส่วนตัว
2. เพิ่มรูปแบบคำตอบ:

   ```text
   Start with a one-sentence purpose reminder.
   Present verified facts in a compact comparison table.
   Put Missing information before Recommendation.
   End recommendations with: "Final vendor selection remains with the authorized procurement owner."
   ```

3. ทดสอบด้วยไฟล์ CSV จาก Module 2
4. ถ้าคำตอบยาวขึ้นแต่ไม่ชัดขึ้น ให้ย้อนกลับเฉพาะการแก้ไขนั้น

### Checkpoint

- คำตอบอ่านง่ายขึ้นและยังไม่เพิ่มอำนาจอนุมัติหรือข้อมูลใหม่

---

## Summary

คุณปรับ UX เพิ่มเติมแล้ว หรือสามารถข้าม Exercise นี้และไปยัง readiness checks ที่รวม minimum requirements ครบ

ขั้นตอนถัดไป → [Exercise 2: Readiness, Publish, Install, and Access](../exercise-2-final-mvp-demo-rehearsal/README.md)
