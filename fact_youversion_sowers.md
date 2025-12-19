# fact_youversion_sowers

## Columns

Total Columns: 26

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| `city` | STRING | From Rock RMS Location. Entity level. The city where the entity is located. |
| `country` | STRING | From location.country. Person level. The country of the person's home address. Typically 'US' for most records. Used for international attendee identification. |
| `county` | STRING | From person_location table. Family-level. County name. Rock > Person > Address. |
| `current_row` | BOOL | Boolean flag indicating the most recent record for each person. Person level. TRUE for the latest record, FALSE for historical records. |
| `days_in_sower_interval` | INT64 | Calculated from sower_start_date and sower_end_date. Interval level. The total number of calendar days the person maintained an active recurring gift to YouVersion during this continuous interval, inclusive of both start and end dates. Calculated as DATE_DIFF(sower_end_date, sower_start_date, DAY) + 1. Integer value >= 1. Used to measure recurring donor retention length and identify long-term vs short-term recurring givers. |
| `email` | STRING | From Rock RMS Person.email. Person level. The person's primary email address as stored in Rock RMS. May be NULL if no email on file. Used for communication and matching. |
| `full_name` | STRING | From Rock RMS Person. Person level. The person's full name constructed as nickname (or first name if no nickname) plus last name. Used for human-readable identification in reports. |
| `home_phone_number` | STRING | The main contact phone number for the individual. Returns NULL if phone number is empty string. |
| `location_type` | STRING | From dimension_giving_persons locations array. Person level. The type of location (e.g., Home, Work, Previous). |
| `mobile_phone_number` | STRING | The main contact phone number for the individual. Returns NULL if phone number is empty string. |
| `percent_recurring_transactions` | FLOAT64 | Calculated metric. Interval level. The percentage of this person's gifts that came from their recurring schedule versus one-time gifts during this interval. Range: 0.00 to 1.00 (e.g., 0.75 = 75% recurring). NULL if no transactions. |
| `postal_code` | STRING | From Rock RMS Location. Entity level. The postal/ZIP code for the entity address. |
| `record_type` | STRING | Person level. Indicates whether the record represents an individual person or a business entity in Rock RMS. |
| `recurring_transactions_count` | INT64 | Calculated from conditional count. Interval level. The number of gifts that were part of a recurring schedule during this interval. Subset of total_transactions where is_recurring = TRUE. |
| `rms_family_id` | INT64 | The primary unique identifier for a family or household in Rock RMS. |
| `rms_person_id` | INT64 | The unique Rock RMS identifier for the individual. Person-level. Links to Person.Id in Rock RMS. Used to join all person-related data across the system. Rock > Person Profile. |
| `sower_end_date` | DATE | From recurring_sowers model. Interval level. The last date when the person had an active recurring gift to YouVersion during this continuous interval. NULL if still active. Format: DATE (YYYY-MM-DD). |
| `sower_start_date` | DATE | From recurring_sowers model. Interval level. The first date when the person had an active recurring gift to YouVersion during this continuous interval. Format: DATE (YYYY-MM-DD). |
| `state` | STRING | From Rock RMS Location. Entity level. The state abbreviation where the entity is located. |
| `street_1` | STRING | From Rock RMS Location.Street1. Entity level. The primary street address line for the entity physical location. |
| `street_2` | STRING | From Rock RMS Location.Street2. Entity level. The secondary address line (suite, building, etc). Returns empty string if NULL. |
| `total_given_amount` | BIGNUMERIC | Calculated from giving aggregation. Interval level. The total dollar amount given by this person interval. Includes both recurring and one-time gifts. Decimal value in USD. |
| `total_giving_count` | INT64 | The total number of financial transactions for the person. Defaults to 0 if null. |
| `total_recurring_given_amount` | BIGNUMERIC | Calculated from giving aggregation. Interval level. The total dollar amount given by this person interval. Includes only recurring. Decimal value in USD. |
| `work_phone_number` | STRING | The main contact phone number for the individual. Returns NULL if phone number is empty string. |
| `youversion_user_id` | INT64 | The current unique identifier for an individual person or business in Rock RMS, despite merges. Cast as STRING for external system compatibility. |

## Column Details

### `city`

- **Type**: STRING
- **Description**: From Rock RMS Location. Entity level. The city where the entity is located.

### `country`

- **Type**: STRING
- **Description**: From location.country. Person level. The country of the person's home address. Typically 'US' for most records. Used for international attendee identification.

### `county`

- **Type**: STRING
- **Description**: From person_location table. Family-level. County name. Rock > Person > Address.

### `current_row`

- **Type**: BOOL
- **Description**: Boolean flag indicating the most recent record for each person. Person level. TRUE for the latest record, FALSE for historical records.

### `days_in_sower_interval`

- **Type**: INT64
- **Description**: Calculated from sower_start_date and sower_end_date. Interval level. The total number of calendar days the person maintained an active recurring gift to YouVersion during this continuous interval, inclusive of both start and end dates. Calculated as DATE_DIFF(sower_end_date, sower_start_date, DAY) + 1. Integer value >= 1. Used to measure recurring donor retention length and identify long-term vs short-term recurring givers.

### `email`

- **Type**: STRING
- **Description**: From Rock RMS Person.email. Person level. The person's primary email address as stored in Rock RMS. May be NULL if no email on file. Used for communication and matching.

### `full_name`

- **Type**: STRING
- **Description**: From Rock RMS Person. Person level. The person's full name constructed as nickname (or first name if no nickname) plus last name. Used for human-readable identification in reports.

### `home_phone_number`

- **Type**: STRING
- **Description**: The main contact phone number for the individual. Returns NULL if phone number is empty string.

### `location_type`

- **Type**: STRING
- **Description**: From dimension_giving_persons locations array. Person level. The type of location (e.g., Home, Work, Previous).

### `mobile_phone_number`

- **Type**: STRING
- **Description**: The main contact phone number for the individual. Returns NULL if phone number is empty string.

### `percent_recurring_transactions`

- **Type**: FLOAT64
- **Description**: Calculated metric. Interval level. The percentage of this person's gifts that came from their recurring schedule versus one-time gifts during this interval. Range: 0.00 to 1.00 (e.g., 0.75 = 75% recurring). NULL if no transactions.

### `postal_code`

- **Type**: STRING
- **Description**: From Rock RMS Location. Entity level. The postal/ZIP code for the entity address.

### `record_type`

- **Type**: STRING
- **Description**: Person level. Indicates whether the record represents an individual person or a business entity in Rock RMS.

### `recurring_transactions_count`

- **Type**: INT64
- **Description**: Calculated from conditional count. Interval level. The number of gifts that were part of a recurring schedule during this interval. Subset of total_transactions where is_recurring = TRUE.

### `rms_family_id`

- **Type**: INT64
- **Description**: The primary unique identifier for a family or household in Rock RMS.

### `rms_person_id`

- **Type**: INT64
- **Description**: The unique Rock RMS identifier for the individual. Person-level. Links to Person.Id in Rock RMS. Used to join all person-related data across the system. Rock > Person Profile.

### `sower_end_date`

- **Type**: DATE
- **Description**: From recurring_sowers model. Interval level. The last date when the person had an active recurring gift to YouVersion during this continuous interval. NULL if still active. Format: DATE (YYYY-MM-DD).

### `sower_start_date`

- **Type**: DATE
- **Description**: From recurring_sowers model. Interval level. The first date when the person had an active recurring gift to YouVersion during this continuous interval. Format: DATE (YYYY-MM-DD).

### `state`

- **Type**: STRING
- **Description**: From Rock RMS Location. Entity level. The state abbreviation where the entity is located.

### `street_1`

- **Type**: STRING
- **Description**: From Rock RMS Location.Street1. Entity level. The primary street address line for the entity physical location.

### `street_2`

- **Type**: STRING
- **Description**: From Rock RMS Location.Street2. Entity level. The secondary address line (suite, building, etc). Returns empty string if NULL.

### `total_given_amount`

- **Type**: BIGNUMERIC
- **Description**: Calculated from giving aggregation. Interval level. The total dollar amount given by this person interval. Includes both recurring and one-time gifts. Decimal value in USD.

### `total_giving_count`

- **Type**: INT64
- **Description**: The total number of financial transactions for the person. Defaults to 0 if null.

### `total_recurring_given_amount`

- **Type**: BIGNUMERIC
- **Description**: Calculated from giving aggregation. Interval level. The total dollar amount given by this person interval. Includes only recurring. Decimal value in USD.

### `work_phone_number`

- **Type**: STRING
- **Description**: The main contact phone number for the individual. Returns NULL if phone number is empty string.

### `youversion_user_id`

- **Type**: INT64
- **Description**: The current unique identifier for an individual person or business in Rock RMS, despite merges. Cast as STRING for external system compatibility.

