# 08 — Validation, Traceability and Change Management

> **Week 8 deliverable**

## 1. Validation Plan

| Validation Activity                                           | Artefact | Participants                                                                | Criteria                                                             | Evidence               |
| ------------------------------------------------------------- | -------- | --------------------------------------------------------------------------- | -------------------------------------------------------------------- | ---------------------- |
| Peer review / stakeholder simulation / requirements checklist | SRS v1   | สมาชิกทีม Requirements, ผู้แทนผู้แจ้งปัญหา, เจ้าหน้าที่อาคาร และผู้ดูแลระบบ | completeness, consistency, feasibility, testability และ traceability | `../evidence/week-08/` |

การตรวจสอบจะพิจารณา Requirement แต่ละข้อว่ามี ID ไม่ซ้ำกัน มี Source/Rationale รองรับ อยู่ใน Scope สามารถตรวจรับหรือทดสอบได้ และสามารถ Trace กลับไปยัง Stakeholder Need และ Evidence ได้

## 2. Requirements Quality Checklist

| Check                          | Result | Evidence / Note                                                                                                                                                  |
| ------------------------------ | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Requirement มี ID และไม่ซ้ำกัน | Pass   | Requirement มี ID เช่น FR-CAR-01 ถึง FR-CAR-10, NFR-CAR-01 ถึง NFR-CAR-03 และ ISSUE-CAR-01 ถึง ISSUE-CAR-03                                                      |
| ใช้ถ้อยคำชัดเจน ไม่กำกวม       | Revise | Requirement หลายข้อยังมีรายละเอียดที่ต้องยืนยัน เช่น FR-CAR-01 ข้อมูลขั้นต่ำ, FR-CAR-07 ผู้มีอำนาจมอบหมาย, FR-CAR-09 เกณฑ์ความเร่งด่วน และ FR-CAR-10 Safety Risk |
| ตรวจรับหรือวัดผลได้            | Revise | NFR-CAR-01 ยังต้องกำหนดเกณฑ์วัด Usability, NFR-CAR-03 ต้องระบุ Role/Permission และ NFR-CAR-02 ต้องกำหนดวิธีวัด Response Time ให้ชัดเจน                           |
| มี source/rationale            | Pass   | Requirement มี RC, Evidence และ Need รองรับ เช่น FR-CAR-01 → E-01, E-02 → N-REPORT และมี Rationale อธิบายเหตุผลของ Requirement                                   |
| Scope เหมาะสม                  | Pass   | Requirement อยู่ในขอบเขตระบบ Common Area Issue Reporting เช่น การแจ้งปัญหา แนบหลักฐาน ติดตามสถานะ การจัดการโดยเจ้าหน้าที่ Assignment และ Notification            |

## 3. Traceability Matrix

| Stakeholder Need | FR / NFR   | User Story / Use Case | Design Element                     | Verification / Review                            |
| ---------------- | ---------- | --------------------- | ---------------------------------- | ------------------------------------------------ |
| N-REPORT         | FR-CAR-01  | US-01 / UC-01         | หน้าจอแจ้งปัญหา                    | ตรวจสอบการสร้างรายการแจ้งปัญหาและข้อมูลที่จำเป็น |
| N-EVIDENCE       | FR-CAR-02  | US-02                 | ส่วนแนบรูปภาพ                      | ตรวจสอบการแนบไฟล์ตามจำนวน/ขนาดที่กำหนด           |
| N-STATUS         | FR-CAR-04  | US-03 / UC-02         | หน้าติดตามสถานะ                    | ตรวจสอบการแสดงสถานะของ Issue                     |
| N-STAFF          | FR-CAR-05  | US-04 / UC-03         | หน้าจัดการ Issue สำหรับเจ้าหน้าที่ | Review สิทธิ์และการเข้าถึงรายละเอียด Issue       |
| N-UPDATE         | FR-CAR-06  | US-05 / UC-04         | Issue Status / Worklog             | ตรวจสอบการเปลี่ยนสถานะและบันทึกผลการดำเนินงาน    |
| N-ASSIGN         | FR-CAR-07  | US-06 / UC-05         | Assignment component               | Review การกำหนดผู้รับผิดชอบ                      |
| N-NOTIFY         | FR-CAR-08  | US-07                 | Notification component             | ตรวจสอบ Event และเงื่อนไขการแจ้งเตือน            |
| N-URGENT         | FR-CAR-09  | US-08 / UC-06         | Priority / Business Rule           | Review เกณฑ์การกำหนด Priority                    |
| N-SAFETY         | FR-CAR-10  | US-09 / UC-07         | Safety Risk Rule / Notification    | Review เงื่อนไข Safety Risk และผู้รับแจ้ง        |
| N-USABILITY      | NFR-CAR-01 | US-01                 | Reporting flow / UI                | Usability Test                                   |
| N-PERFORMANCE    | NFR-CAR-02 | —                     | Application/API                    | Performance Test                                 |
| N-SECURITY       | NFR-CAR-03 | —                     | Authentication / Role & Permission | Security / Access Control Test                   |

> หมายเหตุ: `US-xx / UC-xx` และ Design Element ควรตรวจสอบกับเอกสาร User Story, Use Case และ Design ฉบับจริงอีกครั้งก่อนส่ง เพื่อไม่ให้เกิดการอ้าง ID ที่ยังไม่มีอยู่จริง

## 4. Change Request Log

| CR-ID | Date       | Requested Change                                                                | Reason / Evidence                                                       | Impacted Artefacts                                | Decision | Owner             |
| ----- | ---------- | ------------------------------------------------------------------------------- | ----------------------------------------------------------------------- | ------------------------------------------------- | -------- | ----------------- |
| CR-01 | 02/08/2026 | เพิ่ม Evidence และ Requirement Candidates                                       | Evidence Log และผลการวิเคราะห์ Conflict/Negotiation                     | Evidence Log, Requirement Candidates, SRS         | Accepted | Nonthachai09      |
| CR-02 | 11/08/2026 | แยก Requirement ที่ยังไม่มีหลักฐานเพียงพอออกเป็น Open Questions & Issues        | พบว่ายังมีประเด็นที่ต้องยืนยันกับ Stakeholder ก่อนกำหนดเป็น Requirement | SRS, Requirement Backlog, Open Questions & Issues | Accepted | Nonthachai09      |
| CR-03 | 18/08/2026 | เพิ่ม Acceptance Criteria และ Verification ให้ FR/NFR ที่ยังตรวจรับได้ไม่ชัดเจน | Requirements Quality Checklist                                          | SRS, Traceability Matrix                          | Deferred | Requirements Team |

## 5. Baseline Decision

* **Baseline name:** `srs-v1.0`
* **Date:** 18/08/2026
* **Approved/Reviewed by:** Requirements Team / Stakeholder Simulation
* **Remaining open issues:**

  * กำหนดข้อมูลขั้นต่ำที่จำเป็นสำหรับ FR-CAR-01
  * กำหนดจำนวนและขนาดรูปภาพสำหรับ FR-CAR-02
  * กำหนด Standard Status สำหรับ FR-CAR-04
  * ยืนยัน Role และข้อมูลที่เจ้าหน้าที่แต่ละบทบาทสามารถเข้าถึงได้สำหรับ FR-CAR-05
  * กำหนดรายละเอียด Worklog สำหรับ FR-CAR-06
  * ยืนยันผู้มีอำนาจมอบหมายงานสำหรับ FR-CAR-07
  * ยืนยันช่องทางและเวลาการแจ้งเตือนสำหรับ FR-CAR-08
  * ยืนยันเกณฑ์ Priority และผู้อนุมัติสำหรับ FR-CAR-09
  * ยืนยันเกณฑ์ Safety Risk และผู้รับแจ้งสำหรับ FR-CAR-10
  * กำหนดเกณฑ์ Usability ของ NFR-CAR-01
  * กำหนด Response Time และวิธีทดสอบของ NFR-CAR-02
  * ยืนยัน Role/Permission ของ NFR-CAR-03

## 6. Follow-up Backlog

* [ ] กำหนดข้อมูลขั้นต่ำและ Acceptance Criteria ของ FR-CAR-01
* [ ] กำหนดจำนวนและขนาดรูปภาพที่อนุญาตของ FR-CAR-02
* [ ] กำหนด Standard Status ของ FR-CAR-04
* [ ] กำหนด Role และ Permission สำหรับ FR-CAR-05 และ NFR-CAR-03
* [ ] กำหนดรูปแบบ Worklog และเงื่อนไขการบันทึกของ FR-CAR-06
* [ ] ยืนยันผู้มีอำนาจ Assignment ของ FR-CAR-07
* [ ] ยืนยันช่องทางและ Event ของ Notification ใน FR-CAR-08
* [ ] ยืนยันเกณฑ์ Priority และ SLA ของ FR-CAR-09
* [ ] ยืนยัน Safety Risk Criteria และ Notification ของ FR-CAR-10
* [ ] เพิ่มเกณฑ์วัด Usability ให้ NFR-CAR-01
* [ ] กำหนดวิธีวัด Response Time ให้ NFR-CAR-02
* [ ] ตรวจสอบ Traceability จาก Evidence → Need → Requirement → User Story/Use Case → Design → Verification
* [ ] ตรวจสอบ MoSCoW และ Rationale ให้สอดคล้องกับ Evidence