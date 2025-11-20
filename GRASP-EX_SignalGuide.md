GRASP-EX — Signal Guide (v1)

Reflex801 / VOIDSpire Lineage

# 1. Accepted Signals (สัญญาณที่ระบบ “รับเข้า”)
1.1 Voice Data (สัญญาณเสียง)

เสียงสนทนาภาคสนาม (Field Audio)

โทนเสียง / ลมหายใจ / จังหวะหยุด

ความตั้งใจเชิงอารมณ์ (Emotional Intent)

1.2 Text Message / SME Notes

ข้อความมีแหล่งที่มาชัดเจน (Source-Known)

ข้อความจาก SME / ผู้ขาย / เจ้าของกิจการ

โน้ตที่ผ่านการตรวจสอบ Validity

1.3 Emotional Micro-Signals

แรงกดดัน (Pressure Indicators)

ความลังเล (Hesitation Markers)

สัญญาณความจริงใจจริง (Genuineness)

1.4 Field Context Tags

ตำแหน่งที่เกิดข้อมูล

ประเภทตลาด

เวลา / ช่วงวัน

ปัจจัยร่วม เช่น ฝนตก รถแน่น ช่วงเร่งด่วน

1.5 Meta-Pattern (Cross-Region)

Pattern ที่เกิดซ้ำหลายพื้นที่

ความถี่ของเหตุการณ์

ความสอดคล้องของปัญหา

โอกาสโยงไปสัญญาณระดับประเทศ

# 2. Rejected Signals (สัญญาณที่ “ถูกปฏิเสธ”)
2.1 Source Unclear

ข้อมูลที่ไม่รู้แหล่งที่มา

ข้อมูลจากบุคคลนิรนามแบบไม่มีการยืนยัน

2.2 Intent Unclear

ไม่สามารถระบุ “เจตนา” จากเนื้อหา/โทนเสียงได้

2.3 Bias-Heavy Data

ข้อมูลที่มีอคติแทรกสูง

ข้อมูลที่อาจบิดเบือนบริบทจริง

2.4 Excessive Noise

เสียงรบกวนเกิน NoiseGate

สัญญาณที่ผ่าน NoiseFilter ไม่ได้

2.5 Non-Relevant Signals

ข้อมูลนอก Scope

สัญญาณที่ไม่เข้ากรอบ GRASP-EX

# 3. Grey-Zone Signals (สัญญาณก้ำกึ่ง – ต้องรอดูพฤติกรรม)
3.1 Pending Review

Intent ยังไม่ชัด

ต้องเพิ่มรอบวิเคราะห์

3.2 Ambiguous Emotional Signals

โทนเสียงปนหลายอารมณ์

ไม่แน่ชัดว่าเป็นเชิงบวก / ลบ / กดดัน

3.3 Light Misfire

เกือบเข้า Intent ผิด แต่ยังไม่ผิดเต็ม

รอ cross-check กับ Origin-Protocol

3.4 Repeat Confirmation

รอเหตุการณ์เกิดซ้ำเพื่อยืนยัน Pattern

# 4. Signal Confidence Scale (ระดับความเชื่อมั่นสัญญาณ)
ระดับ	ความหมาย	การกระทำ
L1	สัญญาณท้องถิ่น	เก็บเป็น Context
L2	ข้ามพื้นที่	เข้าชั้น Pattern Engine
L3	Insight คุณค่าสูง (VoiceGold)	ส่งเข้า Lab / Deck
L4	Origin-Critical	ปักหมุดต้นน้ำ / ป้อน Aegis
# 5. Signal Integrity Rules

ต้องมี Timestamp

ต้องมี Source Linkage

ต้องผ่าน NoiseGate

ต้องไม่ซ้ำ (De-duplicate)

ต้อง Traceback ได้ถึงต้นทาง

ต้องผ่าน Grey-Zone ถ้าคลุมเครือ

ต้องเข้า Compatibility ของ Origin-Protocol

# 6. Export Format (รูปแบบส่งออกข้อมูล)

.json

.csv

.md

Audio + Transcript Bundle

SystemMap Visual (v1)

# 7. Linkage to VOIDSpire System

Input → Signal Guide → Runtime Flow → CoreRules

เก็บสัญญาณตาม L-tier → ป้อน VoiceGold Pipeline
