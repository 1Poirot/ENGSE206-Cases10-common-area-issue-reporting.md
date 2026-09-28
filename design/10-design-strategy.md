# 10 — Design Strategy and Rationale

> **Week 10 deliverable**  
> **โครงการ:** ระบบแจ้งปัญหาพื้นที่ส่วนกลางและติดตามการแก้ไข (Common Area Issue Reporting)  
> **ทีม:** Group 10 | **เวอร์ชัน:** 1.0 (Draft for Week 10) | **วันที่:** 23/09/2026  
> **เอกสารอ้างอิงหลัก:** [07-srs-v1.md](../docs/07-srs-v1.md), [05-requirement-backlog.md](../docs/05-requirement-backlog.md), [06-requirement-models.md](../docs/06-requirement-models.md), [decision-log.md](../project-management/decision-log.md)

---

## 1. Design Goals

การแปลง Functional Requirements (FR) และ Non-Functional Requirements (NFR) จากเอกสาร [07-srs-v1.md](../docs/07-srs-v1.md) ให้เป็นเป้าหมายและแนวทางการออกแบบเชิงระบบ (Design Goals):

| Goal | Related Requirement | Design Implication |
|---|---|---|
| **DG-01: การแจ้งปัญหาที่สะดวกรวดเร็วและได้ข้อมูลครบถ้วนในครั้งเดียว (Frictionless & Complete Issue Reporting)** | FR-01, FR-02, NFR-01, BR-01 (FR-CAR-01, FR-CAR-02, NFR-CAR-01) | ออกแบบแบบฟอร์มการแจ้งปัญหาในหน้าเดียวที่ทำรายการสำเร็จได้ภายใน ≤ 3 ขั้นตอน มีตัวเลือก Dropdown สำหรับอาคาร ชั้น และประเภทปัญหาเพื่อลดการพิมพ์ผิดพลาด มีระบบตรวจจับและบังคับแนบรูปภาพอย่างน้อย 1 รูป พร้อมระบบ Client-side Image Preview และ Image Compression เพื่อลดขนาดไฟล์ก่อนอัปโหลด |
| **DG-02: ความโปร่งใสและการติดตามสถานะอย่างต่อเนื่อง (End-to-End Transparency & Status Tracking)** | FR-04, FR-09, NFR-02 (FR-CAR-04, FR-CAR-09, NFR-CAR-02) | ออกแบบสถานะวงจรชีวิตคำร้องให้ชัดเจน (`Open` → `In Progress` → `Resolved`), จัดทำหน้ารายการติดตามงานพร้อมแสดง Timeline ความคืบหน้า และพัฒนาระบบ Event-driven Notification Service เพื่อส่งการแจ้งเตือนไปยังผู้แจ้งทันทีเมื่อสถานะมีการเปลี่ยนแปลง |
| **DG-03: การบริหารคิวงานและการแก้ไขปัญหาของเจ้าหน้าที่อย่างมีประสิทธิภาพ (Effective Operational Management & Workflow Control)** | FR-05, FR-06, FR-07, FR-08 (FR-CAR-05, FR-CAR-06, FR-CAR-07, FR-CAR-08), BR-02, BR-03 | ออกแบบ Staff Management Console สำหรับเจ้าหน้าที่ โดยมีฟังก์ชัน Search, Filter และ Sort ตามอาคารและประเภทปัญหา มีระบบ State Transition Guard บังคับให้เจ้าหน้าที่ต้องกรอกบันทึกผลการดำเนินงาน (Worklog Notes) ก่อนจึงจะสามารถเปลี่ยนสถานะเป็น `Resolved` (ปิดงาน) ได้ |
| **DG-04: การควบคุมความปลอดภัยและการตรวจสอบย้อนหลังได้โดยสมบูรณ์ (Security, Least Privilege & Auditability)** | FR-10, NFR-03, BR-04 (FR-CAR-10, NFR-CAR-03) | บังคับใช้ Role-Based Access Control (RBAC) เพื่อแยกสิทธิ์ระหว่างผู้แจ้ง (Reporter), เจ้าหน้าที่ (Staff) และผู้ดูแลระบบ (Admin) อย่างเด็ดขาด และออกแบบระบบจัดเก็บประวัติการทำงาน (Audit Log) แบบ Append-only ป้องกันการแก้ไขหรือลบข้อมูลย้อนหลัง |
| **DG-05: ประสิทธิภาพการตอบสนองและความพร้อมใช้งานบนอุปกรณ์พกพา (High Performance & Responsive Accessibility)** | NFR-02, EXT-02, EXT-03 (NFR-CAR-02) | ออกแบบสถาปัตยกรรมระบบให้ตอบสนองภายใน ≤ 10 วินาที (และรองรับการประมวลผลทั่วไป ≤ 2–3 วินาที), แยกการจัดเก็บไฟล์รูปภาพไปยัง Dedicated File/Object Storage (EXT-03) และเก็บเฉพาะ URL ในฐานข้อมูลหลัก เพื่อลดภาระของฐานข้อมูลและเพิ่มความเร็วในการ Query |

---

## 2. Design Principles

หลักการออกแบบที่ทีมยึดถือในการตัดสินใจด้าน Architecture, Data และ UX/UI:

1. **Simplicity & Low Friction (ความเรียบง่ายและลดภาระผู้ใช้งาน):**  
   เนื่องจากผู้ใช้แจ้งปัญหาจากพื้นที่จริง มักอยู่ในสถานการณ์เร่งด่วน การรายงานปัญหาต้องรวดเร็ว ชัดเจน มีขั้นตอนไม่เกิน 3 ขั้นตอน ใช้ตัวเลือกแบบ Dropdown/Radio มากกว่าการพิมพ์ข้อความยาว และสามารถถ่าย/แนบรูปภาพได้ทันที
2. **Transparency & Two-Way Feedback Loop (ความโปร่งใสและการสื่อสารสองทิศทาง):**  
   ทุกคำร้องต้องมีหมายเลขอ้างอิง (Report ID) ที่ไม่ซ้ำกัน ผู้ใช้งานสามารถตรวจสอบสถานะได้ตลอดเวลา และเมื่อเจ้าหน้าที่อัปเดตสถานะหรือปิดงาน ระบบต้องส่งข้อความแจ้งเตือนพร้อมแสดงผลการแก้ไขกลับไปยังผู้แจ้งอย่างชัดเจน
3. **Role-Based Separation of Concerns & Least Privilege (การแบ่งแยกหน้าที่และสิทธิ์ขั้นต่ำ):**  
   ผู้ใช้งานแต่ละบทบาท (`Reporter`, `Staff`, `Administrator`) เข้าถึงเฉพาะข้อมูลและฟังก์ชันที่ได้รับมอบหมายเท่านั้น เช่น ผู้แจ้งไม่สามารถเข้าถึงหน้าจัดการคิวงานของเจ้าหน้าที่ และไม่สามารถแก้ไขสถานะคำร้องได้
4. **Data Integrity & Immutability of History (ความถูกต้องของข้อมูลและการคงรูปของประวัติย้อนหลัง):**  
   บันทึกประวัติสถานะ (Status History) และ Audit Log ต้องเป็นแบบ Append-only (ห้ามแก้ไขหรือลบ) เพื่อให้สามารถตรวจสอบย้อนหลังได้อย่างโปร่งใสตามข้อกำหนดการตรวจสอบความถูกต้องของมหาวิทยาลัย
5. **Progressive Disclosure & Proactive Validation (การทยอยแสดงผลและการดักจับข้อผิดพลาดเชิงรุก):**  
   แสดงเฉพาะข้อมูลที่จำเป็นในแต่ละขั้นตอนของหน้าจอ และใช้การตรวจสอบข้อมูล (Validation) ทันทีที่ฝั่ง Client (เช่น ตรวจสอบว่าแนบรูปภาพหรือยัง ระบุอาคารครบถ้วนหรือไม่) เพื่อลดข้อผิดพลาดก่อนส่งข้อมูลเข้าสู่เซิร์ฟเวอร์
6. **Mobile-First & Accessibility (การออกแบบโดยเน้นอุปกรณ์พกพาและการเข้าถึงที่เท่าเทียม):**  
   ระบบต้องรองรับการแสดงผลแบบ Responsive บนเว็บเบราว์เซอร์ของสมาร์ตโฟน มีขนาดปุ่มสัมผัสที่เหมาะสม มีระดับสีและคอนทราสต์ที่ผ่านเกณฑ์ Accessibility เพื่อให้ทุกคนสามารถใช้งานได้สะดวก

---

## 3. Candidate Strategies / Alternatives

การเปรียบเทียบทางเลือกในการออกแบบ สถาปัตยกรรม และเทคโนโลยี พร้อมเหตุผลและ Trade-offs ที่เกิดขึ้น:

| Decision Area | Option A | Option B | Selected Option | Rationale | Trade-off |
|---|---|---|---|---|---|
| **Client Platform Architecture (รูปแบบแพลตฟอร์มฝั่งผู้ใช้งาน)** | **Native Mobile App** (iOS / Android) | **Responsive Web App** (Mobile-first Web / PWA) | **Option B: Responsive Web App** | ผู้ใช้งาน (นักศึกษาและบุคลากร) ต้องการแจ้งปัญหาทันทีเมื่อพบเห็น การใช้ Responsive Web ทำให้สามารถเข้าใช้งานผ่านเบราว์เซอร์บนมือถือหรือสแกน QR Code ประจำจุดได้ทันที โดยไม่ต้องเสียเวลาดาวน์โหลดหรือติดตั้งแอปพลิเคชันจาก Store สอดคล้องกับเกณฑ์ความสะดวกรวดเร็ว (NFR-01) | ไม่สามารถเข้าถึงฟังก์ชันระดับลึกของระบบปฏิบัติการมือถือได้เต็มรูปแบบเหมือน Native App แต่เพียงพอสำหรับฟังก์ชันการแจ้งปัญหา แนบรูปภาพ และติดตามสถานะ |
| **User Authentication & Identity Strategy (การยืนยันตัวตนและการจัดการสิทธิ์)** | **Local User Management** (สร้างระบบสมัครสมาชิกและจัดการรหัสผ่านเอง) | **University Identity Service (SSO)** (เชื่อมต่อระบบยืนยันตัวตนกลางของมหาวิทยาลัย - EXT-01) | **Option B: University Identity Service (SSO)** | มหาวิทยาลัยมีฐานข้อมูลบัญชีนักศึกษาและบุคลากรอยู่แล้ว การเชื่อมต่อ SSO ช่วยลดภาระผู้ใช้ไม่ต้องจำรหัสผ่านใหม่ ป้องกันการสร้างบัญชีปลอม/สแปมคำร้อง และสามารถระบุบทบาท (Role) ของผู้ใช้เพื่อผูกกับสิทธิ์ RBAC ได้อย่างน่าเชื่อถือ (NFR-03) | มี External Dependency กับระบบ Identity กลาง หากระบบดังกล่าวขัดข้องจะส่งผลต่อการเข้าสู่ระบบ จึงจำเป็นต้องมีระบบจัดการ Session และ Error Handling ที่รัดกุม |
| **Media & File Storage Strategy (การจัดเก็บไฟล์รูปภาพประกอบคำร้อง)** | **Database BLOB / Base64** (จัดเก็บไฟล์ภาพลงตารางในฐานข้อมูลหลักโดยตรง) | **Dedicated File/Object Storage** (แยกเก็บไฟล์บน Storage Service แล้วเก็บเฉพาะ URL/Path ในฐานข้อมูล - EXT-03) | **Option B: Dedicated File/Object Storage + Relational DB Metadata** | รูปภาพประกอบมีขนาดใหญ่และมีจำนวนมาก (FR-02) หากเก็บลงฐานข้อมูลหลักจะทำให้ Database มีขนาดใหญ่ขึ้นอย่างรวดเร็ว (Database Bloat) และทำให้การ Query ช้าลง กระทบต่อ Performance (NFR-02) การแยกเก็บไฟล์และอ้างอิงผ่าน URL ช่วยให้ Database ทำงานได้รวดเร็วและบำรุงรักษาง่าย | สถาปัตยกรรมมี 2 จุดจัดเก็บข้อมูล (DB + File Storage) ต้องมีกลไกตรวจสอบ Transaction เพื่อป้องกันไฟล์ตกค้าง (Orphaned Files) กรณีการบันทึกล้มเหลว |
| **Status Notification Delivery Mechanism (กลไกการส่งสัญญาณแจ้งเตือน)** | **Client Polling** (ให้หน้าเว็บทำการ Request เช็กสถานะเป็นระยะๆ) | **Event-Driven Notification Service** (ระบบส่งสัญญาณแจ้งเตือนอัตโนมัติเมื่อเกิด Event เปลี่ยนสถานะ - EXT-02) | **Option B: Event-Driven Notification Service** | การเปลี่ยนสถานะของคำร้องเกิดขึ้นเป็นรายเหตุการณ์ (Event-based) การใช้ Event-driven Service ทำให้ระบบสามารถส่ง Notification ไปยังผู้แจ้งได้ทันทีเมื่อสถานะเปลี่ยน (FR-09) ประหยัด Bandwidth เครือข่าย และลดภาระของ Server ได้ดีกว่าการให้ Client ส่ง Request ถามซ้ำๆ | มีความซับซ้อนในการพัฒนาระบบ Event/Webhook มากกว่าการเขียน Polling แบบพื้นฐาน |
| **Workflow State Management & Audit Logging (การจัดการสถานะและประวัติย้อนหลัง)** | **In-place Status Update** (อัปเดตฟิลด์สถานะทับในตาราง Report โดยตรง) | **Finite State Machine (FSM) + Append-Only Audit Log** (ควบคุมสถานะผ่าน State Rules และบันทึกประวัติการเปลี่ยนแปลงลงตาราง Log แยก) | **Option B: Finite State Machine + Append-Only Audit Log** | ตอบสนองกฎทางธุรกิจ BR-03 (ต้องบันทึกผลงานก่อน Resolved) และ BR-04/FR-10 (ประวัติการทำงานต้องห้ามแก้ไขหรือลบ) FSM ช่วยป้องกันการเปลี่ยนสถานะที่ผิดขั้นตอน และตาราง Log แบบ Append-only ช่วยให้สามารถตรวจสอบย้อนหลัง (Auditability) ได้อย่างโปร่งใส | เพิ่มปริมาณการเขียนข้อมูล (Multi-table Write) ในแต่ละ Transaction และต้องจัดการขนาดของตาราง Audit Log ในระยะยาว |

---

## 4. Quality Attribute Tactics

การนำแท็กติกเชิงสถาปัตยกรรม (Architecture Tactics) มาใช้เพื่อตอบสนองต่อ Non-Functional Requirements (NFR) ของระบบ:

| Quality Attribute | Tactic | Related NFR | Evidence in Design |
|---|---|---|---|
| **Usability (ความสะดวกในการใช้งาน)** | **Minimize Steps & Cognitive Load:** รวมขั้นตอนการแจ้งปัญหาให้อยู่ในหน้าเดียว (Single-step submission form) พร้อมระบบ Dropdown รายการอาคาร/ชั้น/ประเภทปัญหา เพื่อลดการพิมพ์ และมีระบบ Preview รูปภาพก่อนส่ง | NFR-01 (ส่งคำร้องได้ภายใน ≤ 3 ขั้นตอน) | Wireframe หน้าแจ้งปัญหา (Report Form UI), Mobile UI Flow, Client-side Form Validation |
| **Performance (ประสิทธิภาพการตอบสนอง)** | **Resource Separation & Client-side Compression:** ทำ Image Compression ฝั่ง Client ก่อนอัปโหลดไฟล์ภาพ, แยกเก็บไฟล์ภาพไว้ที่ Dedicated File Storage (EXT-03), และทำ Indexing บนฟิลด์ที่ใช้ค้นหาบ่อย (Status, BuildingId, CreatedAt) ในฐานข้อมูล | NFR-02 (ระบบตอบสนองผลลัพธ์หลักภายใน ≤ 10 วินาที และการประมวลผลทั่วไป ≤ 2–3 วินาที) | Storage Architecture Design, Data Model Indexing Scheme, Sequence Diagram การส่งคำร้อง |
| **Security & Access Control (ความปลอดภัยและการควบคุมสิทธิ์)** | **Role-Based Access Control (RBAC) & Least Privilege:** ตรวจสอบสิทธิ์การเข้าถึงผ่าน Authorization Middleware ที่ Application Layer โดยแยกสิทธิ์ของ Reporter, Staff และ Administrator อย่างเด็ดขาด ป้องกันการเข้าถึงหรือแก้ไขข้อมูลข้ามบทบาท | NFR-03 (ควบคุมการเข้าถึงตามบทบาทผู้ใช้) | RBAC Permission Matrix, Data Model (`User.role`), API Route Guard Architecture |
| **Auditability & Data Integrity (ความสามารถในการตรวจสอบและความคงรูปของข้อมูล)** | **Immutable / Append-Only Audit Trail:** ตาราง `AuditLog` และ `StatusHistory` รองรับเฉพาะคำสั่ง `INSERT` เท่านั้น โดยไม่อนุญาตคำสั่ง `UPDATE` หรือ `DELETE` เพื่อบันทึกประวัติการเปลี่ยนสถานะ ผู้ดำเนินการ และเวลาอย่างครบถ้วน | NFR-03, FR-10, BR-04 | Data Model (`DR-05: Audit Log & History`), Trigger/Service Logic ในการบันทึกประวัติ, หน้ารายการ Audit Log |
| **Modifiability & Extensibility (ความยืดหยุ่นและการบำรุงรักษา)** | **Separation of Concerns & Interface Segregation:** ออกแบบระบบแบบ Layered Architecture (Presentation, Service, Data Access) และแยกการเชื่อมต่อระบบภายนอก (EXT-01, EXT-02, EXT-03) ผ่าน Service Interface | NFR-03, CT-02, EXT-01..03 | Conceptual Architecture Diagram (Week 11), Module Dependency Diagram |

---

## 5. Architecture / UX Constraints

ข้อจำกัดด้านสถาปัตยกรรม ประสบการณ์ผู้ใช้งาน และขอบเขตของระบบที่ต้องนำมาเป็นกรอบในการออกแบบ:

1. **Business Data & Input Constraints (ข้อจำกัดด้านข้อมูลนำเข้า - CT-01, BR-01):**  
   - รายการแจ้งปัญหาต้องมีข้อมูลขั้นต่ำครบถ้วน ได้แก่ อาคาร, ชั้น/ตำแหน่งที่เกิดเหตุ, หมวดหมู่ของปัญหา, คำอธิบายปัญหา และรูปภาพประกอบอย่างน้อย 1 รูป ก่อนที่ระบบจะอนุญาตให้ส่งข้อมูลเข้าสู่ระบบได้
2. **Role & Permission Constraints (ข้อจำกัดด้านสิทธิ์การเข้าถึง - CT-02, BR-02):**  
   - ระบบต้องจำกัดการเข้าถึงฟังก์ชันและข้อมูลตามบทบาท (RBAC) โดยผู้แจ้งสามารถติดตามได้เฉพาะคำร้องของตนเอง, เจ้าหน้าที่สามารถดูและจัดการเฉพาะคำร้องที่เกี่ยวข้อง, และผู้ดูแลระบบเท่านั้นที่สามารถดูประวัติ Audit Log และข้อมูลภาพรวม
3. **Workflow State Guard Constraints (ข้อจำกัดการเปลี่ยนผ่านสถานะ - CT-03, BR-03):**  
   - การปิดงานเป็นสถานะ `Resolved` จะกระทำได้ก็ต่อเมื่อเจ้าหน้าที่ได้กรอกบันทึกผลการดำเนินงาน (Work Result / Worklog) ในระบบแล้วเท่านั้น เพื่อป้องกันการปิดงานโดยไม่มีหลักฐาน
4. **Audit Immutability Constraints (ข้อจำกัดด้านการคงรูปของประวัติย้อนหลัง - CT-04, BR-04):**  
   - ข้อมูลประวัติการดำเนินงานและ Audit Log ต้องถูกสร้างขึ้นโดยอัตโนมัติจากระบบ และต้องไม่สามารถแก้ไข ดัดแปลง หรือลบได้โดยผู้ใช้งานทุกกลุ่ม (รวมถึงผู้ดูแลระบบ)
5. **Interaction & Platform Constraints (ข้อจำกัดด้านการใช้งานและแพลตฟอร์ม - NFR-01):**  
   - การแจ้งปัญหาต้องดำเนินการให้เสร็จสิ้นได้ภายในไม่เกิน 3 ขั้นตอน และต้องรองรับการแสดงผลบนสมาร์ตโฟนผ่าน Web Browser (Responsive Web) ภายใต้เครือข่ายของมหาวิทยาลัย
6. **System Scope Boundary Constraints (ข้อจำกัดขอบเขตของระบบ):**  
   - อ้างอิงตาม `docs/00-project-profile.md` และ SRS Section 2.1 ระบบจะไม่ครอบคลุม:
     - ระบบแชตสนทนาแบบเรียลไทม์ระหว่างผู้แจ้งและเจ้าหน้าที่
     - ระบบจัดซื้อจัดจ้างวัสดุอุปกรณ์และครุภัณฑ์
     - ระบบบริหารจัดการงานซ่อมบำรุงโครงสร้างอาคารขนาดใหญ่นอกระบบ
7. **External System Integration Constraints (ข้อจำกัดการเชื่อมต่อระบบภายนอก):**  
   - ระบบต้องพร้อมเชื่อมต่อกับระบบภายนอก 3 ระบบตามข้อกำหนด SRS Section 2.5:
     - **EXT-01 (University Identity Service):** สำหรับตรวจสอบและยืนยันตัวตนผู้ใช้
     - **EXT-02 (Notification Service):** สำหรับส่งสัญญาณแจ้งเตือนความคืบหน้าคำร้อง
     - **EXT-03 (File / Storage Service):** สำหรับอัปโหลดและจัดเก็บไฟล์รูปภาพประกอบ

---

## 6. Design Decisions to Record

การตัดสินใจสำคัญเชิงสถาปัตยกรรมและการออกแบบที่บันทึกไว้ใน [project-management/decision-log.md](../project-management/decision-log.md):

| Decision ID | Date | Decision Summary | Selected Option | Rationale | Impacted Artefacts | Owner |
|---|---|---|---|---|---|---|
| **D-01** | 18/08/2026 | ลบ E-03 ออกจาก Traceability Baseline | Option B: ลบ E-03 และตรวจสอบ Traceability ใหม่ | จาก Baseline Review พบว่า E-03 ไม่สามารถยืนยันความเชื่อมโยงกับ RC-03 / FR-CAR-03 ได้อย่างชัดเจน จึงเลือกตัดออกเพื่อความถูกต้องของ Traceability | `docs/05-requirement-backlog.md`, `docs/08-validation-traceability.md` | นนทชัย ไทยตัน |
| **D-02** | 23/09/2026 | เลือกสถาปัตยกรรม Client ฝั่งผู้ใช้เป็น Responsive Web Application | Option B: Responsive Web Application | ลดอุปสรรคในการใช้งาน ผู้ใช้สามารถแจ้งปัญหาผ่านเบราว์เซอร์หรือสแกน QR Code ได้ทันทีโดยไม่ต้องติดตั้งแอปพลิเคชัน สอดคล้องกับ NFR-01 | `design/10-design-strategy.md`, `design/11-conceptual-architecture.md` | ภูมิพัฒน์ วงศ์ดาว |
| **D-03** | 23/09/2026 | เชื่อมต่อระบบยืนยันตัวตนกลางของมหาวิทยาลัย (SSO) | Option B: University Identity Service (EXT-01) | ใช้ประโยชน์จากฐานข้อมูลบัญชีนักศึกษา/บุคลากรเดิม ป้องกันการปลอมแปลงบัญชี และนำ Role มาใช้กับระบบ RBAC ได้ทันที สอดคล้องกับ NFR-03 | `design/10-design-strategy.md`, `design/11-conceptual-architecture.md` | ณัฐณิชา ปกแก้ว |
| **D-04** | 23/09/2026 | แยกจัดเก็บรูปภาพบน Dedicated File/Object Storage | Option B: Dedicated File Storage (EXT-03) + DB URL | ป้องกันปัญหาฐานข้อมูลบวม (Database Bloat) และรักษาความเร็วในการ Query ข้อมูล สอดคล้องกับ NFR-02 | `design/10-design-strategy.md`, `design/13-detailed-design.md` | นนทชัย ไทยตัน |
| **D-05** | 23/09/2026 | ใช้ Finite State Machine และตาราง Audit Log แบบ Append-Only | Option B: FSM + Append-Only Log | ควบคุมการเปลี่ยนสถานะให้เป็นไปตาม Business Rules (BR-03) และเก็บบันทึกประวัติการทำงานที่ไม่สามารถแก้ไขหรือลบได้ (BR-04, FR-10) | `design/10-design-strategy.md`, `design/13-detailed-design.md` | ภูมิพัฒน์ วงศ์ดาว |
| **D-06** | 23/09/2026 | ใช้ Event-Driven Notification Service แทน Client Polling | Option B: Event-Driven Notification (EXT-02) | ส่งการแจ้งเตือนทันทีเมื่อสถานะเปลี่ยน (FR-09) ประหยัด Bandwidth เครือข่าย และลดภาระของ Server สอดคล้องกับ NFR-02 | `design/10-design-strategy.md`, `design/11-conceptual-architecture.md` | ณัฐณิชา ปกแก้ว |

> ดูรายละเอียดบันทึกการตัดสินใจฉบับเต็มได้ที่ [project-management/decision-log.md](../project-management/decision-log.md)
