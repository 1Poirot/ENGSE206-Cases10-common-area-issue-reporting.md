# 05 — Requirement Backlog v0.1: Campus Resource Booking

## 1. Project Metadata

| Field | Value |
|---|---|
| Course / Week | ENGSE206 / Week05 |
| Team | Group 10 |
| Case | ระบบแจ้งปัญหาพื้นที่ส่วนกลางและติดตามการแก้ไข |
| Source Week04 file | `04-evidence-log.md` |
| Backlog version | `v0.1` |
| Date | 2026-08-11 |

## 2. Prioritization Method

ใช้ MoSCoW โดยไม่ใช้ความรู้สึกของทีมเป็นหลัก แต่ดูจาก 4 มิติ

| Dimension | วิธีใช้ในตัวอย่างนี้ |
|---|---|
| Value | ช่วยผู้แจ้งปัญหาและเจ้าหน้าที่ในการแจ้ง รับเรื่อง แก้ไข และติดตามปัญหาได้หรือไม่|
| Risk | ถ้าขาด Requirement นี้ จะทำให้ปัญหาตกหล่น งานล่าช้า ติดตามไม่ได้ หรือเกิดความเสี่ยงด้านความปลอดภัยหรือไม่ |
| Urgency | จำเป็นต่อ Workflow หลักของระบบใน Release แรก หรือสามารถพัฒนาเพิ่มเติมภายหลังได้ |
| Dependency | ต้องรอ Policy, ผู้รับผิดชอบ, สิทธิ์การเข้าถึง, ช่องทางแจ้งเตือน หรือข้อมูลจากระบบอื่นก่อนหรือไม่ |

## 3. Requirement Backlog v0.1

| Req ID | Source RC | Evidence / Need Trace | Requirement Statement | Type | Priority | Rationale | Status | Open Question | Week06 Use |
|---|---|---|---|---|---|---|---|---|---|
| **FR-CAR-01**    | RC-01     | E-01, E-02 → N-REPORT   | ระบบต้องให้ผู้ใช้งานแจ้งปัญหาพื้นที่ส่วนกลาง โดยระบุรายละเอียดปัญหา อาคาร ตำแหน่ง และประเภทของปัญหา | Functional                     | **Must**      | เป็น capability หลักของระบบและช่วยให้การแจ้งปัญหาเป็นระบบ     | Ready for Week06 | ข้อมูลขั้นต่ำที่ต้องระบุมีอะไรบ้าง             | Use Case + User Story         |
| **FR-CAR-02**    | RC-02     | E-01, E-02 → N-EVIDENCE | ระบบต้องให้ผู้ใช้งานแนบรูปภาพประกอบการแจ้งปัญหาได้                                                  | Functional                     | **Must**      | ช่วยให้เจ้าหน้าที่เห็นหลักฐานและเข้าใจลักษณะของปัญหาได้ชัดเจน | Ready for Week06 | จำนวนและขนาดรูปภาพที่อนุญาตเท่าไร              | User Story + AC               |
| **FR-CAR-03**    | RC-03     | E-03 → N-TRACK          | ระบบต้องสร้างหมายเลขอ้างอิงสำหรับรายการแจ้งปัญหาแต่ละรายการ                                         | Functional                     | **Must**      | ใช้สำหรับอ้างอิงและติดตามรายการปัญหาแต่ละรายการ               | Ready for Week06 | รูปแบบหมายเลขอ้างอิงต้องกำหนดหรือไม่           | Use Case + AC                 |
| **FR-CAR-04**    | RC-04     | E-04, E-05 → N-STATUS   | ระบบต้องแสดงสถานะและความคืบหน้าของปัญหาที่ผู้ใช้งานแจ้ง                                             | Functional                     | **Must**      | ช่วยให้ผู้แจ้งทราบว่าปัญหาดำเนินการถึงขั้นตอนใด               | Ready for Week06 | สถานะมาตรฐานมีอะไรบ้าง                         | User Story + State Rule       |
| **FR-CAR-05**    | RC-05     | E-05, E-06 → N-STAFF    | ระบบต้องให้เจ้าหน้าที่ตรวจสอบรายการปัญหาและรายละเอียดของแต่ละรายการได้                              | Functional                     | **Must**      | เป็น capability หลักของเจ้าหน้าที่ในการรับเรื่องและดำเนินการ  | Ready for Week06 | เจ้าหน้าที่แต่ละบทบาทเห็นข้อมูลอะไรได้บ้าง     | Use Case                      |
| **FR-CAR-06**    | RC-06     | E-06, E-07 → N-UPDATE   | ระบบต้องให้เจ้าหน้าที่เปลี่ยนสถานะและบันทึกผลการดำเนินงานของปัญหาได้                                | Functional                     | **Must**      | ทำให้ข้อมูลความคืบหน้าถูกปรับปรุงและผู้แจ้งสามารถติดตามได้    | Ready for Week06 | ต้องบันทึกผลการดำเนินงานในสถานะใดบ้าง          | Use Case + AC                 |
| **FR-CAR-07**    | RC-07     | E-07, E-08 → N-ASSIGN   | ระบบต้องให้เจ้าหน้าที่ระบุผู้รับผิดชอบหรือหน่วยงานที่ดำเนินการแก้ไขปัญหาได้                         | Functional                     | **Should**    | ช่วยลดปัญหางานตกหล่นและทำให้ทราบผู้รับผิดชอบ                  | Needs Follow-up  | ใครมีอำนาจมอบหมายหรือเปลี่ยนผู้รับผิดชอบ       | Use Case Extension            |
| **FR-CAR-08**    | RC-08     | E-08, E-09 → N-NOTIFY   | ระบบต้องแจ้งเตือนผู้แจ้งเมื่อสถานะของปัญหามีการเปลี่ยนแปลง                                          | Functional                     | **Should**    | ลดความไม่แน่นอนและลดภาระการตรวจสอบสถานะด้วยตนเอง              | Needs Follow-up  | แจ้งเตือนผ่านช่องทางใดและเมื่อใด               | User Story + Event List       |
| **FR-CAR-09**    | RC-09     | E-10, E-11 → N-URGENT   | ระบบต้องสามารถจำแนกระดับความเร่งด่วนของปัญหาตามเกณฑ์ที่กำหนด                                        | Functional + Policy Dependency | **Should**    | ช่วยให้เจ้าหน้าที่จัดลำดับปัญหาที่ต้องดำเนินการก่อน           | Needs Follow-up  | เกณฑ์ความเร่งด่วนมีอะไรบ้าง และใครเป็นผู้กำหนด | Use Case + Business Rule      |
| **FR-CAR-10**    | RC-10     | E-10, E-11 → N-SAFETY   | ระบบต้องแจ้งผู้รับผิดชอบเมื่อพบปัญหาที่เข้าข่ายความเสี่ยงด้านความปลอดภัยตามเกณฑ์ที่กำหนด            | Functional + Policy Dependency | **Should**    | ช่วยลดความเสี่ยงจากปัญหาที่ต้องได้รับการดำเนินการอย่างรวดเร็ว | Needs Follow-up  | ปัญหาใดถือเป็น Safety Risk และต้องแจ้งใครบ้าง  | Alternate Flow                |
| **NFR-CAR-01**   | RC-11     | E-12 → N-USABILITY      | ระบบต้องมีขั้นตอนการแจ้งปัญหาที่เข้าใจง่ายและไม่ซับซ้อนสำหรับผู้ใช้งานทั่วไป                        | NFR / Usability                | **Must**      | หากระบบใช้งานยาก ผู้ใช้อาจกลับไปใช้ช่องทางเดิม                | Needs Follow-up  | จะใช้เกณฑ์ใดวัดความง่ายในการใช้งาน             | Quality Scenario              |
| **NFR-CAR-02**   | RC-12     | E-13 → N-PERFORMANCE    | ระบบต้องตอบสนองต่อการดำเนินการหลัก เช่น การเปิดรายการและส่งการแจ้งปัญหาภายในเวลาที่เหมาะสม          | NFR / Performance              | **Should**    | ลดความล่าช้าในการแจ้งและติดตามปัญหา                           | Needs Follow-up  | ต้องกำหนด Response Time เท่าใด                 | Quality Scenario              |
| **NFR-CAR-03**   | RC-13     | E-14 → N-SECURITY       | ระบบต้องควบคุมการเข้าถึงข้อมูลตามบทบาทของผู้ใช้งาน                                                  | NFR / Security                 | **Must**      | ป้องกันการเข้าถึงหรือแก้ไขข้อมูลโดยไม่ได้รับอนุญาต            | Needs Follow-up  | Role และ Permission ของแต่ละบทบาทมีอะไรบ้าง    | Quality Scenario + Constraint |
| **ISSUE-CAR-01** | E-10      | E-10, E-11 → N-URGENT   | ยังไม่มีหลักฐานยืนยันเกณฑ์ระดับความเร่งด่วนและเวลาที่ต้องดำเนินการในแต่ละระดับ                      | Issue                          | **Won't yet** | ไม่ควรกำหนด Priority หรือ SLA จากการคาดเดา                    | Hold             | ใครเป็นผู้อนุมัติเกณฑ์และ SLA                  | Follow-up only                |
| **ISSUE-CAR-02** | E-09      | E-09 → N-NOTIFY         | ยังไม่ยืนยันช่องทางและเวลาที่ใช้ในการแจ้งเตือนผู้เกี่ยวข้อง                                         | Issue / Dependency             | **Won't yet** | หากกำหนดเองอาจไม่ตรงกับกระบวนการจริง                          | Hold             | ใช้ In-app, Email หรือช่องทางอื่น              | Follow-up only                |
| **ISSUE-CAR-03** | E-14      | E-14 → N-SECURITY       | ยังไม่ยืนยันรายละเอียดสิทธิ์ของนักศึกษา บุคลากร เจ้าหน้าที่ และผู้ดูแลระบบ                          | Issue / Dependency             | **Won't yet** | หากกำหนดสิทธิ์เองอาจทำให้การออกแบบ Role ผิดจากการใช้งานจริง   | Hold             | ใครสามารถดู แก้ไข มอบหมาย และปิดงานได้บ้าง     | Follow-up only                |


## 4. Priority Summary

| Priority | Count | Requirement IDs | เหตุผลรวม |
|---|---:|---|---|
| **Must**      | **8** | FR-CAR-01, FR-CAR-02, FR-CAR-03, FR-CAR-04, FR-CAR-05, FR-CAR-06, NFR-CAR-01, NFR-CAR-03 | เป็นแกนหลักของการแจ้งปัญหา การรับเรื่อง การติดตาม และการควบคุมสิทธิ์                                           |
| **Should**    | **5** | FR-CAR-07, FR-CAR-08, FR-CAR-09, FR-CAR-10, NFR-CAR-02                                   | มีคุณค่าสูงต่อการดำเนินงาน แต่บางข้อยังต้องยืนยันผู้รับผิดชอบ ช่องทางแจ้งเตือน Policy และเกณฑ์ด้านความเร่งด่วน |
| **Could**     | **0** | -                                                                                        | ยังไม่มี Requirement ที่เป็นความสามารถเสริมและมีหลักฐานเพียงพอสำหรับ Release ปัจจุบัน                          |
| **Won't yet** | **3** | ISSUE-CAR-01, ISSUE-CAR-02, ISSUE-CAR-03                                                 | ยังไม่มีหลักฐานหรือ Policy เพียงพอ จึงยังไม่ยกระดับเป็น Requirement สำหรับ Release ปัจจุบัน                    |


## 5. Ready / Follow-up / Hold

| Status | Requirement IDs | สิ่งที่ต้องทำต่อ |
|---|---|---|
| **Ready for Week06** | FR-CAR-01, FR-CAR-02, FR-CAR-03, FR-CAR-04, FR-CAR-05, FR-CAR-06               | ทำ User Story / Use Case / Acceptance Criteria แบบเล็ก          |
| **Needs Follow-up**  | FR-CAR-07, FR-CAR-08, FR-CAR-09, FR-CAR-10, NFR-CAR-01, NFR-CAR-02, NFR-CAR-03 | ถาม Stakeholder / Policy Owner / IT เพิ่ม และเก็บ Open Question |
| **Hold**             | ISSUE-CAR-01, ISSUE-CAR-02, ISSUE-CAR-03                                       | เก็บเป็น Issue; ยังไม่เขียนเป็น Final Rule หรือ Design          |



## 6. Review Checklist

- [x] ทุก requirement มี Source RC หรือ Evidence source
- [x] ทุก requirement อ้าง Evidence / Need Trace
- [x] Type แยกเป็น Functional / NFR / Business Rule / Constraint / Issue
- [x] Priority มี rationale จาก value/risk/urgency/dependency
- [x] Unknown หรือ policy issue ไม่ถูกยกระดับเป็น requirement โดยไม่มีหลักฐาน
- [x] มี Week06 Use สำหรับรายการที่พร้อมทำ model

## 7. Week06 Handoff

Week06 ควรเริ่มจาก requirement ที่พร้อมก่อน:


| Week06 artefact | Input ที่เหมาะสม |
|---|---|
| **User Story**                 | FR-CAR-01, FR-CAR-02, FR-CAR-04                                          |
| **Use Case**                   | FR-CAR-01 เป็น Main Flow; FR-CAR-05 และ FR-CAR-06 เป็น Operational Flow  |
| **Acceptance Criteria**        | FR-CAR-01, FR-CAR-02, FR-CAR-03, FR-CAR-04 หลังยืนยันข้อมูลที่จำเป็น     |
| **Quality Scenario**           | NFR-CAR-01, NFR-CAR-02, NFR-CAR-03 หลังยืนยัน Measure และ Security Rules |
| **State / Status Model**       | FR-CAR-04 หลังยืนยันรายการ Status และลำดับการเปลี่ยนสถานะ                |
| **Extension / Alternate Flow** | FR-CAR-09, FR-CAR-10 หลังยืนยันเกณฑ์ความเร่งด่วนและ Safety Risk          |
| **Follow-up Interview**        | FR-CAR-07, FR-CAR-08, FR-CAR-09, FR-CAR-10 และ ISSUE-CAR-01..03          |

