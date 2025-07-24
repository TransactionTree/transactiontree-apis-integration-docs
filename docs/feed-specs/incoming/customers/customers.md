# Customer File Specifications

**Directory**: `/incoming/customers`

## Filename Patterns

* `Customer_<Date>_<Time>_<fileid>.csv`
* `Contact_<Date>_<Time>_<fileid>.csv`
* `Lead_<Date>_<Time>_<fileid>.csv`
* `Account_<Date>_<Time>_<fileid>.csv`

> **Filename components**:
>
> * `<Date>`: `YYYYMMDD` (e.g. `20250724`)
> * `<Time>`: `HHMMSS` (24‑hour clock)
> * `<fileid>`: partner batch identifier (must match across related files)

## File Format

* **Type**: CSV
* **Separator**: Comma (`,`)
* **Text Enclosure**: Double quotes (`"`)
* **Line Break**: CRLF (`\r\n`)
* **Header**: First row must contain column names

## Columns

| No | Column Name                 | Data Type    | Description                                                                                                                  | Customer | Contact | Lead | Account |
| -- | --------------------------- | ------------ | ---------------------------------------------------------------------------------------------------------------------------- | :------: | :-----: | :--: | :-----: |
| 1  | `PARTY_ID`                  | Varchar(60)  | Assign unique ID. If `EXTERNAL_ID` is mandatory and unique, `PARTY_ID` can be blank; import will generate one automatically. |    Y\*   |   Y\*   |  Y\* |   Y\*   |
| 2  | `EXTERNAL_ID`               | Varchar(255) | Cross reference to external system’s unique ID. Mandatory only when `PARTY_ID` is blank.                                     |    Y\*   |   Y\*   |  Y\* |   Y\*   |
| 3  | `STATUS_ID`                 | Varchar(60)  | Choose: `PARTY_ENABLED` = enabled, `PARTY_DISABLED` = disabled.                                                              |     Y    |    Y    |   Y  |    Y    |
| 4  | `CREATED_DATE`              | Datetime     | Timestamp when party is created; blank uses import timestamp. Format: `YYYY-MM-DD HH:MM:SS` (e.g. `2015-02-22 13:04:22`).    |          |         |      |         |
| 5  | `FIRST_NAME`                | Varchar(100) | Given name.                                                                                                                  |    N/A   |   N/A   |  N/A |   N/A   |
| 6  | `MIDDLE_NAME`               | Varchar(100) | Middle name.                                                                                                                 |    N/A   |   N/A   |  N/A |   N/A   |
| 7  | `LAST_NAME`                 | Varchar(100) | Family name.                                                                                                                 |    N/A   |   N/A   |  N/A |   N/A   |
| 8  | `GENDER`                    | Char(1)      | `M` = Male, `F` = Female, Blank = Unknown.                                                                                   |    N/A   |   N/A   |  N/A |   N/A   |
| 9  | `BIRTH_DATE`                | Date         | Format: `YYYY-MM-DD` (e.g. `2015-02-22`).                                                                                    |    N/A   |   N/A   |  N/A |   N/A   |
| 10 | `LOCAL_STORE_PREFERENCE`    | Varchar(100) | Preferred store code.                                                                                                        |    N/A   |   N/A   |  N/A |   N/A   |
| 11 | `ASSIGNED_STORE`            | Varchar(100) | Current assigned store.                                                                                                      |    N/A   |   N/A   |  N/A |   N/A   |
| 12 | `GROUP_NAME`                | Varchar(100) | Group name.                                                                                                                  |    N/A   |   N/A   |  N/A |    Y    |
| 13 | `COMPANY_NAME`              | Varchar(100) | Organization or employer.                                                                                                    |          |         |      |    Y    |
| 14 | `ACCOUNT_ID`                | Varchar(60)  | Linked account ID.                                                                                                           |    N/A   |   N/A   |  N/A |   N/A   |
| 15 | `RESPONSIBLE_FOR`           | Varchar(60)  | Internal contact responsible code.                                                                                           |          |         |      |         |
| 16 | `TO_NAME`                   | Varchar(100) | Recipient name for mailing.                                                                                                  |          |         |      |         |
| 17 | `ATTN_NAME`                 | Varchar(100) | Attention line name.                                                                                                         |          |         |      |         |
| 18 | `ADDRESS1`                  | Varchar(255) | Street address line 1.                                                                                                       |          |         |      |         |
| 19 | `ADDRESS2`                  | Varchar(255) | Street address line 2.                                                                                                       |          |         |      |         |
| 20 | `CITY`                      | Varchar(100) | City or locality.                                                                                                            |          |         |      |         |
| 21 | `POSTAL_CODE`               | Varchar(60)  | Postal or ZIP code.                                                                                                          |          |         |      |         |
| 22 | `POSTAL_CODE_EXT`           | Varchar(60)  | Postal or ZIP extension.                                                                                                     |          |         |      |         |
| 23 | `COUNTRY_ID`                | Varchar(60)  | ISO country code.                                                                                                            |          |         |      |         |
| 24 | `STATE_PROVINCE_ID`         | Varchar(60)  | State or province code.                                                                                                      |          |         |      |         |
| 25 | `POSTAL_ALLOW_SOLICITATION` | Char(1)      | `Y` = allow, `N` = don’t allow; else = allow.                                                                                |          |         |      |         |
| 26 | `PHONE`                     | Varchar(30)  | Country code, area code, number, ext. Allowed: `# + ( ) - . space "ext" "x"`.                                                |          |         |      |         |
| 27 | `PHONE_ALLOW_SOLICITATION`  | Char(1)      | Same as `POSTAL_ALLOW_SOLICITATION`.                                                                                         |          |         |      |         |
| 28 | `EMAIL`                     | Varchar(255) | Email address.                                                                                                               |          |         |      |         |
| 29 | `EMAIL_ALLOW_SOLICITATION`  | Char(1)      | Same as `POSTAL_ALLOW_SOLICITATION`.                                                                                         |          |         |      |         |
| 30 | `EXTRA_DATA_1`              | Varchar(255) | Extra data for paid custom code; leave blank.                                                                                |          |         |      |         |
| 31 | `EXTRA_DATA_2`              | Varchar(255) | Extra data for paid custom code; leave blank.                                                                                |          |         |      |         |
| 32 | `EXTRA_DATA_3`              | Varchar(255) | Extra data for paid custom code; leave blank.                                                                                |          |         |      |         |
| 33 | `EXTRA_DATA_4`              | Varchar(255) | Extra data for paid custom code; leave blank.                                                                                |          |         |      |         |
| 34 | `EXTRA_DATA_5`              | Varchar(255) | Extra data for paid custom code; leave blank.                                                                                |          |         |      |         |
| 35 | `EXTRA_DATA_6`              | Varchar(255) | Extra data for paid custom code; leave blank.                                                                                |          |         |      |         |
| 36 | `EXTRA_DATA_7`              | Varchar(255) | Extra data for paid custom code; leave blank.                                                                                |          |         |      |         |
| 37 | `EXTRA_DATA_8`              | Varchar(255) | Extra data for paid custom code; leave blank.                                                                                |          |         |      |         |
| 38 | `EXTRA_DATA_9`              | Varchar(255) | Extra data for paid custom code; leave blank.                                                                                |          |         |      |         |
| 39 | `EXTRA_DATA_10`             | Varchar(255) | Extra data for paid custom code; leave blank.                                                                                |          |         |      |         |
| 40 | `EXTRA_DATA_11`             | Varchar(255) | Extra data for paid custom code; leave blank.                                                                                |          |         |      |         |
| 41 | `EXTRA_DATA_12`             | Varchar(255) | Extra data for paid custom code; leave blank.                                                                                |          |         |      |         |
| 42 | `EXTRA_DATA_13`             | Varchar(255) | Extra data for paid custom code; leave blank.                                                                                |          |         |      |         |
| 43 | `EXTRA_DATA_14`             | Varchar(255) | Extra data for paid custom code; leave blank.                                                                                |          |         |      |         |
| 44 | `EXTRA_DATA_15`             | Varchar(255) | Extra data for paid custom code; leave blank.                                                                                |          |         |      |         |

*Notes:*

* `*` Mandatory only when `PARTY_ID` is blank (for `EXTERNAL_ID` and `PARTY_ID`).

---

For any questions regarding the Party file import, contact Data‑Ops at [data‑ops@transactiontree.com](mailto:data‑ops@transactiontree.com).
