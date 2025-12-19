# fact_volunteer_interest

## Columns

Total Columns: 13

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| `email` | STRING | From Rock RMS Person.email. Person level. The person's primary email address as stored in Rock RMS. May be NULL if no email on file. Used for communication and matching. |
| `first_check_in_after_volunteer_interest` | TIMESTAMP | Timestamp of the first volunteer check-in that occurred after this volunteer interest submission for the same ministry and campus. |
| `form_submission_volunteer_interest_campus` | STRING | Short code identifier for the campus where the person wants to serve. |
| `form_submission_volunteer_interest_ministry` | STRING | Preferred ministry area for volunteering, normalized to lowercase with special characters replaced by underscores. |
| `form_submission_volunteer_interest_timestamp` | TIMESTAMP | The timestamp that a volunteer interest form was submitted in CDT. |
| `form_type` | STRING | The type of process that was used to record the form submission (e.g. Connection Request, Workflows, Steps, etc). |
| `is_first_volunteer_interest` | BOOL | Boolean flag indicating if this is the person's first volunteer interest submission for this ministry preference. |
| `is_last_volunteer_interest` | BOOL | Boolean flag indicating if this is the person's most recent volunteer interest submission for this ministry preference. |
| `lc_week_start_date` | DATE | The Sunday that begins the Life.Church operational week for this date. Data source: Calculated from base Date table with adjustments based on staff portal calendar events. Granularity: Date level. Calculation logic: Standard assignment uses the most recent Sunday; adjusted when ministry events span across Sundays - dates before the Sunday are moved to that Sunday's week. UI location: Staff Portal > Calendar Column purpose: Ensures multi-day events are analyzed as a single unit rather than split across weeks. Data format: DATE. |
| `previous_form_submission` | TIMESTAMP | The previous timestamp that a form of the same name was submitted in CDT. |
| `rms_person_id` | INT64 | The unique Rock RMS identifier for the individual. Person-level. Links to Person.Id in Rock RMS. Used to join all person-related data across the system. Rock > Person Profile. |
| `volunteer_interest_id` | STRING | The guid associated with the volunteer interest workflow. |
| `workflow_id` | INT64 | The constant unique identifier for an individual workflow that has been triggered. |

## Column Details

### `email`

- **Type**: STRING
- **Description**: From Rock RMS Person.email. Person level. The person's primary email address as stored in Rock RMS. May be NULL if no email on file. Used for communication and matching.

### `first_check_in_after_volunteer_interest`

- **Type**: TIMESTAMP
- **Description**: Timestamp of the first volunteer check-in that occurred after this volunteer interest submission for the same ministry and campus.

### `form_submission_volunteer_interest_campus`

- **Type**: STRING
- **Description**: Short code identifier for the campus where the person wants to serve.

### `form_submission_volunteer_interest_ministry`

- **Type**: STRING
- **Description**: Preferred ministry area for volunteering, normalized to lowercase with special characters replaced by underscores.

### `form_submission_volunteer_interest_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp that a volunteer interest form was submitted in CDT.

### `form_type`

- **Type**: STRING
- **Description**: The type of process that was used to record the form submission (e.g. Connection Request, Workflows, Steps, etc).

### `is_first_volunteer_interest`

- **Type**: BOOL
- **Description**: Boolean flag indicating if this is the person's first volunteer interest submission for this ministry preference.

### `is_last_volunteer_interest`

- **Type**: BOOL
- **Description**: Boolean flag indicating if this is the person's most recent volunteer interest submission for this ministry preference.

### `lc_week_start_date`

- **Type**: DATE
- **Description**: The Sunday that begins the Life.Church operational week for this date. Data source: Calculated from base Date table with adjustments based on staff portal calendar events. Granularity: Date level. Calculation logic: Standard assignment uses the most recent Sunday; adjusted when ministry events span across Sundays - dates before the Sunday are moved to that Sunday's week. UI location: Staff Portal > Calendar Column purpose: Ensures multi-day events are analyzed as a single unit rather than split across weeks. Data format: DATE.

### `previous_form_submission`

- **Type**: TIMESTAMP
- **Description**: The previous timestamp that a form of the same name was submitted in CDT.

### `rms_person_id`

- **Type**: INT64
- **Description**: The unique Rock RMS identifier for the individual. Person-level. Links to Person.Id in Rock RMS. Used to join all person-related data across the system. Rock > Person Profile.

### `volunteer_interest_id`

- **Type**: STRING
- **Description**: The guid associated with the volunteer interest workflow.

### `workflow_id`

- **Type**: INT64
- **Description**: The constant unique identifier for an individual workflow that has been triggered.

