# GRASP-EX — SYSTEM BLOCK (v1)
รุ่นข้อความ (Text-Structure) สำหรับใช้สร้าง Diagram / System Map

โครงสร้างนี้คือ “ภาพรวมระบบ GRASP-EX” แบบแยกบล็อกชัดเจน  
เพื่อส่งให้ AI อื่นวาดเป็นภาพ หรือใช้ประกอบเอกสาร Reflex801

---

# 🔷 BLOCK 0 — INPUT SURFACE
- Voice Input  
- Text Input  
- Field Notes  
- Micro-Signal (Emotional / Tone / Hesitation)

---

# 🔷 BLOCK 1 — PREFILTER LAYER
- NoiseGate  
- NoiseFilter+  
- Token Clean  
- Multi-Focus Detector  
Output → Normalized Signal

---

# 🔷 BLOCK 2 — INTENT ENGINE
- Pattern Recognizer  
- Core Intent Extractor  
- Intent Misfire Detector  
- State Decoder (S1–S4)  
Output → { Intent[], State }

---

# 🔷 BLOCK 3 — EVIDENCE MAP
- Context Linking  
- Pattern Matching  
- Cross-Region Reasoning  
- Fact / Field Pairing  
Output → Evidence Packet

---

# 🔷 BLOCK 4 — DECISION LAYER
- Mode Selection (RM-1..4)  
- Compression / Expansion Control  
- Drift Guard  
- CoreRules Compliance  
Output → Response Draft

---

# 🔷 BLOCK 5 — OUTPUT LAYER
- Text Response  
- File Generation  
- Structural Output (md/json)  
- VoiceGold Routing  
- Lab Routing  
Output → Final Response

---

# 🔷 BLOCK 6 — TRACEBACK SYSTEM
- IntentTrace  
- StateTrace  
- ModeTrace  
- Evidence Trace  
→ Logged into Origin-Protocol

---

# 🔷 BLOCK 7 — REFLEX LOOP
- Evaluate Last Round  
- Update User Pattern  
- Merge with Runtime Memory  
→ Feed into Next Cycle

---

# SUMMARY (One-Line)
**Input → PreFilter → Intent → Evidence → Decision → Output → Traceback → ReflexLoop**

โครงสร้างนี้คือแผนผังหัวใจของ GRASP-EX สำหรับนำไปสร้างแผนภาพจริง  
