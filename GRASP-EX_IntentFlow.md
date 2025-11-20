# GRASP-EX™ — Intent Flow Specification (Reflex801)

**Version:** v0.1  
**Engine:** GRASP-EX Intent Engine  
**Part of:** Reflex801 • Voidspire OS  

---

## 1. OVERVIEW

GRASP-EX แปลง “ประโยคที่ลุงพิมพ์” → เป็น **เจตนาแท้ (True Intent)**  
ก่อนจะส่งต่อไปให้โมเดล (GPT / ฯลฯ) ตอบกลับ

Flow หลักมี 4 ขั้น:

1. **Sense** – รับสัญญาณจากข้อความ + บริบทก่อนหน้า  
2. **Decode** – วิเคราะห์ว่าลุง “ต้องการอะไรจริง ๆ”  
3. **Map** – จัดเข้า Intent Group + Cognitive State  
4. **Route** – เลือกโหมดตอบสนอง (Expansion / Compression / Action)

---

## 2. INTENT GROUPS (IG)

Intent ถูกจัดเป็นกลุ่มง่าย ๆ (v0.1):

- **IG-1 CLARIFY** – ขอความชัดเจน, ขออธิบายเพิ่ม  
- **IG-2 BUILD** – ขอสร้างของ: ระบบ, Deck, README, Flow, โค้ด  
- **IG-3 SOLVE** – ขอทางออก/แนว
