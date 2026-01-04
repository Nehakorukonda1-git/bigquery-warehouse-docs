How to Find Common Information
This guide helps you find the right columns for common business questions.
Finding People
"How do I find people who give regularly?"
Tables: dimension_person
Columns: giving.is_recurring_giver_tithe_offerings = TRUE
Example:
sqlSELECT person_id, full_name, email
FROM dimension_person
WHERE giving.is_recurring_giver_tithe_offerings = TRUE
"How do I find first-time guests?"
Tables: dimension_person
Columns: first_attendance_timestamp = last_attendance_timestamp
Meaning: They've only attended once
Example:
sqlSELECT person_id, full_name, first_attendance_campus
FROM dimension_person
WHERE first_attendance_timestamp = last_attendance_timestamp
"How do I find active adults?"
Tables: dimension_person
Columns:

is_adult = TRUE (person is 18+)
last_attendance_timestamp >= CURRENT_DATE - 60 (attended in last 60 days)
is_deceased = FALSE (exclude deceased)

Example:
sqlSELECT person_id, full_name, home_campus
FROM dimension_person
WHERE is_adult = TRUE
  AND last_attendance_timestamp >= CURRENT_DATE - 60
  AND is_deceased = FALSE
"How do I find parents with kids?"
Tables: dimension_person
Columns: has_children = TRUE
Example:
sqlSELECT person_id, full_name
FROM dimension_person
WHERE is_adult = TRUE
  AND has_children = TRUE
"How do I find volunteers?"
Tables: dimension_person
Columns:

is_volunteer = TRUE (currently serving)
OR last_volunteer_timestamp (when they last served)

Example:
sqlSELECT person_id, full_name, last_volunteer_timestamp
FROM dimension_person
WHERE is_volunteer = TRUE
"How do I find LifeGroup leaders?"
Tables: dimension_person
Columns: is_lifegroup_leader = TRUE
Example:
sqlSELECT person_id, full_name
FROM dimension_person
WHERE is_lifegroup_leader = TRUE
"How do I find staff members?"
Tables: dimension_person
Columns: is_staff = TRUE

Finding Giving Information
"How do I find total giving for a person?"
Tables: fact_giving
Columns: Sum the amount column
Example:
sqlSELECT 
  person_id,
  SUM(amount) as total_giving
FROM fact_giving
WHERE is_successful = TRUE
GROUP BY person_id
"How do I find when someone first gave?"
Tables: dimension_person
Columns: first_financial_transaction_timestamp
Example:
sqlSELECT 
  person_id, 
  full_name,
  first_financial_transaction_timestamp
FROM dimension_person
WHERE first_financial_transaction_timestamp IS NOT NULL
"How do I find recent givers (last 90 days)?"
Tables: dimension_person
Columns: giving.number_of_gifts_last_90_tithes_and_offerings > 0
Example:
sqlSELECT person_id, full_name
FROM dimension_person
WHERE giving.number_of_gifts_last_90_tithes_and_offerings > 0

Finding Attendance Information
"How do I count someone's total attendance?"
Tables: fact_attendance
Columns: Count rows for that person_id
Note: Each row = one check-in event
Example:
sqlSELECT 
  person_id,
  COUNT(*) as total_attendance_count
FROM fact_attendance
WHERE person_id = 12345 -- Replace with actual person_id
GROUP BY person_id
To get attendance for ALL people:
sqlSELECT 
  p.person_id,
  p.full_name,
  COUNT(a.attendance_id) as total_attendance_count
FROM dimension_person p
LEFT JOIN fact_attendance a ON p.person_id = a.person_id
GROUP BY p.person_id, p.full_name
ORDER BY total_attendance_count DESC
To get attendance in a specific time period:
sqlSELECT 
  p.person_id,
  p.full_name,
  COUNT(a.attendance_id) as attendance_last_90_days
FROM dimension_person p
LEFT JOIN fact_attendance a ON p.person_id = a.person_id
WHERE a.attendance_date >= CURRENT_DATE - 90
GROUP BY p.person_id, p.full_name
"How do I get attendance by campus?"
Tables: fact_attendance, dimension_campus
Example:
sqlSELECT 
  c.campus_name,
  COUNT(*) as total_attendance
FROM fact_attendance a
JOIN dimension_campus c ON a.campus_id = c.campus_id
WHERE a.attendance_date >= '2024-01-01'
GROUP BY c.campus_name
ORDER BY total_attendance DESC
"How do I get attendance for a specific person at a specific campus?"
Tables: fact_attendance, dimension_person, dimension_campus
Example:
sqlSELECT 
  p.full_name,
  c.campus_name,
  COUNT(*) as attendance_count,
  MIN(a.attendance_date) as first_visit,
  MAX(a.attendance_date) as last_visit
FROM fact_attendance a
JOIN dimension_person p ON a.person_id = p.person_id
JOIN dimension_campus c ON a.campus_id = c.campus_id
WHERE p.person_id = 12345
  AND c.campus_short_code = 'EDM'
GROUP BY p.full_name, c.campus_name
"How do I count someone's total attendance?"
Tables: fact_attendance
Columns: Count rows for that person_id
Note: Each row = one check-in event
Example:
sqlSELECT 
  person_id,
  COUNT(*) as total_attendance_count
FROM fact_attendance
WHERE person_id = 12345 -- Replace with actual person_id
GROUP BY person_id
To get attendance for ALL people:
sqlSELECT 
  p.person_id,
  p.full_name,
  COUNT(a.attendance_id) as total_attendance_count
FROM dimension_person p
LEFT JOIN fact_attendance a ON p.person_id = a.person_id
GROUP BY p.person_id, p.full_name
ORDER BY total_attendance_count DESC
To get attendance in a specific time period:
sqlSELECT 
  p.person_id,
  p.full_name,
  COUNT(a.attendance_id) as attendance_last_90_days
FROM dimension_person p
LEFT JOIN fact_attendance a ON p.person_id = a.person_id
WHERE a.attendance_date >= CURRENT_DATE - 90
GROUP BY p.person_id, p.full_name
"How do I find when someone last attended?"
Tables: dimension_person
Columns: last_attendance_timestamp
Example:
sqlSELECT person_id, full_name, last_attendance_timestamp
FROM dimension_person
WHERE last_attendance_timestamp >= CURRENT_DATE - 30
"How do I find LifeKids attendance?"
Tables: fact_lifekids_checkin
Columns: Filter by specific room names
Example:
sqlSELECT 
  person_id,
  check_in_timestamp,
  campus
FROM fact_lifekids_checkin
WHERE room_name = 'The Loop'

Finding Campus Information
"How do I get someone's home campus?"
Tables: dimension_person
Columns: home_campus (best source for campus affiliation)
Example:
sqlSELECT person_id, full_name, home_campus
FROM dimension_person
"How do I get campus names (not codes)?"
Tables: dimension_campus
Join on: campus_short_code
Example:
sqlSELECT 
  p.person_id,
  p.full_name,
  c.campus_name
FROM dimension_person p
JOIN dimension_campus c ON p.home_campus = c.campus_short_code

Finding LifeGroup Information
"How do I find LifeGroup members?"
Tables: fact_life_group_members
Columns: Filter by is_active = TRUE
Example:
sqlSELECT 
  person_id,
  lifegroup_id,
  role
FROM fact_life_group_members
WHERE is_active = TRUE
"How do I find LifeGroup details?"
Tables: dimension_lifegroup
Columns: group_name, campus, meeting_day
Example:
sqlSELECT 
  lifegroup_id,
  group_name,
  campus
FROM dimension_lifegroup
WHERE is_active = TRUE

Common Field Patterns
Age-Related

age - Exact age in years
age_group - Bucketed (e.g., "18-24", "35-44")
birthdate - Actual birth date

Status Fields (Boolean)

is_adult - Person is 18+
is_staff - Employee of Life.Church
is_volunteer - Currently serving
is_deceased - Person has passed away
has_children - Has kids in their family

Timestamp Patterns

first_*_timestamp - When something first happened
last_*_timestamp - Most recent occurrence

Campus Fields

home_campus - Person's primary campus (3-letter code)
*_campus - Campus where something happened
Always join to dimension_campus for full campus names

Giving Fields (in STRUCT)

giving.is_recurring_giver_* - Has active recurring gift
giving.last_financial_transaction_*_timestamp - When they last gave
giving.number_of_gifts_last_90_* - Recent gift count


Table Relationships Quick Reference
dimension_person (person_id)
    ↓
    ├─→ fact_attendance (person_id) - All check-ins
    ├─→ fact_giving (person_id) - Financial transactions
    ├─→ fact_life_group_members (person_id) - LifeGroup participation
    ├─→ fact_lifekids_checkin (person_id) - LifeKids attendance
    └─→ fact_volunteer_interest (person_id) - Volunteer interests

dimension_campus (campus_short_code)
    ↓
    └─→ dimension_person (home_campus) - Person's main campus

dimension_lifegroup (lifegroup_id)
    ↓
    └─→ fact_life_group_members (lifegroup_id) - Members in group

Tips for Writing Queries

Always filter out deceased people unless specifically analyzing deceased records:

sql   WHERE is_deceased = FALSE

Use home_campus for campus affiliation (not first_attendance_campus or last_attendance_campus)
For active people, check recent attendance:

sql   WHERE last_attendance_timestamp >= CURRENT_DATE - 60

For giving queries, check successful transactions:

sql   WHERE is_successful = TRUE

For LifeKids parents, check household fields:

sql   WHERE household.last_lifekids_checkin_timestamp IS NOT NULL