# Week 04 — Evidence Log

> **Team:** Team Example — Campus Resource Booking  
> **Assignment:** `W04-v2.0`  
> **Version:** v1.0 — Completed Teaching Example  
> **Inputs:** Week 03 Elicitation Plan and revised Interview Guide

## 1. Evidence policy

บันทึกนี้แยก **สิ่งที่แหล่งข้อมูลกล่าว/ระบุ** ออกจาก **การตีความของทีม** คำตอบจาก AI stakeholder panel เป็นข้อมูลจำลอง (`SN`) ไม่ใช่นโยบายจริง และทุกข้อที่ไม่มี source/authority ชัดเจนต้องคงสถานะ provisional หรือ unresolved


## 2. Source and session register

| Session | Source/role | Objectives | Control used | Limitation |
|---|---|---|---|---|
| S-00 | Case Card / Problem Brief | ใช้เป็นข้อมูลตั้งต้น (CF) และขอบเขตของปัญหา | อ้างอิง Problem Brief และ Case Card | ให้ข้อมูลเฉพาะบริบทเบื้องต้น |
| S-01 | นักศึกษา / ผู้พบปัญหา | EO-01, EO-03 | Role isolation, Interview Guide, Scenario-based questions | เป็นข้อมูลจำลอง ไม่มี authority ด้านนโยบาย |
| S-02 | เจ้าหน้าที่อาคาร / เจ้าหน้าที่เทคนิค / แม่บ้าน | EO-02, EO-04 | Workflow walkthrough, Interview Guide | สะท้อนกระบวนการทำงานจำลอง ยังไม่ใช่ระเบียบจริง |
| S-03 | ผู้ดูแลความปลอดภัย  | EO-04, EO-05 | Scenario-based discussion, Priority questions | ไม่สามารถยืนยันนโยบายหรือเกณฑ์จริงได้ |
| S-04 | ผู้ดูแลระบบ | EO-05, EO-06 | Constraint check, Security and system management questions | ไม่สามารถกำหนด Business Policy ได้ |


## 3. Tagging and confidence rules

| Tag | Use | Confidence rule |
|---|---|---|
| `CF` | ข้อเท็จจริงจาก Case Card หรือเอกสารที่ได้รับอนุมัติ | **High** เมื่ออ้างอิงแหล่งข้อมูลได้ชัดเจน |
| `CT` | ข้อกำหนดหรือข้อจำกัดที่มีแหล่งอ้างอิงหรือผู้มีอำนาจยืนยัน | **High–Medium** ตามความน่าเชื่อถือของแหล่งข้อมูล |
| `SN` | ข้อมูลหรือความต้องการจากการจำลอง Stakeholder | **Medium** ต้องยืนยันกับผู้ใช้งานหรือเอกสารจริง |
| `OP` | ความคิดเห็นหรือความชอบของ Stakeholder | ไม่ใช้เป็น Requirement โดยตรง  |
| `AS` | สมมติฐานของทีม | ต้องมีแผนตรวจสอบหรือผู้รับผิดชอบ |
| `PS` | แนวทางแก้ไขหรือข้อเสนอที่ Stakeholder เสนอ | ต้องหาความต้องการที่แท้จริง (Underlying Need) ก่อนสร้าง Requirement |
| `OQ` | ประเด็นที่ยังไม่มีคำตอบหรือข้อมูลยืนยัน | ห้ามสรุปหรือสร้างข้อมูลขึ้นเอง ต้องติดตามตรวจสอบเพิ่มเติม |


## 4. Evidence table

| E-ID | Source/role/session | Tag | Statement / observed  | Context | Confidence + reason | Related/conflicting E-ID | Follow-up/owner  |
|---|---|---|---|---|---|---|---|
| E-01 | S-00 Case Description | CF | ผู้ใช้ปัจจุบันแจ้งปัญหาผ่านหลายช่องทาง ทำให้ติดตามสถานะได้ยาก | Current process | High  | E-02 | ใช้เป็นข้อมูลตั้งต้น |
| E-02 | S-01 นักศึกษา | SN | ผู้แจ้งต้องการส่งข้อมูลปัญหาพร้อมรูปภาพ สถานที่ และประเภทของปัญหา | Interview | Medium  i| E-01, E-03 | ยืนยันข้อมูลขั้นต่ำกับเจ้าหน้าที่ |
| E-03 | S-02 เจ้าหน้าที่อาคาร | SN | หากข้อมูลไม่ครบ เจ้าหน้าที่ต้องสอบถามเพิ่มเติมก่อนดำเนินการ | Workflow | Medium  | E-02 | ตรวจสอบแบบฟอร์มจริง |
| E-04 | S-02 เจ้าหน้าที่เทคนิค | SN | งานควรถูกจัดลำดับตามระดับความรุนแรงของปัญหา | Priority | Medium  | E-05 | ยืนยันเกณฑ์ Priority |
| E-05 | S-03 ผู้ดูแลความปลอดภัย | SN | เหตุด้านความปลอดภัยควรได้รับการดำเนินการก่อนงานทั่วไป | Safety | Medium  | E-04 | ตรวจสอบนโยบายจริง |
| E-06 | S-01 นักศึกษา | SN | ผู้แจ้งต้องการทราบสถานะการดำเนินงานหลังแจ้งปัญหา | Tracking | Medium  | E-01 | ยืนยันรูปแบบการแจ้งเตือน |
| E-07 | S-03 ผู้ดูแลความปลอดภัย | SN | ปัญหาเดียวกันอาจมีผู้แจ้งหลายคน ทำให้เกิดรายการแจ้งซ้ำ | Duplicate Issue | Medium  | E-08 | ตรวจสอบแนวทางจัดการรายการซ้ำ |
| E-08 | S-04 ผู้ดูแลระบบ | SN | ระบบควรเก็บประวัติการดำเนินงานและกำหนดสิทธิ์การเข้าถึงข้อมูลตามบทบาท | Security | Medium  | E-07 | ยืนยันสิทธิ์ผู้ใช้งาน |
| E-09 | S-04 ผู้ดูแลระบบ | SN | ผู้ดูแลระบบต้องการค้นหา กรอง และสรุปรายงานการแจ้งปัญหาตามอาคาร ประเภทปัญหา สถานะ ช่วงเวลา และระดับความเร่งด่วน เพื่อใช้ติดตามและวิเคราะห์ข้อมูล | Reporting | Medium  | E-08 | ยืนยันรูปแบบรายงานที่ต้องการ  |


## 5. Triangulation and conflicts

| Topic | Supporting/contradicting E-IDs | Finding | Action |
|---|---|---|---|
| การแจ้งปัญหาพร้อมข้อมูลครบถ้วน | E-01, E-02, E-03 | ผู้ใช้และเจ้าหน้าที่มีความต้องการสอดคล้องกัน | สร้าง RC-01 |
| การติดตามสถานะ | E-01, E-06 | ผู้แจ้งต้องการทราบความคืบหน้า | สร้าง RC-02 |
| การจัดการรายการแจ้งซ้ำ | E-07 | ยังไม่มีแนวทางที่ชัดเจน | เปิด C-03 |
| การจัดลำดับความเร่งด่วน | E-04, E-05 | ต้องกำหนดเกณฑ์ Priority | เปิด C-02 |
| การกำหนดสิทธิ์และ Audit Log | E-08 | สนับสนุนการควบคุมสิทธิ์และตรวจสอบย้อนหลัง | สร้าง RC-05, RC-06 |
| การค้นหาและรายงาน | E-09 | ผู้ดูแลระบบต้องการสรุปรายงานเพื่อวิเคราะห์ข้อมูล | สร้าง RC-08 |


## 6. Evidence quality check

- [✓] ทุก Evidence มี E-ID และแหล่งที่มา
- [✓] แยก Statement ออกจาก Team Interpretation
- [✓] Simulation ถูกระบุเป็น SN
- [✓] ทุก Requirement Candidate อ้างอิง Evidence
- [✓] ทุก Conflict เชื่อมโยงกับ Evidence
- [✓] ไม่มีการอ้างว่าเป็นนโยบายจริงโดยไม่มีหลักฐาน

## 7. Handoff

- ใช้ E-02, E-03 → RC-01
- ใช้ E-01, E-06 → RC-02
- ใช้ E-07 → C-03 และ RC-03
- ใช้ E-04, E-05 → C-02 และ RC-04
- ใช้ E-08 → RC-05, RC-06
- ใช้ E-04 → RC-07
- ใช้ E-09 → RC-08
- Candidate ทั้งหมดต้องอ้าง E-ID ตาม [Requirement Candidates](04-requirement-candidates.md)