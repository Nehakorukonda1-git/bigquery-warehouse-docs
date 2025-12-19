# dimension_lifegroup

## Columns

Total Columns: 27

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| `is_lifegroup_active` | BOOL | Whether or not the group is currently active. |
| `is_lifegroup_archived` | BOOL | Whether or not the LifeGroup has been archived. |
| `is_lifegroup_data_warehouse_active` | BOOL | From Rock RMS Group and _lc_lifegroup tables. LifeGroup level. Boolean flag indicating if the LifeGroup is currently active and not archived in the data warehouse perspective. TRUE when both IsActive=TRUE and IsArchived=FALSE, FALSE otherwise. This provides a single field to determine if a LifeGroup is operationally active for reporting purposes. |
| `is_lifegroup_mentoring` | BOOL | Whether or not the LifeGroup is a 1:1 mentoring LifeGroup. |
| `is_lifegroup_public` | BOOL | Whether or not the LifeGroup is currently marked as public. If FALSE then this LifeGroup will not appear on the LifeGroup search tool nor any campus Info walls since they are no longer accepting additional members at this time. |
| `is_lifegroup_short_term` | BOOL | Whether or not the LifeGroup is a temporary or short-term group (ex: Sister's content LifeGroups). |
| `lifegroup_age_range_end` | INT64 | The oldest age allowed in the LifeGroup. |
| `lifegroup_age_range_start` | INT64 | The youngest age allowed in the LifeGroup. |
| `lifegroup_archived_timestamp` | TIMESTAMP | The timestamp the LifeGroup was archived in Rock, if applicable. |
| `lifegroup_campus` | STRING | The campus short code each LifeGroup is hosted under. |
| `lifegroup_campus_region` | STRING | The campus region each LifeGroup is hosted under. |
| `lifegroup_children_allowed` | STRING | Whether or not children are allowed in the LifeGroup. |
| `lifegroup_created_timestamp` | TIMESTAMP | The timestamp the LifeGroup was created in Rock. |
| `lifegroup_data_warehouse_inactive_timestamp` | DATETIME | From Rock RMS Group table. LifeGroup level. The earliest timestamp when the LifeGroup became inactive or archived, calculated using LEAST function between archiveddatetime and inactivedatetime. Represents when the group stopped being operationally active, regardless of whether it was formally archived or just marked inactive. NULL if group is still active. |
| `lifegroup_day_of_week` | STRING | The day of the week the LifeGroup meets. |
| `lifegroup_description` | STRING | The description of the purpose of the LifeGroup. |
| `lifegroup_genders` | STRING | The lifegroup_genders allowed in the LifeGroup. |
| `lifegroup_id` | INT64 | The unique identifier for each LifeGroup, pulled from the Group table. |
| `lifegroup_inactivated_reason` | STRING | If the group is not active, the official reason of why were they marked as inactive. |
| `lifegroup_inactivated_reason_note` | STRING | Additional notes on why the group was marked as inactive. |
| `lifegroup_inactive_timestamp` | TIMESTAMP | The timestamp the LifeGroup was most recently marked as inactive in Rock. |
| `lifegroup_name` | STRING | The friendly name of the LifeGroup. |
| `lifegroup_number_of_members` | INT64 | The number of members (prospects and leaders) in each group. |
| `lifegroup_season_of_life` | STRING | The general season of life the LifeGroup will host and cater towards. |
| `lifegroup_time_of_day` | STRING | The time of day the LifeGroup meets. |
| `lifegroup_topic` | STRING | The general lifegroup_topic(s) the LifeGroup will discuss. |
| `lifegroup_type` | STRING | The categorical type of LifeGroup represented. |

## Column Details

### `is_lifegroup_active`

- **Type**: BOOL
- **Description**: Whether or not the group is currently active.

### `is_lifegroup_archived`

- **Type**: BOOL
- **Description**: Whether or not the LifeGroup has been archived.

### `is_lifegroup_data_warehouse_active`

- **Type**: BOOL
- **Description**: From Rock RMS Group and _lc_lifegroup tables. LifeGroup level. Boolean flag indicating if the LifeGroup is currently active and not archived in the data warehouse perspective. TRUE when both IsActive=TRUE and IsArchived=FALSE, FALSE otherwise. This provides a single field to determine if a LifeGroup is operationally active for reporting purposes.

### `is_lifegroup_mentoring`

- **Type**: BOOL
- **Description**: Whether or not the LifeGroup is a 1:1 mentoring LifeGroup.

### `is_lifegroup_public`

- **Type**: BOOL
- **Description**: Whether or not the LifeGroup is currently marked as public. If FALSE then this LifeGroup will not appear on the LifeGroup search tool nor any campus Info walls since they are no longer accepting additional members at this time.

### `is_lifegroup_short_term`

- **Type**: BOOL
- **Description**: Whether or not the LifeGroup is a temporary or short-term group (ex: Sister's content LifeGroups).

### `lifegroup_age_range_end`

- **Type**: INT64
- **Description**: The oldest age allowed in the LifeGroup.

### `lifegroup_age_range_start`

- **Type**: INT64
- **Description**: The youngest age allowed in the LifeGroup.

### `lifegroup_archived_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp the LifeGroup was archived in Rock, if applicable.

### `lifegroup_campus`

- **Type**: STRING
- **Description**: The campus short code each LifeGroup is hosted under.

### `lifegroup_campus_region`

- **Type**: STRING
- **Description**: The campus region each LifeGroup is hosted under.

### `lifegroup_children_allowed`

- **Type**: STRING
- **Description**: Whether or not children are allowed in the LifeGroup.

### `lifegroup_created_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp the LifeGroup was created in Rock.

### `lifegroup_data_warehouse_inactive_timestamp`

- **Type**: DATETIME
- **Description**: From Rock RMS Group table. LifeGroup level. The earliest timestamp when the LifeGroup became inactive or archived, calculated using LEAST function between archiveddatetime and inactivedatetime. Represents when the group stopped being operationally active, regardless of whether it was formally archived or just marked inactive. NULL if group is still active.

### `lifegroup_day_of_week`

- **Type**: STRING
- **Description**: The day of the week the LifeGroup meets.

### `lifegroup_description`

- **Type**: STRING
- **Description**: The description of the purpose of the LifeGroup.

### `lifegroup_genders`

- **Type**: STRING
- **Description**: The lifegroup_genders allowed in the LifeGroup.

### `lifegroup_id`

- **Type**: INT64
- **Description**: The unique identifier for each LifeGroup, pulled from the Group table.

### `lifegroup_inactivated_reason`

- **Type**: STRING
- **Description**: If the group is not active, the official reason of why were they marked as inactive.

### `lifegroup_inactivated_reason_note`

- **Type**: STRING
- **Description**: Additional notes on why the group was marked as inactive.

### `lifegroup_inactive_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp the LifeGroup was most recently marked as inactive in Rock.

### `lifegroup_name`

- **Type**: STRING
- **Description**: The friendly name of the LifeGroup.

### `lifegroup_number_of_members`

- **Type**: INT64
- **Description**: The number of members (prospects and leaders) in each group.

### `lifegroup_season_of_life`

- **Type**: STRING
- **Description**: The general season of life the LifeGroup will host and cater towards.

### `lifegroup_time_of_day`

- **Type**: STRING
- **Description**: The time of day the LifeGroup meets.

### `lifegroup_topic`

- **Type**: STRING
- **Description**: The general lifegroup_topic(s) the LifeGroup will discuss.

### `lifegroup_type`

- **Type**: STRING
- **Description**: The categorical type of LifeGroup represented.

