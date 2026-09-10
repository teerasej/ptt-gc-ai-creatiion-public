# แบบฝึกหัดที่ 3: ตั้งค่า Suggested Prompts

เราจะเพิ่ม Suggested prompts ที่หน้า `Overview` เพื่อช่วยให้ผู้ใช้เริ่มต้นงานเปรียบเทียบได้เร็วและเข้าใจขอบเขตของ Agent

> **License:** ต้องมีสิทธิ์แก้ไข Agent ใน `Copilot Studio`

---

## Practice 1: ออกแบบ Suggested Prompts

**Primary target:** เตรียม prompt เริ่มต้นที่ครอบคลุม comparison, missing data และ scope boundary

1. เลือกข้อความสามรายการนี้ หรือปรับถ้อยคำโดยคงเจตนาเดิม:

   ```text
   เปรียบเทียบใบเสนอราคาทั้งหมดในไฟล์นี้
   ```

   ```text
   ตรวจว่าข้อมูล vendor ใดยังขาดก่อนให้คำแนะนำ
   ```

   ```text
   สรุป trade-off ด้านราคา การส่งมอบ และการรับประกัน
   ```

2. เขียน expected behavior สั้น ๆ สำหรับแต่ละ prompt ก่อนตั้งค่า

### Checkpoint

- แต่ละ prompt เริ่มต้นงานคนละมุมและไม่มี prompt ใดสั่งให้ Agent อนุมัติ vendor

---

## Practice 2: ตั้งค่าที่ Overview

**Primary target:** บันทึก Suggested prompts ให้พร้อมแสดงใน published experience

1. เปิด Agent แล้วไปที่ `Overview`
2. หา `Suggested prompts` แล้วเลือกเพิ่ม prompt ใหม่
3. ใส่ Title และ Message สำหรับทั้งสามรายการ
4. กด `Save`
5. ตรวจรายการบน `Overview`

### Checkpoint

- หน้า `Overview` แสดง Suggested prompts ครบสามรายการ

> **⚠️ Note:** Suggested prompts ไม่แสดงใน `Test your agent` ให้ตรวจซ้ำใน published experience ใน Module 5

---

## Summary

คุณได้เตรียมทางลัดให้ผู้ใช้เริ่มงานได้ชัดเจน โดย Module 5 จะตรวจว่าปรากฏหลัง publish จริง

## Microsoft Learn Reference

- [Configure suggested prompts](https://learn.microsoft.com/en-us/microsoft-copilot-studio/configure-starter-prompts)

ขั้นตอนถัดไป → [เพิ่ม Hardening และ Safe Completion](../exercise-4-hardening-and-safe-completion/README.md)
