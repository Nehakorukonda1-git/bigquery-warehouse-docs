# dimension_household

## Columns

Total Columns: 90

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| `address_1` | STRING | From Rock RMS Location.Street1. Entity level. The primary street address line for the entity physical location. |
| `address_2` | STRING | From Rock RMS Location.Street2. Entity level. The secondary address line (suite, building, etc). Returns empty string if NULL. |
| `adults` | STRING | From Rock RMS Person table. Family/household level. Comma-separated list of full names of all adult members in the family. Calculated using STRING_AGG of full_name where is_adult = TRUE. Example values: 'John Smith, Jane Smith' or 'Robert Johnson'. |
| `banned_giver_timestamp` | TIMESTAMP | The timestamp when the person was marked as a banned giver. Person level. CreatedDateTime of the BannedGiver attribute value. Rock > Profile > Person Profile > Attributes > Banned Giver > Created Date. |
| `campus` | STRING | From Data Warehouse, using Rock person data. Person level. The main, home, primary, or preferred campus of the person. This is the best source for identifing which campus a person belongs to. Rock > Profile > Main Contact Details. |
| `children` | STRING | From Rock RMS Person table. Family/household level. Comma-separated list of full names of all children in the family. Calculated using STRING_AGG of full_name where is_adult = FALSE. Example values: 'Sarah Smith, Tommy Smith' or 'Emily Johnson'. |
| `city` | STRING | From Rock RMS Location. Entity level. The city where the entity is located. |
| `country` | STRING | From location.country. Person level. The country of the person's home address. Typically 'US' for most records. Used for international attendee identification. |
| `county` | STRING | From person_location table. Family-level. County name. Rock > Person > Address. |
| `created_timestamp` | TIMESTAMP | When the event or entity was initially created. Event or entity level. Format: YYYY-MM-DD HH:MM:SS. |
| `family_name` | STRING | From household_staging table. Household level. The last name or designated family name for the household. Rock > People > Family. |
| `first_checkin_campus` | STRING | From Rock RMS attendance data. Family/household level. The campus short code (e.g., EDM, OKC, STW) where the household had their first check-in. |
| `first_checkin_timestamp` | TIMESTAMP | From Rock RMS attendance data. Family/household level. The earliest attendance_start_timestamp recorded for any member of the household across all ministries and campuses. Represents the family's first engagement with Life.Church. |
| `first_financial_transaction_campus` | INT64 | The campus short code (e.g., 'EDM', 'STW') where the person made their first financial contribution. Person level. Retrieved from the campus associated with the first transaction. Rock > Profile > Transactions. |
| `first_financial_transaction_timestamp` | TIMESTAMP | The timestamp of the person's first ever financial contribution to Life.Church. Person level. Calculated as the earliest transaction from fact_giving where amount >= 0 and is_successful = TRUE. Rock > Profile > Transactions. |
| `first_host_team_checkin_campus` | STRING | From Rock RMS attendance data. Family/household level. The campus short code where the household first checked into Host Team. |
| `first_host_team_checkin_timestamp` | TIMESTAMP | From Rock RMS attendance data. Family/household level. The earliest attendance_start_timestamp where parent_group_name = 'Host Team' for any member serving in the household. Marks when family first served on Host Team. |
| `first_household_weekend_attendance_campus` | STRING | From Data Warehouse, using Rock attendance data. Household level. The campus where the family first checked in to attend (not serve) on a weekend. Rock > History > Attendance History. |
| `first_household_weekend_attendance_timestamp` | TIMESTAMP | From Data Warehouse, using Rock attendance data. Household level. The date the family first checked in to attend (not serve) on a weekend. Rock > History > Attendance History. |
| `first_household_weekend_physical_attendance_campus` | STRING | From Data Warehouse, using Rock attendance data. Household level. The campus where the family first checked in to attend (not serve) physically (not LCO) on a weekend. Rock > History > Attendance History. |
| `first_household_weekend_physical_attendance_timestamp` | TIMESTAMP | From Data Warehouse, using Rock attendance data. Household level. The date the family first checked in to attend (not serve) physicaly (not LCO) on a weekend. Rock > History > Attendance History. |
| `first_lifekids_checkin_campus` | STRING | From Rock RMS attendance data. Family/household level. The campus short code where the household first checked into LifeKids. |
| `first_lifekids_checkin_timestamp` | TIMESTAMP | From Rock RMS attendance data. Family/household level. The earliest attendance_start_timestamp where parent_group_name = 'LifeKids' for any child in the household. Marks when family first engaged with children's ministry. |
| `first_operations_checkin_campus` | STRING | From Rock RMS attendance data. Family/household level. The campus short code where the household first checked into Operations. |
| `first_operations_checkin_timestamp` | TIMESTAMP | From Rock RMS attendance data. Family/household level. The earliest attendance_start_timestamp where parent_group_name = 'Operations' for any member serving in the household. Marks when family first served on Operations. |
| `first_switch_checkin_campus` | STRING | From Rock RMS attendance data. Family/household level. The campus short code where the household first checked into Switch. |
| `first_switch_checkin_timestamp` | TIMESTAMP | From Rock RMS attendance data. Family/household level. The earliest attendance_start_timestamp where parent_group_name = 'Switch' for any youth in the household. Marks when family first engaged with youth ministry. |
| `first_three_month_tithe_challenge_requested` | BOOL | Boolean indicating whether the person has ever participated in the three-month tithe challenge. Person level. TRUE if three_month_timestamp exists, FALSE otherwise. Rock > Profile > Attributes > Three Month Tithe Challenge. |
| `first_worship_checkin_campus` | STRING | From Rock RMS attendance data. Family/household level. The campus short code where the household first checked into Worship. |
| `first_worship_checkin_timestamp` | TIMESTAMP | From Rock RMS attendance data. Family/household level. The earliest attendance_start_timestamp where parent_group_name = 'Worship' for any member serving in the household. Marks when family first served on Worship. |
| `group_salutation` | STRING | From Rock RMS Group table. Family/household level. The salutation text used for addressing the family group in communications. This is typically used for formal mailings or correspondence. |
| `is_banned_giver` | STRING | String value ('True') indicating the person has been flagged as a banned giver, typically due to fraudulent activity or chargebacks. Person level. From Rock person attribute BannedGiver. Rock > Profile > Person Profile > Attributes > Banned Giver. |
| `is_legacy_team_prospect` | BOOL | From household_staging table calculated using financial transactions. Household level. Boolean flag indicating whether any non-staff member in this household has contributed at least 20,000 within the past 12 months, making them a prospect for the Legacy Team giving program. This flag is applied to all family members since giving is viewed at the household level - if one family member qualifies based on their giving, the entire household is marked as a prospect. Excludes households where any member is already a Legacy Team member (is_legacy_team_member = TRUE). Rock > Contributions. |
| `is_removed_from_mailing_list` | BOOL | From Rock RMS AttributeValue table. Family/household level. Boolean flag indicating if the family has requested to be removed from physical mailings. TRUE when AttributeId = RemovedFromMailingList constant and Value = 'True'. Rock > People > Families > Attributes > Removed From Mailing List. |
| `is_statement_suppressed` | STRING | String value ('True') indicating the person has opted out of receiving printed contribution statements. Person level. From Rock person attribute SuppressSendingContributionStatements. Rock > Profile > Person Profile > Attributes > Suppress Sending Contribution Statements. |
| `last_checkin_campus` | STRING | From Rock RMS attendance data. Family/household level. The campus short code where the household had their most recent check-in. |
| `last_checkin_timestamp` | TIMESTAMP | From Rock RMS attendance data. Family/household level. The most recent attendance_start_timestamp recorded for any member of the household across all ministries and campuses. Indicates current engagement level. |
| `last_financial_transaction_campus` | INT64 | The campus short code where the person made their most recent financial contribution. Person level. Retrieved from the campus associated with the last transaction. Rock > Profile > Transactions. |
| `last_financial_transaction_timestamp` | TIMESTAMP | The timestamp of the person's most recent financial contribution to Life.Church. Person level. Calculated as the latest transaction from fact_giving where amount >= 0 and is_successful = TRUE. Rock > Profile > Transactions. |
| `last_host_team_checkin_campus` | STRING | From Rock RMS attendance data. Family/household level. The campus short code where the household most recently checked into Host Team. |
| `last_host_team_checkin_timestamp` | TIMESTAMP | From Rock RMS attendance data. Family/household level. The most recent attendance_start_timestamp where parent_group_name = 'Host Team' for any member serving in the household. Shows current Host Team engagement. . |
| `last_household_attendance_campus_short_code_crosstown` | STRING | From Rock RMS attendance data. Family/household level. Campus short code for most recent 'Crosstown' attendance. |
| `last_household_attendance_campus_short_code_in_the_jungle` | STRING | From Rock RMS attendance data. Family/household level. Campus short code for most recent 'In The Jungle' attendance. |
| `last_household_attendance_campus_short_code_konnect` | STRING | From Rock RMS attendance data. Family/household level. Campus short code for most recent 'Konnect' attendance. |
| `last_household_attendance_campus_short_code_let_there_be_light` | STRING | From Rock RMS attendance data. Family/household level. Campus short code for most recent 'Let There Be Light' attendance. |
| `last_household_attendance_campus_short_code_starry_night` | STRING | From Rock RMS attendance data. Family/household level. Campus short code for most recent 'Starry Night' attendance. |
| `last_household_attendance_campus_short_code_switch_student` | STRING | From Rock RMS attendance data. Family/household level. Campus short code for most recent 'Switch Student' attendance. . |
| `last_household_attendance_campus_short_code_the_ark` | STRING | From Rock RMS attendance data. Family/household level. Campus short code for most recent 'The Ark' attendance. |
| `last_household_attendance_campus_short_code_the_garden` | STRING | From Rock RMS attendance data. Family/household level. Campus short code for most recent 'The Garden' attendance. |
| `last_household_attendance_campus_short_code_the_loop` | STRING | From Rock RMS attendance data. Family/household level. Campus short code for most recent 'The Loop' attendance. . |
| `last_household_attendance_campus_short_code_under_the_sea` | STRING | From Rock RMS attendance data. Family/household level. Campus short code for most recent 'Under The Sea' attendance. |
| `last_household_attendance_timestamp_crosstown` | TIMESTAMP | From Rock RMS attendance data. Family/household level. Most recent attendance_start_timestamp for 'Crosstown' LifeKids room. Elementary age group check-in. NULL if never attended. |
| `last_household_attendance_timestamp_in_the_jungle` | TIMESTAMP | From Rock RMS attendance data. Family/household level. Most recent attendance_start_timestamp for 'In The Jungle' LifeKids room. Preschool age group check-in. NULL if never attended. |
| `last_household_attendance_timestamp_konnect` | TIMESTAMP | From Rock RMS attendance data. Family/household level. Most recent attendance_start_timestamp for 'Konnect' LifeKids room. 4th-5th grade age group check-in. NULL if never attended. |
| `last_household_attendance_timestamp_let_there_be_light` | TIMESTAMP | From Rock RMS attendance data. Family/household level. Most recent attendance_start_timestamp for 'Let There Be Light' LifeKids room. Elementary age group check-in. NULL if never attended. |
| `last_household_attendance_timestamp_starry_night` | TIMESTAMP | From Rock RMS attendance data. Family/household level. Most recent attendance_start_timestamp for 'Starry Night' LifeKids room. Elementary age group check-in. NULL if never attended. |
| `last_household_attendance_timestamp_switch_student` | TIMESTAMP | From Rock RMS attendance data. Family/household level. Most recent attendance_start_timestamp for 'Switch Student'. NULL if never attended. |
| `last_household_attendance_timestamp_the_ark` | TIMESTAMP | From Rock RMS attendance data. Family/household level. Most recent attendance_start_timestamp for 'The Ark' LifeKids room. Special needs ministry check-in. NULL if never attended. |
| `last_household_attendance_timestamp_the_garden` | TIMESTAMP | From Rock RMS attendance data. Family/household level. Most recent attendance_start_timestamp for 'The Garden' LifeKids room. Nursery age group check-in. NULL if never attended. |
| `last_household_attendance_timestamp_the_loop` | TIMESTAMP | From Rock RMS attendance data. Family/household level. Most recent attendance_start_timestamp for 'The Loop' LifeKids room. Preschool age group check-in. NULL if never attended. |
| `last_household_attendance_timestamp_under_the_sea` | TIMESTAMP | From Rock RMS attendance data. Family/household level. Most recent attendance_start_timestamp for 'Under The Sea' LifeKids room. Preschool age group check-in. NULL if never attended. |
| `last_household_weekend_attendance_campus` | STRING | From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in to attend (not serve) on a weekend. Rock > History > Attendance History. |
| `last_household_weekend_attendance_timestamp` | TIMESTAMP | From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in to attend (not serve) on a weekend. Rock > History > Attendance History. |
| `last_household_weekend_physical_attendance_campus` | STRING | From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in to attend (not serve) physically (not LCO) on a weekend. Rock > History > Attendance History. |
| `last_household_weekend_physical_attendance_timestamp` | TIMESTAMP | From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in to attend (not serve) physicaly (not LCO) on a weekend. Rock > History > Attendance History. |
| `last_lifekids_checkin_campus` | STRING | From Rock RMS attendance data. Family/household level. The campus short code where the household most recently checked into LifeKids. |
| `last_lifekids_checkin_timestamp` | TIMESTAMP | From Rock RMS attendance data. Family/household level. The most recent attendance_start_timestamp where parent_group_name = 'LifeKids' for any child in the household. Shows current LifeKids engagement. |
| `last_operations_checkin_campus` | STRING | From Rock RMS attendance data. Family/household level. The campus short code where the household most recently checked into Operations. |
| `last_operations_checkin_timestamp` | TIMESTAMP | From Rock RMS attendance data. Family/household level. The most recent attendance_start_timestamp where parent_group_name = 'Operations' for any member serving in the household. Shows current Operations engagement. |
| `last_scheduled_financial_transaction_timestamp` | TIMESTAMP | The timestamp of the most recent transaction that was part of a scheduled/recurring gift. Person level. Latest transaction timestamp where financial_transaction_schedule_id is not null. Rock > Profile > Scheduled Transactions > Transaction History. |
| `last_switch_checkin_campus` | STRING | From Rock RMS attendance data. Family/household level. The campus short code where the household most recently checked into Switch. |
| `last_switch_checkin_timestamp` | TIMESTAMP | From Rock RMS attendance data. Family/household level. The most recent attendance_start_timestamp where parent_group_name = 'Switch' for any youth in the household. Shows current Switch engagement. |
| `last_worship_checkin_campus` | STRING | From Rock RMS attendance data. Family/household level. The campus short code where the household most recently checked into Worship. |
| `last_worship_checkin_timestamp` | TIMESTAMP | From Rock RMS attendance data. Family/household level. The most recent attendance_start_timestamp where parent_group_name = 'Worship' for any member serving in the household. Shows current Worship engagement. |
| `latitude` | FLOAT64 | Extracted from Rock RMS Location.GeoPoint using custom function. Entity level. The latitude coordinate of the entity location in decimal degrees. Used for mapping and distance calculations. |
| `list_of_given_funds` | STRING | List of funds the person has given to. |
| `longitude` | FLOAT64 | Extracted from Rock RMS Location.GeoPoint using custom function. Entity level. The longitude coordinate of the entity location in decimal degrees. Used for mapping and distance calculations. |
| `number_of_adults` | INT64 | From Rock RMS Person table. Family/household level. Count of all people in the family where is_adult = TRUE. Calculated by summing adults (age 18+) within each rms_family_id. |
| `number_of_children` | INT64 | From Rock RMS Person table. Family/household level. Count of all people in the family where is_adult = FALSE. Calculated by summing children (under 18) within each rms_family_id. |
| `postal_code` | STRING | From Rock RMS Location.postalcode. Person level. The ZIP code of the person's home address. Used for geographic analysis and drive time calculations. |
| `primary_giving_subtype` | STRING | The specific payment method subtype (e.g., 'Visa', 'Mastercard') used in the person's most recent contribution. Person level. From the latest transaction's transaction_subtype, excluding 'unknown' values. Rock > Profile > Transactions. |
| `primary_giving_type` | STRING | The transaction type (e.g., 'Cash', 'Check', 'ACH', 'Credit Card') used in the person's most recent contribution. Person level. From the latest transaction's transaction_type. Rock > Profile > Transactions. |
| `removed_from_mailing_list_timestamp` | TIMESTAMP | From Rock RMS AttributeValue table. Family/household level. The timestamp when the family was marked as removed from mailing list. Captured from CreatedDateTime when the attribute was set. Note: The config shows 'removed_from_mailing_list_times' but the SQL uses 'removed_from_mailing_list_timestamp'. |
| `rms_family_id` | INT64 | The primary unique identifier for a family or household in Rock RMS. |
| `scheduled_transaction_count` | INT64 | The number of gifts the person has given using a recurring schedule. |
| `state_province` | STRING | From person_location table. Family-level. Full state/province name. Rock > Person > Address. |
| `statement_suppressed_timestamp` | TIMESTAMP | The timestamp when the person opted out of printed contribution statements. Person level. CreatedDateTime of the statement suppression attribute. Rock > Profile > Attributes > Suppress Sending Contribution Statements > Created Date. |
| `three_month_campus` | STRING | The campus short code where the person committed to the three-month tithe challenge. Person level. From the campus attribute in the Three Month Tithe Challenge matrix. Rock > Profile > Attributes > Three Month Tithe Challenge. |
| `three_month_timestamp` | TIMESTAMP | The start date when the person began their three-month tithe challenge commitment. Person level. Retrieved from Rock attribute matrix for Three Month Tithe Challenge. Format: YYYY-MM-DD HH:MM:SS. Rock > Profile > Person > Attributes > Three Month Tithe Challenge. |
| `total_giving_count` | INT64 | The total number of financial transactions for the person. Defaults to 0 if null. |

## Column Details

### `address_1`

- **Type**: STRING
- **Description**: From Rock RMS Location.Street1. Entity level. The primary street address line for the entity physical location.

### `address_2`

- **Type**: STRING
- **Description**: From Rock RMS Location.Street2. Entity level. The secondary address line (suite, building, etc). Returns empty string if NULL.

### `adults`

- **Type**: STRING
- **Description**: From Rock RMS Person table. Family/household level. Comma-separated list of full names of all adult members in the family. Calculated using STRING_AGG of full_name where is_adult = TRUE. Example values: 'John Smith, Jane Smith' or 'Robert Johnson'.

### `banned_giver_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp when the person was marked as a banned giver. Person level. CreatedDateTime of the BannedGiver attribute value. Rock > Profile > Person Profile > Attributes > Banned Giver > Created Date.

### `campus`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock person data. Person level. The main, home, primary, or preferred campus of the person. This is the best source for identifing which campus a person belongs to. Rock > Profile > Main Contact Details.

### `children`

- **Type**: STRING
- **Description**: From Rock RMS Person table. Family/household level. Comma-separated list of full names of all children in the family. Calculated using STRING_AGG of full_name where is_adult = FALSE. Example values: 'Sarah Smith, Tommy Smith' or 'Emily Johnson'.

### `city`

- **Type**: STRING
- **Description**: From Rock RMS Location. Entity level. The city where the entity is located.

### `country`

- **Type**: STRING
- **Description**: From location.country. Person level. The country of the person's home address. Typically 'US' for most records. Used for international attendee identification.

### `county`

- **Type**: STRING
- **Description**: From person_location table. Family-level. County name. Rock > Person > Address.

### `created_timestamp`

- **Type**: TIMESTAMP
- **Description**: When the event or entity was initially created. Event or entity level. Format: YYYY-MM-DD HH:MM:SS.

### `family_name`

- **Type**: STRING
- **Description**: From household_staging table. Household level. The last name or designated family name for the household. Rock > People > Family.

### `first_checkin_campus`

- **Type**: STRING
- **Description**: From Rock RMS attendance data. Family/household level. The campus short code (e.g., EDM, OKC, STW) where the household had their first check-in.

### `first_checkin_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS attendance data. Family/household level. The earliest attendance_start_timestamp recorded for any member of the household across all ministries and campuses. Represents the family's first engagement with Life.Church.

### `first_financial_transaction_campus`

- **Type**: INT64
- **Description**: The campus short code (e.g., 'EDM', 'STW') where the person made their first financial contribution. Person level. Retrieved from the campus associated with the first transaction. Rock > Profile > Transactions.

### `first_financial_transaction_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp of the person's first ever financial contribution to Life.Church. Person level. Calculated as the earliest transaction from fact_giving where amount >= 0 and is_successful = TRUE. Rock > Profile > Transactions.

### `first_host_team_checkin_campus`

- **Type**: STRING
- **Description**: From Rock RMS attendance data. Family/household level. The campus short code where the household first checked into Host Team.

### `first_host_team_checkin_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS attendance data. Family/household level. The earliest attendance_start_timestamp where parent_group_name = 'Host Team' for any member serving in the household. Marks when family first served on Host Team.

### `first_household_weekend_attendance_campus`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The campus where the family first checked in to attend (not serve) on a weekend. Rock > History > Attendance History.

### `first_household_weekend_attendance_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The date the family first checked in to attend (not serve) on a weekend. Rock > History > Attendance History.

### `first_household_weekend_physical_attendance_campus`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The campus where the family first checked in to attend (not serve) physically (not LCO) on a weekend. Rock > History > Attendance History.

### `first_household_weekend_physical_attendance_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The date the family first checked in to attend (not serve) physicaly (not LCO) on a weekend. Rock > History > Attendance History.

### `first_lifekids_checkin_campus`

- **Type**: STRING
- **Description**: From Rock RMS attendance data. Family/household level. The campus short code where the household first checked into LifeKids.

### `first_lifekids_checkin_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS attendance data. Family/household level. The earliest attendance_start_timestamp where parent_group_name = 'LifeKids' for any child in the household. Marks when family first engaged with children's ministry.

### `first_operations_checkin_campus`

- **Type**: STRING
- **Description**: From Rock RMS attendance data. Family/household level. The campus short code where the household first checked into Operations.

### `first_operations_checkin_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS attendance data. Family/household level. The earliest attendance_start_timestamp where parent_group_name = 'Operations' for any member serving in the household. Marks when family first served on Operations.

### `first_switch_checkin_campus`

- **Type**: STRING
- **Description**: From Rock RMS attendance data. Family/household level. The campus short code where the household first checked into Switch.

### `first_switch_checkin_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS attendance data. Family/household level. The earliest attendance_start_timestamp where parent_group_name = 'Switch' for any youth in the household. Marks when family first engaged with youth ministry.

### `first_three_month_tithe_challenge_requested`

- **Type**: BOOL
- **Description**: Boolean indicating whether the person has ever participated in the three-month tithe challenge. Person level. TRUE if three_month_timestamp exists, FALSE otherwise. Rock > Profile > Attributes > Three Month Tithe Challenge.

### `first_worship_checkin_campus`

- **Type**: STRING
- **Description**: From Rock RMS attendance data. Family/household level. The campus short code where the household first checked into Worship.

### `first_worship_checkin_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS attendance data. Family/household level. The earliest attendance_start_timestamp where parent_group_name = 'Worship' for any member serving in the household. Marks when family first served on Worship.

### `group_salutation`

- **Type**: STRING
- **Description**: From Rock RMS Group table. Family/household level. The salutation text used for addressing the family group in communications. This is typically used for formal mailings or correspondence.

### `is_banned_giver`

- **Type**: STRING
- **Description**: String value ('True') indicating the person has been flagged as a banned giver, typically due to fraudulent activity or chargebacks. Person level. From Rock person attribute BannedGiver. Rock > Profile > Person Profile > Attributes > Banned Giver.

### `is_legacy_team_prospect`

- **Type**: BOOL
- **Description**: From household_staging table calculated using financial transactions. Household level. Boolean flag indicating whether any non-staff member in this household has contributed at least 20,000 within the past 12 months, making them a prospect for the Legacy Team giving program. This flag is applied to all family members since giving is viewed at the household level - if one family member qualifies based on their giving, the entire household is marked as a prospect. Excludes households where any member is already a Legacy Team member (is_legacy_team_member = TRUE). Rock > Contributions.

### `is_removed_from_mailing_list`

- **Type**: BOOL
- **Description**: From Rock RMS AttributeValue table. Family/household level. Boolean flag indicating if the family has requested to be removed from physical mailings. TRUE when AttributeId = RemovedFromMailingList constant and Value = 'True'. Rock > People > Families > Attributes > Removed From Mailing List.

### `is_statement_suppressed`

- **Type**: STRING
- **Description**: String value ('True') indicating the person has opted out of receiving printed contribution statements. Person level. From Rock person attribute SuppressSendingContributionStatements. Rock > Profile > Person Profile > Attributes > Suppress Sending Contribution Statements.

### `last_checkin_campus`

- **Type**: STRING
- **Description**: From Rock RMS attendance data. Family/household level. The campus short code where the household had their most recent check-in.

### `last_checkin_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS attendance data. Family/household level. The most recent attendance_start_timestamp recorded for any member of the household across all ministries and campuses. Indicates current engagement level.

### `last_financial_transaction_campus`

- **Type**: INT64
- **Description**: The campus short code where the person made their most recent financial contribution. Person level. Retrieved from the campus associated with the last transaction. Rock > Profile > Transactions.

### `last_financial_transaction_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp of the person's most recent financial contribution to Life.Church. Person level. Calculated as the latest transaction from fact_giving where amount >= 0 and is_successful = TRUE. Rock > Profile > Transactions.

### `last_host_team_checkin_campus`

- **Type**: STRING
- **Description**: From Rock RMS attendance data. Family/household level. The campus short code where the household most recently checked into Host Team.

### `last_host_team_checkin_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS attendance data. Family/household level. The most recent attendance_start_timestamp where parent_group_name = 'Host Team' for any member serving in the household. Shows current Host Team engagement. .

### `last_household_attendance_campus_short_code_crosstown`

- **Type**: STRING
- **Description**: From Rock RMS attendance data. Family/household level. Campus short code for most recent 'Crosstown' attendance.

### `last_household_attendance_campus_short_code_in_the_jungle`

- **Type**: STRING
- **Description**: From Rock RMS attendance data. Family/household level. Campus short code for most recent 'In The Jungle' attendance.

### `last_household_attendance_campus_short_code_konnect`

- **Type**: STRING
- **Description**: From Rock RMS attendance data. Family/household level. Campus short code for most recent 'Konnect' attendance.

### `last_household_attendance_campus_short_code_let_there_be_light`

- **Type**: STRING
- **Description**: From Rock RMS attendance data. Family/household level. Campus short code for most recent 'Let There Be Light' attendance.

### `last_household_attendance_campus_short_code_starry_night`

- **Type**: STRING
- **Description**: From Rock RMS attendance data. Family/household level. Campus short code for most recent 'Starry Night' attendance.

### `last_household_attendance_campus_short_code_switch_student`

- **Type**: STRING
- **Description**: From Rock RMS attendance data. Family/household level. Campus short code for most recent 'Switch Student' attendance. .

### `last_household_attendance_campus_short_code_the_ark`

- **Type**: STRING
- **Description**: From Rock RMS attendance data. Family/household level. Campus short code for most recent 'The Ark' attendance.

### `last_household_attendance_campus_short_code_the_garden`

- **Type**: STRING
- **Description**: From Rock RMS attendance data. Family/household level. Campus short code for most recent 'The Garden' attendance.

### `last_household_attendance_campus_short_code_the_loop`

- **Type**: STRING
- **Description**: From Rock RMS attendance data. Family/household level. Campus short code for most recent 'The Loop' attendance. .

### `last_household_attendance_campus_short_code_under_the_sea`

- **Type**: STRING
- **Description**: From Rock RMS attendance data. Family/household level. Campus short code for most recent 'Under The Sea' attendance.

### `last_household_attendance_timestamp_crosstown`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS attendance data. Family/household level. Most recent attendance_start_timestamp for 'Crosstown' LifeKids room. Elementary age group check-in. NULL if never attended.

### `last_household_attendance_timestamp_in_the_jungle`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS attendance data. Family/household level. Most recent attendance_start_timestamp for 'In The Jungle' LifeKids room. Preschool age group check-in. NULL if never attended.

### `last_household_attendance_timestamp_konnect`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS attendance data. Family/household level. Most recent attendance_start_timestamp for 'Konnect' LifeKids room. 4th-5th grade age group check-in. NULL if never attended.

### `last_household_attendance_timestamp_let_there_be_light`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS attendance data. Family/household level. Most recent attendance_start_timestamp for 'Let There Be Light' LifeKids room. Elementary age group check-in. NULL if never attended.

### `last_household_attendance_timestamp_starry_night`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS attendance data. Family/household level. Most recent attendance_start_timestamp for 'Starry Night' LifeKids room. Elementary age group check-in. NULL if never attended.

### `last_household_attendance_timestamp_switch_student`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS attendance data. Family/household level. Most recent attendance_start_timestamp for 'Switch Student'. NULL if never attended.

### `last_household_attendance_timestamp_the_ark`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS attendance data. Family/household level. Most recent attendance_start_timestamp for 'The Ark' LifeKids room. Special needs ministry check-in. NULL if never attended.

### `last_household_attendance_timestamp_the_garden`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS attendance data. Family/household level. Most recent attendance_start_timestamp for 'The Garden' LifeKids room. Nursery age group check-in. NULL if never attended.

### `last_household_attendance_timestamp_the_loop`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS attendance data. Family/household level. Most recent attendance_start_timestamp for 'The Loop' LifeKids room. Preschool age group check-in. NULL if never attended.

### `last_household_attendance_timestamp_under_the_sea`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS attendance data. Family/household level. Most recent attendance_start_timestamp for 'Under The Sea' LifeKids room. Preschool age group check-in. NULL if never attended.

### `last_household_weekend_attendance_campus`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in to attend (not serve) on a weekend. Rock > History > Attendance History.

### `last_household_weekend_attendance_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in to attend (not serve) on a weekend. Rock > History > Attendance History.

### `last_household_weekend_physical_attendance_campus`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in to attend (not serve) physically (not LCO) on a weekend. Rock > History > Attendance History.

### `last_household_weekend_physical_attendance_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in to attend (not serve) physicaly (not LCO) on a weekend. Rock > History > Attendance History.

### `last_lifekids_checkin_campus`

- **Type**: STRING
- **Description**: From Rock RMS attendance data. Family/household level. The campus short code where the household most recently checked into LifeKids.

### `last_lifekids_checkin_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS attendance data. Family/household level. The most recent attendance_start_timestamp where parent_group_name = 'LifeKids' for any child in the household. Shows current LifeKids engagement.

### `last_operations_checkin_campus`

- **Type**: STRING
- **Description**: From Rock RMS attendance data. Family/household level. The campus short code where the household most recently checked into Operations.

### `last_operations_checkin_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS attendance data. Family/household level. The most recent attendance_start_timestamp where parent_group_name = 'Operations' for any member serving in the household. Shows current Operations engagement.

### `last_scheduled_financial_transaction_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp of the most recent transaction that was part of a scheduled/recurring gift. Person level. Latest transaction timestamp where financial_transaction_schedule_id is not null. Rock > Profile > Scheduled Transactions > Transaction History.

### `last_switch_checkin_campus`

- **Type**: STRING
- **Description**: From Rock RMS attendance data. Family/household level. The campus short code where the household most recently checked into Switch.

### `last_switch_checkin_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS attendance data. Family/household level. The most recent attendance_start_timestamp where parent_group_name = 'Switch' for any youth in the household. Shows current Switch engagement.

### `last_worship_checkin_campus`

- **Type**: STRING
- **Description**: From Rock RMS attendance data. Family/household level. The campus short code where the household most recently checked into Worship.

### `last_worship_checkin_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS attendance data. Family/household level. The most recent attendance_start_timestamp where parent_group_name = 'Worship' for any member serving in the household. Shows current Worship engagement.

### `latitude`

- **Type**: FLOAT64
- **Description**: Extracted from Rock RMS Location.GeoPoint using custom function. Entity level. The latitude coordinate of the entity location in decimal degrees. Used for mapping and distance calculations.

### `list_of_given_funds`

- **Type**: STRING
- **Description**: List of funds the person has given to.

### `longitude`

- **Type**: FLOAT64
- **Description**: Extracted from Rock RMS Location.GeoPoint using custom function. Entity level. The longitude coordinate of the entity location in decimal degrees. Used for mapping and distance calculations.

### `number_of_adults`

- **Type**: INT64
- **Description**: From Rock RMS Person table. Family/household level. Count of all people in the family where is_adult = TRUE. Calculated by summing adults (age 18+) within each rms_family_id.

### `number_of_children`

- **Type**: INT64
- **Description**: From Rock RMS Person table. Family/household level. Count of all people in the family where is_adult = FALSE. Calculated by summing children (under 18) within each rms_family_id.

### `postal_code`

- **Type**: STRING
- **Description**: From Rock RMS Location.postalcode. Person level. The ZIP code of the person's home address. Used for geographic analysis and drive time calculations.

### `primary_giving_subtype`

- **Type**: STRING
- **Description**: The specific payment method subtype (e.g., 'Visa', 'Mastercard') used in the person's most recent contribution. Person level. From the latest transaction's transaction_subtype, excluding 'unknown' values. Rock > Profile > Transactions.

### `primary_giving_type`

- **Type**: STRING
- **Description**: The transaction type (e.g., 'Cash', 'Check', 'ACH', 'Credit Card') used in the person's most recent contribution. Person level. From the latest transaction's transaction_type. Rock > Profile > Transactions.

### `removed_from_mailing_list_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS AttributeValue table. Family/household level. The timestamp when the family was marked as removed from mailing list. Captured from CreatedDateTime when the attribute was set. Note: The config shows 'removed_from_mailing_list_times' but the SQL uses 'removed_from_mailing_list_timestamp'.

### `rms_family_id`

- **Type**: INT64
- **Description**: The primary unique identifier for a family or household in Rock RMS.

### `scheduled_transaction_count`

- **Type**: INT64
- **Description**: The number of gifts the person has given using a recurring schedule.

### `state_province`

- **Type**: STRING
- **Description**: From person_location table. Family-level. Full state/province name. Rock > Person > Address.

### `statement_suppressed_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp when the person opted out of printed contribution statements. Person level. CreatedDateTime of the statement suppression attribute. Rock > Profile > Attributes > Suppress Sending Contribution Statements > Created Date.

### `three_month_campus`

- **Type**: STRING
- **Description**: The campus short code where the person committed to the three-month tithe challenge. Person level. From the campus attribute in the Three Month Tithe Challenge matrix. Rock > Profile > Attributes > Three Month Tithe Challenge.

### `three_month_timestamp`

- **Type**: TIMESTAMP
- **Description**: The start date when the person began their three-month tithe challenge commitment. Person level. Retrieved from Rock attribute matrix for Three Month Tithe Challenge. Format: YYYY-MM-DD HH:MM:SS. Rock > Profile > Person > Attributes > Three Month Tithe Challenge.

### `total_giving_count`

- **Type**: INT64
- **Description**: The total number of financial transactions for the person. Defaults to 0 if null.

