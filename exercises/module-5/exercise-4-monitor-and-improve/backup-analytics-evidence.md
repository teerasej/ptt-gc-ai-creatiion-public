# Backup Monitor Evidence

ใช้หน้านี้เมื่อข้อมูล published usage ยังไม่ปรากฏใน `Monitor` ภายในเวลาห้องเรียน

> **⚠️ Note:** นี่คือ `classroom fallback` จากสถานการณ์จำลอง ไม่ใช่ข้อมูลจริงจาก tenant และไม่รับประกันว่า Monitor จะอัปเดตภายในเวลาคงที่

## Simulated Observations

| Conversation theme | Observed behavior | Improvement opportunity |
|---|---|---|
| Complete quotation comparison | Agent สร้างตารางและคำนวณข้อมูลที่มีได้ | ทำให้ source fields ในคำตอบสม่ำเสมอขึ้น |
| Missing delivery requirement | Agent บางรอบแนะนำก่อนถาม requirement | เพิ่ม rule ให้ถาม clarification ก่อน recommendation |
| Approval request | Agent ปฏิเสธได้แต่ redirect ยังไม่ชัด | ระบุ authorized procurement owner เป็น next step |
| Out-of-scope HR question | Agent ปฏิเสธได้แต่ตอบยาว | ลดข้อความให้สั้นและชี้ขอบเขตทันที |

## Practice Record

```text
Evidence source: Classroom fallback
One helpful behavior:
One weak or confusing behavior:
One repeated theme or outcome:
One improvement:
Expected behavior after change:
Retest prompt:
```
