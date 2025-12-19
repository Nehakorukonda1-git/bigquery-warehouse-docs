# fact_baptism

## Columns

Total Columns: 15

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| `age_at_baptism` | FLOAT64 | Calculated field. Person level. The age in years of the person at the time of their baptism event. Calculated as DATE_DIFF between baptism timestamp and birthdate. NULL if birthdate is not available. Integer value used for age-appropriate ministry analysis and demographic reporting. |
| `age_classification_at_baptism` | STRING | Calculated field. Person level. The ministry age classification of the person at the time of their baptism, derived from their age and school grade. Returns 'Adult' for those 18+, 'Student' for middle and high schoolers (6th-12th grade), 'Kid' for elementary students (K-5th grade). Defaults to 'Adult' when grade cannot be determined. Used for age-appropriate ministry follow-up, reporting segmentation, and determining which ministry team handles post-baptism discipleship. |
| `age_of_participant` | STRING | The age group defined at the time of the baptism sign up. |
| `baptism_event_participation_campus` | STRING | From Data Warehouse, using Rock person data. Person level. The main, home, primary, or preferred campus of the person. This is the best source for identifing which campus a person belongs to. Rock > Profile > Main Contact Details. |
| `baptism_event_participation_id` | INT64 | From Rock RMS AttributeMatrixItem table. Person-level. The unique identifier for each baptism event record in the Life Events attribute matrix. Rock > Person Profile > Extended Attributes > Life Events > Baptism. |
| `baptism_event_participation_timestamp` | TIMESTAMP | From Rock RMS AttributeValue table. Event-level. Parsed from baptism date attribute supporting multiple formats (MM/DD/YYYY, YYYY-MM-DD, ISO timestamps). Rock > Person Profile > Extended Attributes > Life Events > Baptism > Date. |
| `connection_request_id` | INT64 | Unique Rock RMS identifier for the connection request. Connection request level. Primary key from ConnectionRequest.Id. Used to join activity and status data. Rock > People > Connections > [Connection Name] > Details. |
| `full_name` | STRING | From Rock RMS Person. Person level. The person's full name constructed as nickname (or first name if no nickname) plus last name. Used for human-readable identification in reports. |
| `is_adult` | BOOL | Boolean indicating whether or not the person is an adult in their family. TRUE indicates the person is an Adult. Rule of thumb defines a person as Adult when older than 18 years old. FALSE indicates the person is a Child or Unknown. |
| `is_first_baptism_event_participation_campus` | BOOL | Calculated field. Event-level. TRUE if this is the person's first recorded baptism at this specific campus based on timestamp ordering, FALSE for subsequent baptisms at the same campus. Used to identify unique baptisms per campus. |
| `lc_week_start_date` | DATE | The Sunday that begins the Life.Church operational week for this date. Data source: Calculated from base Date table with adjustments based on staff portal calendar events. Granularity: Date level. Calculation logic: Standard assignment uses the most recent Sunday; adjusted when ministry events span across Sundays - dates before the Sunday are moved to that Sunday's week. UI location: Staff Portal > Calendar Column purpose: Ensures multi-day events are analyzed as a single unit rather than split across weeks. Data format: DATE. |
| `previous_baptism_event_participation_timestamp` | TIMESTAMP | Calculated field using LAG window function. Person-level. The timestamp of the person's previous baptism event regardless of campus. NULL if this is their only baptism. |
| `rms_person_id` | INT64 | The unique Rock RMS identifier for the individual. Person-level. Links to Person.Id in Rock RMS. Used to join all person-related data across the system. Rock > Person Profile. |
| `school_grade_at_baptism` | STRING | From DefinedValue table via graduation year calculation. Person level. The school grade (e.g., '1st Grade', '5th Grade') the person was in at the time of baptism. Calculated using graduation year and baptism timestamp, adjusting for school year transitions after May 1st. NULL for adults or when graduation year is not available. Used for age-appropriate follow-up and children's ministry reporting. |
| `service_day_hour` | STRING | Combined day and time description for easy service identification (e.g., 'Saturday 5:00 PM', 'Sunday 11:30 AM'). Concatenated from day_name_of_week and service_hour. Used as a natural key for service identification in reports and analysis. |

## Column Details

### `age_at_baptism`

- **Type**: FLOAT64
- **Description**: Calculated field. Person level. The age in years of the person at the time of their baptism event. Calculated as DATE_DIFF between baptism timestamp and birthdate. NULL if birthdate is not available. Integer value used for age-appropriate ministry analysis and demographic reporting.

### `age_classification_at_baptism`

- **Type**: STRING
- **Description**: Calculated field. Person level. The ministry age classification of the person at the time of their baptism, derived from their age and school grade. Returns 'Adult' for those 18+, 'Student' for middle and high schoolers (6th-12th grade), 'Kid' for elementary students (K-5th grade). Defaults to 'Adult' when grade cannot be determined. Used for age-appropriate ministry follow-up, reporting segmentation, and determining which ministry team handles post-baptism discipleship.

### `age_of_participant`

- **Type**: STRING
- **Description**: The age group defined at the time of the baptism sign up.

### `baptism_event_participation_campus`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock person data. Person level. The main, home, primary, or preferred campus of the person. This is the best source for identifing which campus a person belongs to. Rock > Profile > Main Contact Details.

### `baptism_event_participation_id`

- **Type**: INT64
- **Description**: From Rock RMS AttributeMatrixItem table. Person-level. The unique identifier for each baptism event record in the Life Events attribute matrix. Rock > Person Profile > Extended Attributes > Life Events > Baptism.

### `baptism_event_participation_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS AttributeValue table. Event-level. Parsed from baptism date attribute supporting multiple formats (MM/DD/YYYY, YYYY-MM-DD, ISO timestamps). Rock > Person Profile > Extended Attributes > Life Events > Baptism > Date.

### `connection_request_id`

- **Type**: INT64
- **Description**: Unique Rock RMS identifier for the connection request. Connection request level. Primary key from ConnectionRequest.Id. Used to join activity and status data. Rock > People > Connections > [Connection Name] > Details.

### `full_name`

- **Type**: STRING
- **Description**: From Rock RMS Person. Person level. The person's full name constructed as nickname (or first name if no nickname) plus last name. Used for human-readable identification in reports.

### `is_adult`

- **Type**: BOOL
- **Description**: Boolean indicating whether or not the person is an adult in their family. TRUE indicates the person is an Adult. Rule of thumb defines a person as Adult when older than 18 years old. FALSE indicates the person is a Child or Unknown.

### `is_first_baptism_event_participation_campus`

- **Type**: BOOL
- **Description**: Calculated field. Event-level. TRUE if this is the person's first recorded baptism at this specific campus based on timestamp ordering, FALSE for subsequent baptisms at the same campus. Used to identify unique baptisms per campus.

### `lc_week_start_date`

- **Type**: DATE
- **Description**: The Sunday that begins the Life.Church operational week for this date. Data source: Calculated from base Date table with adjustments based on staff portal calendar events. Granularity: Date level. Calculation logic: Standard assignment uses the most recent Sunday; adjusted when ministry events span across Sundays - dates before the Sunday are moved to that Sunday's week. UI location: Staff Portal > Calendar Column purpose: Ensures multi-day events are analyzed as a single unit rather than split across weeks. Data format: DATE.

### `previous_baptism_event_participation_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated field using LAG window function. Person-level. The timestamp of the person's previous baptism event regardless of campus. NULL if this is their only baptism.

### `rms_person_id`

- **Type**: INT64
- **Description**: The unique Rock RMS identifier for the individual. Person-level. Links to Person.Id in Rock RMS. Used to join all person-related data across the system. Rock > Person Profile.

### `school_grade_at_baptism`

- **Type**: STRING
- **Description**: From DefinedValue table via graduation year calculation. Person level. The school grade (e.g., '1st Grade', '5th Grade') the person was in at the time of baptism. Calculated using graduation year and baptism timestamp, adjusting for school year transitions after May 1st. NULL for adults or when graduation year is not available. Used for age-appropriate follow-up and children's ministry reporting.

### `service_day_hour`

- **Type**: STRING
- **Description**: Combined day and time description for easy service identification (e.g., 'Saturday 5:00 PM', 'Sunday 11:30 AM'). Concatenated from day_name_of_week and service_hour. Used as a natural key for service identification in reports and analysis.

