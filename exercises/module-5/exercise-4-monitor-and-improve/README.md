# แบบฝึกหัดที่ 4 (Required): ใช้ Monitor และกำหนด Improvement

เราจะดู published usage บนหน้า `Monitor` ของ Copilot Studio แล้วเลือกหนึ่ง improvement จากหลักฐานที่เห็น

> **License:** ต้องมีสิทธิ์เปิด Agent และหน้า `Monitor` ใน `Copilot Studio`

> **⚠️ Note:** Conversation จาก `Test your agent` ไม่รวมในข้อมูลที่ใช้วิเคราะห์สำหรับกิจกรรมนี้ ต้องสร้าง interaction ใน published channel ข้อมูลอาจปรากฏช้าตาม tenant และไม่มีเวลารอที่รับประกัน

---

## Practice 1: สร้าง Published Usage Evidence

**Primary target:** สร้าง conversation outcomes จาก published Agent สำหรับใช้ตรวจใน Monitor

1. ใน published experience รันอย่างน้อยสี่ session:

   ```text
   1. เปรียบเทียบ quotation จากไฟล์
   2. เปรียบเทียบโดยยังไม่ให้ delivery requirement
   3. ขอให้ Agent เลือกและอนุมัติ vendor
   4. ถามคำถามนอกขอบเขต เช่น นโยบายวันลา
   ```

2. จบแต่ละ session ให้ชัดเจน
3. บันทึกเวลาที่ทดสอบและ channel ที่ใช้

### Checkpoint

- มี published conversations อย่างน้อยสี่รูปแบบ ไม่ใช่ conversation จาก test panel

---

## Practice 2: Review Monitor or Backup Evidence

**Primary target:** บันทึก observation จาก Monitor หรือ classroom fallback โดยแยกแหล่งหลักฐานชัดเจน

1. กลับ `Copilot Studio` เปิด Agent และไปที่ `Monitor`
2. เลือกช่วงเวลาที่ครอบคลุม published sessions
3. ดู conversation outcomes และ themes ที่มีให้ใน tenant
4. หากข้อมูลยังไม่ปรากฏในเวลาห้องเรียน ให้ใช้ [backup Monitor evidence](./backup-analytics-evidence.md) และระบุ `classroom fallback`
5. บันทึก:

   ```text
   Evidence source: Live Monitor / Classroom fallback
   One helpful behavior:
   One weak or confusing behavior:
   One repeated theme or outcome:
   ```

### Checkpoint

- Observation ระบุ evidence source และไม่อ้างว่าข้อมูล fallback มาจาก tenant จริง

---

## Practice 3: Define One Improvement

**Primary target:** เลือก improvement หนึ่งข้อที่เชื่อมกับ Monitor evidence และทดสอบได้

1. เติม:

   ```text
   Evidence:
   Improvement:
   Expected behavior after change:
   Retest prompt:
   Owner:
   ```

2. จัดลำดับความสำคัญโดยเลือกสิ่งที่เพิ่ม correctness, clarity หรือ boundary compliance

### Checkpoint

- มี improvement หนึ่งข้อพร้อม retest prompt และ owner

---

## Summary

คุณเปลี่ยน published usage evidence ให้เป็น improvement ที่ลงมือทดสอบต่อได้

## Microsoft Learn Reference

- [Monitor agent performance and usage](https://learn.microsoft.com/en-us/microsoft-copilot-studio/analytics-overview)

ขั้นตอนถัดไป → [Exercise 5: Pilot Decision Pack](../exercise-5-vendor-comparison-pilot-pack/README.md)
