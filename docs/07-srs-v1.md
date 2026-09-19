# 07 — Software Requirements Specification (SRS) v1

> **Week 7 deliverable**  
> เวอร์ชัน: v1.0 | สถานะ: Baseline Candidate | วันที่: [DD/MM/YYYY]

## Document Control

| Version | Date | Author | Reviewer | Summary of Change |
|---|---|---|---|---|
| 0.1 | | | | Initial draft |
| 1.0 | | | | Baseline candidate |

## 1. Introduction

### 1.1 Purpose
[กรอก]

### 1.2 Scope
[กรอก]

### 1.3 Definitions, Acronyms and Abbreviations
ดู [Glossary](glossary.md)

### 1.4 References
- Case Card
- Evidence log
- Course materials

## 2. Overall Description

### 2.1 Product Perspective
[กรอก]

### 2.2 User Classes and Characteristics
[กรอก]

### 2.3 Operating Environment
[กรอก]

### 2.4 Constraints
[กรอก]

### 2.5 Assumptions and Dependencies
[กรอก]

## 3. Functional Requirements

> สรุปจาก `05-requirement-backlog.md` และต้องคง ID เดิม

## 3.1 Prepare and Submit

| ID | System requirement | Source | CAP | Priority/admission | W06 model | Status | 
|---|---|---|---|---|---|---|
| FR-01 | ระบบต้องให้ผู้ใช้งานสร้างรายการแจ้งปัญหาพื้นที่ส่วนกลาง โดยต้องระบุรายละเอียดปัญหา อาคาร ตำแหน่งที่เกิดเหตุ | E-01, E-02 | CAP-01 | Must | US-01,UC-01 | Detailed Ready for Modeling |
| FR-02 | ระบบต้องให้ผู้ใช้งานแนบรูปภาพประกอบรายการแจ้งปัญหาได้อย่างน้อย 1 รูป | E-01, E-02 | CAP-01 | Must | US-01,UC-01 | Detailed Ready for Modeling |

## 3.2 Manage Problem Reports

| ID | System requirement | Source | CAP | Priority/admission | W06 model | Status | 
|---|---|---|---|---|---|---|
| FR-05 | ระบบต้องให้เจ้าหน้าที่เปิดดูรายการแจ้งปัญหาและรายละเอียดของแต่ละรายการได้ | E-05, E-06 | CAP-01 | Must | US-03,UC-03 | Detailed Ready for Modeling |
| FR-06 | ระบบต้องให้เจ้าหน้าที่เปลี่ยนสถานะของรายการแจ้งปัญหาได้ตามสถานะที่ระบบกำหนด | E-06, E-07 | CAP-01 | Must | US-04,UC-03 | Detailed Ready for Modeling |
| FR-07 | ระบบต้องให้เจ้าหน้าที่บันทึกผลการดำเนินงานของรายการแจ้งปัญหาได้ | E-06, E-07 | CAP-01 | Must | US-04,UC-03 | Detailed Ready for Modeling |

## 3.1 Track and Notify

| ID | System requirement | Source | CAP | Priority/admission | W06 model | Status | 
|---|---|---|---|---|---|---|
| FR-09 | ระบบต้องแจ้งเตือนผู้แจ้งเมื่อสถานะของรายการแจ้งปัญหามีการเปลี่ยนแปลง |E-08, E-09 | CAP-01 | Must | US-01,UC-02 | Detailed Ready for Modeling |

## 4. Non-functional Requirements

| ID | Requirement | Scenario | Response / Measure | Verification | Status |
|---|---|---|---|---|---|
| NFR-01 | ระบบต้องให้ผู้ใช้งานสามารถส่งรายการแจ้งปัญหาได้โดยมีขั้นตอนการใช้งานที่ชัดเจนและไม่ซับซ้อน | เมื่อผู้ใช้งานเข้าสู่หน้าการแจ้งปัญหาและดำเนินการส่งรายการ | ต้องกำหนดจำนวนขั้นตอนสูงสุดจากการทดสอบ Usability | Usability Testing | Ready |
| NFR-02 | ระบบต้องตอบสนองและแสดงผลลัพธ์ของการดำเนินการหลัก เช่น การเปิดรายการแจ้งปัญหา การค้นหา และการตรวจสอบสถานะ | เมื่อผู้ใช้งานดำเนินการหลักภายใต้การเชื่อมต่อเครือข่ายปกติ | ต้องกำหนดค่า Response Time จาก Performance Requirement | Performance Testing | Ready |
| NFR-03 |ระบบต้องควบคุมการเข้าถึงข้อมูลและฟังก์ชันตามบทบาทของผู้ใช้งานที่กำหนดในระบบ | เมื่อผู้ใช้งานเข้าสู่ระบบและเรียกใช้ข้อมูลหรือฟังก์ชันต่าง ๆ | ผู้ใช้งานสามารถเข้าถึงข้อมูลและฟังก์ชันได้เฉพาะตามสิทธิ์ของบทบาทตนเอง | Inspection + Security Review | Ready |

## 5. External Interface Requirements

### 5.1 User Interfaces
[กรอก]

### 5.2 Software / External System Interfaces
[กรอก]

### 5.3 Data Interfaces
[กรอก]

## 6. Business Rules

| ID | Rule | Related Requirement |
|---|---|---|
| BR-01 | [กรอก] | FR-xx |

## 7. Requirement Models

- Use Case Diagram: [link]
- Activity Diagram(s): [link]
- Domain Model: [link]

## 8. Open Issues

| ID | Issue / Question | Owner | Due / Status |
|---|---|---|---|
| OQ-01 | [กรอก] | [ชื่อ] | Open |

## 9. Approval / Review Record

| Reviewer | Date | Result | Key Feedback |
|---|---|---|---|
| [ชื่อ/บทบาท] | | Approved / Revision | |
