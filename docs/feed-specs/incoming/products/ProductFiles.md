# Product File Specification

**Directory**: `/incoming/products`

## Filename

* `Product_<Date>_<Time>_<fileid>.csv`
* `Category_<Date>_<Time>_<fileid>.csv`
* `ProductLocale_<Date>_<Time>_<fileid>.csv`
* `ProductPrice_<Date>_<Time>_<fileid>.csv`

| Filename                                   | Description                                       |
| ------------------------------------------ | ------------------------------------------------- |
| `Product_<Date>_<Time>_<fileid>.csv`           | Contains detailed metadata for each product, including taxonomy, pricing, and categorization.       |
| `Category_<Date>_<Time>_<fileid>.csv` | Defines product categories and their hierarchy within the catalog.                |
| `ProductLocale_<Date>_<Time>_<fileid>.csv`      | Contains product name and description connected to locale |
| `ProductPrice_<Date>_<Time>_<fileid>.csv`     | Contains product pricing information  |

* `<Date>`: `YYYYMMDD` (e.g. `20250723`)
* `<Time>`: `HHMMSS` (24‑hour clock)
* `<fileid>`: partner batch identifier (must match across related files)

## Purpose

Contains detailed metadata for each product, including taxonomy, pricing, and categorization.

## Format

* **File Type**: CSV
* **Encoding**: UTF‑8, no BOM
* **Delimiter**: Comma (`,`)
* **Text Enclosure**: Double quotes (`"`)
* **Line Break**: CRLF (`\r\n`)
* **Header**: First row must contain column names


---
