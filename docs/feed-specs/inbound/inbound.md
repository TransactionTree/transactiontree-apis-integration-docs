# Inbound File-Feed Specifications

This document defines the format, naming conventions, directory paths, and validation rules for all file feeds sent *to* TransactionTree (Partner → TransactionTree).

---

## 1. Common Rules

* **Encoding**: UTF‑8, no BOM
* **Timestamp**: All filenames include timestamps in `YYYYMMDDHHMMSS` format (24‑hour clock).
* **Delimiter**: As noted per feed; use exact character and no extra whitespace.
* **Compression/Archive**: If `.zip`, must contain only the designated file type inside.

---

## 2. Feed Details

### 2.1 Audit Files

* **Directory**: `/incoming/audit`
* **Filename**: `YYYYMMDDHHMMSS_dailyaudit.csv`
* **Delimiter**: Comma (`,`)
* **Columns**:

  1. `AuditID` (String)
  2. `Timestamp` (ISO 8601)
  3. `User` (String)
  4. `Action` (String)
  5. `Details` (String)
* **Sample**:

  ```csv
  20250701123000_dailyaudit.csv
  AuditID,Timestamp,User,Action,Details
  A123,2025-07-01T12:29:45Z,partnerUser1,UPLOAD,File received
  ```

### 2.2 Customer Updates

* **Directory**: `/incoming/customers`
* **Filename**: `CustomerUpdate_YYYYMMDDHHMMSS.csv`
* **Delimiter**: Pipeline (`|`)
* **Columns**:

  1. `CustomerID` (UUID)
  2. `Name` (String)
  3. `Email` (String)
  4. `Status` (ACTIVE, INACTIVE)
  5. `UpdatedAt` (ISO 8601)
* **Sample**:

  ```csv
  CustomerID|Name|Email|Status|UpdatedAt
  550e8400-e29b-41d4-a716-446655440000|Jane Doe|jane@example.com|ACTIVE|2025-07-01T12:30:00Z
  ```

### 2.3 Legacy Formats

* **Directory**: `/incoming/legacy`
* **Description**: Legacy file formats vary by partner.
* **Action**: Contact Data‑Ops for specifics and templates.

### 2.4 POS Events

* **Directory**: `/incoming/pos-events`
* **Filenames**:

  * `POSEvent_YYYYMMDDHHMM.csv`
  * `POSEventStore_YYYYMMDDHHMM.csv`
* **Delimiter**: Comma (`,`)
* **Description**: Two related files: header (`POSEvent_…`) and line‑items (`POSEventStore_…`).
* **Sample Header**:

  ```csv
  EventID,StoreNo,EventDate,Total
  E123,00001,2025-07-01T12:30:00Z,150.75
  ```

### 2.5 Product Feed

* **Directory**: `/incoming/products`
* **Filename**: `ProductFeed_YYYYMMDD_HHMMSS.zip`
* **Contents**: Single CSV named `products.csv` with comma delimiter.
* **Columns**:

  1. `ProductID` 2. `Name` 3. `Category` 4. `Price` 5. `UpdatedAt`

### 2.6 Store Mapping

* **Directory**: `/incoming/store-mapping`
* **Filenames**:

  * `Store_YYYYMMDD_HHMMSS.csv`
  * `ReceiptFooter.xml` (optional footer definitions)
* **Delimiter**: Comma (`,`)
* **Columns (CSV)**:

  1. `Store_No` 2. `Country` 3. `Region_No` 4. `Region_Name` 5. `District_No` 6. `District_Name` 7. `Territory_No` 8. `LOB_ID` 9. `LineOfBusiness` 10. `LOBGroupName`

---

## 3. Validation & Error Handling

* **Schema Validation**: Reject files missing required columns or with extra columns.
* **Filename Validation**: Reject files that do not match the exact pattern (including timestamp format).
* **Encoding**: Reject non-UTF8 data.
* **Duplicate Files**: If a file with the same name arrives twice, only the first will be processed; subsequent files will be quarantined.

---

*For any questions about specific feed formats or to request custom mappings, contact Data‑Ops at \*\***data‑***[***ops@transactiontree.com***](mailto:ops@transactiontree.com)*.*
