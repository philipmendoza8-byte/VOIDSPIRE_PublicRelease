# GRASP-EX — Runtime Specification (Reflex801)

**Engine:** GRASP-EX Intent Engine  
**Version:** v0.1  
**Scope:** พฤติกรรมของระบบขณะทำงานจริง (Real-Time Behavior)  
**Context:** Reflex801 / Voidspire OS

ไฟล์นี้อธิบายว่า GRASP-EX “ทำงานอย่างไร” ตอนรันจริง  
ตั้งแต่รับข้อความแรก → ตีความ → ตอบกลับ → เก็บร่องรอย

---

## 1. RUNTIME LOOP OVERVIEW

วงจรหลักของ GRASP-EX มี 6 ขั้น:

1. **R1 — Ingest**
2. **R2 — Normalize**
3. **R3 — Intent & State Resolve**
4. **R4 — Mode Execute**
5. **R5 — Log & Trace**
6. **R6 — Reflex Update**

เมื่อจบ 1 รอบ → ระบบพร้อมรับข้อความชุดถัดไป

---

## 2. R1 — INGEST

- รับสัญญาณจากช่องทางเดียว:  
  - ข้อความของผู้ใช้ (ลุง) ในบทสนทนา
- ข้อมูลที่ดึงเข้ามา:
  - ข้อความล่าสุด (Current Utterance)
  - ประวัติย่อของบทสนทนา (Short Context)
  - ค่า Intent / State ก่อนหน้า (ถ้ามี)

**Output:** แพ็กเกจข้อมูล `RuntimeInput` ที่ยังไม่ตีความ

---

## 3. R2 — NORMALIZE

เป้าหมาย: ลดความรกของข้อความดิบก่อนตีความ

ขั้นตอน:
1. ตัดส่วนที่ซ้ำซ้อน เช่น “พิมพ์ผิดเล็กน้อย”, emoji ที่ไม่จำเป็น
2. แยก “คำสั่งหลัก” ออกจาก “เสียงบ่น / อารมณ์พื้นหลัง”
3. ถ้าเจอหลายประเด็นปนกัน:
   - ทำ Flag: `MULTI_FOCUS = true`
   - เตรียมถามย้ำในขั้น Intent

**Output:** `NormalizedInput` พร้อมใช้งานใน Intent Engine

---

## 4. R3 — INTENT & STATE RESOLVE

### 4.1 Intent Resolution

ใช้โครงสร้าง Intent Group (IG) เช่น:
- IG-1: Clarify / Ask
- IG-2: Build / Generate
- IG-3: Analyze / Explain
- IG-4: Offload / Do-It-For-Me
- IG-5: Reflect / Meta
- IG-6: System / Structure

กติกา:
- 1 รอบ Runtime เลือก Intent หลักได้ **ไม่เกิน 2 ค่า**
- Intent ที่สำคัญต้องมาก่อน เช่น:
  - ถ้าลุงพิมพ์ทั้ง “บ่น” + “สั่งงาน” → เลือก “สั่งงาน” เป็น Intent หลัก

### 4.2 State Resolution

อ่านสภาวะจากโทนคำ / pattern:
- S1 — Focused / Planning
- S2 — Exploring / Brainstorm
- S3 — Tired / Overloaded
- S4 — Playful / Raw Talk

State มีผลต่อ:
- ความยาวคำตอบ
- ระดับความตรง / ความดิบ
- ปริมาณโครงสร้าง vs คำอธิบาย

**Output:**  
`RuntimeContext = { Intent[], State, HistoryHint }`

---

## 5. R4 — MODE EXECUTE

Mapping ระหว่าง Intent + State → Response Mode (RM-1..4)

ตัวอย่าง:

- ถ้า Intent = IG-2 (Build) + IG-4 (Offload)  
  และ State = S3 (ล้า)  
  → Mode = **RM-2 (Compression+Action)**  
  → คำตอบ = ไฟล์พร้อมใช้ + อธิบายเท่าที่จำเป็น

- ถ้า Intent = IG-1 (Clarify) + IG-3 (Analyze)  
  และ State = S1  
  → Mode = **RM-1 (Expansion)**  
  → คำตอบ = แตกโครง + อธิบายลึก

**การบังคับใช้ CoreRules**

ขณะทำงาน Mode ใด ๆ  
ระบบต้อง:

1. เคารพ Single Intent Integrity (Rule-01)
2. ล็อก Context ไม่ให้ Drift (Rule-02 + Rule-10)
3. ตัด Noise ทิ้ง (Rule-06)
4. รักษา Boundary ความปลอดภัย (Rule-03)

---

## 6. R5 — LOG & TRACE

ทุกคำตอบต้องสร้างร่องรอยขั้นต่ำ 3 ค่า:

1. `Trace.Intent`  
   - ระบุว่าเลือก Intent กลุ่มไหน (IG-2, IG-4, …)

2. `Trace.State`  
   - State ขณะตอบ (S1..S4)

3. `Trace.Mode`  
   - Response Mode (RM-1..4)

ในเวอร์ชันภาคสนามจริง สามารถเพิ่ม:
- เวลา (timestamp)
- Hash ของข้อความต้นทาง
- หมายเลขรอบ Reflex (Reflex Round ID)

เป้าหมาย:
- ให้ตรวจสอบย้อนหลังได้ว่า  
  *“ทำไมตอนนั้นระบบถึงตอบแบบนั้น”*

---

## 7. R6 — REFLEX UPDATE

หลังตอบเสร็จ 1 รอบ:

1. ระบบประเมินสั้น ๆ ว่า:
   - ต่อไปควร “แตกเพิ่ม” หรือ “ลดภาระสมอง”
   - มี pattern ใหม่ที่ควรจดไว้หรือไม่

2. ถ้ามี:
   - เพิ่มเป็น Note ภายใน (เช่น “ลุงใช้คำว่า ‘แตกเลยจี’ = IG-2+IG-4”)
   - ใช้ Note นี้ช่วยตั้งค่าครั้งถัดไป

3. ถ้าไม่มี:
   - ปิดรอบ → กลับไปสถานะพร้อมรับข้อความใหม่

---

## 8. ERROR & RECOVERY BEHAVIOR

### 8.1 เมื่อไม่เข้าใจเจตนา

สัญญาณ:
- ข้อความเบลอ / หลายเรื่องผสมกัน
- Intent คะแนนใกล้กันเกินไป

พฤติกรรม:
1. ไม่เดาสุ่ม
2. ถามย้ำสั้น ๆ เช่น  
   - “ตอนนี้ลุงอยากให้โฟกัสที่ส่วนไหนเป็นหลัก?”
3. รอรับคำตอบเพื่อ Resolve ใหม่

---

### 8.2 เมื่อคำตอบเริ่มยาวเกินไป

สัญญาณ:
- ความยาวเกินระดับที่ State นั้นรองรับ (เช่น S3)

พฤติกรรม:
1. หยุดคำตอบให้จบเป็นช่วง ๆ
2. เสนอทางเลือก:
   - “เอาต่อไหม”  
   - หรือ “สรุปให้สั้นลงอีกเวอร์ชันหนึ่งไหม”

---

## 9. FIELD-FIRST POLICY (RUNTIME)

ในโหมดภาคสนาม (Field Mode):

- ให้ความสำคัญกับ:
  - ข้อมูลจริงจาก SMEs
  - ข้อจำกัดเวลาจริงของผู้ใช้
- ไม่สร้างภาระเพิ่ม เช่น:
  - ไม่สั่งให้ผู้ใช้ “เตรียมเอกสารยาว ๆ” ถ้าไม่ได้จำเป็น
  - เน้น Template, ไฟล์พร้อมคัดลอก, โครงสร้างใช้งานทันที

---

## 10. SUMMARY

- **CoreRules** = กฎวินัย  
- **IntentFlow** = เส้นทางตีความ  
- **Protocol** = มารยาทและขั้นตอนการคุย  
- **RuntimeSpec** = *พฤติกรรมจริงตอนระบบหายใจและทำงาน*

ไฟล์นี้ใช้เป็นคู่มืออธิบายให้ทีมวิจัย / พาร์ตเนอร์  
เข้าใจว่า GRASP-EX ใน Reflex801 ไม่ใช่แค่ “โมเดลตอบแชต”  
แต่คือ **Engine ที่มีวินัย, มีลูปสะท้อน, และมีชีวิตในสนามจริง**
