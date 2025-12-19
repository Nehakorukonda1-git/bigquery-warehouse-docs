# fact_lifegroup_pending_prospect

## Columns

Total Columns: 23

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| `lifegroup_archived_timestamp` | TIMESTAMP | The timestamp the LifeGroup was archived in Rock, if applicable. |
| `lifegroup_campus` | STRING | The campus short code each LifeGroup is hosted under. |
| `lifegroup_connection_request_completed_timestamp` | TIMESTAMP | The timestamp the connection request was completed, when the pastor or volunteer indicates that the person has been followed up with and hits 'Connected'. |
| `lifegroup_connection_request_created_timestamp` | TIMESTAMP | The timestamp the connection request was created, either automatically by the person submitting an interest form or manually by a pastor adding the information to Rock. |
| `lifegroup_connection_request_id` | INT64 | The unique identifier for the connection request that was initiated after the person submitted LifeGroup interest. The connection request is a process for the pastor or volunteer to follow up with any attender initiated actions. |
| `lifegroup_connection_request_status` | STRING | The status of the connection request, whether or not the person has been followed up with by a pastor or volunteer. |
| `lifegroup_created_timestamp` | TIMESTAMP | The timestamp the LifeGroup was created in Rock. |
| `lifegroup_id` | INT64 | The unique identifier for each LifeGroup, pulled from the Group table. |
| `lifegroup_inactive_timestamp` | TIMESTAMP | The timestamp the LifeGroup was most recently marked as inactive in Rock. |
| `lifegroup_leader_email` | STRING | The email of the primary individual who is leading the LifeGroup. |
| `lifegroup_leader_name` | STRING | The full name of the primary individual who is leading the LifeGroup. |
| `lifegroup_leader_phone` | STRING | The phone number of the primary individual who is leading the LifeGroup. |
| `lifegroup_leader_rms_person_id` | INT64 | The Rock person ID of the primary individual who is leading the LifeGroup. |
| `lifegroup_member_active_timestamp` | TIMESTAMP | The timestamp the person most recently was marked as 'active' in that LifeGroup by a group leader or pastor. |
| `lifegroup_member_id` | INT64 | The unique identifier for the individual in each LifeGroup. |
| `lifegroup_member_inactive_timestamp` | TIMESTAMP | The timestamp the person most recently was marked as 'inavtive' in that LifeGroup by a group leader or pastor. |
| `lifegroup_member_pending_timestamp` | TIMESTAMP | The timestamp the person was first marked as 'pending' in that LifeGroup by initiating interest in the group. |
| `lifegroup_member_status` | STRING | The current group member status (Pending, Active, Inactive) of the person in the group. Can apply to leaders and prospects. |
| `lifegroup_name` | STRING | The friendly name of the LifeGroup. |
| `lifegroup_prospect_email` | STRING | The email of the individual who is wanting to join the LifeGroup as a member or prospect. |
| `lifegroup_prospect_name` | STRING | The full name of the individual who is wanting to join the LifeGroup as a member or prospect. |
| `lifegroup_prospect_phone` | STRING | The phone number of the individual who is wanting to join the LifeGroup as a member or prospect. |
| `lifegroup_prospect_rms_person_id` | INT64 | The Rock person ID of the individual who is wanting to join the LifeGroup as a member or prospect. |

## Column Details

### `lifegroup_archived_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp the LifeGroup was archived in Rock, if applicable.

### `lifegroup_campus`

- **Type**: STRING
- **Description**: The campus short code each LifeGroup is hosted under.

### `lifegroup_connection_request_completed_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp the connection request was completed, when the pastor or volunteer indicates that the person has been followed up with and hits 'Connected'.

### `lifegroup_connection_request_created_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp the connection request was created, either automatically by the person submitting an interest form or manually by a pastor adding the information to Rock.

### `lifegroup_connection_request_id`

- **Type**: INT64
- **Description**: The unique identifier for the connection request that was initiated after the person submitted LifeGroup interest. The connection request is a process for the pastor or volunteer to follow up with any attender initiated actions.

### `lifegroup_connection_request_status`

- **Type**: STRING
- **Description**: The status of the connection request, whether or not the person has been followed up with by a pastor or volunteer.

### `lifegroup_created_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp the LifeGroup was created in Rock.

### `lifegroup_id`

- **Type**: INT64
- **Description**: The unique identifier for each LifeGroup, pulled from the Group table.

### `lifegroup_inactive_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp the LifeGroup was most recently marked as inactive in Rock.

### `lifegroup_leader_email`

- **Type**: STRING
- **Description**: The email of the primary individual who is leading the LifeGroup.

### `lifegroup_leader_name`

- **Type**: STRING
- **Description**: The full name of the primary individual who is leading the LifeGroup.

### `lifegroup_leader_phone`

- **Type**: STRING
- **Description**: The phone number of the primary individual who is leading the LifeGroup.

### `lifegroup_leader_rms_person_id`

- **Type**: INT64
- **Description**: The Rock person ID of the primary individual who is leading the LifeGroup.

### `lifegroup_member_active_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp the person most recently was marked as 'active' in that LifeGroup by a group leader or pastor.

### `lifegroup_member_id`

- **Type**: INT64
- **Description**: The unique identifier for the individual in each LifeGroup.

### `lifegroup_member_inactive_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp the person most recently was marked as 'inavtive' in that LifeGroup by a group leader or pastor.

### `lifegroup_member_pending_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp the person was first marked as 'pending' in that LifeGroup by initiating interest in the group.

### `lifegroup_member_status`

- **Type**: STRING
- **Description**: The current group member status (Pending, Active, Inactive) of the person in the group. Can apply to leaders and prospects.

### `lifegroup_name`

- **Type**: STRING
- **Description**: The friendly name of the LifeGroup.

### `lifegroup_prospect_email`

- **Type**: STRING
- **Description**: The email of the individual who is wanting to join the LifeGroup as a member or prospect.

### `lifegroup_prospect_name`

- **Type**: STRING
- **Description**: The full name of the individual who is wanting to join the LifeGroup as a member or prospect.

### `lifegroup_prospect_phone`

- **Type**: STRING
- **Description**: The phone number of the individual who is wanting to join the LifeGroup as a member or prospect.

### `lifegroup_prospect_rms_person_id`

- **Type**: INT64
- **Description**: The Rock person ID of the individual who is wanting to join the LifeGroup as a member or prospect.

