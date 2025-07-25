# POS Events File Specification

This document outlines the format, structure, and expected content for two CSV files used in POS event processing:

**Directory**: `/incoming/pos-events`

## Filename

* `POSEvent_YYYYMMDDHHMM.csv`
* `POSEventStore_YYYYMMDDHHMM.csv`

## General Information

* **File Type**: CSV
* **Encoding**: UTF-8 (no BOM)
* **Delimiter**: Comma (`,`)
* **Compression**: None
* **Header**: None

---

## `POSEvent_YYYYMMDDHHMM.csv`

### Purpose

This file contains metadata and configuration details for POS deal events.

### File Structure

| Column     | Sample Value      | Description                       | Data Type    | Notes                                               |
| ---------- | ----------------- | --------------------------------- | ------------ | --------------------------------------------------- |
| `Add/Del`    | A/D  | Type of Operation (Add or Delete) | CHAR(1)      | Indicates if the record is new or should be removed |
| `Event Num`  | 5609 | ID | VARCHAR(20)  | Unique identifier for the event                     |
| `Desc`       | 01.BOGO\$1clrABC/ | Description | VARCHAR(255) | Human-readable deal description                     |
| `Start Date` | 3/17/2025         | Start date                        | DATETIME     | Start of event validity |
| `End Date`   | 8/24/2025         | End date                          | DATETIME     | End of event validity|
| `Coupon Req` | Y/N               | Coupon Requirement                | CHAR(1)      | Default is "N" (No)|

---

## `POSEventStore_YYYYMMDDHHMM.csv`

### Purpose

This file maps deal events to individual store numbers.

### File Structure

| Column   | Sample Values |
| -------- | ------------- |
| StoreNum | 1, 12, 14, 20 |
| EventID  | 8391          |

Each record maps a store (by number) to a specific `EventID` as defined in the `POSEvent` file.

---

## Notes

* All fields are required unless otherwise stated.
* Datetime values should be in `MM/DD/YYYY` format or ISO 8601 if supported.
* All `EventID`s listed in `POSEventStore` must reference a valid `Event Num` in `POSEvent`.

---