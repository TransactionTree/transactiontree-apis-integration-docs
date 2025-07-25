# Product Price File Specification

**Directory**: `/incoming/products`

## Filename

```
ProductPrice_<Date>_<Time>_<fileid>.csv
```

* `<Date>`: `YYYYMMDD` (e.g. `20250723`)
* `<Time>`: `HHMMSS` (24‑hour clock)
* `<fileid>`: partner batch identifier (must match across related files)

## Purpose

Contains detailed metadata for each product as related to price.

## Format

* **File Type**: CSV
* **Encoding**: UTF‑8, no BOM
* **Delimiter**: Comma (`,`)
* **Text Enclosure**: Double quotes (`"`)
* **Line Break**: CRLF (`\r\n`)
* **Header**: First row must contain column names

## Columns

| No | Column Name              | Legacy                   | Data Type       | Description                                           | Mandatory |
| --- | ------------------------ | ------------------------ | --------------- | ----------------------------------------------------- | --------- |
| 1   | `PRODUCT_ID`             | `PRODUCTID`              | Varchar(60)     | Assign unique ID.                                     | Y         |
| 2   | `PRODUCT_PRICE_TYPE_ID`  |                          | Varchar(60)     | Either `DEFAULT_PRICE` or `LIST_PRICE`                | Y         |
| 3   | `FROM_DATE`              |                          | DATETIME        | If blank will default to the current date and time    | N         |
| 4   | `THRU_DATE`              |                          | DATETIME        | If blank will be NULL and never ned                   | N         |
| 5   | `PRICE`                  |                          | DECIMAL(18, 3)  | The price of the product                              | Y         |

---
