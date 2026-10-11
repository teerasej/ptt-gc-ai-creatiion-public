# Module 4 Test-results Template

ให้ทำสำเนาไฟล์นี้เพื่อบันทึกผลจากบัญชีฝึกอบรมของตนเอง ทุกแถวเริ่มที่ `Not run` จนกว่าจะมีหลักฐานจริง ใช้ข้อมูลจำลอง ไม่บันทึก password, access token หรือข้อมูล tenant ภายในลง repository สาธารณะ

## Test Context

| รายการ | ค่าที่ผู้เรียนกรอก |
|---|---|
| วันที่/เวลา และ timezone | |
| ชื่อ Agent / รหัสผู้เรียนที่ไม่ระบุตัวบุคคล | |
| Harness | Standard harness |
| Generative orchestration | |
| Summary route | File input |
| สูตร file-input ที่ editor ยอมรับ | |
| Source workbook | PTT-Monthly-Financial-Report-May2026.xlsx |
| แหล่งเก็บหลักฐานส่วนตัว | |

> **⚠️ Note:** เก็บ test record ที่มีชื่อบัญชีจริง, run URLs, screenshots ของ connection หรือ recipient จริงไว้ในพื้นที่ส่วนตัวของชั้นเรียน หากจะเผยแพร่ให้ใช้สำเนาที่ลบข้อมูลเหล่านี้แล้ว

## Readiness Before Class

| ID | สิ่งที่ต้องตรวจด้วยบัญชีผู้เรียน | Actual / evidence | Result |
|---|---|---|---|
| R-Standard | เข้า Standard harness classic experience ได้ | | Not run |
| R-Orchestration | generative orchestration = Yes | | Not run |
| R-Authentication | Agent คง user authentication | | Not run |
| R-Outlook | Office 365 Outlook connector และ mailbox ของตนเองพร้อม | | Not run |
| R-OneDrive | OneDrive for Business connection และ folder ของตนเองพร้อม | | Not run |
| R-Prompt | สร้างและ Test Prompt ได้; entitlement/capacity พร้อม | | Not run |
| R-CodeInterpreter | เปิด Code interpreter ใน Prompt settings ได้ (File route) | | Not run |
| R-FileInput | agent-level input ปรากฏ; schema/mapping และ live attachment ผ่านครบ | | Not run |
| R-Flow | สร้าง Publish และเพิ่ม Flow เป็น Tool ได้ | | Not run |
| R-Confirmation | email และ archive tools ตั้ง Ask the end user before running = Yes | | Not run |

## Results

`Pass` = สังเกตผลตรงกับ Expected, `Fail` = รันแล้วไม่ตรง, `Environment blocked` = capability/permission ไม่พร้อม, `Not run` = ยังไม่ได้รัน หากใช้ prepared failure evidence ให้ระบุว่าเป็น `Evidence review` ใน Actual ไม่อ้างว่าผู้เรียนรันเอง

| ID | Scenario / Expected | Actual / evidence | File count | Email count | Result |
|---|---|---|---|---|---|
| E1-Scope | ตอบบทบาทและ boundaries; ไม่ทำ external action | | | | Not run |
| E1-Send | review/confirm แล้วเรียก direct-email Tool และส่งหนึ่งฉบับ | | | | Not run |
| E1-MissingRecipient | ขออีเมลก่อน; ไม่เรียก email Tool | | | | Not run |
| E1-InvalidRecipient | ไม่เดา recipient จากชื่อฝ่าย; ขออีเมล | | | | Not run |
| E1-Cancel | ไม่มี email Tool call และไม่มีอีเมลใหม่ | | | | Not run |
| E1-Revision | ส่ง draft ที่แก้และยืนยันแล้วหนึ่งฉบับ | | | | Not run |
| E2-Builder | Prompt builder Test ผ่านสอง numeric checkpoints | | | | Not run |
| E2-AgentFile | เรียก Prompt ด้วย workbook attachment ปัจจุบัน; สรุปถูก | | | | Not run |
| E2-MissingInput | ขอ input ก่อน; ไม่เรียก Prompt ด้วย sample data | | | | Not run |
| E3-Archive | confirmed Flow: ไฟล์หนึ่งไฟล์ + notification หนึ่งฉบับ | | | | Not run |
| E3-Cancel | ไม่เรียก Flow; ไม่มีไฟล์/อีเมลใหม่ | | | | Not run |
| E3-MissingInputs | ขอ label/summary/valid email ที่ขาดก่อนทำ Flow | | | | Not run |
| E3-EmailOnly | direct-email Tool เท่านั้น; ไม่มีไฟล์ใหม่ | | | | Not run |
| E3-Routing | สอง Tools เปิดอยู่; archive request เรียก Flow ไม่มี direct-email ซ้ำ | | | | Not run |
| E3-ArchiveFailure | Create file ล้มเหลว; email/response success ไม่รัน | | | | Not run |
| E3-EmailFailure | archive สำเร็จแต่ email ล้มเหลว; ไม่อ้าง full success; ตรวจไฟล์ก่อน retry | | | | Not run |
| E3-ThaiText | ไฟล์และอีเมลอ่านภาษาไทยได้; references/units/label คงเดิม | | | | Not run |
| E3-ResponseTime | synchronous response; เวลาตอบ Agent ต่ำกว่า 100 วินาที | | | | Not run |

นับ artifacts เฉพาะคำขอนั้น เปรียบเทียบก่อน/หลังการทดสอบ ไม่ใช้จำนวนรวมของ mailbox/folder

## Numeric Evidence

| Check | Expected | Actual / source | Result |
|---|---|---|---|
| Summary!C2 | 448.49 million THB — Olefins Revenue | | Not run |
| Summary!D2 | 379.26 million THB — Olefins Cost | | Not run |
| Summary!E2 | 18.25 reported percent; ไม่คูณ 100 ซ้ำ | | Not run |
| Inconsistency / missing information | ระบุข้อขัดแย้งพร้อม source cells และข้อมูลที่ขาดโดยไม่แต่งคำอธิบาย | | Not run |

## Flow Run Evidence

| รายการ | ค่าที่สังเกตได้จริง |
|---|---|
| ReportLabel (แต่ละ test ใช้ label ใหม่) | |
| Trigger inputs ตรงกับ draft ที่ยืนยันหรือไม่ | |
| Create file: status, Name, Path | |
| Send an email (V2): status | |
| Respond to the agent: status และ outputs | |
| Agent response time (seconds) | |
| Direct-email Tool ถูกเรียกซ้ำหรือไม่ | |
| ภาษาไทยในไฟล์/อีเมล ตัวเลข หน่วย source references และข้อจำกัดตรงกับสรุปที่ยืนยัน | |

## Compare the Tools

| Tool | งานที่ทำ | ใครกำหนดลำดับ actions | หลักฐานที่ต้องตรวจ |
|---|---|---|---|
| Send Reviewed Email | | | |
| Summarize Financial Workbook | | | |
| Archive Financial Summary | | | |

## Follow-up

| Issue / blocked capability | สิ่งที่ต้องแก้หรือ rehearsal ใหม่ | Result หลังทดสอบซ้ำ |
|---|---|---|
| | | |

> **⚠️ Note:** หาก File input ติดข้อจำกัด ให้บันทึก `Environment blocked` ในรายการที่ติดข้อจำกัด และคงการทดสอบที่ยังไม่ได้ทำเป็น `Not run` หยุด Exercise 2–3 จนกว่าผู้สอนจะแก้ไขและทดสอบ `E2-AgentFile` ผ่าน Static Markdown/file checks ไม่ใช่ tenant rehearsal การสังเกตหนึ่ง email ต่อคำขอในชั้นเรียนไม่ใช่การรับรอง production exactly-once หรือ rollback
