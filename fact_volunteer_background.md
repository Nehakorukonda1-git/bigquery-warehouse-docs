# fact_volunteer_background

## Columns

Total Columns: 18

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| `application_completed_date` | DATETIME | Timestamp when the workflow was completed, if available. |
| `application_created_date` | DATETIME | Timestamp when the workflow was created (application submitted). |
| `application_id` | STRING | Unique identifier (GUID) of the background check workflow application. |
| `application_status` | STRING | Final status of the workflow (e.g., BGC_Approved, Expired, etc.). |
| `background_check_request_id` | STRING | Identifier of the request sent to the background check provider. |
| `background_check_status` | STRING | The current status of the person's background check. |
| `background_status_source` | STRING | Source of the background check status; always set to 'workflow' in this model. |
| `billed_campus` | STRING | Campus short code used for billing or accounting purposes. |
| `cia_response_date` | DATETIME | Date the background check provider returned a response. |
| `conditional_attendance_agreement` | STRING | Yes/No flag for whether the applicant has a conditional attendance agreement. |
| `cost` | BIGNUMERIC | Numeric cost value recorded for processing the background check. |
| `country` | STRING | From location.country. Person level. The country of the person's home address. Typically 'US' for most records. Used for international attendee identification. |
| `entry_method` | STRING | How the application was submitted (e.g., Online, Paper, HR/Risk, or flex type). |
| `ministry` | STRING | Ministry area associated with the application, if provided. |
| `red_flag` | STRING | Yes/No flag for whether the applicant has a red flag in their record. |
| `renewal` | STRING | Yes/No flag indicating if the application is a renewal rather than the first check. |
| `rms_person_id` | INT64 | The unique Rock RMS identifier for the individual. Person-level. Links to Person.Id in Rock RMS. Used to join all person-related data across the system. Rock > Person Profile. |
| `serving_campus` | STRING | Campus short code indicating where the volunteer intends to serve. |

## Column Details

### `application_completed_date`

- **Type**: DATETIME
- **Description**: Timestamp when the workflow was completed, if available.

### `application_created_date`

- **Type**: DATETIME
- **Description**: Timestamp when the workflow was created (application submitted).

### `application_id`

- **Type**: STRING
- **Description**: Unique identifier (GUID) of the background check workflow application.

### `application_status`

- **Type**: STRING
- **Description**: Final status of the workflow (e.g., BGC_Approved, Expired, etc.).

### `background_check_request_id`

- **Type**: STRING
- **Description**: Identifier of the request sent to the background check provider.

### `background_check_status`

- **Type**: STRING
- **Description**: The current status of the person's background check.

### `background_status_source`

- **Type**: STRING
- **Description**: Source of the background check status; always set to 'workflow' in this model.

### `billed_campus`

- **Type**: STRING
- **Description**: Campus short code used for billing or accounting purposes.

### `cia_response_date`

- **Type**: DATETIME
- **Description**: Date the background check provider returned a response.

### `conditional_attendance_agreement`

- **Type**: STRING
- **Description**: Yes/No flag for whether the applicant has a conditional attendance agreement.

### `cost`

- **Type**: BIGNUMERIC
- **Description**: Numeric cost value recorded for processing the background check.

### `country`

- **Type**: STRING
- **Description**: From location.country. Person level. The country of the person's home address. Typically 'US' for most records. Used for international attendee identification.

### `entry_method`

- **Type**: STRING
- **Description**: How the application was submitted (e.g., Online, Paper, HR/Risk, or flex type).

### `ministry`

- **Type**: STRING
- **Description**: Ministry area associated with the application, if provided.

### `red_flag`

- **Type**: STRING
- **Description**: Yes/No flag for whether the applicant has a red flag in their record.

### `renewal`

- **Type**: STRING
- **Description**: Yes/No flag indicating if the application is a renewal rather than the first check.

### `rms_person_id`

- **Type**: INT64
- **Description**: The unique Rock RMS identifier for the individual. Person-level. Links to Person.Id in Rock RMS. Used to join all person-related data across the system. Rock > Person Profile.

### `serving_campus`

- **Type**: STRING
- **Description**: Campus short code indicating where the volunteer intends to serve.

