# ORIGIN PROTOCOL — กติกาต้นทางของข้อมูล VOIDSPIRE™

Origin Protocol คือสัญญาว่า  
“ทุกเสียง ทุกภาพ ทุกข้อมูลที่เข้า Reflex801/VOIDSPIRE  
จะมีที่มา มีสิทธิ์ และมีขอบเขตการใช้งานที่ชัดเจน”

---

## 1. วัตถุประสงค์

1. ปกป้องเจ้าของข้อมูล (แม่ค้า, พ่อค้า, คนทำงานจริง)
2. ปกป้องลุงในฐานะ Custodian ภาคสนาม
3. ปกป้องพาร์ตเนอร์ Lab/VC ที่จะใช้ข้อมูลต่อ
4. ทำให้ระบบนี้ “โตได้จริง” โดยไม่ชน PDPA และจริยธรรม

---

## 2. โครงสร้าง Origin Record

ตัวอย่างข้อมูลหนึ่งรายการ (Conceptual):

```yaml
origin_id: vg-2025-11-19-UTD-01
collector: Lung Mendoza
location: "ตลาดเช้า จังหวัดอุตรดิตถ์"
timestamp: "2025-11-19T07:32:00+07:00"
subject_role: "แม่ค้าขายอาหารเช้า"
data_types:
  - audio
  - text_note
consent:
  mode: "spoken-consent"
  scope:
    - "research"
    - "deck-anonymous"
  restrictions:
    - "no-direct-face-photo"
pdpa_status: "compliant"
license:
  public_layer: "CC BY-NC 4.0 (summary-only)"
  deep_layer: "Reflex801 Custodian License"
links:
  audio_ref: "G-Roots://vg-2025-11-19-UTD-01-audio"
  note_ref: "VoiceGold://vg-2025-11-19-UTD-01-note"
