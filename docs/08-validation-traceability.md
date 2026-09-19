# 08 — Validation, Traceability and Change Management

> **Week 8 deliverable**

## 1. Validation Plan

| Validation Activity | Artefact | Participants | Criteria | Evidence |
|---|---|---|---|---|
| Peer Review / Stakeholder Simulation / Checklist | docs/01 ถึง docs/05 | [นนทชัย ไทยตัน, ภูมิพัฒน์ วงศ์ดาว,ณัฐณิชา ปกแก้ว] | completeness, consistency, feasibility, testability, traceability, scope alignment, MoSCoW rationale | `evidence/week-05/PeerCross-Review.md` |

## 2. Requirements Quality Checklist

| Check | Result | Evidence / Note |
|---|---|---|
| Requirement มี ID และไม่ซ้ำกัน | Pass | FR-01 ถึง FR-11 และ NFR-01 ถึง NFR-03 มี ID แยกกัน |
| ใช้ถ้อยคำชัดเจน ไม่กำกวม | Pass | Requirement ระบุพฤติกรรมและหน้าที่ของระบบอย่างชัดเจน |
| ตรวจรับหรือวัดผลได้ | Pass | Requirement สามารถใช้เป็นเกณฑ์สำหรับการตรวจสอบระบบได้ |
| มี source/rationale | Pass | อ้างอิงจาก stakeholder needs และประเด็นจากการวิเคราะห์ Requirements |
| Scope เหมาะสม | Pass | ครอบคลุมการแจ้งปัญหา การติดตาม การมอบหมาย และการจัดการสิทธิ์ |

## 3. Traceability Matrix

| Stakeholder Need | FR / NFR | User Story / Use Case | Design Element | Verification / Review |
| --- | --- | --- | --- | --- |
| UN-01 แจ้งปัญหาพื้นที่ส่วนกลาง | FR-01, FR-02 | [รอทำใน Week 06] | Report Issue Screen | Requirement Review |
| UN-02 ติดตามสถานะปัญหา | FR-04 | [รอทำใน Week 06] | Issue Tracking Screen | Functional Review |
| UN-03 เจ้าหน้าที่จัดการรายการแจ้งปัญหา | FR-05, FR-06, FR-07 | [รอทำใน Week 06] | Staff Issue Management | Functional Review |
| UN-04 มอบหมายงานให้ผู้รับผิดชอบ | FR-08 | [รอทำใน Week 06] | Assignment Screen | Functional Review |
| UN-05 จัดการปัญหาที่มีความเร่งด่วนหรือความเสี่ยง | FR-09, FR-10| [รอทำใน Week 06] | Priority / Alert Component | Scenario Review |
| UN-06 ควบคุมการเข้าถึงระบบ | NFR-03 | [รอทำใน Week 06] | Role-based Access Control | Security Review |
| UN-07 ใช้งานระบบได้สะดวกและรวดเร็ว | NFR-01, NFR-02 | [รอทำใน Week 06] | Report / Issue Management UI | Usability & Performance Review |

## Open Question / Assumption

| Req ID | มาจาก Evidence | ผูกกับ Stakeholder | Need/Candidate  | ลากครบ | หมายเหตุ |
|---|---|---|---|---|---|
| **FR-CAR-03** | E-03 | นักศึกษา/ผู้พบปัญหา | RC-03 | ขาด | พบ Gap! ต้องยืนยันว่า E-03 รองรับ RC-03 จริง และต้องระบุว่าเชื่อมโยงกับ Stakeholder ใด รวมถึงรูปแบบหมายเลขอ้างอิง ก่อนนำไปทำ Use Case + AC ใน Week 06 |

## 4. Change Request Log

| CR-ID | Date | Requested Change | Reason / Evidence | Impacted Artefacts | Decision | Owner |
|---|---|---|---|---|---|---|
| CR-01 | [18/08/2026] | [ปรับปรุง RC-01 - RC-08 และ E-01 - E-08 ให้สอดคล้องกับ FR-CAR-01 - FR-CAR-08] | [ผลจากการตรวจพบว่า RC-01 - RC-08 และ E-01 - E-08 ไม่สอดคล้องกับ FR-CAR-01 - FR-CAR-08] | docs/05-requirement-backlog.md, docs/08-validation-traceability.md | Accepted | [นาย นนทชัย ไทยตัน] |
| CR-02 | [18/08/2026] | [เเก้ไขหัวข้อที่ FR-CAR-09 - ISSUE-CAR-03] | [เเก้ไขหัวข้อให้ตรงกับ RC เเละ Evidence/Need Trace ที่มีอยู่จริงตาม 04-evidence-log, 04-requirement-cadidates] | docs/05-requirement-backlog.md, docs/08-validation-traceability.md | Accepted | [นาย ภูมิพัฒน์ วงศ์ดาว] |
| CR-03 | [18/08/2026] | ปรับปรุง Requirement และ Traceability ที่เกี่ยวข้องให้สอดคล้องกับผล Quality & MoSCoW Check ก่อนจัดทำ Baseline v1.0 | ผลจากการตรวจพบ Requirement ที่ยังมี Gap ด้าน Traceability, Verifiable และ Open Question และต้องปรับให้สอดคล้องกับ Requirement Baseline ล่าสุด | docs/05-requirement-backlog.md, docs/08-validation-traceability.md | Accepted | [นางสาว ณัฐณิชา ปกแก้ว]

## 5. Baseline Decision

- Baseline name: srs-v1.0
- Date: 2026-08-18
- Approved/Reviewed by: Project Team
- Remaining open issues: Open Questions ที่ยังต้องยืนยันกับ Stakeholder

## 6. Follow-up Backlog

- [x] เพิ่ม Traceability Link ให้ครบสำหรับ FR-01 – FR-11 และ NFR-02 – NFR-03 โดยเชื่อมโยงกับ Epic ID / User Story ID / Case ID
- [x] ปรับ FR-06 ให้ระบุรายการสถานะที่ระบบรองรับอย่างชัดเจน เพื่อให้สามารถสร้าง Test Case ได้
- [x] กำหนดเงื่อนไข ความเสี่ยงด้านความปลอดภัยของ FR-11 ให้ชัดเจนว่าเหตุการณ์ใดเป็น Trigger ของการแจ้งเตือน
- [x] ปรับเกณฑ์ NFR-02 จากไม่เกิน 10 วินาที เป็นเกณฑ์ที่เหมาะสม เช่น ไม่เกิน 2–3 วินาที
- [x] เพิ่ม Rationale เพื่ออธิบายเหตุผลของระดับ MoSCoW ในแต่ละ Requirement
- [x] พิจารณาปรับ FR-10 จาก Should เป็น Must เนื่องจาก FR-11 ต้องอาศัยการจำแนกระดับความเร่งด่วน
- [x] พิจารณาปรับ FR-02 จาก Should เป็น Must เนื่องจากรูปภาพเป็นหลักฐานประกอบการประเมินปัญหา
- [x] ตรวจสอบ SRS v1 หลังแก้ไข เพื่อให้ Traceability, Testability และ MoSCoW สอดคล้องกันก่อนเริ่ม Design

## 7. Traceability Exceptions & Assumptions Log
เนื่องจากพบว่า Requirement บางข้อยังมี Traceability Gap จากการทำ Baseline Review จึงขออธิบายสมมติฐานและแผนการแก้ไขดังนี้

* **FR-CAR-03 :**
  * **Current Status:** Conditional Baseline (Pending Evidence)
  * **Gap Identified:** ยังขาดหลักฐานที่ยืนยันความเชื่อมโยงระหว่าง Evidence กับ Requirement โดยตรง ทำให้ Traceability ไปยัง Need/Candidate ยังไม่ครบถ้วน
  * **Assumption-01:** กำหนดเบื้องต้นว่า FR-CAR-03 มีที่มาจาก Evidence E-03 และเกี่ยวข้องกับ Stakeholder กลุ่ม นักศึกษา/ผู้พบปัญหา
  * **Resolution / Open Question:** บันทึกเป็น Open Question (OQ-01) เพื่อยืนยันว่า E-03 รองรับ RC-03 จริงหรือไม่ และระบุ Stakeholder กับหมายเลขอ้างอิงให้ชัดเจน ก่อนนำ FR-CAR-03 ไปจัดทำ Use Case และ Acceptance Criteria ใน Week 06