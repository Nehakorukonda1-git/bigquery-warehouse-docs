# fact_household_giving_journey

## Columns

Total Columns: 8

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| `campus_short_code` | STRING | From Data Warehouse, using Rock person data. Person level. The main, home, primary, or preferred campus of the person. This is the best source for identifing which campus a person belongs to. Rock > Profile > Main Contact Details. |
| `current_month_campuses` | STRING | From inc_giving aggregation. Comma-separated list of all campuses the household gave to in the current month. NULL = no giving anywhere. Used to identify migration patterns. |
| `gave_previous_month_same_campus` | BOOL | Calculated using LAG function. Boolean indicating if household gave to this same campus in the prior month. Used to identify consistent vs returning givers. |
| `gave_this_month` | BOOL | From inc_giving. Boolean calculated by checking if household has any transactions at this campus in month_date. TRUE = gave, FALSE = didn't give. |
| `giver_status` | STRING | Calculated classification based on giving pattern logic. Values: 'New Giver' (first gift ever), 'Consistent Giver' (gave both months same campus), 'Returning Giver' (gave after missing), 'Lapsed Giver' (stopped giving), 'Migrated In Giver' (started at new campus), 'Migrated Out Giver' (moved to different campus), NULL (no status change). |
| `month_date` | DATE | Calculated field. The first day of each month from household's first gift date to current month. |
| `previous_month_campuses` | STRING | From inc_giving aggregation. Comma-separated list of all campuses the household gave to in the previous month. NULL = no giving anywhere. |
| `rms_primary_family_id` | INT64 | From Rock RMS Person.PrimaryFamilyId. Person-level. Duplicate of rms_family_id for compatibility. Rock > Person Profile > Family. |

## Column Details

### `campus_short_code`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock person data. Person level. The main, home, primary, or preferred campus of the person. This is the best source for identifing which campus a person belongs to. Rock > Profile > Main Contact Details.

### `current_month_campuses`

- **Type**: STRING
- **Description**: From inc_giving aggregation. Comma-separated list of all campuses the household gave to in the current month. NULL = no giving anywhere. Used to identify migration patterns.

### `gave_previous_month_same_campus`

- **Type**: BOOL
- **Description**: Calculated using LAG function. Boolean indicating if household gave to this same campus in the prior month. Used to identify consistent vs returning givers.

### `gave_this_month`

- **Type**: BOOL
- **Description**: From inc_giving. Boolean calculated by checking if household has any transactions at this campus in month_date. TRUE = gave, FALSE = didn't give.

### `giver_status`

- **Type**: STRING
- **Description**: Calculated classification based on giving pattern logic. Values: 'New Giver' (first gift ever), 'Consistent Giver' (gave both months same campus), 'Returning Giver' (gave after missing), 'Lapsed Giver' (stopped giving), 'Migrated In Giver' (started at new campus), 'Migrated Out Giver' (moved to different campus), NULL (no status change).

### `month_date`

- **Type**: DATE
- **Description**: Calculated field. The first day of each month from household's first gift date to current month.

### `previous_month_campuses`

- **Type**: STRING
- **Description**: From inc_giving aggregation. Comma-separated list of all campuses the household gave to in the previous month. NULL = no giving anywhere.

### `rms_primary_family_id`

- **Type**: INT64
- **Description**: From Rock RMS Person.PrimaryFamilyId. Person-level. Duplicate of rms_family_id for compatibility. Rock > Person Profile > Family.

