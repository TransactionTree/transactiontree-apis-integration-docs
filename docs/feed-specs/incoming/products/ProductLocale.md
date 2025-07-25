# Product Locale File Specification

**Directory**: `/incoming/products`

## Filename

```
ProductLocale_<Date>_<Time>_<fileid>.csv
```

* `<Date>`: `YYYYMMDD` (e.g. `20250723`)
* `<Time>`: `HHMMSS` (24‑hour clock)
* `<fileid>`: partner batch identifier (must match across related files)

## Purpose

Contains detailed metadata for each product as related to language.

## Format

* **File Type**: CSV
* **Encoding**: UTF‑8, no BOM
* **Delimiter**: Comma (`,`)
* **Text Enclosure**: Double quotes (`"`)
* **Line Break**: CRLF (`\r\n`)
* **Header**: First row must contain column names

## Columns

| No | Column Name        | Legacy        | Data Type   | Description                                                      | Mandatory |
| --- | ------------------ | ------------- | ----------- | ---------------------------------------------------------------- | --------- |
| 1   | `PRODUCT_ID`       | `PRODUCTID`   | Varchar(60) | Assign unique ID.                                                | Y         |
| 2   | `LOCALE`           |               | Varchar(60) | ISO 639-1 + ISO 3166 (e.g. en-US, fr-FR)                         | Y         |
| 3   | `INTERNAL_NAME`    |               | Varchar(255)| Internal reference name in language                              | Y         |
| 4   | `DESCRIPTION`      |               | Varchar(255)| Short, localized description for UI displays                     | N         |
| 5   | `LONG_DESCRIPTION` |               | Longtext    | Detailed product description in the target language              | N         |

---
