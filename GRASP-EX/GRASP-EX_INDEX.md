# GRASP-EX — INDEX VIEW (v1)
ภาพรวมสารบัญกลางของ GRASP-EX เพื่อการอ้างอิงและใช้งานในระบบ VOIDSPIRE™

---

## 0. OVERVIEW
- วัตถุประสงค์ของ GRASP-EX  
- โครงสร้างการไหลของข้อมูล  
- Layer ที่ทำงานร่วมกับ Reflex801 / VOIDSPIRE™

---

## 1. CORE RULES
**ไฟล์:** `GRASP-EX_CoreRules.md`  
เนื้อหา:
- กฎหลักของการตีความสัญญาณ  
- ข้อจำกัด, Boundary, และ Operating Range  
- เงื่อนไขที่ถือเป็น Intent ที่ถูกต้อง

---

## 2. INTENT ENGINE
**ไฟล์:**  
- `GRASP-EX_IntentFlow.md`  
- `GRASP-EX_RuntimeFlow.md`  
- `GRASP-EX_RuntimeSpec.md`

เนื้อหา:
- ขั้นตอนแยก Intent  
- Input Layer → Pre-Filter → Evidence Layer  
- Misfire Handling  
- Evidence Mapping

---

## 3. SIGNAL GUIDE
**ไฟล์:** `GRASP-EX_SignalGuide.md`  
เนื้อหา:
- ประเภทสัญญาณที่ระบบยอมรับ  
- Rejected Signals  
- Grey-Zone Protocol  
- Tagging System (L1–L4)

---

## 4. SYSTEM MAP
**ไฟล์:** `GRASP-EX_SYSTEM_BLOCK.md`  
เนื้อหา:
- สถาปัตยกรรม GRASP-EX ในภาพรวม  
- จุดผูกกับ VOIDSPIRE™ Core  
- จุดส่งออกข้อมูล (API / Report / Lab)

---

## 5. PROTOCOLS
**ไฟล์:**  
- `GRASP-EX_Protocol.md`  
- `ORIGIN-PROTOCOL.md`

เนื้อหา:
- มาตรฐานการส่ง-รับข้อมูล  
- โครงสร้าง Origin → Evidence → Intent → Output  
- Boundary ที่ป้องกัน Noise เข้า Layer การตัดสินใจ

---

## 6. DOCUMENT SET
ไฟล์ประกอบ:
- `GRASP-EX_README.md`  
- ชุดเอกสารอธิบาย (docx / pdf)  
- แผนผังภาพรวม (SYSTEM_MAP_v1.png / Diagram Pack)

---

## 7. VERSIONING
- ปัจจุบันใช้ GRASP-EX v1  
- ไฟล์ทั้งหมดอยู่ภายใต้โฟลเดอร์ `/GRASP-EX/`  
- การอัปเดตให้ใช้ commit message รูปแบบ:  
  **`Update GRASP-EX_[MODULE] — v1.x`**

---

## 8. CONTACT / LINKAGE
- เป็นโมดูลย่อยใน VOIDSPIRE™ Public Release  
- ใช้คู่กับ Reflex801 Field Layer  
- ส่วนที่สัมพันธ์: FIELD_METHOD, MASTER_INDEX, OUTREACH Pack

---

> **หมายเหตุ:**  
ไฟล์นี้คือ *แผนที่นำทางกลาง* ของ GRASP-EX — ทุกไฟล์ย่อยควรลิงก์มาที่นี่เพื่อให้ระบบภายนอก (AI/มนุษย์) เข้าใจภาพรวมทันที
