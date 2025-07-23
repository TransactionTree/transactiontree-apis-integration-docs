# StoreHierarchy File Specification

**Directory**: `/incoming/store-mapping`

## Filename

```
StoreHierarchy_<Date>_<Time>_<fileid>.csv
```

* `<Date>`: `YYYYMMDD` (e.g., `20250417`)
* `<Time>`: `HHMMSS` (24‑hour clock)
* `<fileid>`: partner batch identifier (must match across all three files)

## Purpose

Defines the hierarchical grouping of stores by region, district, territory, and line of business.

## Format

* **File Type**: CSV
* **Encoding**: UTF‑8, no BOM
* **Delimiter**: Comma (`,`)
* **Compression**: None
* **Quoting**: All field values MUST be enclosed in double quotes (e.g. `"Value"`).

## Columns

| Column           | Type    | Description                                     |
| ---------------- | ------- | ----------------------------------------------- |
| `Store_No`       | String  | Zero‑padded store ID (e.g. `00001`).            |
| `Country`        | String  | ISO country code (`CA`, `USA`).                 |
| `Region_No`      | Integer | Numeric region ID.                              |
| `Region_Name`    | String  | Descriptive region name (e.g. `Region 7 - ON`). |
| `District_No`    | Integer | Numeric district ID.                            |
| `District_Name`  | String  | District description.                           |
| `Territory_No`   | Integer | Territory code; blank or `0` if unused.         |
| `LOB_ID`         | Integer | Line‑of‑Business ID.                            |
| `LineOfBusiness` | String  | Business unit name.                             |
| `LOBGroupName`   | String  | Group name for LOB.                             |

## Sample

```csv
"Store_No","Country","Region_No","Region_Name","District_No","District_Name","Territory_No","LOB_ID","LineOfBusiness","LOBGroupName"
"8315","CA","7","Region 7 - ON","706","District 706 - Dealer","1","1000","ABC Dealers","ABC"
"1075","CA","6","Region 6 - NS","606","District 606 - Dealer","1","1000","ABC Franchise","ABC"
...
```

## Validation Rules

* Filename pattern must be exact.
* All required columns present and in correct order.
* `Country`, `Region_No`, `District_No`, `LOB_ID` must be valid codes.
* Duplicate files quarantined; only first processed.

---
