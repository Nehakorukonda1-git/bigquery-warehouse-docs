# fact_giving

## Columns

Total Columns: 93

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| `amount_usd` | BIGNUMERIC | From FinancialTransactionDetail.Amount. Transaction-detail level. The monetary value of this specific fund allocation in US dollars. |
| `campus_id` | INT64 | From Rock RMS Campus.Id. Campus level. The unique numeric identifier for each campus in the Rock RMS system. Rock > Admin Tools > General Settings > Campuses > Id field. Primary key for this table. |
| `campus_region` | STRING | From Rock RMS DefinedValue table via Campus Area attribute. Campus level. The geographical region the campus belongs to (e.g., 'Oklahoma', 'Kansas', 'Texas'). Rock > Admin > General Settings > Campuses > Attributes > Campus Area. |
| `campus_short_code` | STRING | From Data Warehouse, using Rock person data. Person level. The main, home, primary, or preferred campus of the person. This is the best source for identifing which campus a person belongs to. Rock > Profile > Main Contact Details. |
| `check_number` | STRING | From Rock RMS FinancialTransaction.TransactionCode. Transaction level. The check number for check payments only. NULL for other payment types. |
| `created_date_time` | DATETIME | From Rock RMS. Entity level. When record was created in Rock. |
| `donor_event` | STRING | From Rock RMS AttributeValue. Transaction level. Special campaign or event designation. |
| `family_name` | STRING | From household_staging table. Household level. The last name or designated family name for the household. Rock > People > Family. |
| `financial_transaction_detail_id` | INT64 | From Rock RMS FinancialTransactionDetail.Id. Transaction-detail level. Unique identifier for each fund allocation within a transaction. |
| `financial_transaction_id` | INT64 | From Rock RMS FinancialTransaction.Id. Transaction level. Unique identifier for each financial transaction record. The same transaction id shows up multiple times if given to different funds. |
| `financial_transaction_schedule_id` | INT64 | From Rock RMS FinancialTransaction.ScheduledTransactionId. Transaction level. Links to parent recurring schedule if applicable. NULL for non-scheduled. |
| `financial_transaction_status_message` | STRING | From Rock RMS FinancialTransaction.StatusMessage. Transaction level. Gateway error details: 'Insufficient funds', 'Card expired'. |
| `financial_transaction_timestamp` | TIMESTAMP | From Rock RMS FinancialTransaction.TransactionDateTime. Transaction level. The exact date and time when the financial transaction was processed. |
| `first_name` | STRING | Employee's legal first name from the employee table. Used for official documentation and reporting. |
| `for_reconciliation` | BOOL | Source table indicator. Record level. TRUE for FinancialTransaction table, FALSE for FailedFinancialTransaction table. Distinguishes data sources for reconciliation. |
| `frequency` | STRING | The frequency of the scheduled transaction (e.g., 'Weekly', 'Monthly', 'One-Time'). From Rock RMS defined values for transaction frequency. |
| `full_name` | STRING | From Rock RMS Person. Person level. The person's full name constructed as nickname (or first name if no nickname) plus last name. Used for human-readable identification in reports. |
| `gateway` | STRING | From Rock RMS FinancialGateway lookup. Transaction level. Payment processor: 'Stripe.com', 'PayPal'. NULL for cash/check. |
| `gateway_transaction_id` | STRING | From Rock RMS FinancialTransaction.TransactionCode. Transaction level. External reference ID from payment processor. |
| `giving_group_id` | INT64 | From Rock RMS Person.GivingGroupId. Person-level. ID for grouping family giving together. |
| `home_campus` | STRING | Synonymous with Rock Campus. See lc_campus for description. |
| `household` | STRUCT<is_first_gift BOOL, is_last_gift BOOL, is_first_gift_on_fund BOOL, is_last_gift_on_fund BOOL, previous_gift_timestamp TIMESTAMP, next_gift_timestamp TIMESTAMP, previous_gift_on_fund_timestamp TIMESTAMP, next_gift_on_fund_timestamp TIMESTAMP> | From Data Warehouse, using Rock person data. Household level. The full name of the family. Rock > Profile > Family Attributes. |
| `household.is_first_gift` | BOOL | Calculated using ROW_NUMBER(). Person level. TRUE if this is chronologically the person's first gift to Life.Church ever. |
| `household.is_first_gift_on_fund` | BOOL | Calculated using ROW_NUMBER() partitioned by fund. Person-fund level. TRUE if first gift to this specific fund. Enables fund-specific donor acquisition tracking. |
| `household.is_last_gift` | BOOL | Calculated using ROW_NUMBER(). Person level. TRUE if this is the person's most recent gift to date. Updated with each new transaction. |
| `household.is_last_gift_on_fund` | BOOL | Calculated using ROW_NUMBER() partitioned by fund. Person-fund level. TRUE if most recent gift to this specific fund. Identifies current fund preferences. |
| `household.next_gift_on_fund_timestamp` | TIMESTAMP | Calculated using LEAD() partitioned by fund. Person-fund level. Timestamp of next gift to same fund. NULL if most recent to fund. |
| `household.next_gift_timestamp` | TIMESTAMP | Calculated using LEAD(). Person level. Timestamp of the donor's next gift across all funds. NULL if most recent gift. |
| `household.previous_gift_on_fund_timestamp` | TIMESTAMP | Calculated using LAG() partitioned by fund. Person-fund level. Timestamp of previous gift to same fund. NULL if first to fund. |
| `household.previous_gift_timestamp` | TIMESTAMP | Calculated using LAG(). Person level. Timestamp of the donor's previous gift across all funds. NULL if first gift. |
| `is_business` | BOOL | From Rock RMS Person.RecordTypeValueId. Person-level. TRUE if record type is Business (ID=2), FALSE for individual persons. Rock > Person. |
| `is_consistent` | BOOL | Calculated from streak. Person level. TRUE if monthly_streak >= 12. Identifies committed regular givers for retention focus. |
| `is_first_gift` | BOOL | Calculated using ROW_NUMBER(). Person level. TRUE if this is chronologically the person's first gift to Life.Church ever. |
| `is_first_gift_on_fund` | BOOL | Calculated using ROW_NUMBER() partitioned by fund. Person-fund level. TRUE if first gift to this specific fund. Enables fund-specific donor acquisition tracking. |
| `is_first_recurring_successful_transaction` | BOOL | Calculated with ROW_NUMBER() and status filter. Person level. TRUE for person's first successful recurring gift ever. Tracks recurring donor acquisition. |
| `is_first_recurring_successful_transaction_by_schedule` | BOOL | Calculated per schedule ID. Schedule level. TRUE for first successful payment in each recurring schedule. Tracks schedule activation. |
| `is_first_recurring_transaction_by_schedule` | BOOL | Calculated per schedule ID. Schedule level. TRUE for first payment regardless of success or failure in each recurring schedule. Tracks schedule activation. |
| `is_greater_than_100k` | BOOL | Calculated from amount. Transaction level. TRUE if amount > $100,000. Triggers executive notification and special acknowledgment. |
| `is_greater_than_5k` | BOOL | Calculated from amount. Transaction level. TRUE if amount > $5,000. Used for major donor identification and special processing. |
| `is_green_giving` | BOOL | Calculated from person ID list. Person level. TRUE if giver is Green family member. Special handling for organizational leadership giving. |
| `is_last_gift` | BOOL | Calculated using ROW_NUMBER(). Person level. TRUE if this is the person's most recent gift to date. Updated with each new transaction. |
| `is_last_gift_on_fund` | BOOL | Calculated using ROW_NUMBER() partitioned by fund. Person-fund level. TRUE if most recent gift to this specific fund. Identifies current fund preferences. |
| `is_last_recurring_successful_transaction` | BOOL | Calculated with ROW_NUMBER() DESC and status filter. Person level. TRUE for person's most recent successful recurring gift. Identifies current recurring donors. |
| `is_last_recurring_successful_transaction_by_schedule` | BOOL | Calculated per schedule ID. Schedule level. TRUE for most recent successful payment in each schedule. Identifies active schedules. |
| `is_legacy_team_member` | BOOL | Boolean indicating whether the person is a Legacy Team member. |
| `is_recurring` | BOOL | From FinancialScheduledTransaction existence check. Transaction level. TRUE if part of automated recurring schedule. FALSE for one-time gifts. |
| `is_recurring_refunded_original_financial_transaction` | BOOL | From Rock RMS FinancialTransaction and FinancialScheduledTransaction tables. Transaction level. Boolean indicating whether the original transaction that was refunded was part of a recurring/scheduled gift series. TRUE if the original transaction had a financial_transaction_schedule_id, FALSE if it was a one-time gift. NULL if no refund or original transaction not found. Used to understand refund patterns for recurring vs one-time gifts. Rock > Contributions > Transaction Detail > Original Transaction > Scheduled Transaction. |
| `is_scheduled_one_time_gift` | BOOL | From FinancialScheduledTransaction.TransactionFrequencyValueId. Transaction level. TRUE if scheduled but non-recurring (future dated one-time). |
| `is_successful` | BOOL | Calculated from status and amount. Transaction level. TRUE if status='succeeded' AND amount>=0. Core metric for successful giving. |
| `last_failed_scheduled_transaction_timestamp` | TIMESTAMP | Calculated using MAX() window function. Schedule level. Previous failed payment timestamp for this schedule. NULL if no failures. |
| `last_name` | STRING | From Data Warehouse, using Rock person data. Person level. The last name of the person. Rock > Profile > Main Contact Details. |
| `last_successful_scheduled_transaction_timestamp` | TIMESTAMP | Calculated using MAX() window function. Schedule level. Previous successful payment timestamp for this schedule. NULL if first. |
| `lc_week_start_date` | DATE | The Sunday that begins the Life.Church operational week for this date. Data source: Calculated from base Date table with adjustments based on staff portal calendar events. Granularity: Date level. Calculation logic: Standard assignment uses the most recent Sunday; adjusted when ministry events span across Sundays - dates before the Sunday are moved to that Sunday's week. UI location: Staff Portal > Calendar Column purpose: Ensures multi-day events are analyzed as a single unit rather than split across weeks. Data format: DATE. |
| `modified_by_person_full_name` | STRING | From Rock RMS Person via ModifiedByPersonAliasId. Transaction level. Full name of last editor. Used for audit trail. |
| `modified_timestamp` | TIMESTAMP | Last modification timestamp for the event or entity. Event or entity level. ModifiedDateTime. Format: YYYY-MM-DD HH:MM:SS. |
| `monthly_streak` | INT64 | From giving_streak calculation. Person level. Consecutive months of giving including current. Integer starting at 1. Resets after gap. |
| `next_gift_on_fund_timestamp` | TIMESTAMP | Calculated using LEAD() partitioned by fund. Person-fund level. Timestamp of next gift to same fund. NULL if most recent to fund. |
| `next_gift_timestamp` | TIMESTAMP | Calculated using LEAD(). Person level. Timestamp of the donor's next gift across all funds. NULL if most recent gift. |
| `previous_gift_on_fund_timestamp` | TIMESTAMP | Calculated using LAG() partitioned by fund. Person-fund level. Timestamp of previous gift to same fund. NULL if first to fund. |
| `previous_gift_timestamp` | TIMESTAMP | Calculated using LAG(). Person level. Timestamp of the donor's previous gift across all funds. NULL if first gift. |
| `refund_reason` | STRING | From Rock RMS DefinedValue. Refund level. |
| `refund_reason_summary` | STRING | From Rock RMS FinancialTransactionRefund.RefundReasonSummary. Refund level. Free text explanation of refund. |
| `refunded` | BOOL | From FinancialTransactionRefund existence. Transaction level. TRUE if transaction was reversed. FALSE if still valid. |
| `refunded_original_financial_transaction_frequency` | STRING | From Rock RMS FinancialScheduledTransaction via original transaction lookup. Transaction level. The recurring frequency of the original transaction that was refunded (e.g., 'Weekly', 'Bi-Weekly', 'Monthly', 'Quarterly'). NULL for one-time gifts or when no refund exists. Helps identify which recurring frequencies have higher refund rates. Rock > Contributions > Scheduled Transaction List > Frequency. |
| `refunded_original_financial_transaction_id` | INT64 | From Rock RMS FinancialTransactionRefund.OriginalTransactionId. Refund level. Links refund to original transaction. NULL if not refunded. |
| `related_names` | STRING | From household_basic_info.group_salutation. Business level. List of related individuals for business accounts. Example: 'John and Jane Smith'. NULL for personal accounts. |
| `rms_person_id` | INT64 | The unique Rock RMS identifier for the individual. Person-level. Links to Person.Id in Rock RMS. Used to join all person-related data across the system. Rock > Person Profile. |
| `rms_primary_family_id` | INT64 | From Rock RMS Person.PrimaryFamilyId. Person-level. Duplicate of rms_family_id for compatibility. Rock > Person Profile > Family. |
| `rock_instance` | STRING | Instance identifier for the source Rock environment from which the transaction originated. Derived in this model as a literal per UNION branch. Example values: 'LC' (Life.Church), 'YV' (YouVersion). Purpose: provenance filtering, cross-instance comparisons, and one source of truth for everyhing income-related. |
| `scheduled_transaction_dimension` | STRUCT<schedule_start_timestamp TIMESTAMP, schedule_end_timestamp TIMESTAMP, schedule_cancel_timestamp TIMESTAMP, schedule_created_timestamp TIMESTAMP, schedule_next_payment_timestamp TIMESTAMP, is_active BOOL, last_successful_transaction TIMESTAMP, last_failed_transaction TIMESTAMP, schedule_source_type STRING, schedule_utm_source STRING, schedule_utm_medium STRING, schedule_utm_campaign STRING, schedule_utm_content STRING> | From lc_scheduled_transactions join. Schedule level. STRUCT with schedule lifecycle data: start, end, cancel timestamps, next payment date, active status. |
| `scheduled_transaction_dimension.is_active` | BOOL | From Rock RMS. Entity level. Boolean flag calculated by checking if entity status of the entity. TRUE indicates an active/open entity state, FALSE indicates inactive/closed. |
| `scheduled_transaction_dimension.last_failed_transaction` | TIMESTAMP | The most recent timestamp when this scheduled transaction failed to process a payment. NULL if no failed transactions exist. |
| `scheduled_transaction_dimension.last_successful_transaction` | TIMESTAMP | The most recent timestamp when this scheduled transaction successfully processed a payment. NULL if no successful transactions exist. |
| `scheduled_transaction_dimension.schedule_cancel_timestamp` | TIMESTAMP | The timestamp when the schedule was cancelled/inactivated. Calculated from multiple sources: inactivatedatetime, modified datetime when isactive changed to false, or history table tracking. This is the most reliable indicator of when a donor stopped their recurring gift. |
| `scheduled_transaction_dimension.schedule_created_timestamp` | TIMESTAMP | The timestamp when the scheduled transaction was initially created in Rock RMS. |
| `scheduled_transaction_dimension.schedule_end_timestamp` | TIMESTAMP | The timestamp when the scheduled transaction is set to end. NULL for indefinite schedules. |
| `scheduled_transaction_dimension.schedule_next_payment_timestamp` | TIMESTAMP | The timestamp when the next payment is scheduled to process. NULL if schedule is cancelled or completed. |
| `scheduled_transaction_dimension.schedule_source_type` | STRING | No description |
| `scheduled_transaction_dimension.schedule_start_timestamp` | TIMESTAMP | The timestamp when the scheduled transaction was set to begin processing payments. |
| `scheduled_transaction_dimension.schedule_utm_campaign` | STRING | No description |
| `scheduled_transaction_dimension.schedule_utm_content` | STRING | No description |
| `scheduled_transaction_dimension.schedule_utm_medium` | STRING | No description |
| `scheduled_transaction_dimension.schedule_utm_source` | STRING | No description |
| `transaction_fund` | STRING | From Rock RMS FinancialAccount.Name. Transaction-detail level. The designated fund name (e.g., 'Tithe', 'Bible Translation''). |
| `transaction_status` | STRING | From Rock RMS FinancialTransaction.Status. Transaction level. Processing outcome: 'succeeded', 'failed', 'pending'. |
| `transaction_subtype` | STRING | From Rock RMS DefinedValue via SourceTypeValueId. Transaction level. Payment sub-classification: 'Visa', 'Mastercard', 'Bank Account'. |
| `transaction_top_type` | STRING | Calculated from payment type. Transaction level. High-level categorization: 'Check', 'Cash', or 'Digital'. Derived from CurrencyTypeValue. |
| `transaction_type` | STRING | From Rock RMS DefinedValue via CurrencyTypeValueId. Transaction level. Payment method: 'Cash', 'Check', 'Credit Card', 'ACH'. |
| `utm_campaign` | STRING | From Segment tracking data. Entity level (attached to the specific record - person, form submission, financial transaction, etc.). Contains the specific campaign name or identifier used to track marketing initiatives. Enables performance analysis across different campaigns and helps measure campaign ROI. |
| `utm_content` | STRING | From Segment tracking data. Entity level (attached to the specific record - person, form submission, financial transaction, etc.). Captures the specific content variant identifier within a campaign, used to differentiate similar content or links within the same ad/campaign for A/B testing and performance analysis. |
| `utm_medium` | STRING | From Segment tracking data. Entity level (attached to the specific record - person, form submission, financial transaction, etc.). Identifies the marketing medium or channel through which the user arrived (e.g., email, social, cpc, organic). Used to analyze channel effectiveness and allocate marketing resources. |
| `utm_source` | STRING | From Segment tracking data. Entity level (attached to the specific record - person, form submission, financial transaction, etc.). Identifies the specific source platform or website that referred the traffic (e.g., google, facebook, newsletter). Critical for understanding which platforms drive engagement and conversions. |
| `utm_term` | STRING | From Segment tracking data. Entity level (attached to the specific record - person, form submission, financial transaction, etc.). Stores the paid search keywords or terms that triggered the ad/link click. Primarily used for paid search campaign analysis and keyword performance tracking. |

## Column Details

### `amount_usd`

- **Type**: BIGNUMERIC
- **Description**: From FinancialTransactionDetail.Amount. Transaction-detail level. The monetary value of this specific fund allocation in US dollars.

### `campus_id`

- **Type**: INT64
- **Description**: From Rock RMS Campus.Id. Campus level. The unique numeric identifier for each campus in the Rock RMS system. Rock > Admin Tools > General Settings > Campuses > Id field. Primary key for this table.

### `campus_region`

- **Type**: STRING
- **Description**: From Rock RMS DefinedValue table via Campus Area attribute. Campus level. The geographical region the campus belongs to (e.g., 'Oklahoma', 'Kansas', 'Texas'). Rock > Admin > General Settings > Campuses > Attributes > Campus Area.

### `campus_short_code`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock person data. Person level. The main, home, primary, or preferred campus of the person. This is the best source for identifing which campus a person belongs to. Rock > Profile > Main Contact Details.

### `check_number`

- **Type**: STRING
- **Description**: From Rock RMS FinancialTransaction.TransactionCode. Transaction level. The check number for check payments only. NULL for other payment types.

### `created_date_time`

- **Type**: DATETIME
- **Description**: From Rock RMS. Entity level. When record was created in Rock.

### `donor_event`

- **Type**: STRING
- **Description**: From Rock RMS AttributeValue. Transaction level. Special campaign or event designation.

### `family_name`

- **Type**: STRING
- **Description**: From household_staging table. Household level. The last name or designated family name for the household. Rock > People > Family.

### `financial_transaction_detail_id`

- **Type**: INT64
- **Description**: From Rock RMS FinancialTransactionDetail.Id. Transaction-detail level. Unique identifier for each fund allocation within a transaction.

### `financial_transaction_id`

- **Type**: INT64
- **Description**: From Rock RMS FinancialTransaction.Id. Transaction level. Unique identifier for each financial transaction record. The same transaction id shows up multiple times if given to different funds.

### `financial_transaction_schedule_id`

- **Type**: INT64
- **Description**: From Rock RMS FinancialTransaction.ScheduledTransactionId. Transaction level. Links to parent recurring schedule if applicable. NULL for non-scheduled.

### `financial_transaction_status_message`

- **Type**: STRING
- **Description**: From Rock RMS FinancialTransaction.StatusMessage. Transaction level. Gateway error details: 'Insufficient funds', 'Card expired'.

### `financial_transaction_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS FinancialTransaction.TransactionDateTime. Transaction level. The exact date and time when the financial transaction was processed.

### `first_name`

- **Type**: STRING
- **Description**: Employee's legal first name from the employee table. Used for official documentation and reporting.

### `for_reconciliation`

- **Type**: BOOL
- **Description**: Source table indicator. Record level. TRUE for FinancialTransaction table, FALSE for FailedFinancialTransaction table. Distinguishes data sources for reconciliation.

### `frequency`

- **Type**: STRING
- **Description**: The frequency of the scheduled transaction (e.g., 'Weekly', 'Monthly', 'One-Time'). From Rock RMS defined values for transaction frequency.

### `full_name`

- **Type**: STRING
- **Description**: From Rock RMS Person. Person level. The person's full name constructed as nickname (or first name if no nickname) plus last name. Used for human-readable identification in reports.

### `gateway`

- **Type**: STRING
- **Description**: From Rock RMS FinancialGateway lookup. Transaction level. Payment processor: 'Stripe.com', 'PayPal'. NULL for cash/check.

### `gateway_transaction_id`

- **Type**: STRING
- **Description**: From Rock RMS FinancialTransaction.TransactionCode. Transaction level. External reference ID from payment processor.

### `giving_group_id`

- **Type**: INT64
- **Description**: From Rock RMS Person.GivingGroupId. Person-level. ID for grouping family giving together.

### `home_campus`

- **Type**: STRING
- **Description**: Synonymous with Rock Campus. See lc_campus for description.

### `household`

- **Type**: STRUCT<is_first_gift BOOL, is_last_gift BOOL, is_first_gift_on_fund BOOL, is_last_gift_on_fund BOOL, previous_gift_timestamp TIMESTAMP, next_gift_timestamp TIMESTAMP, previous_gift_on_fund_timestamp TIMESTAMP, next_gift_on_fund_timestamp TIMESTAMP>
- **Description**: From Data Warehouse, using Rock person data. Household level. The full name of the family. Rock > Profile > Family Attributes.

### `household.is_first_gift`

- **Type**: BOOL
- **Description**: Calculated using ROW_NUMBER(). Person level. TRUE if this is chronologically the person's first gift to Life.Church ever.

### `household.is_first_gift_on_fund`

- **Type**: BOOL
- **Description**: Calculated using ROW_NUMBER() partitioned by fund. Person-fund level. TRUE if first gift to this specific fund. Enables fund-specific donor acquisition tracking.

### `household.is_last_gift`

- **Type**: BOOL
- **Description**: Calculated using ROW_NUMBER(). Person level. TRUE if this is the person's most recent gift to date. Updated with each new transaction.

### `household.is_last_gift_on_fund`

- **Type**: BOOL
- **Description**: Calculated using ROW_NUMBER() partitioned by fund. Person-fund level. TRUE if most recent gift to this specific fund. Identifies current fund preferences.

### `household.next_gift_on_fund_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using LEAD() partitioned by fund. Person-fund level. Timestamp of next gift to same fund. NULL if most recent to fund.

### `household.next_gift_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using LEAD(). Person level. Timestamp of the donor's next gift across all funds. NULL if most recent gift.

### `household.previous_gift_on_fund_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using LAG() partitioned by fund. Person-fund level. Timestamp of previous gift to same fund. NULL if first to fund.

### `household.previous_gift_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using LAG(). Person level. Timestamp of the donor's previous gift across all funds. NULL if first gift.

### `is_business`

- **Type**: BOOL
- **Description**: From Rock RMS Person.RecordTypeValueId. Person-level. TRUE if record type is Business (ID=2), FALSE for individual persons. Rock > Person.

### `is_consistent`

- **Type**: BOOL
- **Description**: Calculated from streak. Person level. TRUE if monthly_streak >= 12. Identifies committed regular givers for retention focus.

### `is_first_gift`

- **Type**: BOOL
- **Description**: Calculated using ROW_NUMBER(). Person level. TRUE if this is chronologically the person's first gift to Life.Church ever.

### `is_first_gift_on_fund`

- **Type**: BOOL
- **Description**: Calculated using ROW_NUMBER() partitioned by fund. Person-fund level. TRUE if first gift to this specific fund. Enables fund-specific donor acquisition tracking.

### `is_first_recurring_successful_transaction`

- **Type**: BOOL
- **Description**: Calculated with ROW_NUMBER() and status filter. Person level. TRUE for person's first successful recurring gift ever. Tracks recurring donor acquisition.

### `is_first_recurring_successful_transaction_by_schedule`

- **Type**: BOOL
- **Description**: Calculated per schedule ID. Schedule level. TRUE for first successful payment in each recurring schedule. Tracks schedule activation.

### `is_first_recurring_transaction_by_schedule`

- **Type**: BOOL
- **Description**: Calculated per schedule ID. Schedule level. TRUE for first payment regardless of success or failure in each recurring schedule. Tracks schedule activation.

### `is_greater_than_100k`

- **Type**: BOOL
- **Description**: Calculated from amount. Transaction level. TRUE if amount > $100,000. Triggers executive notification and special acknowledgment.

### `is_greater_than_5k`

- **Type**: BOOL
- **Description**: Calculated from amount. Transaction level. TRUE if amount > $5,000. Used for major donor identification and special processing.

### `is_green_giving`

- **Type**: BOOL
- **Description**: Calculated from person ID list. Person level. TRUE if giver is Green family member. Special handling for organizational leadership giving.

### `is_last_gift`

- **Type**: BOOL
- **Description**: Calculated using ROW_NUMBER(). Person level. TRUE if this is the person's most recent gift to date. Updated with each new transaction.

### `is_last_gift_on_fund`

- **Type**: BOOL
- **Description**: Calculated using ROW_NUMBER() partitioned by fund. Person-fund level. TRUE if most recent gift to this specific fund. Identifies current fund preferences.

### `is_last_recurring_successful_transaction`

- **Type**: BOOL
- **Description**: Calculated with ROW_NUMBER() DESC and status filter. Person level. TRUE for person's most recent successful recurring gift. Identifies current recurring donors.

### `is_last_recurring_successful_transaction_by_schedule`

- **Type**: BOOL
- **Description**: Calculated per schedule ID. Schedule level. TRUE for most recent successful payment in each schedule. Identifies active schedules.

### `is_legacy_team_member`

- **Type**: BOOL
- **Description**: Boolean indicating whether the person is a Legacy Team member.

### `is_recurring`

- **Type**: BOOL
- **Description**: From FinancialScheduledTransaction existence check. Transaction level. TRUE if part of automated recurring schedule. FALSE for one-time gifts.

### `is_recurring_refunded_original_financial_transaction`

- **Type**: BOOL
- **Description**: From Rock RMS FinancialTransaction and FinancialScheduledTransaction tables. Transaction level. Boolean indicating whether the original transaction that was refunded was part of a recurring/scheduled gift series. TRUE if the original transaction had a financial_transaction_schedule_id, FALSE if it was a one-time gift. NULL if no refund or original transaction not found. Used to understand refund patterns for recurring vs one-time gifts. Rock > Contributions > Transaction Detail > Original Transaction > Scheduled Transaction.

### `is_scheduled_one_time_gift`

- **Type**: BOOL
- **Description**: From FinancialScheduledTransaction.TransactionFrequencyValueId. Transaction level. TRUE if scheduled but non-recurring (future dated one-time).

### `is_successful`

- **Type**: BOOL
- **Description**: Calculated from status and amount. Transaction level. TRUE if status='succeeded' AND amount>=0. Core metric for successful giving.

### `last_failed_scheduled_transaction_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using MAX() window function. Schedule level. Previous failed payment timestamp for this schedule. NULL if no failures.

### `last_name`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock person data. Person level. The last name of the person. Rock > Profile > Main Contact Details.

### `last_successful_scheduled_transaction_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using MAX() window function. Schedule level. Previous successful payment timestamp for this schedule. NULL if first.

### `lc_week_start_date`

- **Type**: DATE
- **Description**: The Sunday that begins the Life.Church operational week for this date. Data source: Calculated from base Date table with adjustments based on staff portal calendar events. Granularity: Date level. Calculation logic: Standard assignment uses the most recent Sunday; adjusted when ministry events span across Sundays - dates before the Sunday are moved to that Sunday's week. UI location: Staff Portal > Calendar Column purpose: Ensures multi-day events are analyzed as a single unit rather than split across weeks. Data format: DATE.

### `modified_by_person_full_name`

- **Type**: STRING
- **Description**: From Rock RMS Person via ModifiedByPersonAliasId. Transaction level. Full name of last editor. Used for audit trail.

### `modified_timestamp`

- **Type**: TIMESTAMP
- **Description**: Last modification timestamp for the event or entity. Event or entity level. ModifiedDateTime. Format: YYYY-MM-DD HH:MM:SS.

### `monthly_streak`

- **Type**: INT64
- **Description**: From giving_streak calculation. Person level. Consecutive months of giving including current. Integer starting at 1. Resets after gap.

### `next_gift_on_fund_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using LEAD() partitioned by fund. Person-fund level. Timestamp of next gift to same fund. NULL if most recent to fund.

### `next_gift_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using LEAD(). Person level. Timestamp of the donor's next gift across all funds. NULL if most recent gift.

### `previous_gift_on_fund_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using LAG() partitioned by fund. Person-fund level. Timestamp of previous gift to same fund. NULL if first to fund.

### `previous_gift_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using LAG(). Person level. Timestamp of the donor's previous gift across all funds. NULL if first gift.

### `refund_reason`

- **Type**: STRING
- **Description**: From Rock RMS DefinedValue. Refund level.

### `refund_reason_summary`

- **Type**: STRING
- **Description**: From Rock RMS FinancialTransactionRefund.RefundReasonSummary. Refund level. Free text explanation of refund.

### `refunded`

- **Type**: BOOL
- **Description**: From FinancialTransactionRefund existence. Transaction level. TRUE if transaction was reversed. FALSE if still valid.

### `refunded_original_financial_transaction_frequency`

- **Type**: STRING
- **Description**: From Rock RMS FinancialScheduledTransaction via original transaction lookup. Transaction level. The recurring frequency of the original transaction that was refunded (e.g., 'Weekly', 'Bi-Weekly', 'Monthly', 'Quarterly'). NULL for one-time gifts or when no refund exists. Helps identify which recurring frequencies have higher refund rates. Rock > Contributions > Scheduled Transaction List > Frequency.

### `refunded_original_financial_transaction_id`

- **Type**: INT64
- **Description**: From Rock RMS FinancialTransactionRefund.OriginalTransactionId. Refund level. Links refund to original transaction. NULL if not refunded.

### `related_names`

- **Type**: STRING
- **Description**: From household_basic_info.group_salutation. Business level. List of related individuals for business accounts. Example: 'John and Jane Smith'. NULL for personal accounts.

### `rms_person_id`

- **Type**: INT64
- **Description**: The unique Rock RMS identifier for the individual. Person-level. Links to Person.Id in Rock RMS. Used to join all person-related data across the system. Rock > Person Profile.

### `rms_primary_family_id`

- **Type**: INT64
- **Description**: From Rock RMS Person.PrimaryFamilyId. Person-level. Duplicate of rms_family_id for compatibility. Rock > Person Profile > Family.

### `rock_instance`

- **Type**: STRING
- **Description**: Instance identifier for the source Rock environment from which the transaction originated. Derived in this model as a literal per UNION branch. Example values: 'LC' (Life.Church), 'YV' (YouVersion). Purpose: provenance filtering, cross-instance comparisons, and one source of truth for everyhing income-related.

### `scheduled_transaction_dimension`

- **Type**: STRUCT<schedule_start_timestamp TIMESTAMP, schedule_end_timestamp TIMESTAMP, schedule_cancel_timestamp TIMESTAMP, schedule_created_timestamp TIMESTAMP, schedule_next_payment_timestamp TIMESTAMP, is_active BOOL, last_successful_transaction TIMESTAMP, last_failed_transaction TIMESTAMP, schedule_source_type STRING, schedule_utm_source STRING, schedule_utm_medium STRING, schedule_utm_campaign STRING, schedule_utm_content STRING>
- **Description**: From lc_scheduled_transactions join. Schedule level. STRUCT with schedule lifecycle data: start, end, cancel timestamps, next payment date, active status.

### `scheduled_transaction_dimension.is_active`

- **Type**: BOOL
- **Description**: From Rock RMS. Entity level. Boolean flag calculated by checking if entity status of the entity. TRUE indicates an active/open entity state, FALSE indicates inactive/closed.

### `scheduled_transaction_dimension.last_failed_transaction`

- **Type**: TIMESTAMP
- **Description**: The most recent timestamp when this scheduled transaction failed to process a payment. NULL if no failed transactions exist.

### `scheduled_transaction_dimension.last_successful_transaction`

- **Type**: TIMESTAMP
- **Description**: The most recent timestamp when this scheduled transaction successfully processed a payment. NULL if no successful transactions exist.

### `scheduled_transaction_dimension.schedule_cancel_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp when the schedule was cancelled/inactivated. Calculated from multiple sources: inactivatedatetime, modified datetime when isactive changed to false, or history table tracking. This is the most reliable indicator of when a donor stopped their recurring gift.

### `scheduled_transaction_dimension.schedule_created_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp when the scheduled transaction was initially created in Rock RMS.

### `scheduled_transaction_dimension.schedule_end_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp when the scheduled transaction is set to end. NULL for indefinite schedules.

### `scheduled_transaction_dimension.schedule_next_payment_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp when the next payment is scheduled to process. NULL if schedule is cancelled or completed.

### `scheduled_transaction_dimension.schedule_source_type`

- **Type**: STRING

### `scheduled_transaction_dimension.schedule_start_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp when the scheduled transaction was set to begin processing payments.

### `scheduled_transaction_dimension.schedule_utm_campaign`

- **Type**: STRING

### `scheduled_transaction_dimension.schedule_utm_content`

- **Type**: STRING

### `scheduled_transaction_dimension.schedule_utm_medium`

- **Type**: STRING

### `scheduled_transaction_dimension.schedule_utm_source`

- **Type**: STRING

### `transaction_fund`

- **Type**: STRING
- **Description**: From Rock RMS FinancialAccount.Name. Transaction-detail level. The designated fund name (e.g., 'Tithe', 'Bible Translation'').

### `transaction_status`

- **Type**: STRING
- **Description**: From Rock RMS FinancialTransaction.Status. Transaction level. Processing outcome: 'succeeded', 'failed', 'pending'.

### `transaction_subtype`

- **Type**: STRING
- **Description**: From Rock RMS DefinedValue via SourceTypeValueId. Transaction level. Payment sub-classification: 'Visa', 'Mastercard', 'Bank Account'.

### `transaction_top_type`

- **Type**: STRING
- **Description**: Calculated from payment type. Transaction level. High-level categorization: 'Check', 'Cash', or 'Digital'. Derived from CurrencyTypeValue.

### `transaction_type`

- **Type**: STRING
- **Description**: From Rock RMS DefinedValue via CurrencyTypeValueId. Transaction level. Payment method: 'Cash', 'Check', 'Credit Card', 'ACH'.

### `utm_campaign`

- **Type**: STRING
- **Description**: From Segment tracking data. Entity level (attached to the specific record - person, form submission, financial transaction, etc.). Contains the specific campaign name or identifier used to track marketing initiatives. Enables performance analysis across different campaigns and helps measure campaign ROI.

### `utm_content`

- **Type**: STRING
- **Description**: From Segment tracking data. Entity level (attached to the specific record - person, form submission, financial transaction, etc.). Captures the specific content variant identifier within a campaign, used to differentiate similar content or links within the same ad/campaign for A/B testing and performance analysis.

### `utm_medium`

- **Type**: STRING
- **Description**: From Segment tracking data. Entity level (attached to the specific record - person, form submission, financial transaction, etc.). Identifies the marketing medium or channel through which the user arrived (e.g., email, social, cpc, organic). Used to analyze channel effectiveness and allocate marketing resources.

### `utm_source`

- **Type**: STRING
- **Description**: From Segment tracking data. Entity level (attached to the specific record - person, form submission, financial transaction, etc.). Identifies the specific source platform or website that referred the traffic (e.g., google, facebook, newsletter). Critical for understanding which platforms drive engagement and conversions.

### `utm_term`

- **Type**: STRING
- **Description**: From Segment tracking data. Entity level (attached to the specific record - person, form submission, financial transaction, etc.). Stores the paid search keywords or terms that triggered the ad/link click. Primarily used for paid search campaign analysis and keyword performance tracking.

