# CpnDaily File Specifications

**Directory**: `/outgoing/coupons/daily`

### Files

* `CpnDaily_PromoStores_YYYYMMDDHHMMSS.csv`
* `CpnDaily_DealCoupon_YYYYMMDDHHMMSS.csv`
* `CpnDaily_Definition_YYYYMMDDHHMMSS.csv`
* `CpnDaily_Event_YYYYMMDDHHMMSS.csv`
* `CpnDaily_ParamReasonList_YYYYMMDDHHMMSS.csv`


### CpnDaily\_Definition\_YYYYMMDDHHMMSS.csv

| Field Name                | Data Type | Description                                                                                                                   |
| ------------------------- | --------- | ----------------------------------------------------------------------------------------------------------------------------- |
| `coupon_identifier`       | string    | The coupon identifier (coupon code for non-serialized, PromoCampaign ID for serialized promotions).                           |
| `eventnum`                | INT       | Unique identifier that stays the same for both serialized and non-serialized promotions.                                      |
| `manager_auth_required`   | Boolean   | 1 if store manager approval is needed; based on attr\_storeManagerAuthorizationRequired flag.                                 |
| `scanned_invalid`         | Boolean   | 1 means coupon cannot be scanned by barcode scanner; 0 means it can.                                                          |
| `manual_invalid`          | Boolean   | 1 means coupon cannot be manually selected from a list; 0 means it can.                                                       |
| `allow_multiple_trans`    | Boolean   | 1 allows coupon to be scanned multiple times in a single transaction; 0 disallows.                                            |
| `manual_display_order`    | INT       | Determines position in display list.                                                                                          |
| `tlog_reason_code`        | INT       | Reason code for transaction log, distinct from Admin Reason Code.                                                             |
| `reason_code_description` | string    | Descriptive explanation for applying the coupon.                                                                              |
| `discount_level`          | INT       | 1 if promotion includes quantity condition; otherwise 2.                                                                      |
| `discount_type`           | INT       | Discount type: 1 = percent, 2 = dollar, 3 = new price, 10,11,12 for overrides.                                                |
| ...                       | ...       | Additional Boolean flags and fields (e.g., `discount_coupon`, `employee_number_active`, `percent_off`, `dollar_amount`, etc.) |


### CpnDaily\_Event\_YYYYMMDDHHMMSS.csv

| Field Name         | Data Type | Description                                    |
| ------------------ | --------- | ---------------------------------------------- |
| `eventnum`         | INT       | Unique ID for each promotion event.            |
| `description`      | String    | Human-readable label or name of the promotion. |
| `startdate`        | Datetime  | Promotion start date/time.                     |
| `stopdate`         | Datetime  | Promotion end date/time.                       |
| `long_description` | String    | Extended version of the event description.     |


### CpnDaily\_ParamReasonList\_YYYYMMDDHHMMSS.csv

| Field Name    | Data Type      | Description / Logic / Comments                                     |
| ------------- | -------------- | ------------------------------------------------------------------ |
| `div_num`     | Integer        | Division number, default = 1.                                      |
| `version_num` | Integer        | Schema or config version, default = 1.                             |
| `store_edit`  | Boolean (0/1)  | Was entry edited in UI, default = 1.                               |
| `edit_date`   | Datetime       | Timestamp of last edit (e.g., 2025-07-16 17:57:27).                |
| `edit_by`     | String         | User who edited the entry (e.g., “SG”).                            |
| `reason_id`   | String/Integer | Grouping reason ID (attr\_grouping).                               |
| `seq_num`     | Integer/String | POS code (attr\_posCode).                                          |
| `literal`     | String         | Display name/label shown in UI.                                    |
| ...           | ...            | Additional fields such as `manager_auth`, `loyalty_required`, etc. |


### CpnDaily\_DealCoupon\_YYYYMMDDHHMMSS.csv

| Field Name          | Data Type | Description                                                                   |
| ------------------- | --------- | ----------------------------------------------------------------------------- |
| `event_num`         | Integer   | Unique ID for the promotion event.                                            |
| `coupon_identifier` | String    | Coupon code (non-serialized) or PromoCampaign ID (serialized) per media type. |
| `dealnum`           | Integer   | Mi9 event number identifying the deal in product\_promo\_deal table.          |


### CpnDaily\_PromoStores\_YYYYMMDDHHMMSS.csv

| Field Name | Data Type | Comments / Behavior                                                  |
| ---------- | --------- | -------------------------------------------------------------------- |
| `StoreNum` | String    | 5-digit zero-padded store number (e.g., 00538, 00001).               |
| `EventID`  | String    | One or more comma-separated `eventnum` values assigned to the store. |


---