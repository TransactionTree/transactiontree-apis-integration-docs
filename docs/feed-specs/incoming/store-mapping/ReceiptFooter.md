# ReceiptFooter XML Specification

**Directory**: `/incoming/store-mapping`

## Filename

```
ReceiptFooter_<Date>_<Time>_<fileid>.xml
```

* `<Date>`: `YYYYMMDD`
* `<Time>`: `HHMMSS`
* `<fileid>`: partner batch identifier (matches across files)

## Purpose

Defines store-specific receipt footers or return policies to be applied in the system.

## Format

* **File Type**: XML
* **Encoding**: UTF‑8
* **Root Element**: `<TransactionTreeSiteImport>`

## Structure

```xml
<?xml version="1.0" encoding="UTF-8"?>
<TransactionTreeSiteImport>
  <HeaderInfo>
    <TTSIVersion>string</TTSIVersion>
    <ApplicationID>string</ApplicationID>
    <MerchantNumber>string</MerchantNumber>
    <DateGenerated>MM/DD/YYYY h:mm:ss A</DateGenerated>
  </HeaderInfo>
  <Locations>
    <Site>
      <StoreNumber>string</StoreNumber>
      <ReturnPolicy>string</ReturnPolicy>
    </Site>
    <!-- repeat <Site> for each store -->
  </Locations>
</TransactionTreeSiteImport>
```

## Elements

| Element          | Type   | Description                                         |
| ---------------- | ------ | --------------------------------------------------- |
| `TTSIVersion`    | String | Integration version identifier.                     |
| `ApplicationID`  | String | Source application ID.                              |
| `MerchantNumber` | String | Merchant account number.                            |
| `DateGenerated`  | String | Generation timestamp (e.g. `3/10/2025 6:02:59 PM`). |
| `StoreNumber`    | String | Zero‑padded store ID (must match other files).      |
| `ReturnPolicy`   | String | Text of the return policy or footer message.        |

## Sample

```xml
<Site>
  <StoreNumber>00900</StoreNumber>
  <ReturnPolicy>Beginning October 25th All Sales are Final</ReturnPolicy>
</Site>
```

## Validation Rules

* Well‑formed XML; reject invalid syntax.
* All `<Site>` elements must include both `<StoreNumber>` and `<ReturnPolicy>`.
* `StoreNumber` must match a store in the corresponding CSV files.

---
