# GRASP-EX — Runtime Flow (v1)

## 1. Input Layer
- รับสัญญาณทุกประเภท (Voice / Text / Field Notes)
- ตรวจสอบความถูกต้องเบื้องต้น (Signal Validity)

## 2. Pre-Filter Layer
- NoiseGate → คัดสิ่งรบกวนพื้นฐาน
- NoiseFilter+ → ปรับแต่งให้เหมาะกับ GRASP-EX Scope

## 3. Intent Extraction Engine
- วิเคราะห์ Pattern
- ตัดสัญญาณผิดฝั่ง (Intent Misfire)
- จับ Intent แก่นกลาง (Core Intent)

## 4. Evidence Mapping
- เชื่อม Intent กับข้อมูลหลักที่ตรวจสอบได้
- Traceable → Auditable → Explainable

## 5. Decision Layer
- ประมวลผลคำตอบ
- ใช้กฎ CoreRules.md ผูกบริบทให้ปลอดภัย

## 6. Output Layer
- จัดรูปผลลัพธ์ให้เหมาะกับปลายทาง (API / Report / Lab)
- Log ทั้งหมดเข้าสู่ Origin-Protocol
# GRASP-EX — Signal Guide (v1)

## 1. สัญญาณที่รองรับ (Accepted Signals)
- Voice Data (สนามจริง)
- Text Message / SME Notes
- Emotional Micro-Signals
- Field Context Tags
- Meta-Pattern (Cross-Region Signals)

## 2. สัญญาณที่ไม่รับ (Rejected Signals)
- ข้อมูลที่ละเมิดสิทธิ์
- ข้อมูลที่ไม่สามารถพิสูจน์ตัวตนแหล่งที่มาได้
- ข้อมูลที่ถูกดัดแปลงโดยไม่มีหลักฐาน
- Noise ระดับสูงที่ไม่ผ่าน NoiseGate

## 3. Grey-Zone Protocol
- สัญญาณไม่ชัดเจน → ส่งเข้าห้องรอ (Pending)
- ทีมสนามตรวจสอบซ้ำ
- หากยังไม่เคลียร์ → ปฏิเสธโดยอัตโนมัติ

## 4. Tagging System
- L1: Local Signal
- L2: Cross-Market Pattern
- L3: High-Value Insight (VoiceGold)
- L4: Origin-Critical
# GRASP-EX — Fail-Safe Map (v1)

## 1. Intent Misfire Detection
- ตรวจพบเมื่อสัญญาณขัดกับ Pattern เดิม
- ตัดเข้าช่อง Misfire_Queue อัตโนมัติ

## 2. High Noise Surge
- เกิด Noise สูงแบบกระชาก
- สั่งระบบเข้าสู่ Safe Mode
- ใช้กฎ Rule-03: Safe Response Boundary

## 3. Evidence Mismatch
- ข้อมูลสนับสนุนไม่สอดคล้องกับ Intent
- ย้ายเข้าหมวด Evidence-Recheck

## 4. System Failure Points
- Input Failure
- Filter Failure
- Intent Engine Failure
- Log Failure (ส่งสัญญาณไปยัง Origin-Protocol)

## 5. Recovery Loop
- เตือนระบบ
- ประมวลซ้ำในรอบปลอดภัย
- ออกผลลัพธ์แบบ De-Risked Output
