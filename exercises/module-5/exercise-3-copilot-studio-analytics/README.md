# แบบฝึกหัดที่ 3: ใช้ Copilot Studio Analytics เพื่อหา Improvement Ideas

🔑 **ต้องการ M365 Copilot License + สิทธิ์เข้าใช้ Copilot Studio + published Agent ที่มีการใช้งานจริงใน Microsoft 365 Copilot**

แบบฝึกหัดนี้จะให้เราใช้ **Agent ตัวเดิมจาก Exercise 1-2** มาดูหน้า Analytics ของ Copilot Studio เพื่อแปลข้อมูลการใช้งานจริงให้กลายเป็นข้อเสนอปรับปรุงที่ชัดเจน ไม่ใช่ดูแค่ว่า Agent ถูกใช้หรือไม่ แต่ต้องเริ่มตอบให้ได้ว่าควรปรับตรงไหนก่อน


---

## Important Notes Before Practice

- session ที่เกิดใน **Test your agent** panel จะไม่ขึ้นใน Analytics
- `Microsoft 365 Copilot` ไม่รองรับ reaction ในรูปแบบเดียวกับบาง channel อื่น
- สำหรับ Exercise นี้ ให้ใช้ published conversation ใน **Microsoft 365 Copilot** เป็น data source หลัก
- Analytics อาจใช้เวลา 5-15 นาทีจึงเริ่มเห็นผล และในบางครั้งอาจช้ากว่านั้นได้แม้รัน session ครบแล้ว

> ⚠️ **Note:** ถ้ารอเกิน 15 นาทีแล้วยังไม่เห็นข้อมูลในหน้า Analytics ให้ใช้ [backup analytics evidence](./backup-analytics-evidence.md) แทน โดยยังคงใช้ worksheet และวิธีคิดชุดเดียวกัน

---

## Practice 1: สร้าง Published Usage Data ด้วย Session Pack เดียวกัน

1. เปิด Agent `PTT GC Procurement Policy Assistant` ที่ publish แล้วใน **Microsoft 365 Copilot**
2. รัน session pack นี้ให้ครบ

   ```text
   Session 1: What documents are required to register a new vendor?
   Session 2: What approval is needed for a THB 180,000 purchase?
   Session 3: Summarize emergency purchase steps.
   Session 4: Can you approve this purchase for me?
   Session 5: I only have the vendor name. Can I start onboarding?
   Session 6: What is the policy for vendor gifts?
   Session 7: Can you help me do procurement faster?
   Session 8: Ask a repeated question and end the session without clear closure.
   ```

3. หากทำงานเป็นทีม ให้แบ่งกันรันหลาย session แต่ต้องใช้ข้อความตามนี้ตรงๆ
4. รอให้ข้อมูล analytics เริ่มปรากฏ โดยใช้กติกานี้

   - รออย่างน้อย 5 นาทีหลังรัน session pack ครบ
   - กลับไป refresh หน้า **Analytics** ทุก 2-3 นาที
   - ตรวจว่า reporting period ครอบคลุมช่วงเวลาที่เพิ่งรัน session pack
   - ถ้าเกิน 15 นาทีแล้วยังไม่เห็นข้อมูลใน `Summary` หรือ tab อื่นยังว่าง ให้สลับไปใช้ [backup analytics evidence](./backup-analytics-evidence.md)

> 💡 Tip: ถ้าข้อมูลขึ้นมาเพียงบางส่วน ให้ใช้ข้อมูลจริงก่อนในส่วนที่เห็น แล้วค่อยใช้ backup evidence เฉพาะ section ที่ยังว่าง

---

## Practice 2: เปิด Analytics และ Review ตามลำดับเดียวกัน

1. กลับไปที่ Copilot Studio
2. เปิด Agent เดิม
3. ไปที่หน้า **Analytics**
4. ตั้ง reporting period ให้ครอบคลุมช่วงเวลาที่เพิ่งรัน session pack
5. เลือกวิธี review แบบใดแบบหนึ่ง

   - ถ้าข้อมูลขึ้นแล้ว ให้ review จากหน้า **Analytics** จริง
   - ถ้าข้อมูลยังไม่ขึ้นทันเวลา ให้เปิด [backup analytics evidence](./backup-analytics-evidence.md)

6. Review ตามลำดับนี้เท่านั้น

   ```text
   1. Summary
   2. Overview
   3. Effectiveness
   4. Use
   ```

7. ระหว่างดูแต่ละส่วน ให้จดสิ่งที่เห็นลง worksheet ทันที อย่ารอให้ดูครบทุก section ก่อน

> ⚠️ **Note:** ถ้าคุณใช้ backup evidence ให้จดกำกับไว้สั้นๆ ใน worksheet ว่าเป็น `classroom fallback` เพื่อให้ทีมจำได้ว่าไม่ได้มาจาก tenant ของตัวเอง

> 💡 Tip: จุดประสงค์ของ Exercise นี้ไม่ใช่จำทุก metric แต่คือฝึกแปลสิ่งที่หน้า Analytics แสดงออกมาเป็นคำถามว่า “Agent มีประโยชน์ตรงไหน” และ “Agent ยังสับสนตรงไหน”

---

## Practice 3: เติม Interpretation Worksheet และเทียบกับตัวอย่างแบบง่าย

ใช้ worksheet นี้สรุปสิ่งที่สังเกตได้

```text
Most common outcome:
One likely reason for that outcome:
One sign the agent is helpful:
One sign the agent is confusing or weak:
One knowledge gap we should fix next:
One instruction change or content change we should test next:
```

ถ้าคุณยังไม่แน่ใจว่าควรสรุปประมาณไหน ให้ดูตัวอย่าง worksheet แบบง่ายนี้ได้เลย

```text
Most common outcome: ผู้ใช้ส่วนใหญ่ถามเกี่ยวกับเอกสารที่ต้องใช้ และเงื่อนไขการอนุมัติ
One likely reason for that outcome: คำถามเหล่านี้ตรงกับขอบเขต knowledge ด้าน procurement ที่ Agent มีอยู่แล้วค่อนข้างดี
One sign the agent is helpful: Agent สามารถอธิบายเอกสาร onboarding และลำดับขั้นตอนถัดไปได้ค่อนข้างชัดเจน
One sign the agent is confusing or weak: ผู้ใช้บางคนยังคาดหวังให้ Agent อนุมัติการจัดซื้อแทนได้
One knowledge gap we should fix next: คำตอบเกี่ยวกับ vendor gifts ยังไม่ชัดพอ
One instruction change or content change we should test next: ควรเพิ่ม instruction ให้ Agent ขอข้อมูลที่ยังขาดก่อนตอบคำถามเชิงกระบวนการ
```

> 💡 Tip: ตัวอย่างนี้ตั้งใจทำให้อ่านง่ายและตีความตรงไปตรงมา เพื่อให้เห็นวิธีแปลง observation ไปเป็น conclusion โดยไม่ต้องเจอ data ที่ซับซ้อนเกินไป

---

## Practice 4: ลองประเมินและเสนอ Improvement Ideas จาก Worksheet

เมื่อเติม worksheet ของตัวเองแล้ว หรือถ้าจำเป็นให้ใช้ตัวอย่างด้านบนเป็นตัวตั้ง ให้เขียน improvement ideas  ข้อ โดยอ้างจากสิ่งที่เห็นจริงใน worksheet

ตัวอย่างแนวคำตอบที่ควรได้ เช่น

- เพิ่ม instruction ให้บอกข้อมูลที่ยังขาดก่อนตอบ
- เพิ่ม knowledge เรื่อง vendor gifts เพราะมีคำถามขึ้นมาแล้วตอบได้ไม่ชัด
- ปรับ demo flow ให้มีคำถามที่โชว์ scope boundary ชัดขึ้น

ถ้าใช้ backup evidence ก็ยังให้เขียน improvement ideas  ตามหลักฐานในไฟล์นั้นได้เลย และถ้าข้อมูลจริงยังน้อยมาก สามารถใช้ sample worksheet ด้านบนเป็นตัวอย่างอ้างอิงเพื่อฝึกการคิดก่อน แล้วค่อยกลับมาเทียบกับข้อมูลจริงของทีม

เป้าหมายของ Practice นี้คือฝึกการตีความและจัดลำดับสิ่งที่ควรปรับ ไม่ใช่รอให้ทุกห้องได้ data สดพร้อมกัน

---

## Student Artifact

- `Analytics page observation sheet`
- `top 3 improvement recommendations from analytics`

---

## Summary

ในแบบฝึกหัดนี้ คุณได้ใช้ published conversation ของ Agent ใน Microsoft 365 Copilot เพื่ออ่านหน้า Analytics อย่างเป็นระบบ แล้วเปลี่ยนข้อมูล usage ให้กลายเป็นข้อเสนอปรับปรุงที่นำไปใช้ต่อได้จริง

ขั้นตอนถัดไป → [สรุปความพร้อมด้วย Pilot Decision Pack](../exercise-4-pilot-decision-pack/README.md)