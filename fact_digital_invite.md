# fact_digital_invite

## Columns

Total Columns: 5

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| `campus_short_code` | STRING | From Data Warehouse, using Rock person data. Person level. The main, home, primary, or preferred campus of the person. This is the best source for identifing which campus a person belongs to. Rock > Profile > Main Contact Details. |
| `digital_invite_id` | INT64 | From Rock RMS Interaction.Id. The unique identifier for each digital invite interaction record. Primary key ensuring each invite is tracked individually. Used for deduplication and joining with other interaction-related data. |
| `invite_date` | DATETIME | From Rock RMS Interaction.CreatedDateTime. The exact timestamp when the digital invite was sent by the person. Format: YYYY-MM-DD HH:MM:SS. Used to track invite timing patterns and calculate time-based metrics. |
| `invite_date_key` | STRING | Calculated from invite_date using FORMAT_DATE. The date of the invite formatted as an integer key (YYYYMMDD) for efficient joining with date dimension tables and partitioning. Example: 20240115 for January 15, 2024. Used for date-based aggregations and reporting. |
| `rms_person_id` | INT64 | The unique Rock RMS identifier for the individual. Person-level. Links to Person.Id in Rock RMS. Used to join all person-related data across the system. Rock > Person Profile. |

## Column Details

### `campus_short_code`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock person data. Person level. The main, home, primary, or preferred campus of the person. This is the best source for identifing which campus a person belongs to. Rock > Profile > Main Contact Details.

### `digital_invite_id`

- **Type**: INT64
- **Description**: From Rock RMS Interaction.Id. The unique identifier for each digital invite interaction record. Primary key ensuring each invite is tracked individually. Used for deduplication and joining with other interaction-related data.

### `invite_date`

- **Type**: DATETIME
- **Description**: From Rock RMS Interaction.CreatedDateTime. The exact timestamp when the digital invite was sent by the person. Format: YYYY-MM-DD HH:MM:SS. Used to track invite timing patterns and calculate time-based metrics.

### `invite_date_key`

- **Type**: STRING
- **Description**: Calculated from invite_date using FORMAT_DATE. The date of the invite formatted as an integer key (YYYYMMDD) for efficient joining with date dimension tables and partitioning. Example: 20240115 for January 15, 2024. Used for date-based aggregations and reporting.

### `rms_person_id`

- **Type**: INT64
- **Description**: The unique Rock RMS identifier for the individual. Person-level. Links to Person.Id in Rock RMS. Used to join all person-related data across the system. Rock > Person Profile.

