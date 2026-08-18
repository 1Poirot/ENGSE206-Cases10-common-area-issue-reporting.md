# Week 04 — Evidence-linked Requirement Candidates

## 1. Candidate writing rule

Candidate ที่ดีใน Week 04 ต้องมี actor/system behavior หรือ quality concern ที่ชัดพอให้วิเคราะห์ต่อ อ้าง E-ID ระบุสถานะ/confidence และบอกช่องว่างที่ต้อง verify โดยยังไม่รีบสร้างรายละเอียด UI/technology/penalty ที่ไม่มี evidence

## 2. Requirement candidates

| RC ID | Candidate statement | Type | Evidence / Decision | Status | Confidence | Follow-up / acceptance hint |
|---|---|---|---|---|---|---|
| **RC-01** | ระบบต้องให้ผู้แจ้งปัญหาสามารถส่งรายงานปัญหาได้ภายในขั้นตอนเดียว โดยแนบรูปภาพ เลือกอาคาร ระบุตำแหน่ง และประเภทของปัญหา เพื่อให้ข้อมูลครบถ้วนสำหรับการดำเนินงาน               | Functional                      | E-01, E-02          | Candidate   | High       | ยืนยันข้อมูลขั้นต่ำ (required fields) และทดสอบว่ารายงานที่ส่งมีข้อมูลเพียงพอต่อการรับเรื่อง |
| **RC-02** | ระบบต้องแสดงสถานะของการดำเนินงานและแจ้งเตือนผู้เกี่ยวข้องเมื่อสถานะเปลี่ยน เช่น รับเรื่องแล้ว กำลังดำเนินการ และเสร็จสิ้น                                                   | Functional / Usability          | E-03, E-04          | Candidate   | High       | ยืนยันเหตุการณ์ที่ต้องแจ้งเตือน ช่องทางการแจ้งเตือน และระยะเวลาที่เหมาะสม                   |
| **RC-03** | ระบบต้องสามารถตรวจจับการแจ้งปัญหาที่อาจเป็นเหตุการณ์เดียวกัน และแจ้งเตือนผู้ใช้ก่อนสร้างรายการใหม่ พร้อมรองรับการรวมรายการโดยไม่สูญเสียข้อมูลผู้แจ้งแต่ละราย                | Functional / Business Rule      | E-05, E-06          | Provisional | Medium     | ยืนยันเกณฑ์การพิจารณาว่าเป็นเหตุการณ์ซ้ำ เช่น ระยะทาง ช่วงเวลา และประเภทของปัญหา            |
| **RC-04** | ระบบต้องจำแนกระดับความเร่งด่วนของเหตุ และแจ้งเตือนผู้รับผิดชอบทันทีเมื่อเป็นเหตุที่มีผลกระทบด้านความปลอดภัย พร้อมแสดงตำแหน่งของเหตุอย่างชัดเจน                              | Functional / Business Rule      | E-07, E-08          | Candidate   | High       | ยืนยันเกณฑ์การจัดระดับความรุนแรง และบทบาทที่ต้องได้รับการแจ้งเตือนในแต่ละระดับ              |
| **RC-05** | ระบบต้องบันทึกประวัติการดำเนินงานทุกขั้นตอน โดยเก็บผู้ดำเนินการ เวลา และรายละเอียดการเปลี่ยนแปลง และต้องไม่อนุญาตให้ผู้ใช้งานทั่วไปแก้ไขหรือลบข้อมูลดังกล่าว                | Functional / Security           | E-09                | Candidate   | High       | ยืนยันข้อมูลที่ต้องบันทึก ระยะเวลาการเก็บรักษา และสิทธิ์การเข้าถึง Audit Log                |
| **RC-06** | ระบบต้องกำหนดสิทธิ์การเข้าถึงข้อมูลและการดำเนินงานตามบทบาทของผู้ใช้งาน เพื่อให้แต่ละบทบาทเข้าถึงเฉพาะข้อมูลและฟังก์ชันที่ได้รับอนุญาต                                       | NFR – Security / Access Control | E-10                | Candidate   | High       | จัดทำ Role Matrix และตรวจสอบสิทธิ์ของแต่ละบทบาทใน Week 05                                   |
| **RC-07** | ระบบต้องรองรับการมอบหมายงานให้ผู้รับผิดชอบตามประเภทของปัญหา แสดงผู้รับผิดชอบปัจจุบัน รองรับการโอนย้ายงาน และบันทึกประวัติการมอบหมาย                                         | Functional                      | E-11, E-12          | Candidate   | Medium     | ยืนยันหลักเกณฑ์การมอบหมาย การโอนย้ายงาน และผู้มีอำนาจเปลี่ยนผู้รับผิดชอบ                    |
| **RC-08** | ระบบต้องสนับสนุนการค้นหา กรอง และสรุปรายงานข้อมูลการแจ้งปัญหาตามช่วงเวลา อาคาร ประเภทปัญหา สถานะ ระดับความเร่งด่วน และผู้รับผิดชอบ เพื่อสนับสนุนการติดตามและวิเคราะห์ข้อมูล | Functional / Reporting          | E-13, E-14          | Candidate   | Medium     | ยืนยันรูปแบบรายงาน ตัวกรองที่จำเป็น และตัวชี้วัดที่ผู้บริหารต้องการ                         |


## 3. Coverage and traceability matrix

| Week 02 source | Week 03 objective/questions | Week 04 evidence/negotiation | Candidate |
|---|---|---|---|
| F-01, OQ-01    | EO-01; Q-01–Q-03            | E-01, E-02                   | RC-01     |
| F-02, OQ-02    | EO-02; Q-04–Q-06            | E-03, E-04                   | RC-02     |
| OQ-03          | EO-03; Q-07–Q-08            | E-05, E-06                   | RC-03     |
| F-03, OQ-04    | EO-04; Q-09–Q-10            | E-07, E-08                   | RC-04     |
| AS-01          | EO-05; Q-11                 | E-09                         | RC-05     |
| AS-02          | EO-06; Q-12                 | E-10                         | RC-06     |
| F-04           | EO-07; Q-13                 | E-11, E-12                   | RC-07     |
| F-05           | EO-08; Q-14                 | E-13, E-14                   | RC-08     |


## 4. Quality review


| Check | Result | Note |
|---|---|---|
| Traceable                 | Pass   | RC ทุกข้อเชื่อมโยงกับ Evidence (E-ID) ที่เกี่ยวข้อง                                   |
| No unsupported approval   | Pass   | ใช้สถานะ Candidate และ Provisional ตามหลักฐานที่มี                                    |
| Solution-neutral          | Pass   | ยังไม่กำหนดเทคโนโลยี ช่องทางแจ้งเตือน หรือรายละเอียด UI                               |
| Atomic enough for Week 05 | Pass   | แต่ละ RC มีขอบเขตชัดเจน สามารถนำไปวิเคราะห์ต่อได้                                     |
| Privacy / Security        | Pass   | RC-05 และ RC-06 ครอบคลุม Audit Log และ Role-based Access Control                      |
| Testability direction     | Pass   | ทุก RC มี Follow-up และ Acceptance Hint สำหรับใช้จัดทำ Acceptance Criteria ใน Week 06 |


## 5. Week 05 handoff backlog

### Analysis tasks

1. จัดประเภท Functional / Business Rule / NFR / Data / Interface
2. แยก RC ที่มีหลาย concern หากจำเป็น
3. ทำ dependency: RC-02 → RC-03; RC-04 ขึ้นกับ authority; RC-07 ขึ้นกับ event/policy
4. จัด priority ด้วย value/risk/dependency ไม่ใช้ความชอบส่วนบุคคล
5. คง issues ของ E-08/E-11 เป็น unresolved และกำหนด owner/due point

### Do not do yet

- อย่ากำหนด penalty/no-show duration จาก simulation
- อย่าฟันธงว่าใช้ LINE, QR, photo, framework หรือ database
- อย่าเลื่อน Provisional เป็น Approved โดยไม่มี authorized validation