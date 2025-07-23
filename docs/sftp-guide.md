# TransactionTree, Inc. SFTP User Guide

This document provides quick‐reference guidance for securely connecting to and using the **BORMC SFTP system**. It outlines connection placeholders, file naming standards, directory structures, and support contact details. This guide is intended for **partner organizations and developers** using the TransactionTree BORMC application.

---

## Quick Reference Guide

### Connection Information

| User                       | Hostname / IP            | Port |
| -------------------------- | ------------------------ | ---- |
| **External**               | `[your-sftp-domain]`     | 2022 |
| **Internal (Application)** | `[your-sftp-ip-address]` | 2022 |

> **Note:** Use the **External** hostname for partner‑initiated uploads outside your network, and the **Internal** IP address for application‑driven transfers within your secure network.

If you do not yet have the SFTP domain or IP address, or if your team encounters connectivity issues, please contact our support team (see below) to obtain or verify these values.

### Directory Usage

* **Incoming**: Partner Organization → TransactionTree
* **Outgoing**: TransactionTree → Partner Organization

### Directory Structure & File Naming

| Directory                    | Usage                    | File Naming Pattern                                                | Delimiter  |   |
| ---------------------------- | ------------------------ | ------------------------------------------------------------------ | ---------- | - |
| `/incoming/audit`            | Daily audit files        | `YYYYMMDDHHMMSS_dailyaudit.csv`                                    | Comma (,)  |   |
| `/incoming/customers`        | New or updated customers | `CustomerUpdate_YYYYMMDDHHMMSS.csv`                                | Pipeline ( | ) |
| `/incoming/legacy`           | Legacy file formats      | *Various legacy formats*; see partner docs                         | N/A        |   |
| `/incoming/pos-events`       | Deal files or headers    | `POSEvent_YYYYMMDDHHMM.csv`  <br> `POSEventStore_YYYYMMDDHHMM.csv` | Comma (,)  |   |
| `/incoming/products`         | Product files            | `ProductFeed_YYYYMMDD_HHMMSS.zip`                                  | Comma (,)  |   |
| `/incoming/store-mapping`    | Location content files   | `Store_YYYYMMDD_HHMMSS.csv`  <br> `ReceiptFooter.xml`              | Comma (,)  |   |
| `/outgoing/audit`            | Audit output files       | `TransAudit_YYYYMMDD_HHMMSS.csv`                                   | Comma (,)  |   |
| `/outgoing/coupons/barcodes` | Generated barcode images | `CpnBarCode-{PromoID}-YYYYMMDDHHMMSS.csv`                          | Pipeline ( | ) |
| `/outgoing/coupons/daily`    | Daily coupon files       | `CpnDaily_YYYYMMDDHHMMSS.sql`                                      | Newline (  |   |
| )                            |                          |                                                                    |            |   |
| `/outgoing/coupons/sameday`  | Same‑day coupon files    | `CpnSameDay_YYYYMMDDHHMMSS.sql`                                    | Newline (  |   |
| )                            |                          |                                                                    |            |   |
| `/outgoing/customers`        | Customer master data     | `CustomerOutput_YYYYMMDDHHMMSS.csv`                                | Pipeline ( | ) |
| `/outgoing/reports`          | Scheduled reports        | `CpnBIData_YYYYMMDDHHMMSS.csv`                                     | Pipeline ( | ) |

---

## Support & Assistance

If you have questions about obtaining or verifying the SFTP domain name or IP address, or if you run into any connection issues, please contact our support team:

* **Email:** [support@transactiontree.com](mailto:support@transactiontree.com)
* **Include in your request:**

  * Your organization name
  * Whether you need the **domain** or **IP address** (or both)
  * Any error messages or screenshots

We’re here to help ensure your file transfers run smoothly and securely.
