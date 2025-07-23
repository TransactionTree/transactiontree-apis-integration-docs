# Outbound File-Feed Specifications

This document defines the format, naming conventions, directory paths, and validation rules for all file feeds sent *from* TransactionTree to partner organizations (TransactionTree → Partner).

---

## 1. Common Rules

> *These rules apply to all outbound feeds.*

* **Encoding**: UTF‑8, no BOM
* **Timestamp**: All filenames include timestamps in `YYYYMMDDHHMMSS` format (24‑hour clock).
* **Delimiter**: As noted per feed; use exact character and no extra whitespace.
* **File Type**: .csv for comma/pipeline-delimited feeds; .sql for SQL scripts; other extensions as specified.

---

## 2. Feed Details

### 2.1 Audit Output

* **Directory**: `/outgoing/audit`
* **Filename**: `TransAudit_YYYYMMDD_HHMMSS.csv`
* **Delimiter**: Comma (`, `)
* **Description**: Daily audit report for processed inbound files.
* **Columns** (sample):

  1. `AuditID` (String)
  2. `OriginalFile` (String)
  3. `ProcessedAt` (ISO 8601)
  4. `Status` (SUCCESS, ERROR)
  5. `Message` (String)

### 2.2 Coupon Barcodes

* **Directory**: `/outgoing/coupons/barcodes`
* **Filename**: `CpnBarCode-{PromoID}-YYYYMMDDHHMMSS.csv`
* **Delimiter**: Pipeline (`|`)
* **Description**: One CSV per promotion containing generated barcode values.
* **Columns**:

  1. `BarcodeID` (String)
  2. `PromoID` (String)
  3. `CustomerID` (UUID)
  4. `IssueDate` (ISO 8601)

### 2.3 Coupon Daily

* **Directory**: `/outgoing/coupons/daily`
* **Filename**: `CpnDaily_YYYYMMDDHHMMSS.sql`
* **Delimiter**: Newline (`\n`)
* **Description**: SQL script for daily coupon inventory load.
* **Contents**: Series of `INSERT` statements into the coupon table.

### 2.4 Coupon Same-Day

* **Directory**: `/outgoing/coupons/sameday`
* **Filename**: `CpnSameDay_YYYYMMDDHHMMSS.sql`
* **Delimiter**: Newline (`\n`)
* **Description**: SQL script for same-day coupon issuance.
* **Contents**: Series of `INSERT` statements for same-day coupons.

### 2.5 Customer Master Data

* **Directory**: `/outgoing/customers`
* **Filename**: `CustomerOutput_YYYYMMDDHHMMSS.csv`
* **Delimiter**: Pipeline (`|`)
* **Description**: Complete or incremental dump of customer master records.
* **Columns** (sample):

  1. `CustomerID` (UUID)
  2. `Name` (String)
  3. `Email` (String)
  4. `Status` (ACTIVE, INACTIVE)
  5. `CreatedAt` (ISO 8601)
  6. `UpdatedAt` (ISO 8601)

### 2.6 Scheduled Reports

* **Directory**: `/outgoing/reports`
* **Filename**: `CpnBIData_YYYYMMDDHHMMSS.csv`
* **Delimiter**: Pipeline (`|`)
* **Description**: Business intelligence CSV export with scheduled metrics and KPIs.
* **Columns**: Defined per report type; see report template in partner docs.

---

## 3. Validation & Error Handling

* **Filename Validation**: Reject if filename deviates from pattern (including timestamp).
* **Delimiter Validation**: Reject if wrong delimiter or inconsistent quoting.
* **SQL Script Validation**: Reject if syntax errors detected (basic parsing).
* **Quarantine**: Any file failing validation is quarantined and notifications sent to Data‑Ops.

---

*For questions about outbound feed structure, sample templates, or customizations, contact Data‑Ops at **data‑[ops@transactiontree.com](mailto:ops@transactiontree.com)**.*
