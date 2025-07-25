# Coupons File Specifications

**Root Directory**: `/outgoing/coupons`

This document outlines the file patterns, directory structure, column requirements, and best practices for all coupon-related exports.

## Table of Contents

* [Directory Structure](#directory-structure)
* [Barcode Metadata Files](#barcode-metadata-files)
* [Daily Coupons Files](#daily-coupons-files)
* [Same‑Day Coupons Files](#same‑day-coupons-files)
* [Schema Reference](#schema-reference)
* [Data Validation & Ingestion](#data-validation--ingestion)
* [General Notes](#general-notes)
* [Version History](#version-history)
* [Contact](#contact)

---

## Directory Structure

```
/outgoing/coupons
├── barcodes      # Serialized and non‑serialized coupon barcodes
├── daily         # Daily coupon definitions and performance
└── sameday       # Same‑day coupon summaries and details
```

Each subdirectory contains files following strict naming conventions and schema definitions to support automated processing and ingestion.

---

## Barcode Metadata Files

**Directory**: `/outgoing/coupons/barcodes`

**Filename Pattern**: `CpnBarCode-<PromoID>-<YYYYMMDDHHMMSS>.csv`
**Separator**: Pipe (`|`)

For detailed column definitions, see the [barcodes metadata reference](barcodes/barcodes.md).

---

## Daily Coupons Files

**Directory**: `/outgoing/coupons/daily`

**Filename Patterns**:

| Filename                                   | Description                                       |
| ------------------------------------------ | ------------------------------------------------- |
| `CpnDaily_Event_<timestamp>.csv`           | Promotion event identifiers and date ranges       |
| `CpnDaily_ParamReasonList_<timestamp>.csv` | Reason codes and parameter listing                |
| `CpnDaily_DealCoupon_<timestamp>.csv`      | Deal‑level coupon redemption and forecast metrics |
| `CpnDaily_PromoStores_<timestamp>.csv`     | Per‑store coupon activity and circulation counts  |
| `CpnDaily_Definition_<timestamp>.csv`      | Coupon definition, eligibility flags, and rules   |

> **Note**: `<timestamp>` = `<YYYYMMDDHHMMSS>` in 24‑hour format.

### Schema Reference

All daily file schemas are defined in the daily dictionary file: [`CpnDaily.md`](daily/CpnDaily.md).
Refer to that document for full column names, data types, and in‑depth descriptions.

**Tip**: Before loading into downstream systems, validate each CSV against the dictionary schema to ensure no missing or extra columns.

---

## Same‑Day Coupons Files

**Directory**: `/outgoing/coupons/sameday`

**Filename Patterns**:

| Filename                                     | Description                                                  |
| -------------------------------------------- | ------------------------------------------------------------ |
| `CpnSameDay_Event_<timestamp>.csv`           | Hourly promo event definitions (ID, names, start/stop times) |
| `CpnSameDay_ParamReasonList_<timestamp>.csv` | Parameter & reason codes for same‑day promotions             |
| `CpnSameDay_DealCoupon_<timestamp>.csv`      | Coupon redemption details by deal for the day                |
| `CpnSameDay_PromoStores_<timestamp>.csv`     | Store‑level coupon activity snapshots                        |
| `CpnSameDay_Definition_<timestamp>.csv`      | Definition and eligibility flags for same‑day coupons        |

### Column Definitions

Same‑day files follow the same base schema as daily exports (see: [`CpnSameDay.md`](sameday/CpnSameDay.md)), but capture intra‑day snapshots.

---

## Data Validation & Ingestion

* **Header Validation**: Reject files with missing, extra, or misordered columns.
* **Schema Check**: Ensure data types and nullability align with the BI Data Dictionary.
* **Timestamp Verification**: Filename timestamp must match the UTC timestamp in file header when applicable.
* **File Integrity**: Validate non‑zero row counts; alert if empty.
* **Delivery Mechanism**: SFTP to `/outgoing/coupons/...`; files must be read‑only post‑delivery.

Automate these checks in your ETL pipelines to catch issues early and reduce manual intervention.

---

## General Notes

* **Naming Conventions**: Use exact casing and separators; deviations break automation.
* **Archival**: Move processed files to `/archive/coupons/YYYY/MM/DD/`.
* **Error Handling**: Log schema mismatches and notify Data Ops via email and monitoring channels.
* **Security**: Ensure SFTP credentials and directories are restricted to authorized users only.

---

## Version History

| Version | Date       | Changes                                                |
| ------- | ---------- | ------------------------------------------------------ |
| 1.0     | 2025‑07‑25 | Initial creation and specification update              |
| 1.1     | 2025‑07‑26 | Added Same‑Day file patterns and key column references |

---

## Contact

For questions or support, contact the Data Ops team: [data-ops@transactiontree.com](mailto:data-ops@transactiontree.com)
