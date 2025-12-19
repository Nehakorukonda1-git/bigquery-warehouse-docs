# fact_connection_request

## Columns

Total Columns: 48

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| `baptism_dimensions` | STRUCT<service_day_hour STRING, age_of_participant STRING> | From Rock. One of the main connection request types is baptism, which has a very particular set of dimension attributes to it. This struct was created to centralize the attributes in one place when it comes to baptism. |
| `baptism_dimensions.age_of_participant` | STRING | The age group defined at the time of the baptism sign up. |
| `baptism_dimensions.service_day_hour` | STRING | Combined day and time description for easy service identification (e.g., 'Saturday 5:00 PM', 'Sunday 11:30 AM'). Concatenated from day_name_of_week and service_hour. Used as a natural key for service identification in reports and analysis. |
| `campus_code` | STRING | From Data Warehouse, using Rock person data. Person level. The main, home, primary, or preferred campus of the person. This is the best source for identifing which campus a person belongs to. Rock > Profile > Main Contact Details. |
| `connection_opportunity` | STRING | Name of the ministry opportunity requiring span of care. Connection request level. Values include 'LGLM', 'Host Team', etc. Sourced from ConnectionOpportunity.Name. Rock > People > Connections > [Connection Name] > Name. |
| `connection_opportunity_id` | INT64 | Rock RMS identifier linking to the specific ministry opportunity. Connection request level. Foreign key to ConnectionOpportunity.Id. Determines which ministry team this connection belongs to. Rock > People > Connections > [Connection Name] > Check URL. |
| `connection_request_activities` | ARRAY<STRUCT<connection_request_activity_timestamp TIMESTAMP, connection_activity_type_name STRING>> | From Rock. A connection request may have many activities within. This is a convenient struct to list all activities in a connection request. We are keeping this as a struct to preserve the dimension aspect of this table, so that each row is still a connection request. |
| `connection_request_activities.connection_activity_type_name` | STRING | From Rock. The name of the activity. |
| `connection_request_activities.connection_request_activity_timestamp` | TIMESTAMP | From Rock. The timestamp the activity took place. |
| `connection_request_details` | ARRAY<STRUCT<attribute_id INT64, attribute_name STRING, attribute_value STRING>> | From Rock. Connection requests usually have many details attached to them. This is a generic array that contains all details available for each connection request. |
| `connection_request_details.attribute_id` | INT64 | From Rock. The identifier of the attribute. |
| `connection_request_details.attribute_name` | STRING | From Rock. The friendly name of the attribute. |
| `connection_request_details.attribute_value` | STRING | From Rock. The actual value of the attribute. Sometimes it might require an additional join to get the value behind a GUID. |
| `connection_request_id` | INT64 | Unique Rock RMS identifier for the connection request. Connection request level. Primary key from ConnectionRequest.Id. Used to join activity and status data. Rock > People > Connections > [Connection Name] > Details. |
| `connection_state` | STRING | Workflow state of the connection. Connection request level. Values: 0 (Active), 1 (Inactive), 2 (FutureFollowUp), 3 (Connected). Numeric representation of connection progress. Filtered to exclude active state (value 2). Rock > People > Connections > State. |
| `connection_state_id` | INT64 | Workflow state of the connection. Connection request level. Values: 0 (Active), 1 (Inactive), 2 (FutureFollowUp), 3 (Connected). Numeric representation of connection progress. Filtered to exclude active state (value 2). Rock > People > Connections > State. |
| `connection_status` | STRING | Current workflow status of the connection request. Connection request level. Examples: 'New', 'In Progress', 'Connected', 'Follow Up Needed'. Sourced from ConnectionStatus.Name. Indicates where the request is in the follow-up process. Rock > People > Connections > [Connection Name] > Status. |
| `connection_status_id` | INT64 | Rock RMS identifier for the connection status. Connection request level. Foreign key to ConnectionStatus.Id. Used for status-based filtering and reporting. Rock > People > Connections > Status. |
| `connection_type` | STRING | The connection category in Rock RMS. Connection request level. Always 'Span of Care' for this view. Sourced from ConnectionType.Name. Filtered to only include Span of Care type connections. Rock > Admin > General Settings > Connection Types. |
| `connection_type_id` | INT64 | The connection category in Rock RMS. Connection request level. Always 'Span of Care' for this view. Sourced from ConnectionType.Name. Filtered to only include Span of Care type connections. Rock > Admin > General Settings > Connection Types. |
| `connector_name` | STRING | From Rock RMS Person. Person level. The person's full name constructed as nickname (or first name if no nickname) plus last name. Used for human-readable identification in reports. |
| `connector_person_alias_id` | INT64 | Rock RMS PersonAlias identifier for the connector. Connection request level. Links to PersonAlias.Id. Internal identifier used for Rock RMS person merging. Rock > People > Connections > [Connection Name] > Connector > Extended Attributes. |
| `connector_person_id` | INT64 | Rock RMS Person ID of the person assigned to connect. Person level. Links to Person.Id via ConnectorPersonAliasId. The individual responsible for follow-up. Rock > People > Connections > [Request] > Connector. |
| `created_timestamp` | TIMESTAMP | When the event or entity was initially created. Event or entity level. Format: YYYY-MM-DD HH:MM:SS. |
| `followup_date` | DATE | Target date for next connection follow-up. Connection request level. Calculated as COALESCE of FollowupDate, future follow-up activity, or created date. Format: YYYY-MM-DD. Used for prioritizing connector outreach. Rock > People > Connections > [Connection Name] > Details. |
| `international_background_check_process` | STRUCT<first_reference_contact_timestamp TIMESTAMP, first_reference_pending_timestamp TIMESTAMP, first_reference_review_timestamp TIMESTAMP, first_reference_unresponsive_timestamp TIMESTAMP, first_interview_pending_timestamp TIMESTAMP, first_interview_review_timestamp TIMESTAMP, first_interview_unresponsive_timestamp TIMESTAMP, last_reference_contact_timestamp TIMESTAMP, last_reference_pending_timestamp TIMESTAMP, last_reference_review_timestamp TIMESTAMP, last_reference_unresponsive_timestamp TIMESTAMP, last_interview_pending_timestamp TIMESTAMP, last_interview_review_timestamp TIMESTAMP, last_interview_unresponsive_timestamp TIMESTAMP> | From Rock. The steps for an international person/volunteer to get their background check. Rock > Life.Church Online > Volunteer Onboarding > International BGC Process. |
| `international_background_check_process.first_interview_pending_timestamp` | TIMESTAMP | From Rock RMS ConnectionRequestActivity table. Person-step level. The earliest timestamp when the international background check connection request reached this step. Uses MIN aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process. |
| `international_background_check_process.first_interview_review_timestamp` | TIMESTAMP | From Rock RMS ConnectionRequestActivity table. Person-step level. The earliest timestamp when the international background check connection request reached this step. Uses MIN aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process. |
| `international_background_check_process.first_interview_unresponsive_timestamp` | TIMESTAMP | From Rock RMS ConnectionRequestActivity table. Person-step level. The earliest timestamp when the international background check connection request reached this step. Uses MIN aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process. |
| `international_background_check_process.first_reference_contact_timestamp` | TIMESTAMP | From Rock RMS ConnectionRequestActivity table. Person-step level. The earliest timestamp when the international background check connection request reached this step. Uses MIN aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process. |
| `international_background_check_process.first_reference_pending_timestamp` | TIMESTAMP | From Rock RMS ConnectionRequestActivity table. Person-step level. The earliest timestamp when the international background check connection request reached this step. Uses MIN aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process. |
| `international_background_check_process.first_reference_review_timestamp` | TIMESTAMP | From Rock RMS ConnectionRequestActivity table. Person-step level. The earliest timestamp when the international background check connection request reached this step. Uses MIN aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process. |
| `international_background_check_process.first_reference_unresponsive_timestamp` | TIMESTAMP | From Rock RMS ConnectionRequestActivity table. Person-step level. The earliest timestamp when the international background check connection request reached this step. Uses MIN aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process. |
| `international_background_check_process.last_interview_pending_timestamp` | TIMESTAMP | From Rock RMS ConnectionRequestActivity table. Person-step level. The latest timestamp when the international background check connection request reached this step. Uses MAX aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process. |
| `international_background_check_process.last_interview_review_timestamp` | TIMESTAMP | From Rock RMS ConnectionRequestActivity table. Person-step level. The latest timestamp when the international background check connection request reached this step. Uses MAX aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process. |
| `international_background_check_process.last_interview_unresponsive_timestamp` | TIMESTAMP | From Rock RMS ConnectionRequestActivity table. Person-step level. The latest timestamp when the international background check connection request reached this step. Uses MAX aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process. |
| `international_background_check_process.last_reference_contact_timestamp` | TIMESTAMP | From Rock RMS ConnectionRequestActivity table. Person-step level. The latest timestamp when the international background check connection request reached this step. Uses MAX aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process. |
| `international_background_check_process.last_reference_pending_timestamp` | TIMESTAMP | From Rock RMS ConnectionRequestActivity table. Person-step level. The latest timestamp when the international background check connection request reached this step. Uses MAX aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process. |
| `international_background_check_process.last_reference_review_timestamp` | TIMESTAMP | From Rock RMS ConnectionRequestActivity table. Person-step level. The latest timestamp when the international background check connection request reached this step. Uses MAX aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process. |
| `international_background_check_process.last_reference_unresponsive_timestamp` | TIMESTAMP | From Rock RMS ConnectionRequestActivity table. Person-step level. The latest timestamp when the international background check connection request reached this step. Uses MAX aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process. |
| `last_activity_date` | DATETIME | Most recent activity timestamp on this connection. Connection request level. Sourced from ConnectionRequestActivity.CreatedDateTime. NULL if no activities recorded. Format: YYYY-MM-DD HH:MM:SS. Rock > People > Connections > [Request] > Activities. |
| `modified_timestamp` | TIMESTAMP | Last modification timestamp for the event or entity. Event or entity level. ModifiedDateTime. Format: YYYY-MM-DD HH:MM:SS. |
| `referrer` | STRING | From Rock RMS AttributeValue for 'Referrer' attribute or derived logic. Request level. Identifies who or what referred the person to submit this request. Returns 'Physical Communication Card' when created by someone else on behalf of the requestor. NULL if self-submitted digitally. Rock > People > Connections Requests. |
| `region` | STRING | From Rock RMS DefinedValue table via Campus Area attribute. Campus level. The geographical region the campus belongs to (e.g., 'Oklahoma', 'Kansas', 'Texas'). Rock > Admin > General Settings > Campuses > Attributes > Campus Area. |
| `requestor_email` | STRING | The main contact phone number for the individual. Returns NULL if phone number is empty string. |
| `requestor_name` | STRING | From Rock RMS Person. Person level. The person's full name constructed as nickname (or first name if no nickname) plus last name. Used for human-readable identification in reports. |
| `requestor_person_id` | INT64 | Rock RMS Person ID of the requestor. Person level. Links to Person.Id.Rock > Person Profile > Check URL |
| `requestor_phone_number` | STRING | The main contact phone number for the individual. Returns NULL if phone number is empty string. |

## Column Details

### `baptism_dimensions`

- **Type**: STRUCT<service_day_hour STRING, age_of_participant STRING>
- **Description**: From Rock. One of the main connection request types is baptism, which has a very particular set of dimension attributes to it. This struct was created to centralize the attributes in one place when it comes to baptism.

### `baptism_dimensions.age_of_participant`

- **Type**: STRING
- **Description**: The age group defined at the time of the baptism sign up.

### `baptism_dimensions.service_day_hour`

- **Type**: STRING
- **Description**: Combined day and time description for easy service identification (e.g., 'Saturday 5:00 PM', 'Sunday 11:30 AM'). Concatenated from day_name_of_week and service_hour. Used as a natural key for service identification in reports and analysis.

### `campus_code`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock person data. Person level. The main, home, primary, or preferred campus of the person. This is the best source for identifing which campus a person belongs to. Rock > Profile > Main Contact Details.

### `connection_opportunity`

- **Type**: STRING
- **Description**: Name of the ministry opportunity requiring span of care. Connection request level. Values include 'LGLM', 'Host Team', etc. Sourced from ConnectionOpportunity.Name. Rock > People > Connections > [Connection Name] > Name.

### `connection_opportunity_id`

- **Type**: INT64
- **Description**: Rock RMS identifier linking to the specific ministry opportunity. Connection request level. Foreign key to ConnectionOpportunity.Id. Determines which ministry team this connection belongs to. Rock > People > Connections > [Connection Name] > Check URL.

### `connection_request_activities`

- **Type**: ARRAY<STRUCT<connection_request_activity_timestamp TIMESTAMP, connection_activity_type_name STRING>>
- **Description**: From Rock. A connection request may have many activities within. This is a convenient struct to list all activities in a connection request. We are keeping this as a struct to preserve the dimension aspect of this table, so that each row is still a connection request.

### `connection_request_activities.connection_activity_type_name`

- **Type**: STRING
- **Description**: From Rock. The name of the activity.

### `connection_request_activities.connection_request_activity_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock. The timestamp the activity took place.

### `connection_request_details`

- **Type**: ARRAY<STRUCT<attribute_id INT64, attribute_name STRING, attribute_value STRING>>
- **Description**: From Rock. Connection requests usually have many details attached to them. This is a generic array that contains all details available for each connection request.

### `connection_request_details.attribute_id`

- **Type**: INT64
- **Description**: From Rock. The identifier of the attribute.

### `connection_request_details.attribute_name`

- **Type**: STRING
- **Description**: From Rock. The friendly name of the attribute.

### `connection_request_details.attribute_value`

- **Type**: STRING
- **Description**: From Rock. The actual value of the attribute. Sometimes it might require an additional join to get the value behind a GUID.

### `connection_request_id`

- **Type**: INT64
- **Description**: Unique Rock RMS identifier for the connection request. Connection request level. Primary key from ConnectionRequest.Id. Used to join activity and status data. Rock > People > Connections > [Connection Name] > Details.

### `connection_state`

- **Type**: STRING
- **Description**: Workflow state of the connection. Connection request level. Values: 0 (Active), 1 (Inactive), 2 (FutureFollowUp), 3 (Connected). Numeric representation of connection progress. Filtered to exclude active state (value 2). Rock > People > Connections > State.

### `connection_state_id`

- **Type**: INT64
- **Description**: Workflow state of the connection. Connection request level. Values: 0 (Active), 1 (Inactive), 2 (FutureFollowUp), 3 (Connected). Numeric representation of connection progress. Filtered to exclude active state (value 2). Rock > People > Connections > State.

### `connection_status`

- **Type**: STRING
- **Description**: Current workflow status of the connection request. Connection request level. Examples: 'New', 'In Progress', 'Connected', 'Follow Up Needed'. Sourced from ConnectionStatus.Name. Indicates where the request is in the follow-up process. Rock > People > Connections > [Connection Name] > Status.

### `connection_status_id`

- **Type**: INT64
- **Description**: Rock RMS identifier for the connection status. Connection request level. Foreign key to ConnectionStatus.Id. Used for status-based filtering and reporting. Rock > People > Connections > Status.

### `connection_type`

- **Type**: STRING
- **Description**: The connection category in Rock RMS. Connection request level. Always 'Span of Care' for this view. Sourced from ConnectionType.Name. Filtered to only include Span of Care type connections. Rock > Admin > General Settings > Connection Types.

### `connection_type_id`

- **Type**: INT64
- **Description**: The connection category in Rock RMS. Connection request level. Always 'Span of Care' for this view. Sourced from ConnectionType.Name. Filtered to only include Span of Care type connections. Rock > Admin > General Settings > Connection Types.

### `connector_name`

- **Type**: STRING
- **Description**: From Rock RMS Person. Person level. The person's full name constructed as nickname (or first name if no nickname) plus last name. Used for human-readable identification in reports.

### `connector_person_alias_id`

- **Type**: INT64
- **Description**: Rock RMS PersonAlias identifier for the connector. Connection request level. Links to PersonAlias.Id. Internal identifier used for Rock RMS person merging. Rock > People > Connections > [Connection Name] > Connector > Extended Attributes.

### `connector_person_id`

- **Type**: INT64
- **Description**: Rock RMS Person ID of the person assigned to connect. Person level. Links to Person.Id via ConnectorPersonAliasId. The individual responsible for follow-up. Rock > People > Connections > [Request] > Connector.

### `created_timestamp`

- **Type**: TIMESTAMP
- **Description**: When the event or entity was initially created. Event or entity level. Format: YYYY-MM-DD HH:MM:SS.

### `followup_date`

- **Type**: DATE
- **Description**: Target date for next connection follow-up. Connection request level. Calculated as COALESCE of FollowupDate, future follow-up activity, or created date. Format: YYYY-MM-DD. Used for prioritizing connector outreach. Rock > People > Connections > [Connection Name] > Details.

### `international_background_check_process`

- **Type**: STRUCT<first_reference_contact_timestamp TIMESTAMP, first_reference_pending_timestamp TIMESTAMP, first_reference_review_timestamp TIMESTAMP, first_reference_unresponsive_timestamp TIMESTAMP, first_interview_pending_timestamp TIMESTAMP, first_interview_review_timestamp TIMESTAMP, first_interview_unresponsive_timestamp TIMESTAMP, last_reference_contact_timestamp TIMESTAMP, last_reference_pending_timestamp TIMESTAMP, last_reference_review_timestamp TIMESTAMP, last_reference_unresponsive_timestamp TIMESTAMP, last_interview_pending_timestamp TIMESTAMP, last_interview_review_timestamp TIMESTAMP, last_interview_unresponsive_timestamp TIMESTAMP>
- **Description**: From Rock. The steps for an international person/volunteer to get their background check. Rock > Life.Church Online > Volunteer Onboarding > International BGC Process.

### `international_background_check_process.first_interview_pending_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS ConnectionRequestActivity table. Person-step level. The earliest timestamp when the international background check connection request reached this step. Uses MIN aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process.

### `international_background_check_process.first_interview_review_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS ConnectionRequestActivity table. Person-step level. The earliest timestamp when the international background check connection request reached this step. Uses MIN aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process.

### `international_background_check_process.first_interview_unresponsive_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS ConnectionRequestActivity table. Person-step level. The earliest timestamp when the international background check connection request reached this step. Uses MIN aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process.

### `international_background_check_process.first_reference_contact_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS ConnectionRequestActivity table. Person-step level. The earliest timestamp when the international background check connection request reached this step. Uses MIN aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process.

### `international_background_check_process.first_reference_pending_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS ConnectionRequestActivity table. Person-step level. The earliest timestamp when the international background check connection request reached this step. Uses MIN aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process.

### `international_background_check_process.first_reference_review_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS ConnectionRequestActivity table. Person-step level. The earliest timestamp when the international background check connection request reached this step. Uses MIN aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process.

### `international_background_check_process.first_reference_unresponsive_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS ConnectionRequestActivity table. Person-step level. The earliest timestamp when the international background check connection request reached this step. Uses MIN aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process.

### `international_background_check_process.last_interview_pending_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS ConnectionRequestActivity table. Person-step level. The latest timestamp when the international background check connection request reached this step. Uses MAX aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process.

### `international_background_check_process.last_interview_review_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS ConnectionRequestActivity table. Person-step level. The latest timestamp when the international background check connection request reached this step. Uses MAX aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process.

### `international_background_check_process.last_interview_unresponsive_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS ConnectionRequestActivity table. Person-step level. The latest timestamp when the international background check connection request reached this step. Uses MAX aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process.

### `international_background_check_process.last_reference_contact_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS ConnectionRequestActivity table. Person-step level. The latest timestamp when the international background check connection request reached this step. Uses MAX aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process.

### `international_background_check_process.last_reference_pending_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS ConnectionRequestActivity table. Person-step level. The latest timestamp when the international background check connection request reached this step. Uses MAX aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process.

### `international_background_check_process.last_reference_review_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS ConnectionRequestActivity table. Person-step level. The latest timestamp when the international background check connection request reached this step. Uses MAX aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process.

### `international_background_check_process.last_reference_unresponsive_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS ConnectionRequestActivity table. Person-step level. The latest timestamp when the international background check connection request reached this step. Uses MAX aggregation when multiple occurrences exist. Connection requests can revisit steps and may skip certain steps in the process.  Rock > Life.Church Online > Volunteer Onboarding > International BGC Process.

### `last_activity_date`

- **Type**: DATETIME
- **Description**: Most recent activity timestamp on this connection. Connection request level. Sourced from ConnectionRequestActivity.CreatedDateTime. NULL if no activities recorded. Format: YYYY-MM-DD HH:MM:SS. Rock > People > Connections > [Request] > Activities.

### `modified_timestamp`

- **Type**: TIMESTAMP
- **Description**: Last modification timestamp for the event or entity. Event or entity level. ModifiedDateTime. Format: YYYY-MM-DD HH:MM:SS.

### `referrer`

- **Type**: STRING
- **Description**: From Rock RMS AttributeValue for 'Referrer' attribute or derived logic. Request level. Identifies who or what referred the person to submit this request. Returns 'Physical Communication Card' when created by someone else on behalf of the requestor. NULL if self-submitted digitally. Rock > People > Connections Requests.

### `region`

- **Type**: STRING
- **Description**: From Rock RMS DefinedValue table via Campus Area attribute. Campus level. The geographical region the campus belongs to (e.g., 'Oklahoma', 'Kansas', 'Texas'). Rock > Admin > General Settings > Campuses > Attributes > Campus Area.

### `requestor_email`

- **Type**: STRING
- **Description**: The main contact phone number for the individual. Returns NULL if phone number is empty string.

### `requestor_name`

- **Type**: STRING
- **Description**: From Rock RMS Person. Person level. The person's full name constructed as nickname (or first name if no nickname) plus last name. Used for human-readable identification in reports.

### `requestor_person_id`

- **Type**: INT64
- **Description**: Rock RMS Person ID of the requestor. Person level. Links to Person.Id.Rock > Person Profile > Check URL

### `requestor_phone_number`

- **Type**: STRING
- **Description**: The main contact phone number for the individual. Returns NULL if phone number is empty string.

