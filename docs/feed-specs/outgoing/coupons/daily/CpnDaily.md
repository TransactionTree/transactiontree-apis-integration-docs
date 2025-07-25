# CpnDaily File Specifications

**Directory**: `/outgoing/coupons/daily`

### Files

* `CpnDaily_PromoStores_YYYYMMDDHHMMSS.csv`
* `CpnDaily_DealCoupon_YYYYMMDDHHMMSS.csv`
* `CpnDaily_Definition_YYYYMMDDHHMMSS.csv`
* `CpnDaily_Event_YYYYMMDDHHMMSS.csv`
* `CpnDaily_ParamReasonList_YYYYMMDDHHMMSS.csv`


### CpnDaily\_Definition\_YYYYMMDDHHMMSS.csv

| Field Name                            | Data Type | Description                                                                                                                                         |
|--------------------------------------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| `coupon_identifier`                  | string    | The coupon identifier (coupon code for non-serialized, PromoCampaign ID for serialized promotions).                                                |
| `eventnum`                           | INT       | Unique identifier that stays the same for both serialized and non-serialized promotions.                                                           |
| `manager_auth_required`             | Boolean   | 1 if store manager approval is needed; based on `attr_storeManagerAuthorizationRequired` flag.                                                     |
| `scanned_invalid`                   | Boolean   | 1 means coupon cannot be scanned by barcode scanner; 0 means it can.                                                                                |
| `manual_invalid`                    | Boolean   | 1 means coupon cannot be manually selected from a list; 0 means it can.                                                                             |
| `allow_multiple_trans`              | Boolean   | 1 allows coupon to be scanned multiple times in a single transaction; 0 disallows.                                                                  |
| `manual_display_order`              | INT       | Determines position in display list.                                                                                                                |
| `tlog_reason_code`                  | INT       | Reason code for transaction log, distinct from Admin Reason Code.                                                                                   |
| `reason_code_description`           | string    | Descriptive explanation for applying the coupon.                                                                                                    |
| `discount_level`                    | INT       | 1 if promotion includes quantity condition; otherwise 2.                                                                                            |
| `discount_type`                     | INT       | Discount type: 1 = percent, 2 = dollar, 3 = new price, 10 = percent override, 11 = dollar override, 12 = new price override.                        |
| `discount_coupon`                   | string    | Specifies if coupon is marked as discount coupon; defaults to "Default".                                                                            |
| `employee_number_active`            | Boolean   | Indicates if an employee number is required for the promotion; defaults to 0.                                                                       |
| `employee_number`                   | string    | Holds the employee number when applicable; defaults to "Default".                                                                                   |
| `is_percent_active`                 | Boolean   | 1 if percentage discount applies; 0 otherwise. Set to 0 if POS_PROMO_ID exists; else 1 if configured as PROMO_ORDER_PERCENT.                        |
| `percent_off`                       | Decimal   | Percentage discount value; null if POS_PROMO_ID exists, else reflects PROMO_ORDER_PERCENT.                                                          |
| `Is_dollar_active`                  | Boolean   | 1 if dollar discount applies; 0 otherwise. Set to 0 if POS_PROMO_ID exists; else 1 if configured as PROMO_ORDER_AMOUNT.                             |
| `dollar_amount`                     | INT       | Dollar discount amount; null if POS_PROMO_ID exists; else reflects PROMO_ORDER_AMOUNT.                                                              |
| `new_price_active`                  | Boolean   | 1 if new price discount is active; 0 otherwise. Null by default; 0 if PROMO_NEW_PRICE is included.                                                  |
| `new_price`                         | INT       | New price set by promotion; null if not defined.                                                                                                    |
| `allow_grace_period`                | Boolean   | 1 allows coupon to be used after expiration (grace period); 0 does not. Defaults to 1.                                                              |
| `grace_period`                      | INT       | Days after expiration coupon is accepted; derived from `attr_couponGracePeriod`, or 0 if not set.                                                  |
| `grace_manager_required`            | Boolean   | 1 requires manager approval for using expired coupons; 0 does not.                                                                                  |
| `dealnum_active`                    | Boolean   | 1 if discount is associated with a deal; 0 otherwise.                                                                                               |
| `dealnum`                           | INT       | Deal number from `product_promo_deal` table (Mi9 event number).                                                                                     |
| `allow_start_grace_period`         | Boolean   | 1 allows coupon use before start date; 0 does not. Defaults to 1.                                                                                   |
| `start_grace_period`                | Boolean   | Days before activation a coupon is accepted; derived from `attr_couponGracePeriodStart`, or 0 if not set.                                          |
| `start_grace_manager_required`     | Boolean   | 1 requires manager approval for early use; 0 does not.                                                                                              |
| `deal_trigger`                      | Boolean   | 1 if coupon triggers a deal; 0 otherwise.                                                                                                           |
| `auto_apply_line_item_disc_hi_lo_item` | Boolean | 1 enables auto-application to qualifying item; 0 disables. Defaults to 1 if `autoApplyCoupon` is 'Y'.                                               |
| `auto_apply_hi_lo_choice`           | Boolean   | 1 applies to highest-priced item; 0 to lowest-priced.                                                                                               |
| `mgr_required_coupon_applied_multiply` | Boolean | 1 requires manager approval if coupon applied more than once to an item; 0 does not.                                                                |
| `allow_coupon_employee_transaction` | Boolean   | 1 if coupon is allowed in employee sales; 0 otherwise. Based on `attr_allowEmplSales`.                                                              |
| `allow_coupon_non_employee_transaction` | Boolean | 1 if coupon is allowed in non-employee sales; 0 otherwise. Based on `attr_allowRegular`.                                                            |
| `single_use`                        | Boolean   | 1 if coupon is single-use; 0 if reusable. Set to 0 if `isNonSerialized` is 'Y'.                                                                     |
| `host_defined`                      | Boolean   | 1 if coupon is host (loyalty) defined; 0 otherwise. Based on `attr_hostDefined`.                                                                    |
| `InstantSend`                       | Boolean   | 1 if coupon is configured for instant send; 0 otherwise. Based on `attr_instandSend`.                                                               |
| `brand_sg`                          | Boolean   | 1 if SG brand (`ifattr_1`) is active; 0 otherwise.                                                                                                  |
| `brand_sgc`                         | Boolean   | 1 if SGC brand (`attr_9`) is active; 0 otherwise.                                                                                                   |
| `brand_spi`                         | Boolean   | 1 if SPI brand (`ifattr_6`) is active; 0 otherwise.                                                                                                 |
| `brand_spc`                         | Boolean   | 1 if SPC brand (`attr_7`) is active; 0 otherwise.                                                                                                   |
| `pos_desc`                          | string    | Description to display on point of sale.                                                                                                            |
| `receipt_desc`                      | string    | Description to print on receipt.                                                                                                                    |
| `dsm_auth`                          | Boolean   | 1 if DSM (District Sales Manager) authorization is required; 0 otherwise. Based on `attr_posRc1`.                                                  |



### CpnDaily\_Event\_YYYYMMDDHHMMSS.csv

| Field Name         | Data Type | Description                                    |
| ------------------ | --------- | ---------------------------------------------- |
| `eventnum`         | INT       | Unique ID for each promotion event.            |
| `description`      | String    | Human-readable label or name of the promotion. |
| `startdate`        | Datetime  | Promotion start date/time.                     |
| `stopdate`         | Datetime  | Promotion end date/time.                       |
| `long_description` | String    | Extended version of the event description.     |


### CpnDaily\_ParamReasonList\_YYYYMMDDHHMMSS.csv

| Field Name          | Data Type         | Description                                                       |
|---------------------|-------------------|-------------------------------------------------------------------|
| `div_num`           | Integer           | Division number. Default = 1.                                     |
| `version_num`       | Integer           | Schema or config version. Default = 1.                            |
| `store_edit`        | Boolean (0/1)     | Was entry edited in UI. Default = 1.                              |
| `edit_date`         | Datetime          | When the entry was edited. Example: `2025-07-16 17:57:27`.        |
| `edit_by`           | String (varchar)  | Who edited the entry. Example: `"SG"`.                            |
| `reason_id`         | String or Integer | Grouping reason ID (`attr_grouping`).                             |
| `seq_num`           | Integer or String | POS code (`attr_posCode`).                                        |
| `literal`           | String (varchar)  | Display name / label (shown in UI or reports).                    |
| `manager_auth`      | Boolean (0/1)     | 1 if `storeManagerAuthorizationRequired = Y`, else 0.             |
| `loyalty_required`  | Boolean (0/1)     | Is loyalty required. Default = 0.                                 |
| `comment_required`  | Boolean (0/1)     | 1 if `commReq = Y`, else 0.                                       |
| `hidden`            | Boolean (0/1)     | Whether the reason code is visible. Default = 0.                  |
| `dsm_auth`          | Boolean (0/1)     | 1 if `attr_posRc1 = Y`, else 0.                                   |
| `eventnum`          | Integer           | Coupon event ID, shared across serialized and non-serialized.     |
| `brand_sg`          | Boolean (0/1)     | 1 if `ifattr_1 = Y`, else 0.                                      |
| `brand_sgc`         | Boolean (0/1)     | 1 if `attr_9 = Y`, else 0.                                        |
| `brand_spi`         | Boolean (0/1)     | 1 if `ifattr_6 = Y`, else 0.                                      |
| `brand_spc`         | Boolean (0/1)     | 1 if `attr_7 = Y`, else 0.                                        |



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