# fact_form_submission

## Columns

Total Columns: 8

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| `form_name` | STRING | Name of the form that was submitted. |
| `form_purpose` | STRING | Categorizes the intent of the form submission. Values: 'account_acquisition' for new user capture, 'next_steps' for spiritual growth forms, 'volunteer_interest' for serving opportunities. |
| `form_source` | STRING | Identifies the source system where the form was submitted. Values: 'hubspot' for HubSpot forms, 'rock' for Rock RMS forms. |
| `form_submission_campus` | STRING | The campus that the form was submitted to. If null or INT associated with LCO. |
| `form_submission_timestamp` | TIMESTAMP | The timestamp that a form was submitted in CDT. |
| `previous_form_submission` | TIMESTAMP | The previous timestamp that a form of the same name was submitted in CDT. |
| `rms_person_id` | INT64 | The unique Rock RMS identifier for the individual. Person-level. Links to Person.Id in Rock RMS. Used to join all person-related data across the system. Rock > Person Profile. |
| `workflow_id` | STRING | The constant unique identifier for an individual workflow that has been triggered. |

## Column Details

### `form_name`

- **Type**: STRING
- **Description**: Name of the form that was submitted.

### `form_purpose`

- **Type**: STRING
- **Description**: Categorizes the intent of the form submission. Values: 'account_acquisition' for new user capture, 'next_steps' for spiritual growth forms, 'volunteer_interest' for serving opportunities.

### `form_source`

- **Type**: STRING
- **Description**: Identifies the source system where the form was submitted. Values: 'hubspot' for HubSpot forms, 'rock' for Rock RMS forms.

### `form_submission_campus`

- **Type**: STRING
- **Description**: The campus that the form was submitted to. If null or INT associated with LCO.

### `form_submission_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp that a form was submitted in CDT.

### `previous_form_submission`

- **Type**: TIMESTAMP
- **Description**: The previous timestamp that a form of the same name was submitted in CDT.

### `rms_person_id`

- **Type**: INT64
- **Description**: The unique Rock RMS identifier for the individual. Person-level. Links to Person.Id in Rock RMS. Used to join all person-related data across the system. Rock > Person Profile.

### `workflow_id`

- **Type**: STRING
- **Description**: The constant unique identifier for an individual workflow that has been triggered.

