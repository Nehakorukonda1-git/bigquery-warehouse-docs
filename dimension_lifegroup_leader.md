# dimension_lifegroup_leader

## Columns

Total Columns: 5

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| `is_lifegroup_active` | BOOL | Whether or not the group is currently active. |
| `lifegroup_campus` | STRING | The campus short code each LifeGroup is hosted under. |
| `lifegroup_id` | INT64 | The unique identifier for each LifeGroup, pulled from the Group table. |
| `lifegroup_member_rms_person_id` | INT64 | From Rock group member data. The unique RMS identifier for each person associated with the group. RMS > Profile > Extended Attributes > Person Debug. |
| `lifegroup_member_role` | STRING | From Rock group type role data. The role of each person within the group (e.g., Leader, LGLM Coach). RMS > Groups > Group List. |

## Column Details

### `is_lifegroup_active`

- **Type**: BOOL
- **Description**: Whether or not the group is currently active.

### `lifegroup_campus`

- **Type**: STRING
- **Description**: The campus short code each LifeGroup is hosted under.

### `lifegroup_id`

- **Type**: INT64
- **Description**: The unique identifier for each LifeGroup, pulled from the Group table.

### `lifegroup_member_rms_person_id`

- **Type**: INT64
- **Description**: From Rock group member data. The unique RMS identifier for each person associated with the group. RMS > Profile > Extended Attributes > Person Debug.

### `lifegroup_member_role`

- **Type**: STRING
- **Description**: From Rock group type role data. The role of each person within the group (e.g., Leader, LGLM Coach). RMS > Groups > Group List.

