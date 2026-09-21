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
| FR-05 | ระบบต้องให้เจ้าหน้าที่เปิดดูรายการแจ้งปัญหาและรายละเอียดของแต่ละรายการได้ | E-05, E-06 | CAP-02 | Must | US-03,UC-03 | Detailed Ready for Modeling |
| FR-06 | ระบบต้องให้เจ้าหน้าที่เปลี่ยนสถานะของรายการแจ้งปัญหาได้ตามสถานะที่ระบบกำหนด | E-06, E-07 | CAP-02 | Must | US-04,UC-03 | Detailed Ready for Modeling |
| FR-07 | ระบบต้องให้เจ้าหน้าที่บันทึกผลการดำเนินงานของรายการแจ้งปัญหาได้ | E-06, E-07 | CAP-02 | Must | US-04,UC-03 | Detailed Ready for Modeling |

## 3.3 Track and Notify

| ID | System requirement | Source | CAP | Priority/admission | W06 model | Status | 
|---|---|---|---|---|---|---|
| FR-09 | ระบบต้องแจ้งเตือนผู้แจ้งเมื่อสถานะของรายการแจ้งปัญหามีการเปลี่ยนแปลง |E-08, E-09 | CAP-03 | Must | US-01,UC-02 | Detailed Ready for Modeling |
| FR-10 | ระบบต้องสามารถรองรับการเรียกดูประวัติการแจ้งปัญหาย้อนหลัง เพื่อให้ผู้ใช้งานสามารถตรวจสอบรายละเอียด สถานะการดำเนินงาน และผลการแก้ไขปัญหาที่ผ่านมาได้อย่างเป็นระบบ |E-08, E-09 | CAP-03 | Must | US-09,UC-04 | Detailed Ready for Modeling |

### Deep Specification 1 — ระบบสร้างและส่งรายการแจ้งปัญหา (Prepare and Submit System)

> *(รวมข้อกำหนด FR-01 และ FR-02 ในระบบสร้างและส่งรายการแจ้งปัญหา)*

| ฟิลด์ | รายละเอียด |
|---|---|
| **Requirement IDs** | **FR-01, FR-02** |
| **System Name** | ระบบสร้างและส่งรายการแจ้งปัญหา (Prepare and Submit System) |
| **Statement** | ระบบต้องให้ผู้ใช้งานสร้างรายการแจ้งปัญหาพื้นที่ส่วนกลาง โดยระบุรายละเอียดปัญหา อาคาร ตำแหน่งที่เกิดเหตุ (ชั้น/จุดสังเกต) พร้อมแนบรูปภาพประกอบได้อย่างน้อย 1 รูป และออกหมายเลขอ้างอิง (Report ID) ให้ผู้แจ้งทราบทันทีเมื่อทำรายการสำเร็จ |
| **Rationale** | แก้ปัญหาข้อมูลการแจ้งปัญหากระจัดกระจาย ขาดความชัดเจน และไม่มีหลักฐานรูปภาพในการเข้าตรวจสอบพื้นที่จริง (E-01, E-02) |
| **Trigger** | ผู้ใช้เปิดหน้าแบบฟอร์มแจ้งปัญหา กรอกข้อมูล เลือกอาคาร/ตำแหน่ง แนบรูปภาพ แล้วกด "ส่งรายการแจ้งปัญหา" |
| **เงื่อนไขก่อนทำรายการ** | 1. เข้าสู่หน้าแบบฟอร์มแจ้งปัญหา <br> 2. กรอกข้อมูลระบุอาคาร ตำแหน่ง และรายละเอียดปัญหาครบถ้วน (BR-01) <br> 3. แนบรูปภาพประกอบอย่างน้อย 1 รูป (FR-02) |
| **ผลลัพธ์ที่คาดหวัง** | 1. ระบบสร้าง Record คำร้องใหม่ในสถานะ `Open` ลงในฐานข้อมูล <br> 2. ออกหมายเลขอ้างอิง (Report ID) แบบไม่ซ้ำกันแสดงให้ผู้แจ้งทราบทันที <br> 3. ส่งสัญญาณข้อมูลคำร้องเข้าสู่คิวงานของเจ้าหน้าที่ |
| **Business Rules** | **BR-01** (รายการแจ้งปัญหาต้องมีข้อมูลสถานที่ ประเภทปัญหา และรูปภาพประกอบครบถ้วนก่อนส่ง) |
| **NFR ที่เกี่ยวข้อง** | **NFR-01** (ส่งคำร้องสำเร็จได้ภายใน ≤ 3 ขั้นตอน), **NFR-02** (Response Time ≤ 10 วินาที) |
| **วิธีตรวจสอบ** | **Scenario Test (VF-01)**: กรอกข้อมูลเลือกอาคารเรียนรวม 1 ชั้น 2 + แนบรูปภาพ 1 รูป + กดส่ง -> ระบบสร้าง Report ID และแสดงสถานะ Open สอดคล้องตาม AC-01 |

---

### Deep Specification 2 — ระบบจัดการคำร้องและอัปเดตผลการดำเนินงาน (Manage Problem Reports System)

> *(รวมข้อกำหนด FR-05, FR-06 และ FR-07 ในระบบจัดการและอัปเดตผลงานสำหรับเจ้าหน้าที่)*

| ฟิลด์ | รายละเอียด |
|---|---|
| **Requirement IDs** | **FR-05, FR-06, FR-07** |
| **System Name** | ระบบจัดการคำร้องและอัปเดตผลการดำเนินงาน (Manage Problem Reports System) |
| **Statement** | ระบบต้องให้เจ้าหน้าที่เปิดดูรายการคำร้อง ค้นหา กรองรายละเอียด เปลี่ยนสถานะการดำเนินงาน (Open -> In Progress -> Resolved) และบันทึกผลการดำเนินงานพร้อมรายละเอียดการแก้ไขปัญหาประกอบคำร้องก่อนปิดงานได้ |
| **Rationale** | เพื่อให้เจ้าหน้าที่สามารถบริหารจัดการคิวงานอย่างเป็นระบบ อัปเดตสถานะงาน และบันทึกหลักฐานการแก้ไขงานเพื่อความโปร่งใส (E-05, E-06, E-07) |
| **Trigger** | เจ้าหน้าที่เปิดหน้ารายการคำร้องที่ได้รับมอบหมาย เลือกคำร้อง กด "เปลี่ยนสถานะ" หรือ "บันทึกผลการดำเนินงาน" |
| **เงื่อนไขก่อนทำรายการ** | 1. เข้าสู่ระบบด้วยบทบาทเจ้าหน้าที่ (`Staff`, `Admin`) ตามสิทธิ์ RBAC (BR-02) <br> 2. รายการคำร้องอยู่ในสถานะที่อนุญาตให้ดำเนินการได้ <br> 3. กรณีปิดงาน (`Resolved`): ต้องบันทึกรายละเอียดผลการดำเนินงานเรียบร้อยแล้ว (FR-07, BR-03) |
| **ผลลัพธ์ที่คาดหวัง** | 1. สถานะคำร้องเปลี่ยนเป็นสถานะใหม่ (`In Progress`, `Resolved`) <br> 2. ระบบบันทึกผลการแก้ไข เวลา และผู้ทำรายการลงในฐานข้อมูล (DR-04) <br> 3. ระบบลง Audit Log อัตโนมัติ (BR-04) และส่งสัญญาณแจ้งเตือนไปยังผู้แจ้ง (FR-09) |
| **Business Rules** | **BR-02** (เฉพาะเจ้าหน้าที่ที่มีสิทธิ์เท่านั้น), **BR-03** (ต้องระบุผลงานก่อน Resolved), **BR-04** (บันทึก Audit Log อัตโนมัติ) |
| **NFR ที่เกี่ยวข้อง** | **NFR-03** (ควบคุมการเข้าถึงและจัดการข้อมูลตามสิทธิ์ RBAC) |
| **วิธีตรวจสอบ** | **Demonstration (VF-02, VF-03)**: เจ้าหน้าที่เปิดดูรายการคำร้อง -> เปลี่ยนสถานะเป็น In Progress -> บันทึกรายละเอียดการซ่อมแซม -> เปลี่ยนเป็น Resolved -> สถานะเปลี่ยนและบันทึกลงระบบทันที |

---

### Deep Specification 3 — ระบบแจ้งเตือนการเปลี่ยนแปลงสถานะ (Status Notification System)

> *(ข้อกำหนด FR-09 สำหรับระบบแจ้งเตือนเมื่อสถานะมีการเปลี่ยนแปลง)*

| ฟิลด์ | รายละเอียด |
|---|---|
| **Requirement ID** | **FR-09** |
| **System Name** | ระบบแจ้งเตือนการเปลี่ยนแปลงสถานะ (Status Notification System) |
| **Statement** | ระบบต้องส่งสัญญาณการแจ้งเตือน (Notification) ไปยังผู้แจ้งอัตโนมัติเมื่อสถานะของรายการแจ้งปัญหามีการเปลี่ยนแปลง (เช่น จาก Open เป็น In Progress หรือ Resolved) |
| **Rationale** | เพื่อให้ผู้แจ้งทราบความคืบหน้าการแก้ไขปัญหาทันที ลดภาระในการคอยสอบถามซ้ำซ้อน และเพิ่มความโปร่งใส (E-08, E-09) |
| **Trigger** | เกิดเหตุการณ์การเปลี่ยนสถานะของคำร้องฝั่งเจ้าหน้าที่สำเร็จ (เช่น ใน FR-06) |
| **เงื่อนไขก่อนทำรายการ** | 1. มีรายการแจ้งปัญหาบันทึกอยู่ในระบบ <br> 2. เจ้าหน้าที่ทำการเปลี่ยนสถานะรายการสำเร็จ |
| **ผลลัพธ์ที่คาดหวัง** | 1. ระบบสร้างและส่งข้อความแจ้งเตือนไปยังผู้แจ้งผ่านบริการ Notification (EXT-02) <br> 2. หน้าติดตามสถานะฝั่งผู้แจ้งอัปเดตสถานะใหม่ตรงกันทันที |
| **Business Rules** | **BR-04** (เชื่อมโยงเหตุการณ์เปลี่ยนสถานะจากระบบ) |
| **NFR ที่เกี่ยวข้อง** | **NFR-02** (ระบบส่งสัญญาณแจ้งเตือนและอัปเดตสถานะอย่างรวดเร็วภายใน 10 วินาที) |
| **วิธีตรวจสอบ** | **Scenario Test (VF-04)**: เจ้าหน้าที่กดเปลี่ยนสถานะคำร้องเป็น In Progress หรือ Resolved -> ผู้แจ้งได้รับการแจ้งเตือนและหน้าติดตามสถานะแสดงข้อมูลใหม่ทันที |

---

### Deep Specification 4 — ระบบเรียกดูประวัติการแจ้งปัญหาย้อนหลัง (Historical Tracking System)

> *(ข้อกำหนด FR-10 สำหรับระบบเรียกดูประวัติการแจ้งปัญหาย้อนหลัง)*

| ฟิลด์ | รายละเอียด |
|---|---|
| **Requirement ID** | **FR-10** |
| **System Name** | ระบบเรียกดูประวัติการแจ้งปัญหาย้อนหลัง (Historical Tracking System) |
| **Statement** | ระบบต้องรองรับการเรียกดูประวัติการแจ้งปัญหาย้อนหลัง เพื่อให้ผู้ใช้งานและผู้ดูแลระบบสามารถตรวจสอบรายละเอียด สถานะการดำเนินงาน ประวัติการเปลี่ยนสถานะ และผลการแก้ไขปัญหาที่ผ่านมาได้อย่างเป็นระบบ |
| **Rationale** | เพื่อให้ผู้แจ้งตรวจสอบประวัติคำร้องเดิมของตนเอง และให้ผู้ดูแลใช้ในการตรวจสอบย้อนหลัง (Auditability) และวิเคราะห์ผลการแก้ไขปัญหา (E-08, E-09) |
| **Trigger** | ผู้ใช้งานกดเข้าสู่หน้า "ประวัติการแจ้งปัญหาย้อนหลัง" หรือผู้ดูแลระบบเรียกดูประวัติคำร้อง |
| **เงื่อนไขก่อนทำรายการ** | 1. ลงชื่อเข้าใช้งานระบบด้วยบทบาทผู้ใช้ <br> 2. ระบบมีข้อมูลประวัติคำร้องและ Audit Log บันทึกอยู่ในฐานข้อมูล (DR-05) |
| **ผลลัพธ์ที่คาดหวัง** | 1. ระบบแสดงรายการประวัติคำร้องย้อนหลังเรียงตามลำดับเวลา <br> 2. แสดงรายละเอียดสถานที่ สถานะ บันทึกผลการแก้ไข และประวัติเวลาการดำเนินการครบถ้วน <br> 3. ระบบป้องกันการแก้ไขหรือลบข้อมูลประวัติโดยผู้ใช้ทุกกลุ่ม (Append-only / Read-only) |
| **Business Rules** | **BR-04** (ประวัติการดำเนินงานและ Audit Log ต้องถูกบันทึกโดยอัตโนมัติและไม่อาจถูกแก้ไขหรือลบได้) |
| **NFR ที่เกี่ยวข้อง** | **NFR-03** (ควบคุมการเข้าถึงข้อมูลประวัติตามบทบาท RBAC) |
| **วิธีตรวจสอบ** | **Audit Inspection (VF-05)**: เข้าสู่หน้าเรียกดูประวัติย้อนหลัง -> เรียกดูคำร้องที่เสร็จสิ้นแล้ว -> ตรวจสอบรายละเอียดและผลการแก้ไข -> ทดสอบพยายามแก้ไข/ลบข้อมูล -> ระบบปฏิเสธการแก้ไข |

---

#### 4. Business Rules
| BR ID | Rule Statement | Applied Target | Source |
| ------ | ------ | ------ | ------ |
| BR-01 | รายการแจ้งปัญหาต้องมีข้อมูลสถานที่ (อาคาร/ชั้น/จุด) รายละเอียดประเภทปัญหา และรูปภาพประกอบครบถ้วนก่อนส่งเข้าสู่ระบบ | FR-01, FR-02 | C-01, N-01 |
| BR-02 | เฉพาะเจ้าหน้าที่ที่มีสิทธิ์ตามบทบาท (RBAC) เท่านั้นที่มีสิทธิ์เปิดดู เปลี่ยนสถานะคำร้อง หรือบันทึกผลการดำเนินงาน | FR-05, FR-06, FR-07 | RC-06, E-08 |
| BR-03 | คำร้องจะสามารถเปลี่ยนสถานะเป็น 'Resolved' ได้ ต้องมีการบันทึกผลการดำเนินงานเรียบร้อยแล้วเท่านั้น | FR-06, FR-07 | RC-06, E-07 |
| BR-04 | บันทึกประวัติการดำเนินงานและ Audit Log ต้องถูกบันทึกโดยอัตโนมัติและไม่สามารถถูกแก้ไขหรือลบได้โดยผู้ใช้ทุกกลุ่ม | FR-10, NFR-03 | RC-05, E-08 |

---

#### 5. Non-functional Requirements
| NFR ID | Quality Requirement | Measure / Constraint | Priority | Verification |
| ------ | ------ | ------ | ------ | ------ |
| NFR-01 | ระบบต้องให้ผู้ใช้งานสร้างและส่งรายการแจ้งปัญหาได้ภายในไม่เกิน 3 ขั้นตอน หลังเข้าสู่หน้าแจ้งปัญหา | Steps ≤ 3 | Should | Usability Test |
| NFR-02 | ระบบต้องตอบสนองและแสดงผลลัพธ์ของการดำเนินการหลัก (การสร้างคำร้อง อัปเดตสถานะ ส่งแจ้งเตือน) ภายในไม่เกิน 10 วินาที ภายใต้เครือข่ายปกติ | Response Time ≤ 10s | Must | Performance Test |
| NFR-03 | ระบบต้องควบคุมการเข้าถึงข้อมูลและฟังก์ชันตามบทบาทของผู้ใช้งาน (RBAC) และจัดเก็บประวัติการทำงานแบบ Append-only | Role-based Access & Append-only | Must | Security Audit |

---

#### 6. Data Requirements (Conceptual Data Requirements)
ส่วนนี้ระบุข้อกำหนดข้อมูลระดับแนวคิด (Conceptual Data Model) สำหรับระบบแจ้งปัญหาพื้นที่ส่วนกลาง

| DR ID | Concept / Entity | Minimum Required Data | Relationships | Classification | Source | Status |
| ------ | ------ | ------ | ------ | ------ | ------ | ------ |
| **DR-01** | **Issue Report (รายการแจ้งปัญหา)** | Report ID, Issue Category, Building, Floor/Spot, Description, Photo URL/Path, Created Timestamp, Current Status | 1:Many กับ Worklog, 1:Many กับ Audit Log, Many:1 กับ Location Master | Core Domain Data | FR-01, FR-02, E-01, E-02 | **Ready / Covered** |
| **DR-02** | **Location Master (สถานที่และอาคาร)** | Building ID, Building Name, Floor Level, Zone/Spot Description | 1:Many กับ Issue Report | Master Data | FR-01, 01-problem-brief-v0.1.md | **Ready / Covered** |
| **DR-03** | **User & Role (ผู้ใช้งานและสิทธิ์)** | User ID, Full Name, User Type/Role (Student, Staff, Admin), Contact Info | 1:Many กับ Issue Report, 1:Many กับ Worklog | Master / Security Data | NFR-03, 02-stakeholder-context-scope.md | **Ready / Covered** |
| **DR-04** | **Task Progress & Worklog (ผลการทำงาน)** | Worklog ID, Report ID, Performed By (Staff ID), Action Notes, Completion Timestamp | Many:1 กับ Issue Report | Transaction Data | FR-06, FR-07, E-06, E-07 | **Ready / Covered** |
| **DR-05** | **Audit Log & History (ประวัติย้อนหลัง)** | Log ID, Report ID, Action Type, Action Timestamp, Performed By, Old Status, New Status | Many:1 กับ Issue Report | Audit / Compliance Data | FR-10, BR-04, E-08, E-09 | **Ready / Covered** |
| **DR-06** | **Notification Payload (ข้อมูลแจ้งเตือน)** | Notification ID, Report ID, Recipient ID, Message Text, Sent Timestamp, Read Status | Many:1 กับ Issue Report, Many:1 กับ User | Event Data | FR-09, E-08, E-09 | **Ready / Covered** |

##### รายละเอียดของโครงสร้างข้อมูล:
* **DR-01: Issue Report (รายการแจ้งปัญหา)**
  * **ความหมายทางธุรกิจ**: ข้อมูลคำร้องแจ้งปัญหาพื้นที่ส่วนกลางที่ผู้ใช้งานส่งเข้าสู่ระบบ
  * **ข้อมูลขั้นต่ำที่จำเป็น**: Report ID (หมายเลขอ้างอิง), Category ID, Building ID, Floor/Spot, Description, Photo URL/Path, Created Timestamp, Current Status (`Open`, `In Progress`, `Resolved`)
  * **ความสัมพันธ์**: Many:1 กับ Location Master, 1:Many กับ Task Progress & Worklog, 1:Many กับ Audit Log & History
* **DR-04: Task Progress & Worklog (ผลการทำงาน)**
  * **ความหมายทางธุรกิจ**: บันทึกการปฏิบัติงานและรายละเอียดผลการดำเนินงานแก้ไขปัญหาของเจ้าหน้าที่
  * **ข้อมูลขั้นต่ำที่จำเป็น**: Worklog ID, Report ID, Staff ID, Action Notes (รายละเอียดการแก้ไข), Completion Timestamp
* **DR-05: Audit Log & History (ประวัติย้อนหลัง)**
  * **ความหมายทางธุรกิจ**: ประวัติบันทึกการดำเนินงานย้อนหลังสำหรับเรียกดูและตรวจสอบย้อนหลัง
  * **ข้อมูลขั้นต่ำที่จำเป็น**: Log ID, Report ID, Action Type, Timestamp, Performed By, Before/After State ( Append-only ป้องกันการแก้ไข/ลบ)

---

#### 7. Behavioral Model References
| Model | IDs / Version | Requirement Anchors | Coverage / Gap | SRS Use |
| ------ | ------ | ------ | ------ | ------ |
| **User Stories** | US-01, US-02, US-03, US-04, US-09 / v1.0 | FR-01, FR-02, FR-05, FR-06, FR-07, FR-09, FR-10 | Covered | Section 3, Section 4, Section 5 |
| **Use Cases** | UC-01, UC-02, UC-03, UC-04 / v1.0 | FR-01, FR-02, FR-05, FR-06, FR-07, FR-09, FR-10 | Covered | Section 3, Section 4, Section 5 |
| **Acceptance Criteria** | AC-01, AC-02, AC-03, AC-04, AC-09 / v1.0 | FR-01, FR-02, FR-05, FR-06, FR-07, FR-09, FR-10 | Covered | Section 11 |

##### 7.1 Lifecycle Rules & State Transitions
| From State | Trigger Event | To State | Guard Condition / Rule | Source |
| ------ | ------ | ------ | ------ | ------ |
| None | ผู้แจ้งส่งรายงานปัญหาสำเร็จ | Open | ข้อมูลสถานที่และรูปภาพครบถ้วน (BR-01) | FR-01, FR-02 |
| Open | เจ้าหน้าที่เปิดดูและรับเรื่องดำเนินการ | In Progress | ดำเนินการโดยเจ้าหน้าที่ที่มีสิทธิ์ (BR-02) | FR-05, FR-06 |
| In Progress | เจ้าหน้าที่แก้ไขเสร็จและบันทึกผลงาน | Resolved | บันทึกผลการดำเนินงานเรียบร้อย (BR-03) | FR-06, FR-07 |
| Any State | เกิดการเปลี่ยนสถานะหรืออัปเดตข้อมูล | (Current State) | ส่ง Notification ไปผู้แจ้ง (FR-09) & บันทึกลง Audit Log (BR-04) | FR-09, FR-10 |

#### 8. External Interface Requirements
| Interface | Requirement/data | Direction | Owner | Failure/privacy concern | Status |
| ------ | ------ | ------ | ------ | ------ | ------ |
| **EXT-01** (University Identity Service) | User Credentials, Role Data (Inbound) | Inbound | Dev Team | ระบบยืนยันตัวตนล่ม หรือ Token ผิดพลาด | Core Scope |
| **EXT-02** (Notification Service) | Event Alert, Status Update Payload | Outbound | Dev Team | สัญญาณเครือข่ายขัดข้อง ทำให้แจ้งเตือนล่าช้า | Core Scope |
| **EXT-03** (File / Storage Service) | Photo Upload Binary, Image URL | Bi-directional | Dev Team | อัปโหลดไฟล์ล้มเหลว หรือขนาดไฟล์เกินกำหนด | Supporting Scope |

---

#### 9. Traceability and Coverage
| Source Evidence | W05 Requirement | W06 Behavioral Model | SRS Section | Verification ID | Coverage Status |
| ------ | ------ | ------ | ------ | ------ | ------ |
| E-01, E-02 | FR-01 (Must) | US-01, UC-01, AC-01 | Section 3.1, 3.4 | VF-01 | **Covered** |
| E-01, E-02 | FR-02 (Must) | US-01, UC-01, AC-01 | Section 3.1, 3.4 | VF-01 | **Covered** |
| E-05, E-06 | FR-05 (Must) | US-03, UC-03, AC-03 | Section 3.2, 3.4 | VF-02 | **Covered** |
| E-06, E-07 | FR-06 (Must) | US-04, UC-03, AC-04 | Section 3.2, 3.4 | VF-03 | **Covered** |
| E-06, E-07 | FR-07 (Must) | US-04, UC-03, AC-04 | Section 3.2, 3.4 | VF-03 | **Covered** |
| E-08, E-09 | FR-09 (Must) | US-02, UC-02, AC-02 | Section 3.3, 3.4 | VF-04 | **Covered** |
| E-08, E-09 | FR-10 (Must) | US-09, UC-04, AC-09 | Section 3.3, 3.4 | VF-05 | **Covered** |
| C-01, N-01 | BR-01 (Must) | US-01, UC-01, AC-01 | Section 4 | VF-01 | **Covered** |
| RC-06, E-08 | BR-02 (Must) | US-03, US-04, UC-03 | Section 4 | VF-02, VF-03 | **Covered** |
| RC-06, E-07 | BR-03 (Must) | US-04, UC-03, AC-04 | Section 4 | VF-03 | **Covered** |
| RC-05, E-08 | BR-04 (Must) | US-09, UC-04, AC-09 | Section 4 | VF-05 | **Covered** |
| E-09 | NFR-01 (Should) | - | Section 5 | VF-06 | **Covered** |
| E-13 | NFR-02 (Must) | - | Section 5 | VF-07 | **Covered** |
| E-14, E-08 | NFR-03 (Must) | US-09, UC-04, AC-09 | Section 5 | VF-05 | **Covered** |

---

#### 10. Open Issues
| OI | Question/TBD | Affected IDs | Owner | Next action | Expected evidence | Needed by |
| ------ | ------ | ------ | ------ | ------ | ------ | ------ |
| **ISS-01** | รูปแบบและประเภทไฟล์รูปภาพที่อนุญาตสำหรับการแนบประกอบคำร้อง (Max file size / formats) | FR-02, EXT-03 | นาย นนทชัย ไทยตัน | สรุปเกณฑ์ขนาดไฟล์รูปภาพและนโยบายจัดเก็บ | Storage Specification Doc | Week 08 |
| **ISS-02** | ช่องทางและรูปแบบการส่ง Notification (In-app, Push Notification) | FR-09, EXT-02 | นาย ภูมิพัฒน์ วงศ์ดาว | สอบถามผู้ใช้และทีมพัฒนาเพื่อสรุปรูปแบบข้อความและช่องทางส่ง | Notification Spec | Week 08 |
| **ISS-03** | ระยะเวลาการจัดเก็บข้อมูลประวัติย้อนหลัง (Data Retention Policy for History Log) | FR-10, BR-04 |นางสาว ณัฐณิชา ปกแก้ว | กำหนดกรอบเวลาการสำรองและเก็บประวัติคำร้องย้อนหลัง | Data Retention Policy | Week 08 |

---

#### 11. Verification Plan
| VF ID | Method | Target IDs | Procedure / Evidence | Owner | Status |
| ------ | ------ | ------ | ------ | ------ | ------ |
| **VF-01** | Demonstration | FR-01, FR-02, BR-01 | **Procedure**: กรอกข้อมูลแจ้งปัญหา ระบุสถานที่ แนบรูป 1 รูป แล้วกดส่ง <br>**Pass Criteria**: ระบบบันทึกคำร้อง ออก Report ID และแสดงสถานะ Open สัมฤทธิ์ผล | QA Tester | Planned |
| **VF-02** | Inspection | FR-05, BR-02 | **Procedure**: เจ้าหน้าที่เปิดดูหน้ารายการคำร้องที่เข้ามา <br>**Pass Criteria**: แสดงรายการคำร้องและรายละเอียดทั้งหมดได้อย่างถูกต้องตามสิทธิ์ RBAC | QA Tester | Planned |
| **VF-03** | Boundary Test | FR-06, FR-07, BR-03 | **Procedure**: ทดสอบเปลี่ยนสถานะเป็น Resolved โดยเว้นว่างช่องบันทึกผลงาน และทดสอบกรอกผลงานแล้วเปลี่ยนสถานะ <br>**Pass Criteria**: ระบบปฏิเสธกรณีไม่กรอกผลงาน และเปลี่ยนสถานะสำเร็จเมื่อกรอกข้อมูลครบถ้วน | QA Tester | Planned |
| **VF-04** | Scenario Test | FR-09 | **Procedure**: เปลี่ยนสถานะคำร้องของฝั่งเจ้าหน้าที่ แล้วตรวจุดการแจ้งเตือนฝั่งผู้แจ้ง <br>**Pass Criteria**: ผู้แจ้งได้รับการแจ้งเตือนและหน้าติดตามสถานะอัปเดตข้อมูลตรงกันทันที | QA Tester | Planned |
| **VF-05** | Audit Test | FR-10, BR-04, NFR-03 | **Procedure**: เรียกดูหน้าประวัติการแจ้งปัญหาย้อนหลัง และทดสอบพยายามแก้ไข/ลบประวัติ <br>**Pass Criteria**: แสดงประวัติถูกต้องตามลำดับเวลา และระบบไม่อนุญาตให้แก้ไข/ลบประวัติข้อมูล | Security Auditor | Planned |
| **VF-06** | Usability Test | NFR-01 | **Procedure**: ทดสอบผู้ใช้ใหม่สร้างรายการแจ้งปัญหาตั้งแต่เปิดหน้าฟอร์มจนส่งสำเร็จ <br>**Pass Criteria**: สามารถทำรายการสำเร็จได้ภายในไม่เกิน 3 ขั้นตอน | UX Designer | Planned |
| **VF-07** | Performance Test | NFR-02 | **Procedure**: วัดเวลาตอบสนองของระบบในการบันทึกข้อมูล อัปเดตสถานะ และแสดงผล <br>**Pass Criteria**: ประมวลผลและแสดงผลสำเร็จภายในไม่เกิน 10 วินาที | Backend Dev | Planned |

---

#### 12. Review Gate
* [x] W05 FR/BR/NFR/DR ทุกข้อมี disposition
* [x] W06 US/UC/AC ย้อนกลับ W05 ได้
* [x] Deep Specification ทั้ง 4 ระบบย่อยครอบคลุม FR-01, FR-02, FR-05, FR-06, FR-07, FR-09, FR-10 สมบูรณ์
* [x] Open Issues ทุกข้อมี owner/action/evidence
* [x] Status เป็น Baseline Candidate

---

#### Appendix A — Requirement Disposition
| Backlog ID | Included/Deferred/Extension/Issue | SRS section | Reason |
| ------ | ------ | ------ | ------ |
| FR-01 | End-to-End Core | Section 3.1, 3.4 | ความสามารถหลักในการแจ้งปัญหาพื้นที่ส่วนกลาง |
| FR-02 | End-to-End Core | Section 3.1, 3.4 | หลักฐานรูปภาพประกอบคำร้อง |
| FR-05 | End-to-End Core | Section 3.2, 3.4 | ความสามารถของเจ้าหน้าที่ในการเปิดดูคำร้อง |
| FR-06 | End-to-End Core | Section 3.2, 3.4 | ความสามารถของเจ้าหน้าที่ในการอัปเดตสถานะ |
| FR-07 | End-to-End Core | Section 3.2, 3.4 | บันทึกผลการดำเนินงานและผลการแก้ไขงาน |
| FR-09 | End-to-End Core | Section 3.3, 3.4 | การแจ้งเตือนผู้แจ้งเมื่อสถานะเปลี่ยนแปลง |
| FR-10 | End-to-End Core | Section 3.3, 3.4 | การเรียกดูประวัติการแจ้งปัญหาย้อนหลังอย่างเป็นระบบ |
| BR-01 | End-to-End Core | Section 4 | กฎข้อมูลขั้นต่ำและการแนบรูปภาพก่อนส่ง |
| BR-02 | End-to-End Core | Section 4 | กฎสิทธิ์การเข้าถึงและการจัดการคำร้องโดยเจ้าหน้าที่ |
| BR-03 | End-to-End Core | Section 4 | กฎบังคับบันทึกผลการดำเนินงานก่อนปิดงาน |
| BR-04 | End-to-End Core | Section 4 | กฎการบันทึก Audit Log และประวัติแบบ Append-only |
| NFR-01 | Supporting Core | Section 5 | ข้อกำหนดด้าน Usability (≤ 3 ขั้นตอน) |
| NFR-02 | Supporting Core | Section 5 | ข้อกำหนดด้าน Performance (Response ≤ 10s) |
| NFR-03 | End-to-End Core | Section 5 | ข้อกำหนดด้าน Security & RBAC |

---

#### Appendix B — Review and Revision History
| Item | Before | After | Reason / Source | Reviewer |
| ------ | ------ | ------ | ------ | ------ |
| **REV-01** | ใช้ขอบเขต FR หลากหลายและยังไม่จัดกลุ่ม Deep Specification ตามระบบย่อย | ปรับปรุง Section 3 ปรับตาราง FR-01, FR-02, FR-05, FR-06, FR-07, FR-09, FR-10 ตามข้อกำหนดใหม่ | จัดทำขอบเขตและโครงสร้างระบบให้ชัดเจนตามความต้องการของโครงการ | System Analyst |
| **REV-02** | Deep Specification แยกรายข้อ | จัดกลุ่ม Deep Specification ออกเป็น 4 ระบบย่อย: (1) FR-01+FR-02, (2) FR-05+FR-06+FR-07, (3) FR-09, (4) FR-10 | ตามข้อกำหนดการจัดกลุ่มระบบของโครงการ | System Analyst |
| **REV-03** | เอกสารปรับอัปเดตต่อเนื่อง | ปรับอัปเดต Traceability, Verification Plan, Data Requirements ให้ตรงกับ 7 FRs | เพื่อความสอดคล้องสมบูรณ์ของเอกสาร SRS ทั้งเล่ม | System Analyst |

---
