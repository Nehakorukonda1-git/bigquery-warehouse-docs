# dimension_dates

## Columns

Total Columns: 31

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| `calendar_quarter` | INT64 | Standard calendar quarter. Data source: Date.CalendarQuarter. Quarter level. Quarter number (1-4) within the calendar year. Q1=Jan-Mar, Q2=Apr-Jun, Q3=Jul-Sep, Q4=Oct-Dec. Format: INTEGER (1-4). |
| `calendar_year` | INT64 | Standard calendar year. Data source: Date.CalendarYear. Year level. The four-digit calendar year. Format: INTEGER. Example: 2005. |
| `calendar_year_month` | STRING | Year-month combination for calendar. Data source: Date.CalendarYearMonth. Month level. Concatenated year and month for easy month-level grouping and sorting. Format: STRING. Example: '2005-01'. |
| `calendar_year_quarter` | STRING | Year-quarter combination for calendar. Data source: Date.CalendarYearQuarter. Quarter level. Concatenated year and quarter for quarter-level analysis. Format: STRING. Example: '2005Q1'. |
| `date_key` | INT64 | Integer representation of the date. Data source: Date.DateKey. Date level. The date formatted as YYYYMMDD for efficient indexing and sorting. Format: INTEGER. Example: 20050101. |
| `date_name` | STRING | Human-readable date format. Data source: Date.DateName. Date level. The date formatted as M/D/YYYY for display purposes in reports and dashboards. Format: STRING. Example: '1/1/2005'. |
| `day_name_of_week` | STRING | Text name of the weekday. Data source: Date.DayNameOfWeek. Date level. Full weekday name (Sunday, Monday, Tuesday, etc.). Used for human-readable reports. Format: STRING. |
| `day_of_month` | INT64 | Calendar day within the month. Data source: Date.DayOfMonth. Date level. Ranges from 1 to 31 depending on the month. Format: INTEGER (1-31). |
| `day_of_week` | INT64 | Numeric day of the week. Data source: Date.DayOfWeek. Date level. Sunday = 1, Monday = 2, through Saturday = 7. Used for day-of-week analysis and scheduling logic. Format: INTEGER (1-7). |
| `day_of_year` | INT64 | Sequential day number within the year. Data source: Date.DayOfYear. Date level. January 1 = 1, December 31 = 365/366. Used for year-over-year day comparisons. Format: INTEGER (1-366). |
| `fiscal_month_of_year` | INT64 | Fiscal month number. Data source: Date.FiscalMonthOfYear. Month level. Month number (1-12) within Life.Church's fiscal year, which begins January 1. Format: INTEGER (1-12). |
| `fiscal_quarter` | INT64 | Fiscal quarter number. Data source: Date.FiscalQuarter. Quarter level. Quarter number (1-4) within the fiscal year. Format: INTEGER (1-4). |
| `fiscal_year` | INT64 | Fiscal year designation. Data source: Date.FiscalYear. Year level. The fiscal year for financial reporting, aligns with calendar year at Life.Church. Format: INTEGER. Example: 2005. |
| `fiscal_year_month` | STRING | Fiscal year-month combination. Data source: Date.FiscalYearMonth. Month level. Concatenated fiscal year and month for fiscal reporting. Format: STRING. Example: 'FY2005-01'. |
| `fiscal_year_quarter` | STRING | Fiscal year-quarter combination. Data source: Date.FiscalYearQuarter. Quarter level. Concatenated fiscal year and quarter for quarterly fiscal analysis. Format: STRING. Example: 'FY2005Q1'. |
| `full_date` | DATE | The complete calendar date. Data source: Base Date table. Date level. Represents each individual calendar day from 1996-01-01 to 10 years in the future. This is the primary key for joining to fact tables on specific dates. Format: DATE (YYYY-MM-DD). Example: 2005-01-01. |
| `is_christmas_weekend` | BOOL | Christmas weekend indicator. Calculated field. Week level. TRUE if ministry_event or weekend_message contains 'christmas' (case-insensitive), FALSE otherwise. Used for Christmas season analysis. Format: BOOLEAN. |
| `is_easter_weekend` | BOOL | Easter weekend indicator. Calculated field. Week level. TRUE if ministry_event or weekend_message contains 'easter' (case-insensitive), FALSE otherwise. Critical for analyzing Easter impact on metrics. Format: BOOLEAN. |
| `is_last_day_of_month` | BOOL | Month-end indicator flag. Data source: Date.IsLastDayOfMonth. Date level. Boolean flag indicating if this date is the last day of its calendar month. Used for month-end reporting and processes. Format: BOOLEAN. |
| `lc_month_name` | STRING | Life.Church operational month name. Data source: Date.LCMonthName. Month level. The month name aligned with LC's operational calendar. Format: STRING. Example: 'January'. |
| `lc_month_of_year` | INT64 | Life.Church operational month number. Data source: Date.LCMonthOfYear. Month level. The month number (1-12) within the LC operational year. Format: INTEGER (1-12). |
| `lc_week_of_year` | INT64 | Life.Church week number within the LC year. Data source: Date.LCWeekOfYear. Week level. The week number (1-53) within the Life.Church fiscal/operational year. Critical for week-over-week comparisons. Format: INTEGER (1-53). |
| `lc_week_start_date` | DATE | The Sunday that begins the Life.Church operational week for this date. Data source: Calculated from base Date table with adjustments based on staff portal calendar events. Granularity: Date level. Calculation logic: Standard assignment uses the most recent Sunday; adjusted when ministry events span across Sundays - dates before the Sunday are moved to that Sunday's week. UI location: Staff Portal > Calendar Column purpose: Ensures multi-day events are analyzed as a single unit rather than split across weeks. Data format: DATE. |
| `lc_year` | INT64 | Life.Church operational year. Data source: Date.LCYear. Year level. The year designation in LC's operational calendar, which may differ from calendar year for dates near year boundaries. Format: INTEGER. Example: 2004. |
| `ministry_event` | STRING | Special ministry events for the week from Staff Portal. Data source: Aggregated from calendar.title where EventTypeID matches ministry event types. Week level. Pipe-separated list of ministry events or holidays occurring during this LC week. NULL if no special events. Used to identify special weekends for analysis. Staffp Portal > Calendar. |
| `month_name` | STRING | Standard calendar month name. Data source: Date.MonthName. Month level. Full month name (January, February, etc.). Format: STRING. |
| `month_of_year` | INT64 | Standard calendar month number. Data source: Date.MonthOfYear. Month level. Month number within the calendar year (1=January, 12=December). Format: INTEGER (1-12). |
| `series` | STRING | Weekend message series name. Data source: Coalesced from media_metadata_series.name via Magnolia API or calendar.title for Weekend Message events. Week level. The name of the sermon series being preached during this week. NULL if no series data available. Used for content performance analysis. Format: STRING. Example: 'ATM Reverse The Curse', 'Easter at Life.Church'. |
| `speaker` | STRING | Weekend message speaker names. Data source: Aggregated from media_metadata_episodes.speaker_name via Magnolia API. Week level. Comma-separated list of all speakers who preached during this week. NULL if no speaker data available. Format: STRING. Example: 'Craig Groeschel', 'Sam Roberts, Bobby Gruenewald'. |
| `week_of_year` | INT64 | Standard ISO week number. Data source: Date.WeekOfYear. Week level. The ISO week number (1-53) within the calendar year. Used for standard calendar reporting. Format: INTEGER (1-53). |
| `weekday_weekend` | STRING | Weekday/Weekend classification. Data source: Date.WeekdayWeekend. Date level. Categorizes dates as either 'Weekday' (Monday-Friday) or 'Weekend' (Saturday-Sunday). Used for weekend-specific analysis. Format: STRING. Values: 'Weekday', 'Weekend'. |

## Column Details

### `calendar_quarter`

- **Type**: INT64
- **Description**: Standard calendar quarter. Data source: Date.CalendarQuarter. Quarter level. Quarter number (1-4) within the calendar year. Q1=Jan-Mar, Q2=Apr-Jun, Q3=Jul-Sep, Q4=Oct-Dec. Format: INTEGER (1-4).

### `calendar_year`

- **Type**: INT64
- **Description**: Standard calendar year. Data source: Date.CalendarYear. Year level. The four-digit calendar year. Format: INTEGER. Example: 2005.

### `calendar_year_month`

- **Type**: STRING
- **Description**: Year-month combination for calendar. Data source: Date.CalendarYearMonth. Month level. Concatenated year and month for easy month-level grouping and sorting. Format: STRING. Example: '2005-01'.

### `calendar_year_quarter`

- **Type**: STRING
- **Description**: Year-quarter combination for calendar. Data source: Date.CalendarYearQuarter. Quarter level. Concatenated year and quarter for quarter-level analysis. Format: STRING. Example: '2005Q1'.

### `date_key`

- **Type**: INT64
- **Description**: Integer representation of the date. Data source: Date.DateKey. Date level. The date formatted as YYYYMMDD for efficient indexing and sorting. Format: INTEGER. Example: 20050101.

### `date_name`

- **Type**: STRING
- **Description**: Human-readable date format. Data source: Date.DateName. Date level. The date formatted as M/D/YYYY for display purposes in reports and dashboards. Format: STRING. Example: '1/1/2005'.

### `day_name_of_week`

- **Type**: STRING
- **Description**: Text name of the weekday. Data source: Date.DayNameOfWeek. Date level. Full weekday name (Sunday, Monday, Tuesday, etc.). Used for human-readable reports. Format: STRING.

### `day_of_month`

- **Type**: INT64
- **Description**: Calendar day within the month. Data source: Date.DayOfMonth. Date level. Ranges from 1 to 31 depending on the month. Format: INTEGER (1-31).

### `day_of_week`

- **Type**: INT64
- **Description**: Numeric day of the week. Data source: Date.DayOfWeek. Date level. Sunday = 1, Monday = 2, through Saturday = 7. Used for day-of-week analysis and scheduling logic. Format: INTEGER (1-7).

### `day_of_year`

- **Type**: INT64
- **Description**: Sequential day number within the year. Data source: Date.DayOfYear. Date level. January 1 = 1, December 31 = 365/366. Used for year-over-year day comparisons. Format: INTEGER (1-366).

### `fiscal_month_of_year`

- **Type**: INT64
- **Description**: Fiscal month number. Data source: Date.FiscalMonthOfYear. Month level. Month number (1-12) within Life.Church's fiscal year, which begins January 1. Format: INTEGER (1-12).

### `fiscal_quarter`

- **Type**: INT64
- **Description**: Fiscal quarter number. Data source: Date.FiscalQuarter. Quarter level. Quarter number (1-4) within the fiscal year. Format: INTEGER (1-4).

### `fiscal_year`

- **Type**: INT64
- **Description**: Fiscal year designation. Data source: Date.FiscalYear. Year level. The fiscal year for financial reporting, aligns with calendar year at Life.Church. Format: INTEGER. Example: 2005.

### `fiscal_year_month`

- **Type**: STRING
- **Description**: Fiscal year-month combination. Data source: Date.FiscalYearMonth. Month level. Concatenated fiscal year and month for fiscal reporting. Format: STRING. Example: 'FY2005-01'.

### `fiscal_year_quarter`

- **Type**: STRING
- **Description**: Fiscal year-quarter combination. Data source: Date.FiscalYearQuarter. Quarter level. Concatenated fiscal year and quarter for quarterly fiscal analysis. Format: STRING. Example: 'FY2005Q1'.

### `full_date`

- **Type**: DATE
- **Description**: The complete calendar date. Data source: Base Date table. Date level. Represents each individual calendar day from 1996-01-01 to 10 years in the future. This is the primary key for joining to fact tables on specific dates. Format: DATE (YYYY-MM-DD). Example: 2005-01-01.

### `is_christmas_weekend`

- **Type**: BOOL
- **Description**: Christmas weekend indicator. Calculated field. Week level. TRUE if ministry_event or weekend_message contains 'christmas' (case-insensitive), FALSE otherwise. Used for Christmas season analysis. Format: BOOLEAN.

### `is_easter_weekend`

- **Type**: BOOL
- **Description**: Easter weekend indicator. Calculated field. Week level. TRUE if ministry_event or weekend_message contains 'easter' (case-insensitive), FALSE otherwise. Critical for analyzing Easter impact on metrics. Format: BOOLEAN.

### `is_last_day_of_month`

- **Type**: BOOL
- **Description**: Month-end indicator flag. Data source: Date.IsLastDayOfMonth. Date level. Boolean flag indicating if this date is the last day of its calendar month. Used for month-end reporting and processes. Format: BOOLEAN.

### `lc_month_name`

- **Type**: STRING
- **Description**: Life.Church operational month name. Data source: Date.LCMonthName. Month level. The month name aligned with LC's operational calendar. Format: STRING. Example: 'January'.

### `lc_month_of_year`

- **Type**: INT64
- **Description**: Life.Church operational month number. Data source: Date.LCMonthOfYear. Month level. The month number (1-12) within the LC operational year. Format: INTEGER (1-12).

### `lc_week_of_year`

- **Type**: INT64
- **Description**: Life.Church week number within the LC year. Data source: Date.LCWeekOfYear. Week level. The week number (1-53) within the Life.Church fiscal/operational year. Critical for week-over-week comparisons. Format: INTEGER (1-53).

### `lc_week_start_date`

- **Type**: DATE
- **Description**: The Sunday that begins the Life.Church operational week for this date. Data source: Calculated from base Date table with adjustments based on staff portal calendar events. Granularity: Date level. Calculation logic: Standard assignment uses the most recent Sunday; adjusted when ministry events span across Sundays - dates before the Sunday are moved to that Sunday's week. UI location: Staff Portal > Calendar Column purpose: Ensures multi-day events are analyzed as a single unit rather than split across weeks. Data format: DATE.

### `lc_year`

- **Type**: INT64
- **Description**: Life.Church operational year. Data source: Date.LCYear. Year level. The year designation in LC's operational calendar, which may differ from calendar year for dates near year boundaries. Format: INTEGER. Example: 2004.

### `ministry_event`

- **Type**: STRING
- **Description**: Special ministry events for the week from Staff Portal. Data source: Aggregated from calendar.title where EventTypeID matches ministry event types. Week level. Pipe-separated list of ministry events or holidays occurring during this LC week. NULL if no special events. Used to identify special weekends for analysis. Staffp Portal > Calendar.

### `month_name`

- **Type**: STRING
- **Description**: Standard calendar month name. Data source: Date.MonthName. Month level. Full month name (January, February, etc.). Format: STRING.

### `month_of_year`

- **Type**: INT64
- **Description**: Standard calendar month number. Data source: Date.MonthOfYear. Month level. Month number within the calendar year (1=January, 12=December). Format: INTEGER (1-12).

### `series`

- **Type**: STRING
- **Description**: Weekend message series name. Data source: Coalesced from media_metadata_series.name via Magnolia API or calendar.title for Weekend Message events. Week level. The name of the sermon series being preached during this week. NULL if no series data available. Used for content performance analysis. Format: STRING. Example: 'ATM Reverse The Curse', 'Easter at Life.Church'.

### `speaker`

- **Type**: STRING
- **Description**: Weekend message speaker names. Data source: Aggregated from media_metadata_episodes.speaker_name via Magnolia API. Week level. Comma-separated list of all speakers who preached during this week. NULL if no speaker data available. Format: STRING. Example: 'Craig Groeschel', 'Sam Roberts, Bobby Gruenewald'.

### `week_of_year`

- **Type**: INT64
- **Description**: Standard ISO week number. Data source: Date.WeekOfYear. Week level. The ISO week number (1-53) within the calendar year. Used for standard calendar reporting. Format: INTEGER (1-53).

### `weekday_weekend`

- **Type**: STRING
- **Description**: Weekday/Weekend classification. Data source: Date.WeekdayWeekend. Date level. Categorizes dates as either 'Weekday' (Monday-Friday) or 'Weekend' (Saturday-Sunday). Used for weekend-specific analysis. Format: STRING. Values: 'Weekday', 'Weekend'.

