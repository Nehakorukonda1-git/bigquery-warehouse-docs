# fact_attendance_scaffolded

## Columns

Total Columns: 11

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| `attendance_attendance_id` | INT64 | No description |
| `attendance_group_name` | STRING | From Rock RMS Group.Name. Record level. The specific area/team name where the check-in occurred. For attenders: room names like 'Konnect', 'The Loop'. For volunteers: team names like 'Parking Team', 'LifeKids Konnect'. |
| `campus` | STRING | From Data Warehouse, using Rock person data. Person level. The main, home, primary, or preferred campus of the person. This is the best source for identifing which campus a person belongs to. Rock > Profile > Main Contact Details. |
| `full_name` | STRING | From Rock RMS Person. Person level. The person's full name constructed as nickname (or first name if no nickname) plus last name. Used for human-readable identification in reports. |
| `is_volunteer_attendance_type` | BOOL | Attendance level. Boolean flag distinguishing volunteer check-ins from regular attendance. Always FALSE in this attender-focused table. |
| `lc_week_start_date` | DATE | The Sunday that begins the Life.Church operational week for this date. Data source: Calculated from base Date table with adjustments based on staff portal calendar events. Granularity: Date level. Calculation logic: Standard assignment uses the most recent Sunday; adjusted when ministry events span across Sundays - dates before the Sunday are moved to that Sunday's week. UI location: Staff Portal > Calendar Column purpose: Ensures multi-day events are analyzed as a single unit rather than split across weeks. Data format: DATE. |
| `parent_group_name` | STRING | From Rock RMS parent Group.Name with transformations. Attendance level. The overarching ministry area, normalized from various naming patterns (e.g., 'Switch' from 'switch'/'swerve', 'LifeKids', 'Host Team'). Groups related attendance areas. |
| `previous_attendance_campus` | STRING | Calculated using LAG() window function on campus_short_code. Person level. The campus code where the person had their previous check-in. NULL if first record. Used to track campus movement patterns. |
| `previous_combined_attendance_campus` | STRING | Calculated using LAG() on campus_short_code across all check-ins. Person level. The campus code of the person's previous check-in (attendance or serving). NULL if first engagement. Tracks cross-campus movement patterns. |
| `rms_family_id` | INT64 | The primary unique identifier for a family or household in Rock RMS. |
| `rms_person_id` | INT64 | The unique Rock RMS identifier for the individual. Person-level. Links to Person.Id in Rock RMS. Used to join all person-related data across the system. Rock > Person Profile. |

## Column Details

### `attendance_attendance_id`

- **Type**: INT64

### `attendance_group_name`

- **Type**: STRING
- **Description**: From Rock RMS Group.Name. Record level. The specific area/team name where the check-in occurred. For attenders: room names like 'Konnect', 'The Loop'. For volunteers: team names like 'Parking Team', 'LifeKids Konnect'.

### `campus`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock person data. Person level. The main, home, primary, or preferred campus of the person. This is the best source for identifing which campus a person belongs to. Rock > Profile > Main Contact Details.

### `full_name`

- **Type**: STRING
- **Description**: From Rock RMS Person. Person level. The person's full name constructed as nickname (or first name if no nickname) plus last name. Used for human-readable identification in reports.

### `is_volunteer_attendance_type`

- **Type**: BOOL
- **Description**: Attendance level. Boolean flag distinguishing volunteer check-ins from regular attendance. Always FALSE in this attender-focused table.

### `lc_week_start_date`

- **Type**: DATE
- **Description**: The Sunday that begins the Life.Church operational week for this date. Data source: Calculated from base Date table with adjustments based on staff portal calendar events. Granularity: Date level. Calculation logic: Standard assignment uses the most recent Sunday; adjusted when ministry events span across Sundays - dates before the Sunday are moved to that Sunday's week. UI location: Staff Portal > Calendar Column purpose: Ensures multi-day events are analyzed as a single unit rather than split across weeks. Data format: DATE.

### `parent_group_name`

- **Type**: STRING
- **Description**: From Rock RMS parent Group.Name with transformations. Attendance level. The overarching ministry area, normalized from various naming patterns (e.g., 'Switch' from 'switch'/'swerve', 'LifeKids', 'Host Team'). Groups related attendance areas.

### `previous_attendance_campus`

- **Type**: STRING
- **Description**: Calculated using LAG() window function on campus_short_code. Person level. The campus code where the person had their previous check-in. NULL if first record. Used to track campus movement patterns.

### `previous_combined_attendance_campus`

- **Type**: STRING
- **Description**: Calculated using LAG() on campus_short_code across all check-ins. Person level. The campus code of the person's previous check-in (attendance or serving). NULL if first engagement. Tracks cross-campus movement patterns.

### `rms_family_id`

- **Type**: INT64
- **Description**: The primary unique identifier for a family or household in Rock RMS.

### `rms_person_id`

- **Type**: INT64
- **Description**: The unique Rock RMS identifier for the individual. Person-level. Links to Person.Id in Rock RMS. Used to join all person-related data across the system. Rock > Person Profile.

