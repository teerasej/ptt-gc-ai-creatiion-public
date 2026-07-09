# Backup Analytics Evidence

ใช้ไฟล์นี้เฉพาะเมื่อหน้า Analytics ของ Copilot Studio ยังไม่ขึ้นข้อมูลทันเวลาของคลาส แม้รัน session pack ครบแล้วและรอเกิน 15 นาที

> ⚠️ **Note:** หลักฐานในหน้านี้เป็น `classroom fallback` สำหรับการฝึกเท่านั้น ไม่ใช่ข้อมูลจริงจาก tenant ของทีมคุณ

## วิธีใช้

1. เปิดไฟล์นี้คู่กับ [Exercise 3](./README.md)
2. Review ตามลำดับเดียวกัน: `Summary` → `Overview` → `Effectiveness` → `Use`
3. จด observation ลง worksheet ทันทีหลังดูแต่ละ section
4. เขียนกำกับใน worksheet ว่า `classroom fallback`
5. ถ้าหน้า Analytics จริงขึ้นมาเพียงบางส่วน ให้ใช้ข้อมูลจริงก่อน แล้วใช้ไฟล์นี้เฉพาะส่วนที่ยังว่าง

---

## 1. Summary

### สิ่งที่เห็น

- มีการใช้งานจาก session pack ครบหลายรูปแบบ ทั้งคำถามเชิง policy, onboarding, approval boundary และคำถามกว้างๆ
- คำถามที่ตอบได้ดีที่สุดมักเป็นคำถามที่อ้างอิง knowledge ได้ตรง เช่น เอกสารที่ต้องใช้ หรือขั้นตอน procurement ที่ชัดเจน
- คำถามที่เสี่ยงอ่อนลงคือคำถามที่คาดหวังการอนุมัติแทนผู้ใช้ หรือถามกว้างเกินไปโดยไม่บอกบริบท

### ตีความได้ว่าอะไร

- Agent มีคุณค่าในฐานะตัวช่วยอธิบาย policy และ checklist
- Agent ยังต้องสื่อ scope boundary ให้คมขึ้นเมื่อผู้ใช้ขอให้ตัดสินใจหรืออนุมัติแทน

### ตัวอย่างสิ่งที่เขียนลง worksheet ได้

```text
Most common outcome: คำถามเชิง policy และขั้นตอนการทำงานมักได้รับคำตอบได้ดีกว่าคำขออนุมัติหรือคำถามกว้างๆ
One likely reason for that outcome: knowledge ที่มีอยู่สอดคล้องกับคำถามเชิงข้อมูล procurement มากกว่าคำขอที่ให้ Agent ลงมือทำแทน
```

---

## 2. Overview

### สิ่งที่เห็น

- กลุ่มคำถามหลักวนอยู่รอบเรื่อง `vendor onboarding`, `purchase approval`, และ `policy explanation`
- มีอย่างน้อย 1 session ที่จบแบบไม่ค่อยชัดเจน เพราะผู้ใช้ถามซ้ำหรือจบ conversation โดยไม่มี closure ที่ดี
- คำถามบางข้อชี้ให้เห็นว่าผู้ใช้ยังไม่แน่ใจว่า Agent ช่วย `ตอบตาม policy` หรือ `ลงมืออนุมัติ` ได้จริงแค่ไหน

### ตีความได้ว่าอะไร

- ผู้ใช้สนใจ use case ตรงกับโจทย์หลักของ Agent อยู่แล้ว
- แต่ชื่อ Agent, opening message, หรือ instruction อาจยังไม่ช่วยตั้งความคาดหวังเรื่อง scope ได้ชัดพอ

### ตัวอย่างสิ่งที่เขียนลง worksheet ได้

```text
One sign the agent is helpful: ผู้ใช้สามารถถามเรื่อง onboarding และ policy ได้ด้วยภาษาธรรมชาติ
One sign the agent is confusing or weak: ผู้ใช้บางคำถามยังคาดหวังว่า Agent จะอนุมัติหรือทำงานแทนได้
```

---

## 3. Effectiveness

### สิ่งที่เห็น

- เมื่อคำถามมี intent ชัดและอยู่ในขอบเขต knowledge เดิม Agent มีแนวโน้มตอบได้มั่นใจกว่า
- เมื่อคำถามขาดข้อมูลสำคัญ หรือเป็นคำขอที่เกิน scope เช่น `Can you approve this purchase for me?` คุณภาพคำตอบจะขึ้นอยู่กับว่า instruction กันขอบเขตไว้ดีแค่ไหน
- คำถามกว้างๆ เช่น `Can you help me do procurement faster?` มีโอกาสทำให้คำตอบหลุดไปเป็นคำแนะนำกว้างเกินไป ถ้าไม่มีการขอข้อมูลเพิ่ม

### ตีความได้ว่าอะไร

- จุดที่ควรปรับก่อนคือ instruction ที่ช่วยให้ Agent ขอข้อมูลเพิ่ม และปฏิเสธงานนอก scope อย่างสม่ำเสมอ
- จุดที่ควรทดสอบต่อคือการใส่ตัวอย่าง boundary prompt และ expected redirect ให้ชัดขึ้น

### ตัวอย่างสิ่งที่เขียนลง worksheet ได้

```text
One knowledge gap we should fix next: ควรทำให้เนื้อหาเรื่อง vendor gifts และขอบเขตการอนุมัติการจัดซื้อชัดขึ้น
One instruction change or content change we should test next: ควรเพิ่ม instruction ให้ Agent ขอข้อมูล procurement ที่ยังขาดก่อนแนะนำขั้นตอน
```

---

## 4. Use

### สิ่งที่เห็น

- Agent เหมาะกับการใช้เป็นตัวช่วยค้นข้อมูลและสรุปขั้นตอน โดยเฉพาะเวลาผู้ใช้ต้องการหาว่าเอกสารอะไรต้องใช้ หรือขั้นตอนใดมาก่อนหลัง
- Agent ยังไม่ควรถูกมองว่าเป็นตัวแทนของ approver หรือคนตัดสินใจในกระบวนการจัดซื้อ
- ถ้าเปิด pilot จริง ควรติดตามว่าผู้ใช้เข้าใจขอบเขตนี้เร็วแค่ไหน และยังถามนอก scope ซ้ำบ่อยหรือไม่

### ตีความได้ว่าอะไร

- Value proposition ของ Agent ควรสื่อให้ชัดว่าเป็น `policy assistant` ไม่ใช่ `approval bot`
- KPI ของ pilot ควรสะท้อนทั้ง usefulness และ boundary compliance

### ตัวอย่างสิ่งที่เขียนลง worksheet ได้

```text
Most common outcome: Agent มีประโยชน์มากที่สุดเมื่อใช้ตอบเรื่อง policy เอกสารที่ต้องใช้ หรือขั้นตอนถัดไป
One sign the agent is confusing or weak: ผู้ใช้บางคนยังคาดหวังให้ Agent ช่วยอนุมัติหรือดำเนินการแทน แทนที่จะเป็นการให้คำแนะนำ
```

---

## Sample Improvement Ideas

- เพิ่ม instruction ให้ Agent บอกทันทีเมื่อคำขอเป็นเรื่อง `approval` ว่าอยู่นอก scope และ redirect ไปยังขั้นตอนที่ถูกต้อง
- เพิ่ม knowledge หรือ wording ที่ช่วยตอบคำถามเรื่อง `vendor gifts` และ `onboarding prerequisites` ให้คมขึ้น
- ปรับ opening message หรือ demo introduction ให้ผู้ใช้เข้าใจตั้งแต่ต้นว่า Agent นี้มีหน้าที่ช่วยอธิบาย policy, checklist และขั้นตอน ไม่ใช่อนุมัติแทนผู้ใช้

## Student Artifact Reminder

เมื่อใช้ fallback file นี้ ผลลัพธ์ที่ต้องส่งยังเหมือนเดิม

- `Analytics page observation sheet`
- `top 3 improvement recommendations from analytics`
