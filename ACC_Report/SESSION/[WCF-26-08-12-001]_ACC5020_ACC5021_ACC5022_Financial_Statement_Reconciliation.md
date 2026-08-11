# [WCF-26-08-12-001] ACC5020 / ACC5021 / ACC5022 — Financial Statement Reconciliation

## Session Objective
บันทึกผลการวิเคราะห์ความสัมพันธ์และแนวทางควบคุมการตรวจสอบรายงาน ACC5020, ACC5021 และ ACC5022 สำหรับโครงการ WCF DIGITAL โดยใช้หลัก WCFUAT VS WCFLEGACY เท่านั้น

## Reports in Scope
1. ACC5020 — งบทดลอง (Trial Balance)
2. ACC5021 — งบแสดงฐานะการเงิน
3. ACC5022 — งบแสดงผลการดำเนินงาน

## Accounting Relationship
แหล่งข้อมูลบัญชีทำงานตามลำดับโดยสรุป:

เอกสาร/รายการบัญชี -> สมุดรายวันรับ/จ่าย/ใบโอน -> บัญชีแยกประเภท (GL) -> ACC5020 -> ACC5021 / ACC5022

### ACC5020
ทำหน้าที่เป็นฐานยอดบัญชีจาก GL ครอบคลุมหมวด:
- 1xxxxxxx สินทรัพย์
- 2xxxxxxx หนี้สิน
- 3xxxxxxx ทุน
- 4xxxxxxx รายได้
- 5xxxxxxx ค่าใช้จ่าย

### ACC5022
รับยอดบัญชีรายได้และค่าใช้จ่ายจากฐานบัญชี แล้วคำนวณ:

รายได้รวม - ค่าใช้จ่ายรวม = รายได้สูง (ต่ำ) กว่าค่าใช้จ่าย

ผลดังกล่าวสัมพันธ์กับบัญชีทุน/ผลการดำเนินงาน และส่งผลต่อ ACC5021

### ACC5021
ใช้ยอดสินทรัพย์ หนี้สิน และทุนจากฐานบัญชี และต้องผ่านสมการควบคุม:

สินทรัพย์ = หนี้สิน + ทุน

โดยส่วนทุนมีความสัมพันธ์กับผลรายได้สูง (ต่ำ) กว่าค่าใช้จ่ายจาก ACC5022

## Mandatory Cross-Report Reconciliation
แม้ ACC5020, ACC5021 และ ACC5022 จะ PASS เมื่อเทียบ WCFUAT VS WCFLEGACY แบบแยกรายงาน ก็ยังไม่เพียงพอ ต้องมี Cross-Report Reconciliation เพิ่มอีกหนึ่ง Gate

### Control 1: ACC5020 <-> ACC5022
- ตรวจบัญชีรายได้และค่าใช้จ่ายทุก Account/Amount
- ห้ามใช้เพียง Row Count
- ยอดใน ACC5022 ต้อง Trace กลับไปยัง ACC5020 ได้

### Control 2: ACC5022 <-> ACC5021
- ค่า “รายได้สูง (ต่ำ) กว่าค่าใช้จ่าย” ต้องตรงกัน
- ต้องตรวจจำนวนเงินจริง ไม่ใช่เฉพาะจำนวนรายการ

### Control 3: ACC5020 <-> ACC5021
- Asset / Liability / Equity ทุก Account/Amount ที่เกี่ยวข้องต้อง Trace ได้
- ตรวจยอดรวมและ Balance Equation

### Control 4: Common Scope
ทั้ง 3 รายงานต้องใช้ Scope เดียวกัน ได้แก่:
- หน่วยงาน/สำนักงานเดียวกัน
- วันที่/งวดเดียวกัน
- งบเดือนหรืองบสะสมประเภทเดียวกัน
- Parameter การประมวลผลเดียวกัน

## Data Validation Rule
DATA ต้องเทียบรายการและจำนวนเงินจริงทุกรายการ ไม่ใช้เพียงจำนวนแถว

กรณีรายการเหมือนกันครบแต่ลำดับแถวต่างกัน:
- ไม่ถือเป็น Fail
- Comment: “ข้อมูลจัดเรียงไม่เหมือนกัน”

## Calculation Validation Rule
Calculation ต้องตรวจจำนวนจริงทุกรายการ รวมถึง:
- Subtotal
- Grand Total
- Revenue - Expense
- Assets = Liabilities + Equity
- Cross-report carried-forward values

## Final Gate Rule
Final Financial Statement Gate จะ PASS ต่อเมื่อ:
1. ACC5020 WCFUAT VS WCFLEGACY = PASS
2. ACC5021 WCFUAT VS WCFLEGACY = PASS
3. ACC5022 WCFUAT VS WCFLEGACY = PASS
4. ACC5020 <-> ACC5022 Reconciliation = PASS
5. ACC5022 <-> ACC5021 Reconciliation = PASS
6. ACC5020 <-> ACC5021 Reconciliation = PASS

ดังนั้นให้จัดกลุ่ม ACC5020 / ACC5021 / ACC5022 เป็นชุดควบคุมเดียวกันชื่อ:

**Financial Statement Reconciliation Set**

## Current Session Findings
- ACC5020 ทำหน้าที่เป็นฐานยอดบัญชีหลัก
- ACC5022 ใช้รายได้/ค่าใช้จ่ายเพื่อคำนวณผลการดำเนินงาน
- ACC5021 ใช้สินทรัพย์/หนี้สิน/ทุน และรับผลกระทบจากผลการดำเนินงานของ ACC5022
- การตรวจแยกทีละรายงานอย่างเดียวไม่เพียงพอ ต้อง Reconcile ระหว่างทั้ง 3 รายงาน
- ประเด็น ACC5021 ส่วนต่าง 100,000,000.00 ที่เคยสรุปเป็น UAT defect ถูกยกเลิกหลัง Recheck เพราะเป็นการเทียบคนละ View; WCFUAT และ WCFLEGACY แสดงพฤติกรรมเดียวกัน

## Governance / Evidence Rule
- WCFUAT VS WCFLEGACY เท่านั้นสำหรับ Comparison Scope
- No Evidence = No Progress
- ผล PASS ต้องตรวจได้ถึงระดับ Account/Amount และ Cross-Report linkage
- ห้ามสรุปจาก Row Count เพียงอย่างเดียว

## Next Recommended Action
สร้าง Combined Reconciliation Workbook สำหรับ ACC5020 + ACC5021 + ACC5022 เพื่อทำ Final Financial Statement Gate โดยมีอย่างน้อย:
1. Executive Summary
2. ACC5020-to-ACC5022 Mapping
3. ACC5020-to-ACC5021 Mapping
4. ACC5022-to-ACC5021 Carry-forward Check
5. Balance Equation Check
6. Exception / Difference Register
7. Programmer Recommendation
8. Final Reconciliation Gate
