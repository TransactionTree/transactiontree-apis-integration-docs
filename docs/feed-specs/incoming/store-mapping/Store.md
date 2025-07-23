# Store File Specification

**Directory**: `/incoming/store-mapping`

## Filename

```
Store_<Date>_<Time>_<fileid>.csv
```

* `<Date>`: `YYYYMMDD`
* `<Time>`: `HHMMSS`
* `<fileid>`: partner batch identifier (matches across files)

## Purpose

Provides detailed metadata for each store location, including address, contact, and operational attributes.

## Format

* **File Type**: CSV
* **Encoding**: UTF‑8, no BOM
* **Delimiter**: Comma (`,`)
* **Compression**: None
* **Quoting**: All field values **MUST** be enclosed in double quotes (e.g., `"Value"`).

## Columns

| Column            | Type    | Description                                                 |
| ----------------- | ------- | ----------------------------------------------------------- |
| `storeNumber`     | String  | Zero‑padded store ID (e.g. `00001`).                        |
| `storeName`       | String  | Official store name.                                        |
| `addressLine1`    | String  | Primary street address.                                     |
| `addressLine2`    | String  | Secondary address (suite/unit); blank if none.              |
| `country`         | String  | ISO country code.                                           |
| `city`            | String  | City or municipality.                                       |
| `state`           | String  | State or province code.                                     |
| `zipCode`         | String  | Postal or ZIP code.                                         |
| `Region_No`       | Integer | Must match `Region_No` in the hierarchy file.               |
| `Region_Name`     | String  | Must match `Region_Name` in the hierarchy file.             |
| `District_No`     | Integer | Must match `District_No` in the hierarchy file.             |
| `District_Name`   | String  | Must match `District_Name` in the hierarchy file.           |
| `phone`           | String  | Store phone number (digits only).                           |
| `storeEmail`      | String  | Contact email address, if available.                        |
| `latitude`        | Float   | Geographic latitude (decimal degrees).                      |
| `longitude`       | Float   | Geographic longitude (decimal degrees).                     |
| `storestatus`     | String  | Operational status (e.g. `Open`, `Closed`).                 |
| `localname`       | String  | Local‑language name, if different.                          |
| `SiteId`          | String  | Internal system/site identifier.                            |
| `storeOpenDate`   | String  | Opening date (e.g. `Sep 18 1998 12:00AM`; ISO recommended). |
| `activeFlag`      | String  | `Y` = active; `N` = closed/decommissioned.                  |
| `BOSSEnableFlag`  | String  | `Y` if BOSS enabled; otherwise `N` or blank.                |
| `BOPISEnableFlag` | String  | `Y` if BOPIS enabled; otherwise `N` or blank.               |
| `MallType`        | String  | Retail environment type (e.g. `MALL`, `OUTLET`).            |
| `manager`         | String  | Full name of the store manager.                             |
| `url1`            | String  | Primary store webpage URL.                                  |
| `url2`            | String  | Secondary or alternate URL (e.g. mobile site).              |
| `url3`            | String  | Promotions or events page URL.                              |
| `url4`            | String  | Loyalty program or customer portal URL.                     |
| `storeImageurl`   | String  | Public URL to the store’s main image asset.                 |
| `storeImage`      | String  | Image filename or Base64‑encoded image blob.                |
| `storeHTML`       | String  | HTML snippet for embedding a store preview widget.          |
| `brand`           | String  | Brand banner/trade name under which the store operates.     |
| `returnPolicy`    | String  | Plain‑text summary or link to the store’s return policy.    |

## Sample

```csv
"00001","Cherry Hill Mall","Cherry Hill Mall","2000 NJ-38, Suite 1390","USA","Cherry Hill","NJ","08002","8","Region 8 - Rick Nunez","13","District 13 - Danielle Voelkel","","","39.94110","-75.02613","Open","Cherry Hill Mall","1","Sep 18 1998 12:00AM","Y","Y","Y","MALL"
...
```

## Validation Rules

* Filename pattern must match exactly.
* Columns must be present and ordered as specified.
* Geographic coordinates within valid ranges.
* `Region_No`, `District_No` match hierarchy values.

---
