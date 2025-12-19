# fact_attendance

## Columns

Total Columns: 77

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| `address_1` | STRING | From Rock RMS Location.Street1. Entity level. The primary street address line for the entity physical location. |
| `address_2` | STRING | From Rock RMS Location.Street2. Entity level. The secondary address line (suite, building, etc). Returns empty string if NULL. |
| `address_to_checked_in_campus_distance_miles` | FLOAT64 | Calculated using ST_DISTANCE with geographic points. Person-attendance level. Distance in miles between person's home address and the campus they checked into. Decimal value used for drive time analysis. |
| `attendance_attendance_id` | INT64 | From Rock RMS Attendance.Id. Record level. The unique identifier for this individual attendance record. Primary key ensuring each check-in (attendance or serving) is uniquely identifiable. |
| `attendance_day_of_week` | STRING | Derived using FORMAT_TIMESTAMP from attendance_start_timestamp. Record level. The day name extracted from the timestamp (e.g., 'Sunday', 'Wednesday'). Used for pattern analysis by day of week. |
| `attendance_group_id` | INT64 | From Rock RMS Group.Id. Record level. The unique numeric identifier for the specific group/area. Primary reference for joining group-related data. |
| `attendance_group_name` | STRING | From Rock RMS Group.Name. Record level. The specific area/team name where the check-in occurred. For attenders: room names like 'Konnect', 'The Loop'. For volunteers: team names like 'Parking Team', 'LifeKids Konnect'. |
| `attendance_service_day_hour` | STRING | Calculated concatenation of day and time. Record level. For attenders: combines day of week with service time rounded to nearest 30-minute increment for grouping similar services. For volunteers: combines day with exact service time for precise scheduling. |
| `attendance_service_time` | STRING | Derived using FORMAT_TIMESTAMP from attendance_start_timestamp. Record level. The time portion formatted as 12-hour time with AM/PM (e.g., '9:00 AM', '11:30 AM'). Represents the scheduled time slot. |
| `attendance_start_timestamp` | TIMESTAMP | From Rock RMS Attendance.StartDateTime with Schedule.iCalendarContent parsing. Record level. The scheduled start time extracted from iCalendar format when available (parsing DTSTART property), otherwise uses Attendance.StartDateTime. Represents when the service/activity was scheduled to begin. |
| `birthdate` | DATE | From Rock RMS Person.Birthdate. Person level. The person's date of birth. Format: YYYY-MM-DD. Used for age calculations and age-appropriate room assignments. |
| `campus_id` | INT64 | From Rock RMS Campus.Id. Campus level. The unique numeric identifier for each campus in the Rock RMS system. Rock > Admin Tools > General Settings > Campuses > Id field. Primary key for this table. |
| `campus_short_code` | STRING | From Rock RMS Campus.ShortCode. Campus level. The three-letter code uniquely representing each campus (e.g., 'OKC', 'TUL', 'EDM'). Rock > Admin Tools > General Settings > Campuses > Short Code field. Used for abbreviated campus references throughout the system. |
| `check_in_type` | STRING | From Rock RMS Attendance.SearchTypeValueId. Attendance level. The method used to check in: 'Phone Number', 'Name', 'Name & Phone', 'Barcode', 'Family Id', or 'Communication Card'. Indicates how the person was identified at check-in. |
| `checked_in_timestamp` | DATETIME | From Rock RMS Attendance.CreatedDateTime. Attendance level. The actual timestamp when the check-in record was created in the system. May differ from scheduled time. |
| `city` | STRING | From Rock RMS Location. Entity level. The city where the entity is located. |
| `country` | STRING | From location.country. Person level. The country of the person's home address. Typically 'US' for most records. Used for international attendee identification. |
| `email` | STRING | From Rock RMS Person.email. Person level. The person's primary email address as stored in Rock RMS. May be NULL if no email on file. Used for communication and matching. |
| `full_name` | STRING | From Rock RMS Person. Person level. The person's full name constructed as nickname (or first name if no nickname) plus last name. Used for human-readable identification in reports. |
| `gender` | STRING | Employee gender from employee.gender. Used for diversity analytics. NULL for requisitions. |
| `group_role` | STRING | From Rock RMS GroupMemberHistorical.GroupRoleName via temporal join. Record level. For volunteers: the role at time of serving (e.g., 'Leader', 'Member'). For attenders: The volunteer's role in the group (e.g., leader, helper). Primarily used in LifeKids to track student vs. adult leaders. Due to process issues where people aren't properly deactivated before role changes, this column prioritizes adult roles over student roles when conflicts exist. |
| `group_type_id` | INT64 | From Rock RMS GroupType.Id. Attendance level. The numeric identifier for the type of group activity. Determines the nature of the attendance record. |
| `is_app_check_in` | BOOL | From GroupType.GroupTypePurposeValueId comparison. Attendance level. TRUE when attendance was recorded via the Life.Church mobile app (streak-type check-ins), FALSE for physical location check-ins. |
| `is_deceased` | BOOL | From Rock RMS Person.isdeceased. Person level. Boolean flag indicating if the person is marked as deceased in Rock RMS. TRUE if deceased, FALSE if living. Important for data hygiene and filtering. |
| `is_first_check_in` | BOOL | Calculated using ROW_NUMBER() window function. Person level. TRUE if this is the person's first attendance record ever (ordered by timestamp), FALSE otherwise. Identifies new attendees. |
| `is_first_check_in_at_campus` | BOOL | Calculated using ROW_NUMBER() partitioned by campus_id and is_volunteer_attendance_type. Person-campus-type level. TRUE if this is the person's first check-in of this specific type (attendance OR volunteer) at this campus across all groups. A person will have two separate 'firsts' at each campus - one for their first attendance and one for their first volunteer check-in. Used to identify initial campus engagement for each check-in type separately. |
| `is_first_check_in_group` | BOOL | Calculated using ROW_NUMBER() partitioned by attendance_group_name. Person level. TRUE if this is the person's first check-in to this specific room/group. |
| `is_first_check_in_group_at_campus` | BOOL | Calculated using ROW_NUMBER() partitioned by attendance_group_name, campus_id, and is_volunteer_attendance_type. Person-campus-group-type level. TRUE if this is the person's first check-in for this specific attendance type (attendance OR volunteer) within this attendance group at this campus. For example, first time volunteering in The Loop at OKC and first time attending The Loop at OKC are tracked separately. Used to track initial engagement with a specific room/team at a campus for each check-in type separately. |
| `is_first_check_in_parent_group` | BOOL | Calculated using ROW_NUMBER() partitioned by parent_group_name. Person level. TRUE if this is the person's first check-in to this ministry area (e.g., first time in LifeKids). |
| `is_first_check_in_parent_group_at_campus` | BOOL | Calculated using ROW_NUMBER() partitioned by parent_group_name, campus_id, and is_volunteer_attendance_type. Person-campus-ministry-type level. TRUE if this is the person's first check-in for this specific attendance type (attendance OR volunteer) within this parent group at this campus. For example, a person's first Host Team volunteer check-in at EDM would be TRUE, but their later first Host Team attendance check-in at EDM would also be TRUE since they're different types. Used to track initial engagement within a ministry at a specific location for each check-in type separately. |
| `is_first_combined_attendance` | BOOL | Calculated using ROW_NUMBER() window function across all records. Person level. TRUE if this is the person's very first check-in of any type (attendance or serving), FALSE otherwise. Identifies when someone first engaged with Life.Church in any capacity. |
| `is_last_check_in` | BOOL | Calculated using ROW_NUMBER() DESC window function. Person level. TRUE if this is the person's most recent attendance record, FALSE otherwise. Identifies current engagement state. |
| `is_last_check_in_at_campus` | BOOL | Calculated using ROW_NUMBER() DESC partitioned by campus_id and is_volunteer_attendance_type. Person-campus-type level. TRUE if this is the person's most recent check-in of this specific type (attendance OR volunteer) at this campus across all groups. Attendance and volunteer activities maintain separate 'last' records. Used to identify the end of overall campus engagement for each check-in type separately. |
| `is_last_check_in_group` | BOOL | Calculated using ROW_NUMBER() DESC partitioned by attendance_group_name. Person level. TRUE if this is the person's most recent check-in to this specific room/group. |
| `is_last_check_in_group_at_campus` | BOOL | Calculated using ROW_NUMBER() DESC partitioned by attendance_group_name, campus_id, and is_volunteer_attendance_type. Person-campus-group-type level. TRUE if this is the person's most recent check-in for this specific attendance type (attendance OR volunteer) within this attendance group at this campus. Attendance and volunteer records are evaluated independently. Used to identify the end of engagement with a specific room/team at a campus for each check-in type separately. |
| `is_last_check_in_parent_group` | BOOL | Calculated using ROW_NUMBER() DESC partitioned by parent_group_name. Person level. TRUE if this is the person's most recent check-in to this ministry area. |
| `is_last_check_in_parent_group_at_campus` | BOOL | Calculated using ROW_NUMBER() DESC partitioned by parent_group_name, campus_id, and is_volunteer_attendance_type. Person-campus-ministry-type level. TRUE if this is the person's most recent check-in for this specific attendance type (attendance OR volunteer) within this parent group at this campus. Tracks separately for attendance vs volunteer - a person could have their last volunteer check-in and later have an attendance check-in, both marked TRUE. Used to identify the end of engagement with a ministry at a location for each check-in type separately. |
| `is_last_combined_attendance` | BOOL | Calculated using ROW_NUMBER() DESC window function across all records. Person level. TRUE if this is the person's most recent check-in of any type (attendance or serving), FALSE otherwise. Indicates current engagement status across all activities. |
| `is_volunteer_attendance_type` | BOOL | Attendance level. Boolean flag distinguishing volunteer check-ins from regular attendance. Always FALSE in this attender-focused table. |
| `lc_week_start_date` | DATE | The Sunday that begins the Life.Church operational week for this date. Data source: Calculated from base Date table with adjustments based on staff portal calendar events. Granularity: Date level. Calculation logic: Standard assignment uses the most recent Sunday; adjusted when ministry events span across Sundays - dates before the Sunday are moved to that Sunday's week. UI location: Staff Portal > Calendar Column purpose: Ensures multi-day events are analyzed as a single unit rather than split across weeks. Data format: DATE. |
| `lifekids_smiley_face` | BOOL | Calculated business rule. Attendance level. TRUE when a child returns to LifeKids after 3+ month absence, triggering special welcome. FALSE otherwise. Indicates re-engagement opportunity. |
| `next_attendance_at_campus_start_timestamp` | TIMESTAMP | Calculated using LEAD() partitioned by campus_id. Person level. Timestamp of the person's next attendance at this same campus. NULL if last time at campus. |
| `next_attendance_campus` | STRING | Calculated using LEAD() window function on campus_short_code. Person level. The campus code where the person will have their next check-in. NULL if this is their last record. |
| `next_attendance_group_start_timestamp` | TIMESTAMP | Calculated using LEAD() partitioned by attendance_group_name. Person level. Timestamp of the person's next attendance in the same specific room. NULL if last time. |
| `next_attendance_parent_group_start_timestamp` | TIMESTAMP | Calculated using LEAD() partitioned by parent_group_name. Person level. Timestamp of the person's next attendance in the same ministry area. NULL if last time. |
| `next_attendance_start_timestamp` | TIMESTAMP | Calculated using LEAD() window function ordered by timestamp. Person level. The timestamp of this person's next check-in of this type. NULL if this is their last record. |
| `next_combined_attendance_at_campus_start_timestamp` | TIMESTAMP | Calculated using LEAD() partitioned by campus_id across all check-ins. Person level. Timestamp of the next check-in at this campus for any activity. NULL if this is their last time at this campus. |
| `next_combined_attendance_campus` | STRING | Calculated using LEAD() on campus_short_code across all check-ins. Person level. The campus code of the person's next check-in (attendance or serving). NULL if this is their last recorded engagement. Useful for campus migration analysis. |
| `next_combined_attendance_group_start_timestamp` | TIMESTAMP | Calculated using LEAD() partitioned by attendance_group_name across all check-ins. Person level. Timestamp of the next check-in in the same specific group/team. NULL if this is their last time in this group. |
| `next_combined_attendance_parent_group_start_timestamp` | TIMESTAMP | Calculated using LEAD() partitioned by parent_group_name across all check-ins. Person level. Timestamp of the next check-in in the same ministry area. NULL if this is their last time in this ministry. |
| `next_combined_attendance_start_timestamp` | TIMESTAMP | Calculated using LEAD() ordered by timestamp across all check-ins. Person level. Timestamp of the person's next check-in of any type. NULL if this is their last recorded engagement. Used for engagement gap analysis. |
| `parent_1_email` | STRING | The email address of the oldest adult in the attendee's family (Parent 1). Provides primary parent/guardian contact information for LifeKids check-ins and family engagement. Sourced from person_basic_info.email. NULL if Parent 1 does not exist or has no email address. |
| `parent_1_name` | STRING | The full name of the oldest adult in the attendee's family. Calculated by joining to person_basic_info where family_position = 'Adult', then ranking by age descending within each rms_family_id. Parent 1 is rank 1 (oldest adult). NULL if no adults exist in the family or if the attendee is the only adult. |
| `parent_1_phone` | STRING | The phone number of the oldest adult in the attendee's family (Parent 1). Provides primary parent/guardian contact information for LifeKids check-ins and family engagement. Sourced from person_basic_info.phone_number. NULL if Parent 1 does not exist or has no phone number. |
| `parent_2_email` | STRING | The email address of the second oldest adult in the attendee's family (Parent 2). Provides secondary parent/guardian contact information for LifeKids check-ins and family engagement. Sourced from person_basic_info.email. NULL if Parent 2 does not exist or has no email address. |
| `parent_2_name` | STRING | The full name of the second oldest adult in the attendee's family. Calculated by joining to person_basic_info where family_position = 'Adult', then ranking by age descending within each rms_family_id. Parent 2 is rank 2 (second oldest adult). NULL if fewer than two adults exist in the family. |
| `parent_2_phone` | STRING | The phone number of the second oldest adult in the attendee's family (Parent 2). Provides secondary parent/guardian contact information for LifeKids check-ins and family engagement. Sourced from person_basic_info.phone_number. NULL if Parent 2 does not exist or has no phone number. |
| `parent_group_id` | INT64 | From Rock RMS parent Group.Id. Attendance level. The unique identifier for the parent group/ministry area. Links attendance to broader organizational structure. |
| `parent_group_name` | STRING | From Rock RMS parent Group.Name with transformations. Attendance level. The overarching ministry area, normalized from various naming patterns (e.g., 'Switch' from 'switch'/'swerve', 'LifeKids', 'Host Team'). Groups related attendance areas. |
| `phone_number` | STRING | The main contact phone number for the individual. Returns NULL if phone number is empty string. |
| `postal_code` | STRING | From Rock RMS Location.postalcode. Person level. The ZIP code of the person's home address. Used for geographic analysis and drive time calculations. |
| `previous_attendance_at_campus_start_timestamp` | TIMESTAMP | Calculated using LAG() partitioned by campus_id. Person level. Timestamp of the person's previous attendance at this same campus. NULL if first time at campus. |
| `previous_attendance_campus` | STRING | Calculated using LAG() window function on campus_short_code. Person level. The campus code where the person had their previous check-in. NULL if first record. Used to track campus movement patterns. |
| `previous_attendance_group_start_timestamp` | TIMESTAMP | Calculated using LAG() partitioned by attendance_group_name. Person level. Timestamp of the person's previous attendance in the same specific room. NULL if first time. |
| `previous_attendance_parent_group_start_timestamp` | TIMESTAMP | Calculated using LAG() partitioned by parent_group_name. Person level. Timestamp of the person's previous attendance in the same ministry area. NULL if first time. Used for gap analysis. |
| `previous_attendance_start_timestamp` | TIMESTAMP | Calculated using LAG() window function ordered by timestamp. Person level. The timestamp of this person's previous check-in of this type (attendance or serving). NULL if this is their first record. |
| `previous_combined_attendance_at_campus_start_timestamp` | TIMESTAMP | Calculated using LAG() partitioned by campus_id across all check-ins. Person level. Timestamp of the previous check-in at this campus for any activity type. NULL if first time at this campus. Used for campus-specific engagement tracking. |
| `previous_combined_attendance_campus` | STRING | Calculated using LAG() on campus_short_code across all check-ins. Person level. The campus code of the person's previous check-in (attendance or serving). NULL if first engagement. Tracks cross-campus movement patterns. |
| `previous_combined_attendance_group_start_timestamp` | TIMESTAMP | Calculated using LAG() partitioned by attendance_group_name across all check-ins. Person level. Timestamp of the previous check-in in the same specific group/team, regardless of attendance or serving. NULL if first time in this group. |
| `previous_combined_attendance_parent_group_start_timestamp` | TIMESTAMP | Calculated using LAG() partitioned by parent_group_name across all check-ins. Person level. Timestamp of the previous check-in in the same ministry area, whether attending or serving. NULL if first time in this ministry. Tracks engagement continuity within ministries. |
| `previous_combined_attendance_start_timestamp` | TIMESTAMP | Calculated using LAG() ordered by timestamp across all check-ins. Person level. Timestamp of the person's previous check-in of any type. NULL if this is their first engagement. Key metric for calculating engagement frequency. |
| `region` | STRING | From Rock RMS DefinedValue table via Campus Area attribute. Campus level. The geographical region the campus belongs to (e.g., 'Oklahoma', 'Kansas', 'Texas'). Rock > Admin > General Settings > Campuses > Attributes > Campus Area. |
| `rms_family_id` | INT64 | The primary unique identifier for a family or household in Rock RMS. |
| `rms_person_id` | INT64 | The unique Rock RMS identifier for the individual. Person-level. Links to Person.Id in Rock RMS. Used to join all person-related data across the system. Rock > Person Profile. |
| `schedule_name` | STRING | From Rock RMS Schedule.Name. Attendance level. The descriptive name of the scheduled service time (e.g., 'Sunday 11:30 AM'). Directly from the schedule configuration in Rock. |
| `school_grade` | STRING | From Rock RMS DefinedValue lookup based on graduation year. Person level. The current school grade descriptor (e.g., 'Kindergarten', '1st Grade'). Calculated from graduation year and current date. |
| `state_province_code` | STRING | From Rock RMS Location.state. Person level. Two-character state/province code of the person's home address (e.g., 'OK', 'TX'). Used for geographic analysis. |

## Column Details

### `address_1`

- **Type**: STRING
- **Description**: From Rock RMS Location.Street1. Entity level. The primary street address line for the entity physical location.

### `address_2`

- **Type**: STRING
- **Description**: From Rock RMS Location.Street2. Entity level. The secondary address line (suite, building, etc). Returns empty string if NULL.

### `address_to_checked_in_campus_distance_miles`

- **Type**: FLOAT64
- **Description**: Calculated using ST_DISTANCE with geographic points. Person-attendance level. Distance in miles between person's home address and the campus they checked into. Decimal value used for drive time analysis.

### `attendance_attendance_id`

- **Type**: INT64
- **Description**: From Rock RMS Attendance.Id. Record level. The unique identifier for this individual attendance record. Primary key ensuring each check-in (attendance or serving) is uniquely identifiable.

### `attendance_day_of_week`

- **Type**: STRING
- **Description**: Derived using FORMAT_TIMESTAMP from attendance_start_timestamp. Record level. The day name extracted from the timestamp (e.g., 'Sunday', 'Wednesday'). Used for pattern analysis by day of week.

### `attendance_group_id`

- **Type**: INT64
- **Description**: From Rock RMS Group.Id. Record level. The unique numeric identifier for the specific group/area. Primary reference for joining group-related data.

### `attendance_group_name`

- **Type**: STRING
- **Description**: From Rock RMS Group.Name. Record level. The specific area/team name where the check-in occurred. For attenders: room names like 'Konnect', 'The Loop'. For volunteers: team names like 'Parking Team', 'LifeKids Konnect'.

### `attendance_service_day_hour`

- **Type**: STRING
- **Description**: Calculated concatenation of day and time. Record level. For attenders: combines day of week with service time rounded to nearest 30-minute increment for grouping similar services. For volunteers: combines day with exact service time for precise scheduling.

### `attendance_service_time`

- **Type**: STRING
- **Description**: Derived using FORMAT_TIMESTAMP from attendance_start_timestamp. Record level. The time portion formatted as 12-hour time with AM/PM (e.g., '9:00 AM', '11:30 AM'). Represents the scheduled time slot.

### `attendance_start_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS Attendance.StartDateTime with Schedule.iCalendarContent parsing. Record level. The scheduled start time extracted from iCalendar format when available (parsing DTSTART property), otherwise uses Attendance.StartDateTime. Represents when the service/activity was scheduled to begin.

### `birthdate`

- **Type**: DATE
- **Description**: From Rock RMS Person.Birthdate. Person level. The person's date of birth. Format: YYYY-MM-DD. Used for age calculations and age-appropriate room assignments.

### `campus_id`

- **Type**: INT64
- **Description**: From Rock RMS Campus.Id. Campus level. The unique numeric identifier for each campus in the Rock RMS system. Rock > Admin Tools > General Settings > Campuses > Id field. Primary key for this table.

### `campus_short_code`

- **Type**: STRING
- **Description**: From Rock RMS Campus.ShortCode. Campus level. The three-letter code uniquely representing each campus (e.g., 'OKC', 'TUL', 'EDM'). Rock > Admin Tools > General Settings > Campuses > Short Code field. Used for abbreviated campus references throughout the system.

### `check_in_type`

- **Type**: STRING
- **Description**: From Rock RMS Attendance.SearchTypeValueId. Attendance level. The method used to check in: 'Phone Number', 'Name', 'Name & Phone', 'Barcode', 'Family Id', or 'Communication Card'. Indicates how the person was identified at check-in.

### `checked_in_timestamp`

- **Type**: DATETIME
- **Description**: From Rock RMS Attendance.CreatedDateTime. Attendance level. The actual timestamp when the check-in record was created in the system. May differ from scheduled time.

### `city`

- **Type**: STRING
- **Description**: From Rock RMS Location. Entity level. The city where the entity is located.

### `country`

- **Type**: STRING
- **Description**: From location.country. Person level. The country of the person's home address. Typically 'US' for most records. Used for international attendee identification.

### `email`

- **Type**: STRING
- **Description**: From Rock RMS Person.email. Person level. The person's primary email address as stored in Rock RMS. May be NULL if no email on file. Used for communication and matching.

### `full_name`

- **Type**: STRING
- **Description**: From Rock RMS Person. Person level. The person's full name constructed as nickname (or first name if no nickname) plus last name. Used for human-readable identification in reports.

### `gender`

- **Type**: STRING
- **Description**: Employee gender from employee.gender. Used for diversity analytics. NULL for requisitions.

### `group_role`

- **Type**: STRING
- **Description**: From Rock RMS GroupMemberHistorical.GroupRoleName via temporal join. Record level. For volunteers: the role at time of serving (e.g., 'Leader', 'Member'). For attenders: The volunteer's role in the group (e.g., leader, helper). Primarily used in LifeKids to track student vs. adult leaders. Due to process issues where people aren't properly deactivated before role changes, this column prioritizes adult roles over student roles when conflicts exist.

### `group_type_id`

- **Type**: INT64
- **Description**: From Rock RMS GroupType.Id. Attendance level. The numeric identifier for the type of group activity. Determines the nature of the attendance record.

### `is_app_check_in`

- **Type**: BOOL
- **Description**: From GroupType.GroupTypePurposeValueId comparison. Attendance level. TRUE when attendance was recorded via the Life.Church mobile app (streak-type check-ins), FALSE for physical location check-ins.

### `is_deceased`

- **Type**: BOOL
- **Description**: From Rock RMS Person.isdeceased. Person level. Boolean flag indicating if the person is marked as deceased in Rock RMS. TRUE if deceased, FALSE if living. Important for data hygiene and filtering.

### `is_first_check_in`

- **Type**: BOOL
- **Description**: Calculated using ROW_NUMBER() window function. Person level. TRUE if this is the person's first attendance record ever (ordered by timestamp), FALSE otherwise. Identifies new attendees.

### `is_first_check_in_at_campus`

- **Type**: BOOL
- **Description**: Calculated using ROW_NUMBER() partitioned by campus_id and is_volunteer_attendance_type. Person-campus-type level. TRUE if this is the person's first check-in of this specific type (attendance OR volunteer) at this campus across all groups. A person will have two separate 'firsts' at each campus - one for their first attendance and one for their first volunteer check-in. Used to identify initial campus engagement for each check-in type separately.

### `is_first_check_in_group`

- **Type**: BOOL
- **Description**: Calculated using ROW_NUMBER() partitioned by attendance_group_name. Person level. TRUE if this is the person's first check-in to this specific room/group.

### `is_first_check_in_group_at_campus`

- **Type**: BOOL
- **Description**: Calculated using ROW_NUMBER() partitioned by attendance_group_name, campus_id, and is_volunteer_attendance_type. Person-campus-group-type level. TRUE if this is the person's first check-in for this specific attendance type (attendance OR volunteer) within this attendance group at this campus. For example, first time volunteering in The Loop at OKC and first time attending The Loop at OKC are tracked separately. Used to track initial engagement with a specific room/team at a campus for each check-in type separately.

### `is_first_check_in_parent_group`

- **Type**: BOOL
- **Description**: Calculated using ROW_NUMBER() partitioned by parent_group_name. Person level. TRUE if this is the person's first check-in to this ministry area (e.g., first time in LifeKids).

### `is_first_check_in_parent_group_at_campus`

- **Type**: BOOL
- **Description**: Calculated using ROW_NUMBER() partitioned by parent_group_name, campus_id, and is_volunteer_attendance_type. Person-campus-ministry-type level. TRUE if this is the person's first check-in for this specific attendance type (attendance OR volunteer) within this parent group at this campus. For example, a person's first Host Team volunteer check-in at EDM would be TRUE, but their later first Host Team attendance check-in at EDM would also be TRUE since they're different types. Used to track initial engagement within a ministry at a specific location for each check-in type separately.

### `is_first_combined_attendance`

- **Type**: BOOL
- **Description**: Calculated using ROW_NUMBER() window function across all records. Person level. TRUE if this is the person's very first check-in of any type (attendance or serving), FALSE otherwise. Identifies when someone first engaged with Life.Church in any capacity.

### `is_last_check_in`

- **Type**: BOOL
- **Description**: Calculated using ROW_NUMBER() DESC window function. Person level. TRUE if this is the person's most recent attendance record, FALSE otherwise. Identifies current engagement state.

### `is_last_check_in_at_campus`

- **Type**: BOOL
- **Description**: Calculated using ROW_NUMBER() DESC partitioned by campus_id and is_volunteer_attendance_type. Person-campus-type level. TRUE if this is the person's most recent check-in of this specific type (attendance OR volunteer) at this campus across all groups. Attendance and volunteer activities maintain separate 'last' records. Used to identify the end of overall campus engagement for each check-in type separately.

### `is_last_check_in_group`

- **Type**: BOOL
- **Description**: Calculated using ROW_NUMBER() DESC partitioned by attendance_group_name. Person level. TRUE if this is the person's most recent check-in to this specific room/group.

### `is_last_check_in_group_at_campus`

- **Type**: BOOL
- **Description**: Calculated using ROW_NUMBER() DESC partitioned by attendance_group_name, campus_id, and is_volunteer_attendance_type. Person-campus-group-type level. TRUE if this is the person's most recent check-in for this specific attendance type (attendance OR volunteer) within this attendance group at this campus. Attendance and volunteer records are evaluated independently. Used to identify the end of engagement with a specific room/team at a campus for each check-in type separately.

### `is_last_check_in_parent_group`

- **Type**: BOOL
- **Description**: Calculated using ROW_NUMBER() DESC partitioned by parent_group_name. Person level. TRUE if this is the person's most recent check-in to this ministry area.

### `is_last_check_in_parent_group_at_campus`

- **Type**: BOOL
- **Description**: Calculated using ROW_NUMBER() DESC partitioned by parent_group_name, campus_id, and is_volunteer_attendance_type. Person-campus-ministry-type level. TRUE if this is the person's most recent check-in for this specific attendance type (attendance OR volunteer) within this parent group at this campus. Tracks separately for attendance vs volunteer - a person could have their last volunteer check-in and later have an attendance check-in, both marked TRUE. Used to identify the end of engagement with a ministry at a location for each check-in type separately.

### `is_last_combined_attendance`

- **Type**: BOOL
- **Description**: Calculated using ROW_NUMBER() DESC window function across all records. Person level. TRUE if this is the person's most recent check-in of any type (attendance or serving), FALSE otherwise. Indicates current engagement status across all activities.

### `is_volunteer_attendance_type`

- **Type**: BOOL
- **Description**: Attendance level. Boolean flag distinguishing volunteer check-ins from regular attendance. Always FALSE in this attender-focused table.

### `lc_week_start_date`

- **Type**: DATE
- **Description**: The Sunday that begins the Life.Church operational week for this date. Data source: Calculated from base Date table with adjustments based on staff portal calendar events. Granularity: Date level. Calculation logic: Standard assignment uses the most recent Sunday; adjusted when ministry events span across Sundays - dates before the Sunday are moved to that Sunday's week. UI location: Staff Portal > Calendar Column purpose: Ensures multi-day events are analyzed as a single unit rather than split across weeks. Data format: DATE.

### `lifekids_smiley_face`

- **Type**: BOOL
- **Description**: Calculated business rule. Attendance level. TRUE when a child returns to LifeKids after 3+ month absence, triggering special welcome. FALSE otherwise. Indicates re-engagement opportunity.

### `next_attendance_at_campus_start_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using LEAD() partitioned by campus_id. Person level. Timestamp of the person's next attendance at this same campus. NULL if last time at campus.

### `next_attendance_campus`

- **Type**: STRING
- **Description**: Calculated using LEAD() window function on campus_short_code. Person level. The campus code where the person will have their next check-in. NULL if this is their last record.

### `next_attendance_group_start_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using LEAD() partitioned by attendance_group_name. Person level. Timestamp of the person's next attendance in the same specific room. NULL if last time.

### `next_attendance_parent_group_start_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using LEAD() partitioned by parent_group_name. Person level. Timestamp of the person's next attendance in the same ministry area. NULL if last time.

### `next_attendance_start_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using LEAD() window function ordered by timestamp. Person level. The timestamp of this person's next check-in of this type. NULL if this is their last record.

### `next_combined_attendance_at_campus_start_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using LEAD() partitioned by campus_id across all check-ins. Person level. Timestamp of the next check-in at this campus for any activity. NULL if this is their last time at this campus.

### `next_combined_attendance_campus`

- **Type**: STRING
- **Description**: Calculated using LEAD() on campus_short_code across all check-ins. Person level. The campus code of the person's next check-in (attendance or serving). NULL if this is their last recorded engagement. Useful for campus migration analysis.

### `next_combined_attendance_group_start_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using LEAD() partitioned by attendance_group_name across all check-ins. Person level. Timestamp of the next check-in in the same specific group/team. NULL if this is their last time in this group.

### `next_combined_attendance_parent_group_start_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using LEAD() partitioned by parent_group_name across all check-ins. Person level. Timestamp of the next check-in in the same ministry area. NULL if this is their last time in this ministry.

### `next_combined_attendance_start_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using LEAD() ordered by timestamp across all check-ins. Person level. Timestamp of the person's next check-in of any type. NULL if this is their last recorded engagement. Used for engagement gap analysis.

### `parent_1_email`

- **Type**: STRING
- **Description**: The email address of the oldest adult in the attendee's family (Parent 1). Provides primary parent/guardian contact information for LifeKids check-ins and family engagement. Sourced from person_basic_info.email. NULL if Parent 1 does not exist or has no email address.

### `parent_1_name`

- **Type**: STRING
- **Description**: The full name of the oldest adult in the attendee's family. Calculated by joining to person_basic_info where family_position = 'Adult', then ranking by age descending within each rms_family_id. Parent 1 is rank 1 (oldest adult). NULL if no adults exist in the family or if the attendee is the only adult.

### `parent_1_phone`

- **Type**: STRING
- **Description**: The phone number of the oldest adult in the attendee's family (Parent 1). Provides primary parent/guardian contact information for LifeKids check-ins and family engagement. Sourced from person_basic_info.phone_number. NULL if Parent 1 does not exist or has no phone number.

### `parent_2_email`

- **Type**: STRING
- **Description**: The email address of the second oldest adult in the attendee's family (Parent 2). Provides secondary parent/guardian contact information for LifeKids check-ins and family engagement. Sourced from person_basic_info.email. NULL if Parent 2 does not exist or has no email address.

### `parent_2_name`

- **Type**: STRING
- **Description**: The full name of the second oldest adult in the attendee's family. Calculated by joining to person_basic_info where family_position = 'Adult', then ranking by age descending within each rms_family_id. Parent 2 is rank 2 (second oldest adult). NULL if fewer than two adults exist in the family.

### `parent_2_phone`

- **Type**: STRING
- **Description**: The phone number of the second oldest adult in the attendee's family (Parent 2). Provides secondary parent/guardian contact information for LifeKids check-ins and family engagement. Sourced from person_basic_info.phone_number. NULL if Parent 2 does not exist or has no phone number.

### `parent_group_id`

- **Type**: INT64
- **Description**: From Rock RMS parent Group.Id. Attendance level. The unique identifier for the parent group/ministry area. Links attendance to broader organizational structure.

### `parent_group_name`

- **Type**: STRING
- **Description**: From Rock RMS parent Group.Name with transformations. Attendance level. The overarching ministry area, normalized from various naming patterns (e.g., 'Switch' from 'switch'/'swerve', 'LifeKids', 'Host Team'). Groups related attendance areas.

### `phone_number`

- **Type**: STRING
- **Description**: The main contact phone number for the individual. Returns NULL if phone number is empty string.

### `postal_code`

- **Type**: STRING
- **Description**: From Rock RMS Location.postalcode. Person level. The ZIP code of the person's home address. Used for geographic analysis and drive time calculations.

### `previous_attendance_at_campus_start_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using LAG() partitioned by campus_id. Person level. Timestamp of the person's previous attendance at this same campus. NULL if first time at campus.

### `previous_attendance_campus`

- **Type**: STRING
- **Description**: Calculated using LAG() window function on campus_short_code. Person level. The campus code where the person had their previous check-in. NULL if first record. Used to track campus movement patterns.

### `previous_attendance_group_start_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using LAG() partitioned by attendance_group_name. Person level. Timestamp of the person's previous attendance in the same specific room. NULL if first time.

### `previous_attendance_parent_group_start_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using LAG() partitioned by parent_group_name. Person level. Timestamp of the person's previous attendance in the same ministry area. NULL if first time. Used for gap analysis.

### `previous_attendance_start_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using LAG() window function ordered by timestamp. Person level. The timestamp of this person's previous check-in of this type (attendance or serving). NULL if this is their first record.

### `previous_combined_attendance_at_campus_start_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using LAG() partitioned by campus_id across all check-ins. Person level. Timestamp of the previous check-in at this campus for any activity type. NULL if first time at this campus. Used for campus-specific engagement tracking.

### `previous_combined_attendance_campus`

- **Type**: STRING
- **Description**: Calculated using LAG() on campus_short_code across all check-ins. Person level. The campus code of the person's previous check-in (attendance or serving). NULL if first engagement. Tracks cross-campus movement patterns.

### `previous_combined_attendance_group_start_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using LAG() partitioned by attendance_group_name across all check-ins. Person level. Timestamp of the previous check-in in the same specific group/team, regardless of attendance or serving. NULL if first time in this group.

### `previous_combined_attendance_parent_group_start_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using LAG() partitioned by parent_group_name across all check-ins. Person level. Timestamp of the previous check-in in the same ministry area, whether attending or serving. NULL if first time in this ministry. Tracks engagement continuity within ministries.

### `previous_combined_attendance_start_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated using LAG() ordered by timestamp across all check-ins. Person level. Timestamp of the person's previous check-in of any type. NULL if this is their first engagement. Key metric for calculating engagement frequency.

### `region`

- **Type**: STRING
- **Description**: From Rock RMS DefinedValue table via Campus Area attribute. Campus level. The geographical region the campus belongs to (e.g., 'Oklahoma', 'Kansas', 'Texas'). Rock > Admin > General Settings > Campuses > Attributes > Campus Area.

### `rms_family_id`

- **Type**: INT64
- **Description**: The primary unique identifier for a family or household in Rock RMS.

### `rms_person_id`

- **Type**: INT64
- **Description**: The unique Rock RMS identifier for the individual. Person-level. Links to Person.Id in Rock RMS. Used to join all person-related data across the system. Rock > Person Profile.

### `schedule_name`

- **Type**: STRING
- **Description**: From Rock RMS Schedule.Name. Attendance level. The descriptive name of the scheduled service time (e.g., 'Sunday 11:30 AM'). Directly from the schedule configuration in Rock.

### `school_grade`

- **Type**: STRING
- **Description**: From Rock RMS DefinedValue lookup based on graduation year. Person level. The current school grade descriptor (e.g., 'Kindergarten', '1st Grade'). Calculated from graduation year and current date.

### `state_province_code`

- **Type**: STRING
- **Description**: From Rock RMS Location.state. Person level. Two-character state/province code of the person's home address (e.g., 'OK', 'TX'). Used for geographic analysis.

