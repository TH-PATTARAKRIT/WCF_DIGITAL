# [WCF-26-08-10-001] STATE01_SOURCE_OF_TRUTH_RECOVERY

## Control Status
- STATE: 01_SOURCE_OF_TRUTH
- STATUS: IN PROGRESS / SOURCE BASELINE REGISTER CREATED
- EXECUTION AUTHORITY: Boss approved continuous execution in this session; BATCH execution is excluded and deferred to a separate Boss-controlled session.
- MASTER ROOT: https://drive.google.com/drive/folders/1y5XrMuOwqRcbQiTNvGXLoJL61Cqtl9ri
- STATE01 FOLDER: https://drive.google.com/drive/folders/1GuNCqEpboR8zTxf_HTQJNBC9HZh6Nyjd
- SOURCE REGISTER: https://docs.google.com/spreadsheets/d/1s8wn9TYZGEd-rJ2RE4R7YTz7VsUKkBP_Mfe4c6L3eTQ/edit

## Structure Decision
The 00-12 folder structure is the only master STATE structure. Temporary STATE01-STATE07 classifications are superseded working classifications and are not the master structure.

## Source of Truth Hierarchy
1. P1 — Primary Accounting Source of Truth
   - `การบันทึกบัญชีกองทุนเงินทดแทน (รวม)-จังหวัด.pdf`
2. P2 — DATA BATCH / Processing Source of Truth
   - BATCH ORIGINAL; source location confirmed, but all BATCH analysis/execution is deferred to a separate session.
3. P3 — Business Process Sources
   - 0310 / 0311 / 0410 / 0411 / 0510
4. P4 — Master / Cross-check Sources
   - ACCOUNT_ITEM, Chart of Accounts, SDS, SRS
5. P5 — Evidence / Expected Result
   - WCFLEGACY and accounting report evidence only. WCFUAT is not a Source of Truth.

## Source Recovery / Availability Confirmed in STATE01
- `การบันทึกบัญชีกองทุนเงินทดแทน (รวม)-จังหวัด.pdf`
  - https://drive.google.com/file/d/1AXrWO7ri6A8ErGb2clY4zpbZn1m7ePcI/view
- `รหัสรายการทางบัญชี ACCOUNT_ITEM`
  - https://docs.google.com/spreadsheets/d/1ptTHQKXBe_2le30osii26jU8uGAEo0M7WDE5jjFao8Q/edit
- `0310 กระบวนการทำงานของระบบสมทบของ wcf`
  - https://docs.google.com/spreadsheets/d/1pg5N28SJLLBNWSXFkLFu6VIqfG_q_jWiEKxOVkmDErA/edit
- `0311 กระบวนการทำงานของการเงินรับ wcf`
  - https://docs.google.com/spreadsheets/d/1yZcqV9hK5LqATq04JQcvzasmQFjJit_98_L8jyEVlRs/edit
- `0410 กระบวนการทำงานของระบบทดแทน wcf`
  - https://docs.google.com/spreadsheets/d/1OdwQ8Jrn2HU7fzXwgMNBQSuZO-V1ssKigT5UJqUTnVc/edit
- `0411 กระบวนการทำงานของการเงินจ่าย wcf`
  - https://docs.google.com/spreadsheets/d/1e0WT_97ox3KHizgCbqPxkxBX7sv1PPc13D_9yg4oHCU/edit
- `0510 กระบวนการทำงานของระบบบัญชี wcf`
  - https://docs.google.com/spreadsheets/d/1obfNdz4fYbD8Hn3y8Y9MGE9cKhCVoYu2He4tmD3QV54/edit
- `ผังบัญชีWAY_1.xlsx`
  - https://docs.google.com/spreadsheets/d/1Us3mhjaJOO-j7gS_FiHMR0gsxosMc-5_/edit
- `Phase-5_2_02 SDS งวดที่ 5 ระบบบัญชี V1_2025 10 10_25681208.docx`
  - https://docs.google.com/document/d/1pe4Ykv2x0arhVpgPPCFNGy0XP7L2Jh0o/edit
- `G3 เอกสาร SRS งวดที่ 5 ระบบบัญชี V002_25681009.docx`
  - https://docs.google.com/document/d/1VhOU5TWs1p-ldzmw4bSm667xu8_p4rb1/edit
- `รายงานระบบบัญชี_ACC_WCFDIGITAL`
  - https://docs.google.com/spreadsheets/d/1XwwVhKjyBKwe0PYIZTKTiFr6lhzdGqCNkHot7mWJVHQ/edit
- `ACC5030_RAW_WCFLEGACY_REV02_20260727.csv`
  - https://drive.google.com/file/d/19rke8Y9CPlM_muM3Fqhb8xOGg9dVaIFO/view
- `processes.zip`
  - https://drive.google.com/file/d/1EIHiomKdFL_SttI2PRS6EiF25b-QuHbs/view
- `WCF DIGITAL Project Constitution - Report Evidence Reference Standard`
  - https://docs.google.com/document/d/1-LWATZ8Nsi2vDZldKAFpoL-f-1-aKgxpVrVWjEfeSaY/edit

## BATCH Scope Lock
- BATCH ORIGINAL is recognized as the processing reference baseline because Boss states it works 100% in the legacy system.
- BATCH V2.0 is not a Source of Truth and is a comparison target only.
- No BATCH logic, content validation, or programmer conclusion will be executed in this session.
- Any dependency discovered in another STATE must be marked `DEFERRED TO SEPARATE BATCH SESSION`.

## Evidence Rule
No Evidence = No Confirmed Requirement. A source being present in STATE01 means `FOUND`, not automatically `VERIFIED`. Content-level verification and conflict checks must still be performed before a source can support a confirmed requirement.

## STATE01 Deliverable Created
`STATE01_Source_of_Truth_Master_Register_20260810` contains the initial source hierarchy, Drive links, verification status, related STATE mapping, WCFLEGACY relation, BATCH relation, and notes.

## Remaining Work Within STATE01
1. Perform content-level verification of P1/P3/P4/P5 sources.
2. Identify duplicates/versions and designate official owner copy where required.
3. Trace each source to TOR, business process, E2E event, COA, accounting reports, and WCFLEGACY evidence.
4. Record conflicts as OPEN GAP; never silently reconcile contradictory sources.
5. Close STATE01 only after the register and evidence are reviewable and all critical sources have a status.
