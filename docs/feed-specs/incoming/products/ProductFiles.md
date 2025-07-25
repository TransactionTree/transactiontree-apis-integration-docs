# Product File Specification

**Directory**: `/incoming/products`

## Filename

| Filename                                   | Column Definitions                | Description                                                                                   |
| ------------------------------------------ | --------------------------------- | --------------------------------------------------------------------------------------------- |
| `Product_<Date>_<Time>_<fileid>.csv`       | [Product](Product.md)             | Contains detailed metadata for each product, including taxonomy, pricing, and categorization. |
| `Category_<Date>_<Time>_<fileid>.csv`      | [Category](Category.md)           | Defines product categories and their hierarchy within the catalog.                            |
| `ProductLocale_<Date>_<Time>_<fileid>.csv` | [ProductLocale](ProductLocale.md) | Contains localized product names and descriptions per locale.                                 |
| `ProductPrice_<Date>_<Time>_<fileid>.csv`  | [ProductPrice](ProductPrice.md)   | Contains product pricing information, including promotional and base prices.                  |

---
* `<Date>`: `YYYYMMDD` (e.g. `20250723`)
* `<Time>`: `HHMMSS` (24‑hour clock)
* `<fileid>`: partner batch identifier (must match across related files)

## Format

* **File Type**: CSV
* **Encoding**: UTF‑8, no BOM
* **Delimiter**: Comma (`,`)
* **Text Enclosure**: Double quotes (`"`)
* **Line Break**: CRLF (`\r\n`)
* **Header**: First row must contain column names



---
