# fact_staff_background

## Columns

Total Columns: 21

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| `background_check_completed_timestamp` | DATE | From Step table. Person level. The date when the person's most recent background check was completed. Used to track expiration and renewal needs. |
| `background_check_status` | STRING | The current status of the person's background check. |
| `campus` | STRING | From Data Warehouse, using Rock person data. Person level. The main, home, primary, or preferred campus of the person. This is the best source for identifing which campus a person belongs to. Rock > Profile > Main Contact Details. |
| `category` | STRING | Employment classification of the person. Values: 'Staff' for Life.Church employees, 'Independent Contractor' for contractors identified through Rock RMS attributes. Used to determine background check requirements and compliance tracking. |
| `email` | STRING | From Rock RMS Person.email. Person level. The person's primary email address as stored in Rock RMS. May be NULL if no email on file. Used for communication and matching. |
| `first_name` | STRING | Employee's legal first name from the employee table. Used for official documentation and reporting. |
| `foreign_key` | STRING | From Rock RMS. External system reference identifier used to link Rock RMS groups to other systems or legacy data sources. May contain identifiers from previous database migrations. |
| `full_name` | STRING | From Rock RMS Person. Person level. The person's full name constructed as nickname (or first name if no nickname) plus last name. Used for human-readable identification in reports. |
| `group_name` | STRING | From Rock RMS Group.Name. The specific ministry group or team name where the staff member or contractor serves. Examples include ministry teams, operational groups, or leadership committees. NULL if person has no group memberships. |
| `group_type` | STRING | From Rock RMS. Entity level. The category or classification of the associated group (e.g., 'Host Team', 'Capacity Volunteer'). |
| `group_type_id` | INT64 | From Rock RMS GroupType.Id. Attendance level. The numeric identifier for the type of group activity. Determines the nature of the attendance record. |
| `home_campus` | STRING | Synonymous with Rock Campus. See lc_campus for description. |
| `is_active` | BOOL | From Rock RMS. Entity level. Boolean flag calculated by checking if entity status of the entity. TRUE indicates an active/open entity state, FALSE indicates inactive/closed. |
| `is_archived` | BOOL | From Rock RMS. Entity level. Boolean flag calculated by checking if entity status of the entity. TRUE indicates an active/open entity state, FALSE indicates archived/closed. |
| `is_leader` | BOOL | From Rock RMS. Entity Level. Boolean flag indicating whether the person's role within the group includes leadership responsibilities. TRUE for leadership positions, FALSE for non-leadership roles. |
| `is_lifegroup_leader` | BOOL | Boolean indicating whether or not the person is a LifeGroup leader. Defaults to FALSE if null. |
| `is_staff` | BOOL | Boolean indicating whether or not the person is a staff member for Life.Church. Defaults to FALSE if null. |
| `last_name` | STRING | From Data Warehouse, using Rock person data. Person level. The last name of the person. Rock > Profile > Main Contact Details. |
| `last_served_timestamp` | TIMESTAMP | From volunteer_check_in table. Person level. The timestamp of the person's most recent volunteer serving check-in across all ministries. Indicates current volunteer engagement. |
| `name` | STRING | From Rock RMS GroupMemberHistorical.GroupRoleName via temporal join. Record level. For volunteers: the role at time of serving (e.g., 'Leader', 'Member'). For attenders: The volunteer's role in the group (e.g., leader, helper). Primarily used in LifeKids to track student vs. adult leaders. Due to process issues where people aren't properly deactivated before role changes, this column prioritizes adult roles over student roles when conflicts exist. |
| `rms_person_id` | INT64 | The unique Rock RMS identifier for the individual. Person-level. Links to Person.Id in Rock RMS. Used to join all person-related data across the system. Rock > Person Profile. |

## Column Details

### `background_check_completed_timestamp`

- **Type**: DATE
- **Description**: From Step table. Person level. The date when the person's most recent background check was completed. Used to track expiration and renewal needs.

### `background_check_status`

- **Type**: STRING
- **Description**: The current status of the person's background check.

### `campus`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock person data. Person level. The main, home, primary, or preferred campus of the person. This is the best source for identifing which campus a person belongs to. Rock > Profile > Main Contact Details.

### `category`

- **Type**: STRING
- **Description**: Employment classification of the person. Values: 'Staff' for Life.Church employees, 'Independent Contractor' for contractors identified through Rock RMS attributes. Used to determine background check requirements and compliance tracking.

### `email`

- **Type**: STRING
- **Description**: From Rock RMS Person.email. Person level. The person's primary email address as stored in Rock RMS. May be NULL if no email on file. Used for communication and matching.

### `first_name`

- **Type**: STRING
- **Description**: Employee's legal first name from the employee table. Used for official documentation and reporting.

### `foreign_key`

- **Type**: STRING
- **Description**: From Rock RMS. External system reference identifier used to link Rock RMS groups to other systems or legacy data sources. May contain identifiers from previous database migrations.

### `full_name`

- **Type**: STRING
- **Description**: From Rock RMS Person. Person level. The person's full name constructed as nickname (or first name if no nickname) plus last name. Used for human-readable identification in reports.

### `group_name`

- **Type**: STRING
- **Description**: From Rock RMS Group.Name. The specific ministry group or team name where the staff member or contractor serves. Examples include ministry teams, operational groups, or leadership committees. NULL if person has no group memberships.

### `group_type`

- **Type**: STRING
- **Description**: From Rock RMS. Entity level. The category or classification of the associated group (e.g., 'Host Team', 'Capacity Volunteer').

### `group_type_id`

- **Type**: INT64
- **Description**: From Rock RMS GroupType.Id. Attendance level. The numeric identifier for the type of group activity. Determines the nature of the attendance record.

### `home_campus`

- **Type**: STRING
- **Description**: Synonymous with Rock Campus. See lc_campus for description.

### `is_active`

- **Type**: BOOL
- **Description**: From Rock RMS. Entity level. Boolean flag calculated by checking if entity status of the entity. TRUE indicates an active/open entity state, FALSE indicates inactive/closed.

### `is_archived`

- **Type**: BOOL
- **Description**: From Rock RMS. Entity level. Boolean flag calculated by checking if entity status of the entity. TRUE indicates an active/open entity state, FALSE indicates archived/closed.

### `is_leader`

- **Type**: BOOL
- **Description**: From Rock RMS. Entity Level. Boolean flag indicating whether the person's role within the group includes leadership responsibilities. TRUE for leadership positions, FALSE for non-leadership roles.

### `is_lifegroup_leader`

- **Type**: BOOL
- **Description**: Boolean indicating whether or not the person is a LifeGroup leader. Defaults to FALSE if null.

### `is_staff`

- **Type**: BOOL
- **Description**: Boolean indicating whether or not the person is a staff member for Life.Church. Defaults to FALSE if null.

### `last_name`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock person data. Person level. The last name of the person. Rock > Profile > Main Contact Details.

### `last_served_timestamp`

- **Type**: TIMESTAMP
- **Description**: From volunteer_check_in table. Person level. The timestamp of the person's most recent volunteer serving check-in across all ministries. Indicates current volunteer engagement.

### `name`

- **Type**: STRING
- **Description**: From Rock RMS GroupMemberHistorical.GroupRoleName via temporal join. Record level. For volunteers: the role at time of serving (e.g., 'Leader', 'Member'). For attenders: The volunteer's role in the group (e.g., leader, helper). Primarily used in LifeKids to track student vs. adult leaders. Due to process issues where people aren't properly deactivated before role changes, this column prioritizes adult roles over student roles when conflicts exist.

### `rms_person_id`

- **Type**: INT64
- **Description**: The unique Rock RMS identifier for the individual. Person-level. Links to Person.Id in Rock RMS. Used to join all person-related data across the system. Rock > Person Profile.

