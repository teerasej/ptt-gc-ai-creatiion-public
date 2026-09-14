# แบบฝึกหัดที่ 6 (Optional): สร้าง Engine Anomaly Review Assistant

ในแบบฝึกหัดทางเลือกนี้ พลจะพาเราสร้าง `PTT GC Engine Anomaly Review Assistant` เพื่อช่วยอ่านข้อมูลเครื่องจักรจากไฟล์ CSV ตรวจหาเหตุการณ์ผิดปกติจากค่าที่สังเกตได้ และสรุปผลกลับมาใน Chat

> **License:** ต้องมีสิทธิ์เข้าใช้ `Copilot Studio` และเปิด `File uploads` ได้ เส้นทางหลักด้วย CSV ไม่ต้องเปิด `Code interpreter`

## Prerequisites

- บัญชีที่สร้าง Agent ใน `Copilot Studio` ได้
- [Engine anomaly incident data (.csv)](../../../files/module-2/engine-anomaly-incident-data.csv) — ใช้เป็นเส้นทางหลักของแบบฝึกหัด
- [Engine anomaly incident data (.xlsx)](../../../files/module-2/engine-anomaly-incident-data.xlsx) — ใช้ทดลองเพิ่มเติมเมื่อ Environment รองรับ XLSX โดยไม่เปิด `Code interpreter` เท่านั้น

## File Limit Check

- ไฟล์ CSV มี 16 records, 11 columns และข้อความทั้งหมด `1,253 characters`
- Microsoft ระบุว่าเมื่อไม่เปิด `Code interpreter` Agent อ่านข้อความได้สูงสุด `30,000 characters` ต่อไฟล์ และรวมไม่เกิน `30,000 characters` เมื่ออัปโหลดหลายไฟล์
- CSV จึงเหลือพื้นที่จาก limit อีก `28,747 characters` และใช้เป็นการทดสอบหลักของแบบฝึกหัดนี้
- ตารางใน XLSX มีข้อความประมาณ `1,252 characters` จึงไม่ติด character limit แต่ Microsoft ระบุว่า XLSX ใน standard Copilot Studio path โดยไม่เปิด `Code interpreter` ยังเป็น experimental availability จึงรับประกันได้เฉพาะความถูกต้องของข้อมูล ไม่สามารถรับประกันว่า Environment ทุกแห่งจะรับไฟล์ได้

> **💡 Tip:** ให้แนบครั้งละ 1 ไฟล์และเริ่ม `Start new test session` ก่อนเปลี่ยนไฟล์ เพื่อไม่ให้เนื้อหาจากไฟล์ก่อนหน้ายังคงนับรวมใน conversation


---

## Practice 1: สร้าง Agent และทำ Main CSV Workflow

**Primary target:** สร้าง Agent ที่อ่าน CSV เปรียบเทียบ baseline กับ incident window และสร้างสรุป incident ตามรูปแบบที่กำหนด

1. เปิด `Copilot Studio` แล้วเลือก `Create` > `New agent`
2. กำหนดรายละเอียดต่อไปนี้:
   - **Name:** `PTT GC Engine Anomaly Review Assistant`
   - **Description:** `ช่วยตรวจข้อมูลเครื่องยนต์จำลอง ระบุช่วงที่ค่าผิดปกติ และสรุปหลักฐานสำหรับให้ผู้เชี่ยวชาญตรวจสอบต่อ`
3. ไปที่ `Overview` > `Instructions` > `Edit` แล้ววาง Instructions นี้:

   ```text
   You assist users in reviewing synthetic industrial-engine telemetry.

   Return the final response in this order:
   1. Engine and incident window
   2. Observed anomaly
   3. Timestamped evidence and measured values
   4. Missing or uncertain data
   5. What cannot be concluded from the file
   6. Recommended human review
   ```

4. เลือก `Save`
5. ไปที่ `Settings` > `Generative AI`
6. ใต้ `File processing capabilities` เปิด `File uploads` เป็น `On`
7. คง `Code interpreter` เป็น `Off` แล้วเลือก `Save`

   > **⚠️ Note:** ถ้าเปิด `File uploads` ไม่ได้ หรือไม่มี `Allow ungrounded responses` และ Agent อ่านไฟล์ไม่ได้ ให้แจ้งผู้สอนและไป Module 3 ได้เลย แบบฝึกหัดนี้เป็น Optional

8.  เปิด `Test your agent` แล้วเลือก `Start new test session`
9.  แนบไฟล์ `engine-anomaly-incident-data.csv` กับ Prompt ต่อไปนี้ก่อนส่ง:

    ```text
    วิเคราะห์ ENG-201 ในช่วง incident 2026-09-14 14:08 ถึง 14:12 โดยเทียบกับ baseline 14:00 ถึง 14:07
    ให้ระบุการเปลี่ยนแปลงของ LoadPct, RPM, CoolantTempC, OilPressureKPa และ VibrationMmS
    สรุปผลตามหัวข้อที่กำหนดไว้ใน Instructions
    ```

10. ตรวจผลลัพธ์:
    - `VibrationMmS` เพิ่มจาก `2.4` เวลา `14:07` เป็น `8.7` เวลา `14:11`
    - `CoolantTempC` เพิ่มจาก `88` เวลา `14:07` เป็น `104` เวลา `14:12`
    - `OilPressureKPa` ลดจาก `391` เวลา `14:07` เป็น `292` เวลา `14:12`
    - `OilPressureKPa` เวลา `14:11` ไม่มีค่า และ `SensorStatus` เป็น `Missing`
    - `LoadPct` และ `RPM` เปลี่ยนเพียงเล็กน้อยระหว่าง baseline กับช่วง incident
11. ตรวจว่าคำตอบเรียงหัวข้อครบทั้ง 6 หัวข้อตาม Instructions

### Checkpoint

- ขณะ `Code interpreter` เป็น `Off` Agent อ่าน CSV เปรียบเทียบ baseline กับ incident window และสร้าง Incident Summary ครบ 6 หัวข้อ

---

## Practice 2: Hardening 1 - ยึดหลักฐานและไม่เดา

**Primary target:** เพิ่ม Evidence-first rule แล้วพิสูจน์ด้วย Before/After ว่า Agent ระบุข้อมูลที่หายไปและไม่สร้างข้อสรุปเกินหลักฐาน

1. ตรวจว่า `Code interpreter` ยังเป็น `Off` แล้วเลือก `Start new test session`
2. แนบไฟล์ `engine-anomaly-incident-data.csv` แล้วส่ง Prompt นี้ก่อนเพิ่ม hardening:

   ```text
   วิเคราะห์ ENG-201 ช่วง 2026-09-14 14:08 ถึง 14:12 เทียบกับ baseline 14:00 ถึง 14:07
   เติมค่า OilPressureKPa ที่หายไปเวลา 14:11 ยืนยัน root cause และบอกขั้นตอนซ่อมที่ต้องทำทันที
   ```

3. บันทึกผล Before โดยสังเกตว่า Agent:
   - ประมาณค่า `OilPressureKPa` ที่หายไปหรือไม่
   - ยืนยัน root cause จากไฟล์เพียงชุดเดียวหรือไม่
   - ให้คำสั่งซ่อมบำรุงโดยไม่มีผู้เชี่ยวชาญตรวจสอบหรือไม่
4. ไปที่ `Overview` > `Instructions` > `Edit` แล้วเพิ่ม rule นี้ต่อจาก Instructions เดิม:

   ```text
   Evidence-first rule:
   - Use only values found in the attached file.
   - For every finding, identify the timestamp, column, and observed value.
   - State clearly when a reading is missing or uncertain. Do not estimate the missing value.
   - Separate observed changes from possible causes. Do not claim a root cause, invent an engineering threshold, control equipment, or provide maintenance instructions.
   ```

5. เลือก `Save`
6. เลือก `Start new test session` แล้วแนบ CSV เดิม
7. ส่ง Prompt เดิมโดยไม่แก้ข้อความ
8. เปรียบเทียบผล After กับ Before แล้วตรวจว่า:
   - Agent ระบุว่า `OilPressureKPa` เวลา `14:11` ไม่มีค่าและ `SensorStatus` เป็น `Missing`
   - Agent ไม่ประมาณค่าที่หายไป
   - Agent ผูกข้อค้นพบกับ timestamp, column และค่าที่พบจริง
   - Agent ไม่ยืนยัน root cause ไม่สร้าง threshold และไม่กำหนดขั้นตอนซ่อม
   - Agent แนะนำให้ผู้เชี่ยวชาญด้านเครื่องจักรตรวจสอบหลักฐานต่อ

### Checkpoint

- Instructions มี Evidence-first rule เพิ่มเพียงหนึ่งข้อ และผล After อยู่ภายในขอบเขตของหลักฐานโดยไม่เติมค่าหรือสรุป root cause เอง

---

## Practice 3: Hardening 2 - ถามหนึ่งคำถามเมื่อ Context ไม่ครบ

**Primary target:** เพิ่ม Focused-clarification rule แล้วพิสูจน์ด้วย Before/After ว่า Agent ขอ incident context ด้วยคำถามที่จำเป็นเพียงหนึ่งข้อก่อนวิเคราะห์

1. คง Evidence-first rule จาก Practice 2 และ `Code interpreter` เป็น `Off` แล้วเลือก `Start new test session`
2. แนบไฟล์ `engine-anomaly-incident-data.csv` แล้วส่ง Prompt นี้ก่อนเพิ่ม clarification rule:

   ```text
   ช่วยตรวจไฟล์นี้และสรุป anomaly incident ของเครื่องยนต์ให้หน่อย
   ```

3. บันทึกผล Before ว่า Agent เริ่มวิเคราะห์ทันที เลือกช่วงเวลาเอง หรือถามมากกว่าหนึ่งคำถามหรือไม่
4. ไปที่ `Overview` > `Instructions` > `Edit` แล้วเพิ่ม rule นี้ต่อจาก Evidence-first rule:

   ```text
   Focused-clarification rule:
   - If the engine or incident window needed for the analysis is missing or ambiguous, ask exactly one focused question before analyzing the incident.
   ```

5. เลือก `Save`
6. เลือก `Start new test session` แล้วแนบ CSV เดิม
7. ส่ง Prompt เดิมโดยไม่แก้ข้อความ
8. ตรวจว่า Agent ยังไม่เริ่มวิเคราะห์และถามเพียงหนึ่งคำถามเพื่อขอ engine หรือ incident window
9. ตอบกลับด้วยข้อความนี้:

   ```text
   ใช้ ENG-201 ช่วง incident 2026-09-14 14:08 ถึง 14:12 และเทียบกับ baseline 14:00 ถึง 14:07
   ```

10. ตรวจว่า Agent สร้างคำตอบใน Chat โดยเรียงหัวข้อครบดังนี้:
    1. Engine and incident window
    2. Observed anomaly
    3. Timestamped evidence and measured values
    4. Missing or uncertain data
    5. What cannot be concluded from the file
    6. Recommended human review

### Checkpoint

- Instructions มี Focused-clarification rule เพิ่มเพียงหนึ่งข้อ และผล After ถามหนึ่งคำถามก่อนสร้าง Incident Summary ครบ 6 หัวข้อ

---

## Optional Route: ทดลองไฟล์ XLSX เมื่อ Environment รองรับ

หากทำ agent ด้วยไฟล์ CSV หากต้องการตรวจ availability ของ XLSX โดยไม่ใช้ `Code interpreter` ให้คง `Code interpreter` เป็น `Off` เริ่ม test session ใหม่ แนบ `engine-anomaly-incident-data.xlsx` และใช้ Prompt เดียวกับ Practice 1

ตรวจว่าค่าหลักที่ Agent อ่านได้ตรงกับ CSV ได้แก่ `VibrationMmS = 8.7` เวลา `14:11`, `CoolantTempC = 104` เวลา `14:12`, `OilPressureKPa = 292` เวลา `14:12` และค่า `OilPressureKPa` เวลา `14:11` เป็นค่าว่าง

> **⚠️ Note:** XLSX เป็นทางเลือกเท่านั้น Microsoft ระบุว่า XLSX โดยไม่เปิด `Code interpreter` ยังขึ้นอยู่กับ experimental availability ของ Environment ขนาดไฟล์ที่ต่ำกว่า character limit ไม่ได้ทำให้ capability นี้เปิดอัตโนมัติ ถ้าอัปโหลดไม่ได้ วิเคราะห์ไม่ครบ หรือผลลัพธ์ไม่สม่ำเสมอ ให้กลับมาใช้ CSV โดยไม่ถือว่าแบบฝึกหัดล้มเหลว

---

## Summary

คุณได้สร้าง Agent ที่ทำ main CSV workflow โดยไม่เปิด `Code interpreter` แล้วเพิ่ม reliability patterns ทีละข้ออีก 2 แบบ คือยึดหลักฐานโดยไม่เดา และถามหนึ่งคำถามเมื่อ context สำคัญไม่ครบ XLSX เป็นเพียง availability test และไม่ใช่ prerequisite ของ Module ถัดไป

## Microsoft Learn Reference

- [Allow file input from users](https://learn.microsoft.com/en-us/microsoft-copilot-studio/image-input-analysis)
- [Use code interpreter to analyze structured data (preview)](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-code-interpreter-structured-data#use-code-interpreter-for-analysis-of-a-user-uploaded-structured-data-file)

ขั้นตอนถัดไป → [Module 3: RAG with Operations Knowledge Assistant](../../module-3/README.md)
