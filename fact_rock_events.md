# fact_rock_events

## Columns

Total Columns: 6

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| `campus` | STRING | From Data Warehouse, using Rock person data. Person level. The main, home, primary, or preferred campus of the person. This is the best source for identifing which campus a person belongs to. Rock > Profile > Main Contact Details. |
| `previous_start_timestamp` | TIMESTAMP | The timestamp of the person's previous interaction of the same type. NULL if this is their first interaction of this type. |
| `rms_person_id` | INT64 | The unique Rock RMS identifier for the individual. Person-level. Links to Person.Id in Rock RMS. Used to join all person-related data across the system. Rock > Person Profile. |
| `start_timestamp` | TIMESTAMP | The timestamp when the interaction occurred. |
| `step` | STRING | The type and sequence of interaction (e.g., 'Attendance 1', 'Serving 2', form name, 'Transaction 3', 'Created', 'BaptismAttribute', 'KnownAttribute'). |
| `step_id` | INT64 | The unique identifier for each interaction or step. This varies based on the interaction type (attendance_id, serving_id, workflow_id, transaction_id, person_id, or baptism_id). |

## Column Details

### `campus`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock person data. Person level. The main, home, primary, or preferred campus of the person. This is the best source for identifing which campus a person belongs to. Rock > Profile > Main Contact Details.

### `previous_start_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp of the person's previous interaction of the same type. NULL if this is their first interaction of this type.

### `rms_person_id`

- **Type**: INT64
- **Description**: The unique Rock RMS identifier for the individual. Person-level. Links to Person.Id in Rock RMS. Used to join all person-related data across the system. Rock > Person Profile.

### `start_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp when the interaction occurred.

### `step`

- **Type**: STRING
- **Description**: The type and sequence of interaction (e.g., 'Attendance 1', 'Serving 2', form name, 'Transaction 3', 'Created', 'BaptismAttribute', 'KnownAttribute').

### `step_id`

- **Type**: INT64
- **Description**: The unique identifier for each interaction or step. This varies based on the interaction type (attendance_id, serving_id, workflow_id, transaction_id, person_id, or baptism_id).

