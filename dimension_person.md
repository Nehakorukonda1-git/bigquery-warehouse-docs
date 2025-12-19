# dimension_person

## Columns

Total Columns: 449

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| `address_1` | STRING | From Rock RMS Location.Street1. Entity level. The primary street address line for the entity physical location. |
| `address_2` | STRING | From Rock RMS Location.Street2. Entity level. The secondary address line (suite, building, etc). Returns empty string if NULL. |
| `address_to_primary_campus_distance_miles` | FLOAT64 | From person_location table. Person-level. Calculated distance in miles from home address to primary campus. |
| `age` | INT64 | The age in years of the person. |
| `age_group` | STRING | The person's age in bucketed groups. |
| `background_check_completed_timestamp` | DATE | From Step table. Person level. The date when the person's most recent background check was completed. Used to track expiration and renewal needs. |
| `background_check_status` | STRING | The current status of the person's background check. |
| `banned_giver_timestamp` | TIMESTAMP | The timestamp when the person was marked as a banned giver. Person level. CreatedDateTime of the BannedGiver attribute value. Rock > Profile > Person Profile > Attributes > Banned Giver > Created Date. |
| `birthdate` | DATE | From Rock RMS Person.Birthdate. Person level. The person's date of birth. Format: YYYY-MM-DD. Used for age calculations and age-appropriate room assignments. |
| `city` | STRING | From Rock RMS Location. Entity level. The city where the entity is located. |
| `country` | STRING | From location.country. Person level. The country of the person's home address. Typically 'US' for most records. Used for international attendee identification. |
| `county` | STRING | From person_location table. Family-level. County name. Rock > Person > Address. |
| `current_attendance_flow_classification` | STRING | From attendance_flow model calculations. Person level (inherited from family level). The current attendance stage of the person's family based on their check-in patterns. Represents which of the 5 stages (New, Retained, Re-engaged, Absent, or Inactive) the family is currently in. New = first 4 weeks after first check-in, Retained = attending at least once every 4 weeks, Re-engaged = returned after 4+ weeks absence, Absent = no attendance for 4-8 weeks, Inactive = no attendance for 8+ weeks. Example values: 'New', 'Retained', 'Re-engaged', 'Absent', 'Inactive', NULL. |
| `decade_of_life` | FLOAT64 | The age in years of the person, rounded or truncated to the earliest decade or 10 years. |
| `deletion_requested_timestamp` | TIMESTAMP | From Rock RMS Person where InactiveReasonNote contains deletion request. Person-level. Timestamp of GDPR deletion request. Rock > Person Profile > Inactive Reason Note. |
| `email` | STRING | From Rock RMS Person.email. Person level. The person's primary email address as stored in Rock RMS. May be NULL if no email on file. Used for communication and matching. |
| `engagement_status_self_identified` | STRING | The engagement status as self-identified by the person. |
| `family_position` | STRING | Family hierarchy, whether the person is an Adult or Child in their family. |
| `first_attendance_app_campus` | STRING | From attender_check_in filtered for app check-ins. Person level. The campus code where the person first checked in via the app. Rock > Person > History. |
| `first_attendance_app_timestamp` | TIMESTAMP | From attender_check_in filtered for app check-ins. Person level. The timestamp of the person's first attendance check-in via the Life.Church mobile app. NULL if never used app check-in. Rock > Person > History. |
| `first_attendance_campus` | STRING | From attendance_combined filtered for non-volunteer attendance. Person level. The campus code where the person first attended a experience. Rock > Person > History. |
| `first_attendance_combined_campus` | STRING | From attendance_combined including all attendance types. Person level. The campus code where the person had their first check-in of any type. Rock > Person > History. |
| `first_attendance_combined_parent_group` | STRING | From attendance_combined including all attendance types. Person level. The parent group name of the person's first check-in (e.g., Host Team, LifeKids, Switch). Indicates their entry point into Life.Church. |
| `first_attendance_combined_timestamp` | TIMESTAMP | From attendance_combined including all attendance types. Person level. The timestamp of the person's first check-in of any type (attendance or volunteer). The earliest interaction with Life.Church. Rock > Person > History. |
| `first_attendance_host_team_campus` | STRING | From attender_check_in via parent group pivot. Person level. The campus code where the person first served on Host Team. Rock > Person > History. |
| `first_attendance_host_team_timestamp` | TIMESTAMP | From attender_check_in via parent group pivot. Person level. The timestamp of the person's first check-in as a Host Team volunteer. NULL if never served. Rock > Person > History. |
| `first_attendance_lifekids_campus_crosstown` | STRING | From attender_check_in via attendance group pivot. Person level. The campus code where the person first attended Crosstown LifeKids room. Rock > Person > History. |
| `first_attendance_lifekids_campus_in_the_jungle` | STRING | From attender_check_in via attendance group pivot. Person level. The campus code where the person first attended In The Jungle LifeKids room. Rock > Person > History. |
| `first_attendance_lifekids_campus_konnect` | STRING | From attender_check_in via attendance group pivot. Person level. The campus code where the person first attended Konnect LifeKids room. Rock > Person > History. |
| `first_attendance_lifekids_campus_let_there_be_light` | STRING | From attender_check_in via attendance group pivot. Person level. The campus code where the person first attended Let There Be Light LifeKids room. Rock > Person > History. |
| `first_attendance_lifekids_campus_starry_night` | STRING | From attender_check_in via attendance group pivot. Person level. The campus code where the person first attended Starry Night LifeKids room. Rock > Person > History. |
| `first_attendance_lifekids_campus_the_ark` | STRING | From attender_check_in via attendance group pivot. Person level. The campus code where the person first attended The Ark LifeKids room. Rock > Person > History. |
| `first_attendance_lifekids_campus_the_garden` | STRING | From attender_check_in via attendance group pivot. Person level. The campus code where the person first attended The Garden LifeKids room. Rock > Person > History. |
| `first_attendance_lifekids_campus_the_loop` | STRING | From attender_check_in via attendance group pivot. Person level. The campus code where the person first attended The Loop LifeKids room. Paired with timestamp - both NULL or both populated. Rock > Person > History. |
| `first_attendance_lifekids_campus_under_the_sea` | STRING | From attender_check_in via attendance group pivot. Person level. The campus code where the person first attended Under The Sea LifeKids room. Rock > Person > History. |
| `first_attendance_lifekids_timestamp_crosstown` | TIMESTAMP | From attender_check_in via attendance group pivot. Person level. The timestamp of the person's first check-in to Crosstown LifeKids room (5th grade). NULL if never attended. Rock > Person > History. |
| `first_attendance_lifekids_timestamp_in_the_jungle` | TIMESTAMP | From attender_check_in via attendance group pivot. Person level. The timestamp of the person's first check-in to In The Jungle LifeKids room (age 4). NULL if never attended. Rock > Person > History. |
| `first_attendance_lifekids_timestamp_konnect` | TIMESTAMP | From attender_check_in via attendance group pivot. Person level. The timestamp of the person's first check-in to Konnect LifeKids room (1st-2nd grade). NULL if never attended. Rock > Person > History. |
| `first_attendance_lifekids_timestamp_let_there_be_light` | TIMESTAMP | From attender_check_in via attendance group pivot. Person level. The timestamp of the person's first check-in to Let There Be Light LifeKids room (age 3). NULL if never attended. Rock > Person > History. |
| `first_attendance_lifekids_timestamp_starry_night` | TIMESTAMP | From attender_check_in via attendance group pivot. Person level. The timestamp of the person's first check-in to Starry Night LifeKids room (age 5). NULL if never attended. Rock > Person > History. |
| `first_attendance_lifekids_timestamp_the_ark` | TIMESTAMP | From attender_check_in via attendance group pivot. Person level. The timestamp of the person's first check-in to The Ark LifeKids room. NULL if never attended. Rock > Person > History. |
| `first_attendance_lifekids_timestamp_the_garden` | TIMESTAMP | From attender_check_in via attendance group pivot. Person level. The timestamp of the person's first check-in to The Garden LifeKids room (3rd-4th grade). NULL if never attended. Rock > Person > History. |
| `first_attendance_lifekids_timestamp_the_loop` | TIMESTAMP | From attender_check_in via attendance group pivot. Person level. The timestamp of the person's first check-in to The Loop LifeKids room (ages 1-2). NULL if never attended. Rock > Person > History. |
| `first_attendance_lifekids_timestamp_under_the_sea` | TIMESTAMP | From attender_check_in via attendance group pivot. Person level. The timestamp of the person's first check-in to Under The Sea LifeKids room (kindergarten). NULL if never attended. Rock > Person > History. |
| `first_attendance_switch_campus` | STRING | From attender_check_in via parent group pivot. Person level. The campus code where the person first attended Switch student ministry. Rock > Person > History. |
| `first_attendance_switch_campus_student` | STRING | From attender_check_in via attendance group pivot. Person level. The campus code where the person first attended Switch student ministry. Rock > Person > History. |
| `first_attendance_switch_timestamp` | TIMESTAMP | From attender_check_in via parent group pivot. Person level. The timestamp of the person's first check-in to Switch student ministry (parent group level). NULL if never attended. Rock > Person > History. |
| `first_attendance_switch_timestamp_student` | TIMESTAMP | From attender_check_in via attendance group pivot. Person level. The timestamp of the person's first check-in to Switch student ministry (6th-12th grade). NULL if never attended. Rock > Person > History. |
| `first_attendance_timestamp` | TIMESTAMP | From attendance_combined filtered for non-volunteer attendance. Person level. The timestamp of the person's first attendance at any Life.Church campus (excludes volunteer check-ins). Rock > Person > History. |
| `first_connection_request_event_interest_campus_baptism` | STRING | From ConnectionRequest filtered by connection opportunity ID. Person level. The campus associated with their first connection request for this event. |
| `first_connection_request_event_interest_campus_baptism_class_kids` | STRING | From ConnectionRequest filtered by connection opportunity ID. Person level. The campus associated with their first connection request for this event. |
| `first_connection_request_event_interest_timestamp_baptism` | TIMESTAMP | From ConnectionRequest filtered by connection opportunity ID. Person level. The earliest timestamp when this person expressed interest in this event through a connection request. |
| `first_connection_request_event_interest_timestamp_baptism_class_kids` | TIMESTAMP | From ConnectionRequest filtered by connection opportunity ID. Person level. The earliest timestamp when this person expressed interest in this event through a connection request. |
| `first_event_participation_campus_baptism` | STRING | From Rock Attributes tables. The first recorded Life.Church campus at which the person was baptized. Rock > Extended Attributes > Life Events > Baptism. |
| `first_event_participation_campus_child_dedication` | STRING | From Rock Attributes tables. The first recorded Life.Church campus at which the person dedicated a child at Life.Church. Rock > Extended Attributes > Life Events > Child Dedication. |
| `first_event_participation_campus_known` | STRING | From Rock Attributes tables and Steps tables. The first recorded Life.Church campus at which the person attended any form of Known Event (previously called 'Open Door'). Rock > Steps > Known. |
| `first_event_participation_timestamp_baptism` | TIMESTAMP | From Rock Attributes tables. The first recorded timestamp of when the person was baptized. Rock > Extended Attributes > Life Events > Baptism. |
| `first_event_participation_timestamp_child_dedication` | TIMESTAMP | From Rock Attributes tables. The first recorded timestamp of when the person dedicated a child at Life.Church. Rock > Extended Attributes > Life Events > Child Dedication. |
| `first_event_participation_timestamp_known` | TIMESTAMP | From Rock Attributes tables and Steps tables. The first recorded timestamp of when the person attended any form of Known Event (previously called 'Open Door'). Rock > Steps > Known. |
| `first_financial_transaction_campus` | STRING | The campus short code (e.g., 'EDM', 'STW') where the person made their first financial contribution. Person level. Retrieved from the campus associated with the first transaction. Rock > Profile > Transactions. |
| `first_financial_transaction_timestamp` | TIMESTAMP | The timestamp of the person's first ever financial contribution to Life.Church. Person level. Calculated as the earliest transaction from fact_giving where amount >= 0 and is_successful = TRUE. Rock > Profile > Transactions. |
| `first_form_submission_account_acquisition_timestamp_addiction` | TIMESTAMP | Calculated via PIVOT MIN on form_submission_timestamp. Person level. The earliest timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department. |
| `first_form_submission_account_acquisition_timestamp_anxiety` | TIMESTAMP | Calculated via PIVOT MIN on form_submission_timestamp. Person level. The earliest timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department. |
| `first_form_submission_account_acquisition_timestamp_burnout` | TIMESTAMP | Calculated via PIVOT MIN on form_submission_timestamp. Person level. The earliest timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department. |
| `first_form_submission_account_acquisition_timestamp_finance` | TIMESTAMP | Calculated via PIVOT MIN on form_submission_timestamp. Person level. The earliest timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department. |
| `first_form_submission_account_acquisition_timestamp_friendship` | TIMESTAMP | Calculated via LEAST function combining friendship and friendships form variants. Person level. The earliest timestamp when this person submitted any friendship-related account acquisition form through HubSpot paid marketing campaigns managed by the Reach department, accounting for historical form naming variations. |
| `first_form_submission_account_acquisition_timestamp_grief` | TIMESTAMP | Calculated via PIVOT MIN on form_submission_timestamp. Person level. The earliest timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department. |
| `first_form_submission_account_acquisition_timestamp_habits` | TIMESTAMP | Calculated via PIVOT MIN on form_submission_timestamp. Person level. The earliest timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department. |
| `first_form_submission_account_acquisition_timestamp_parenting` | TIMESTAMP | Calculated via PIVOT MIN on form_submission_timestamp. Person level. The earliest timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department. |
| `first_form_submission_next_steps_campus_baptism` | STRING | Filtered for specific form using constants. Person level. The campus where this person first submitted this next steps form. |
| `first_form_submission_next_steps_campus_commit_to_christ` | STRING | Filtered for specific form using constants. Person level. The campus where this person first submitted this next steps form. |
| `first_form_submission_next_steps_campus_general_question` | STRING | Filtered for specific form using constants. Person level. The campus where this person first submitted this next steps form. |
| `first_form_submission_next_steps_campus_im_new_here` | STRING | Filtered for specific form using constants. Person level. The campus where this person first submitted this next steps form. |
| `first_form_submission_next_steps_campus_known` | STRING | Filtered for specific form using constants. Person level. The campus where this person first submitted this next steps form. |
| `first_form_submission_next_steps_campus_prayer_request` | STRING | Filtered for specific form using constants. Person level. The campus where this person first submitted this next steps form. |
| `first_form_submission_next_steps_campus_renewing_commitment_to_christ` | STRING | Filtered for specific form using constants. Person level. The campus where this person first submitted this next steps form. |
| `first_form_submission_next_steps_timestamp_baptism` | TIMESTAMP | Filtered for specific form using constants. Person level. The earliest timestamp when this person submitted this particular next steps form representing deeper spiritual engagement. |
| `first_form_submission_next_steps_timestamp_commit_to_christ` | TIMESTAMP | Filtered for specific form using constants. Person level. The earliest timestamp when this person submitted this particular next steps form representing deeper spiritual engagement. |
| `first_form_submission_next_steps_timestamp_general_question` | TIMESTAMP | Filtered for specific form using constants. Person level. The earliest timestamp when this person submitted this particular next steps form representing deeper spiritual engagement. |
| `first_form_submission_next_steps_timestamp_im_new_here` | TIMESTAMP | Filtered for specific form using constants. Person level. The earliest timestamp when this person submitted this particular next steps form representing deeper spiritual engagement. |
| `first_form_submission_next_steps_timestamp_known` | TIMESTAMP | Filtered for specific form using constants. Person level. The earliest timestamp when this person submitted this particular next steps form representing deeper spiritual engagement. |
| `first_form_submission_next_steps_timestamp_prayer_request` | TIMESTAMP | Filtered for specific form using constants. Person level. The earliest timestamp when this person submitted this particular next steps form representing deeper spiritual engagement. |
| `first_form_submission_next_steps_timestamp_renewing_commitment_to_christ` | TIMESTAMP | Filtered for specific form using constants. Person level. The earliest timestamp when this person submitted this particular next steps form representing deeper spiritual engagement. |
| `first_name` | STRING | Employee's legal first name from the employee table. Used for official documentation and reporting. |
| `first_segment_interaction_timestamp` | TIMESTAMP | From aggregated Segment events. Person level. The earliest timestamp across all tracked sources, representing the person's first known digital interaction with any Life.Church platform. Used to determine overall engagement start date. Calculated as MIN of all source-specific first interactions. |
| `first_segment_interaction_timestamp_chop_prod` | TIMESTAMP | From Segment events table. Person level. The timestamp of the person's first interaction with Church Online Platform (CHOP) production environment tracked by Segment. Tracks when they first engaged with online church services. |
| `first_segment_interaction_timestamp_finds_life_prod` | TIMESTAMP | From Segment events table. Person level. The timestamp of the person's first interaction with finds.life website. Tracks engagement with the articles. |
| `first_segment_interaction_timestamp_hubspot_email_events_dev` | TIMESTAMP | From Segment events table. Person level. The timestamp of the person's first email interaction tracked through HubSpot integration. Captures initial email engagement like opens or clicks. |
| `first_segment_interaction_timestamp_hubspot_form_submission` | TIMESTAMP | From Segment events table. Person level. The timestamp of the person's first form submission tracked through HubSpot integration. Records initial form completions across Life.Church properties. |
| `first_segment_interaction_timestamp_kotlin_android` | TIMESTAMP | From Segment events table. Person level. The timestamp of the person's first interaction with the Life.Church Android app (Kotlin version). Indicates when they first used the newer Android application. |
| `first_segment_interaction_timestamp_lc_ios_swift` | TIMESTAMP | From Segment events table. Person level. The timestamp of the person's first interaction with the Life.Church iOS app (Swift version). Indicates when they first used the newer iOS application. |
| `first_segment_interaction_timestamp_lcweb` | TIMESTAMP | From Segment events table. Person level. The timestamp of the person's first interaction with the main Life.Church website. Tracks initial web engagement. |
| `first_segment_interaction_timestamp_lifechurch_android` | TIMESTAMP | From Segment events table. Person level. The timestamp of the person's first interaction with the legacy Life.Church Android app. Tracks usage of the older Android application version. |
| `first_segment_interaction_timestamp_lifechurch_ios` | TIMESTAMP | From Segment events table. Person level. The timestamp of the person's first interaction with the legacy Life.Church iOS app. Tracks usage of the older iOS application version. |
| `first_segment_interaction_timestamp_rms_prod_js` | TIMESTAMP | From Segment events table. Person level. The timestamp of the person's first interaction tracked by Rock RMS JavaScript SDK in production. Captures initial engagement with Rock-integrated web properties. |
| `first_serving_check_in_activity` | STRING | From volunteer_check_in table. Person level. The specific serving role or activity name from the person's first volunteer check-in. Provides context for their initial serving experience. |
| `first_serving_check_in_campus` | STRING | From volunteer_check_in and Campus tables. Person level. The three-letter campus code where the person first checked in to serve. |
| `first_serving_check_in_timestamp` | TIMESTAMP | From volunteer_check_in table. Person level. The timestamp of the person's first ever volunteer serving check-in across all ministries. Marks the transition from interest to action. |
| `first_step_next_steps_campus_you_said_yes` | STRING | From Step table filtered by YSY step type. Person level. The campus where this person first completed the You Said Yes step. |
| `first_step_next_steps_timestamp_you_said_yes` | TIMESTAMP | From Step table filtered by YSY step type. Person level. The earliest timestamp when this person completed the You Said Yes step. |
| `first_three_month_tithe_challenge_requested` | BOOL | Boolean indicating whether the person has ever participated in the three-month tithe challenge. Person level. TRUE if three_month_timestamp exists, FALSE otherwise. Rock > Profile > Attributes > Three Month Tithe Challenge. |
| `first_volunteer_campus` | STRING | From attendance_combined filtered for volunteer attendance. Person level. The campus code where the person first served as a volunteer. Rock > Person > History. |
| `first_volunteer_interest_campus_short_code_host_team` | STRING | From volunteer_interest_forms table. Person level. The three-letter campus code where the person first expressed interest in Host Team volunteering. |
| `first_volunteer_interest_campus_short_code_lifegroups_lifemissions` | STRING | From volunteer_interest_forms table. Person level. The three-letter campus code where the person first expressed interest in LifeGroups/LifeMissions volunteering. |
| `first_volunteer_interest_campus_short_code_media` | STRING | From volunteer_interest_forms table. Person level. The three-letter campus code where the person first expressed interest in Media/Tech volunteering. |
| `first_volunteer_interest_campus_short_code_operations_team` | STRING | From volunteer_interest_forms table. Person level. The three-letter campus code where the person first expressed interest in Operations volunteering. |
| `first_volunteer_interest_campus_short_code_switch` | STRING | From volunteer_interest_forms table. Person level. The three-letter campus code where the person first expressed interest in Switch volunteering. |
| `first_volunteer_interest_host_team_timestamp` | TIMESTAMP | From volunteer_interest_forms table. Person level. The timestamp when the person first submitted a volunteer interest form for Host Team ministry. Indicates initial interest in greeting, ushering, or hospitality roles. |
| `first_volunteer_interest_lifegroups_lifemissions_timestamp` | TIMESTAMP | From volunteer_interest_forms table. Person level. The timestamp when the person first submitted a volunteer interest form for LifeGroups or LifeMissions ministry. Indicates interest in small group leadership or missions involvement. |
| `first_volunteer_interest_media_timestamp` | TIMESTAMP | From volunteer_interest_forms table. Person level. The timestamp when the person first submitted a volunteer interest form for Media, Social Media, Photography, or Tech Team. Indicates interest in creative or technical ministries. |
| `first_volunteer_interest_operations_team_timestamp` | TIMESTAMP | From volunteer_interest_forms table. Person level. The timestamp when the person first submitted a volunteer interest form for Operations Team. Indicates interest in facilities, logistics, or technical operations. |
| `first_volunteer_interest_switch_timestamp` | TIMESTAMP | From volunteer_interest_forms table. Person level. The timestamp when the person first submitted a volunteer interest form for Switch ministry. Indicates interest in youth ministry volunteering. |
| `first_volunteer_interest_timestamp` | TIMESTAMP | Calculated from all volunteer interest forms. Person level. The earliest timestamp across all ministry-specific volunteer interest forms, representing when the person first expressed any volunteer interest. Calculated using LEAST function with null handling. |
| `first_volunteer_timestamp` | TIMESTAMP | From attendance_combined filtered for volunteer attendance. Person level. The timestamp of the person's first volunteer serving check-in at any campus or role. Rock > Person > History. |
| `frequency` | STRING | The frequency of the scheduled transaction (e.g., 'Weekly', 'Monthly', 'One-Time'). From Rock RMS defined values for transaction frequency. |
| `full_name` | STRING | From Rock RMS Person. Person level. The person's full name constructed as nickname (or first name if no nickname) plus last name. Used for human-readable identification in reports. |
| `gender` | STRING | Employee gender from employee.gender. Used for diversity analytics. NULL for requisitions. |
| `giving` | STRUCT<is_recurring_giver_tithe_offerings BOOL, is_recurring_giver_tithe_offerings_campus STRING, last_financial_transaction_tithes_offerings_campus STRING, last_financial_transaction_tithes_offerings_timestamp TIMESTAMP, number_of_gifts_last_90_tithes_and_offerings INT64, is_recurring_giver_new_locations BOOL, is_recurring_giver_new_locations_campus STRING, last_financial_transaction_new_locations_campus STRING, last_financial_transaction_new_locations_timestamp TIMESTAMP, is_recurring_giver_local_and_global_missions BOOL, is_recurring_giver_local_and_global_missions_campus STRING, last_financial_transaction_local_global_missions_campus STRING, last_financial_transaction_local_global_missions_timestamp TIMESTAMP, is_recurring_giver_free_resources BOOL, is_recurring_giver_free_resources_campus STRING, last_financial_transaction_free_resources_campus STRING, last_financial_transaction_free_resources_timestamp TIMESTAMP, is_recurring_giver_digital_reach BOOL, is_recurring_giver_digital_reach_campus STRING, is_recurring_giver_youversion_and_bible_translation BOOL, is_recurring_giver_youversion_and_bible_translation_campus STRING, last_financial_transaction_digital_reach_campus STRING, last_financial_transaction_digital_reach_timestamp TIMESTAMP, last_financial_transaction_youversion_bible_translation_campus STRING, last_financial_transaction_youversion_bible_translation_timestamp TIMESTAMP, last_financial_transaction_giving_type STRING> | Nested structure containing detailed giving patterns and recurring donation information across all Life.Church funds |
| `giving.is_recurring_giver_digital_reach` | BOOL | Boolean indicating if the person has an active recurring gift schedule for Digital Reach fund. Person level. TRUE if active scheduled transaction exists for this fund. Rock > Contributions > Scheduled Transaction List. |
| `giving.is_recurring_giver_digital_reach_campus` | STRING | The campus short code associated with the person's recurring Digital Reach gift. Person level. From the campus of the scheduled transaction detail. Rock > Contributions > Scheduled Transaction List. |
| `giving.is_recurring_giver_free_resources` | BOOL | Boolean indicating if the person has an active recurring gift schedule for Free Resources fund. Person level. TRUE if active scheduled transaction exists for this fund. Rock > Contributions > Scheduled Transaction List. |
| `giving.is_recurring_giver_free_resources_campus` | STRING | The campus short code associated with the person's recurring Free Resources gift. Person level. From the campus of the scheduled transaction detail. Rock > Contributions > Scheduled Transaction List. |
| `giving.is_recurring_giver_local_and_global_missions` | BOOL | Boolean indicating if the person has an active recurring gift schedule for Local & Global Missions fund. Person level. TRUE if active scheduled transaction exists for this fund. Rock > Contributions > Scheduled Transaction List. |
| `giving.is_recurring_giver_local_and_global_missions_campus` | STRING | The campus short code associated with the person's recurring Local & Global Missions gift. Person level. From the campus of the scheduled transaction detail. Rock > Contributions > Scheduled Transaction List. |
| `giving.is_recurring_giver_new_locations` | BOOL | Boolean indicating if the person has an active recurring gift schedule for New Locations fund. Person level. TRUE if active scheduled transaction exists for this fund. Rock > Profile > Scheduled Transactions. |
| `giving.is_recurring_giver_new_locations_campus` | STRING | The campus short code associated with the person's recurring New Locations gift. Person level. From the campus of the scheduled transaction detail. Rock > Contributions > Scheduled Transaction List. |
| `giving.is_recurring_giver_tithe_offerings` | BOOL | Boolean indicating if the person has an active recurring gift schedule for Tithes & Offerings fund. Person level. TRUE if active scheduled transaction exists for this fund. Rock > Contributions > Scheduled Transaction List. |
| `giving.is_recurring_giver_tithe_offerings_campus` | STRING | The campus short code associated with the person's recurring Tithes & Offerings gift. Person level. From the campus of the scheduled transaction detail.Rock > Contributions > Scheduled Transaction List. |
| `giving.is_recurring_giver_youversion_and_bible_translation` | BOOL | From Data Warehouse, using Rock financial transaction data. Household level. Whether or not the family has a recurring gift to the Youversion and Bible Translations fund. Rock > Profile > Transactions. Or Rock > Contributions. |
| `giving.is_recurring_giver_youversion_and_bible_translation_campus` | STRING | The campus short code associated with the person's recurring YouVersion & Bible Translation gift. Person level. From the campus of the scheduled transaction detail. Rock > Contributions > Scheduled Transaction List. |
| `giving.last_financial_transaction_digital_reach_campus` | STRING | The campus short code where the person made their most recent Digital Reach contribution. Person level. Extracted using window function for transactions matching Digital Reach fund descriptions defined in constants. NULL if person has never given to this fund. Rock > Profile > Transactions. |
| `giving.last_financial_transaction_digital_reach_timestamp` | TIMESTAMP | The timestamp of the person's most recent Digital Reach contribution. Person level. Calculated using ROW_NUMBER() window function filtering for Digital Reach fund transactions. Format: YYYY-MM-DD HH:MM:SS UTC. NULL if no Digital Reach giving history. Rock > Profile > Transactions. |
| `giving.last_financial_transaction_free_resources_campus` | STRING | The campus short code where the person made their most recent Free Resources contribution. Person level. Derived from the latest transaction where fund description matches Free Resources accounts in constants. NULL for non-givers to this fund. Rock > Profile > Transactions. |
| `giving.last_financial_transaction_free_resources_timestamp` | TIMESTAMP | The timestamp of the person's most recent Free Resources contribution. Person level. Identified as the top-ranked transaction by timestamp for Free Resources fund type. Format: YYYY-MM-DD HH:MM:SS UTC. NULL if person has never contributed to Free Resources. Rock > Profile > Transactions. |
| `giving.last_financial_transaction_giving_type` | STRING | The transaction type (e.g., 'Cash', 'Check', 'ACH', 'Credit Card', 'Non-Cash') of the person's most recent contribution across all fund types. Person level. Extracted using ROW_NUMBER() = 1 ordered by timestamp DESC across all transactions regardless of fund. Indicates the person's most recent giving method. Rock > Profile > Transactions. |
| `giving.last_financial_transaction_local_global_missions_campus` | STRING | The campus short code where the person made their most recent Local & Global Missions contribution. Person level. Extracted from transactions matching Local & Global Missions fund descriptions using window function ranking. NULL if no giving history to missions. Rock > Profile > Transactions. |
| `giving.last_financial_transaction_local_global_missions_timestamp` | TIMESTAMP | The timestamp of the person's most recent Local & Global Missions contribution. Person level. Calculated as the latest transaction timestamp for Local & Global Missions fund type. Format: YYYY-MM-DD HH:MM:SS UTC. NULL for non-missions givers. Rock > Profile > Transactions. |
| `giving.last_financial_transaction_new_locations_campus` | STRING | The campus short code where the person made their most recent New Locations contribution. Person level. Derived using ROW_NUMBER() = 1 for New Locations fund transactions ordered by timestamp DESC. NULL if person has never given to church expansion. Rock > Profile > Transactions. |
| `giving.last_financial_transaction_new_locations_timestamp` | TIMESTAMP | The timestamp of the person's most recent New Locations contribution. Person level. Identified as the most recent transaction for New Locations fund type using window function. Format: YYYY-MM-DD HH:MM:SS UTC. NULL for those who haven't given to this fund. Rock > Profile > Transactions. |
| `giving.last_financial_transaction_tithes_offerings_campus` | STRING | The campus short code (e.g., 'EDM', 'STW', 'ONL') where the person made their most recent Tithes & Offerings contribution. Person level. Extracted using ROW_NUMBER() window function ordering by timestamp DESC for transactions matching Tithes & Offerings fund descriptions. NULL if person has never given to this fund. Rock > Profile > Transactions. |
| `giving.last_financial_transaction_tithes_offerings_timestamp` | TIMESTAMP | The timestamp of the person's most recent Tithes & Offerings contribution. Person level. Identified using ROW_NUMBER() = 1 partitioned by person and fund type, ordered by timestamp DESC. Format: YYYY-MM-DD HH:MM:SS UTC. NULL if person has never given to this fund. Rock > Profile > Transactions. |
| `giving.last_financial_transaction_youversion_bible_translation_campus` | STRING | The campus short code where the person made their most recent YouVersion & Bible Translation contribution. Person level. Extracted from the latest transaction matching YouVersion & Bible Translation fund descriptions. NULL if no YouVersion giving history. Rock > Profile > Transactions. |
| `giving.last_financial_transaction_youversion_bible_translation_timestamp` | TIMESTAMP | The timestamp of the person's most recent YouVersion & Bible Translation contribution. Person level. Calculated using window function to find the latest YouVersion fund transaction. Format: YYYY-MM-DD HH:MM:SS UTC. NULL for non-YouVersion contributors. Rock > Profile > Transactions. |
| `giving.number_of_gifts_last_90_tithes_and_offerings` | INT64 | The count of Tithes & Offerings contributions made by the person in the last 90 days. Person level. Calculated by counting transactions where fund description matches Tithes & Offerings and timestamp >= CURRENT_TIMESTAMP - 90 days. COALESCE ensures 0 for non-givers. Used for recent giving activity analysis and donor engagement metrics. Rock > Profile > Transactions. |
| `giving_group_id` | INT64 | From Rock RMS Person.GivingGroupId. Person-level. ID for grouping family giving together. |
| `has_children` | BOOL | Boolean indicating whether or not the Adult person has children in their family, according to Rock RMS. |
| `has_children_in_school_grade` | STRUCT<has_children_in_school_grade_kindergarten BOOL, has_children_in_school_grade_1st BOOL, has_children_in_school_grade_2nd BOOL, has_children_in_school_grade_3rd BOOL, has_children_in_school_grade_4th BOOL, has_children_in_school_grade_5th BOOL, has_children_in_school_grade_6th BOOL, has_children_in_school_grade_7th BOOL, has_children_in_school_grade_8th BOOL, has_children_in_school_grade_freshman BOOL, has_children_in_school_grade_sophomore BOOL, has_children_in_school_grade_junior BOOL, has_children_in_school_grade_senior BOOL> | STRUCT containing boolean flags for each school grade level. Person level. Indicates which grades the adult has children enrolled in, based on family relationships and children's school_grade values. Used for parent communication targeting. Data sourced from Rock RMS Person and DefinedValue tables for grades pre-defined. |
| `has_children_in_school_grade.has_children_in_school_grade_1st` | BOOL | No description |
| `has_children_in_school_grade.has_children_in_school_grade_2nd` | BOOL | No description |
| `has_children_in_school_grade.has_children_in_school_grade_3rd` | BOOL | No description |
| `has_children_in_school_grade.has_children_in_school_grade_4th` | BOOL | No description |
| `has_children_in_school_grade.has_children_in_school_grade_5th` | BOOL | No description |
| `has_children_in_school_grade.has_children_in_school_grade_6th` | BOOL | No description |
| `has_children_in_school_grade.has_children_in_school_grade_7th` | BOOL | No description |
| `has_children_in_school_grade.has_children_in_school_grade_8th` | BOOL | No description |
| `has_children_in_school_grade.has_children_in_school_grade_freshman` | BOOL | No description |
| `has_children_in_school_grade.has_children_in_school_grade_junior` | BOOL | No description |
| `has_children_in_school_grade.has_children_in_school_grade_kindergarten` | BOOL | No description |
| `has_children_in_school_grade.has_children_in_school_grade_senior` | BOOL | No description |
| `has_children_in_school_grade.has_children_in_school_grade_sophomore` | BOOL | No description |
| `has_form_submission_email_subscription_lco_service_reminder` | BOOL | From form_submitted table. Person level. Boolean flag indicating whether the person has submitted the Life.Church Online email subscription form to receive service reminders. TRUE if they've opted in, FALSE if no submission found. Used to determine email eligibility. |
| `home_campus` | STRING | Synonymous with Rock Campus. See lc_campus for description. |
| `home_campus_region` | STRING | The geographical region or area grouping for the campus (e.g., 'Region 2A - Bryan Hill', 'Region 1B - Oklahoma'). Sourced from Rock RMS Campus Area attribute via campus_staging table. Used for regional analysis and leadership reporting structures. |
| `household` | STRUCT<family_name STRING, campus STRING, first_lifekids_checkin_timestamp TIMESTAMP, first_lifekids_checkin_campus STRING, last_lifekids_checkin_timestamp TIMESTAMP, last_lifekids_checkin_campus STRING, first_financial_transaction_timestamp TIMESTAMP, first_financial_transaction_campus INT64, last_financial_transaction_timestamp TIMESTAMP, last_financial_transaction_campus INT64, last_checkin_timestamp TIMESTAMP, last_checkin_campus STRING, first_checkin_timestamp TIMESTAMP, first_checkin_campus STRING, address_1 STRING, address_2 STRING, postal_code STRING, city STRING, state_province STRING, country STRING, county STRING, longitude FLOAT64, latitude FLOAT64, is_legacy_team_prospect BOOL, first_household_weekend_attendance_timestamp TIMESTAMP, first_household_weekend_attendance_campus STRING, last_household_weekend_attendance_timestamp TIMESTAMP, last_household_weekend_attendance_campus STRING, first_household_weekend_physical_attendance_timestamp TIMESTAMP, first_household_weekend_physical_attendance_campus STRING, last_household_weekend_physical_attendance_timestamp TIMESTAMP, last_household_weekend_physical_attendance_campus STRING, last_household_attendance_timestamp_the_loop TIMESTAMP, last_household_attendance_campus_short_code_the_loop STRING, last_household_attendance_timestamp_let_there_be_light TIMESTAMP, last_household_attendance_campus_short_code_let_there_be_light STRING, last_household_attendance_timestamp_in_the_jungle TIMESTAMP, last_household_attendance_campus_short_code_in_the_jungle STRING, last_household_attendance_timestamp_starry_night TIMESTAMP, last_household_attendance_campus_short_code_starry_night STRING, last_household_attendance_timestamp_under_the_sea TIMESTAMP, last_household_attendance_campus_short_code_under_the_sea STRING, last_household_attendance_timestamp_konnect TIMESTAMP, last_household_attendance_campus_short_code_konnect STRING, last_household_attendance_timestamp_the_garden TIMESTAMP, last_household_attendance_campus_short_code_the_garden STRING, last_household_attendance_timestamp_switch_student TIMESTAMP, last_household_attendance_campus_short_code_switch_student STRING, last_household_attendance_timestamp_crosstown TIMESTAMP, last_household_attendance_campus_short_code_crosstown STRING, last_household_attendance_timestamp_the_ark TIMESTAMP, last_household_attendance_campus_short_code_the_ark STRING> | From Data Warehouse, using Rock person data. Household level. The full name of the family. Rock > Profile > Family Attributes. |
| `household.address_1` | STRING | From Rock RMS Location.Street1. Entity level. The primary street address line for the entity physical location. |
| `household.address_2` | STRING | From Rock RMS Location.Street2. Entity level. The secondary address line (suite, building, etc). Returns empty string if NULL. |
| `household.campus` | STRING | From Data Warehouse, using Rock person data. Person level. The main, home, primary, or preferred campus of the person. This is the best source for identifing which campus a person belongs to. Rock > Profile > Main Contact Details. |
| `household.city` | STRING | From Rock RMS Location. Entity level. The city where the entity is located. |
| `household.country` | STRING | From location.country. Person level. The country of the person's home address. Typically 'US' for most records. Used for international attendee identification. |
| `household.county` | STRING | From person_location table. Family-level. County name. Rock > Person > Address. |
| `household.family_name` | STRING | From household_staging table. Household level. The last name or designated family name for the household. Rock > People > Family. |
| `household.first_checkin_campus` | STRING | From Data Warehouse, using Rock attendance data. Household level. The campus where the family first checked in for attendance (not serving). Rock > History > Attendance History. |
| `household.first_checkin_timestamp` | TIMESTAMP | From Data Warehouse, using Rock attendance data. Household level. The date the family first checked in for attendance (not serving). Rock > History > Attendance History. |
| `household.first_financial_transaction_campus` | INT64 | From Data Warehouse, using Rock financial transaction data. Household level. The campus where the family first gave a gift. Rock > Profile > Transactions. Or Rock > Contributions. |
| `household.first_financial_transaction_timestamp` | TIMESTAMP | From Data Warehouse, using Rock financial transaction data. Household level. The date the family first gave a gift. Rock > Profile > Transactions. Or Rock > Contributions. |
| `household.first_household_weekend_attendance_campus` | STRING | From Data Warehouse, using Rock attendance data. Household level. The campus where the family first checked in to attend (not serve) on a weekend. Rock > History > Attendance History. |
| `household.first_household_weekend_attendance_timestamp` | TIMESTAMP | From Data Warehouse, using Rock attendance data. Household level. The date the family first checked in to attend (not serve) on a weekend. Rock > History > Attendance History. |
| `household.first_household_weekend_physical_attendance_campus` | STRING | From Data Warehouse, using Rock attendance data. Household level. The campus where the family first checked in to attend (not serve) physically (not LCO) on a weekend. Rock > History > Attendance History. |
| `household.first_household_weekend_physical_attendance_timestamp` | TIMESTAMP | From Data Warehouse, using Rock attendance data. Household level. The date the family first checked in to attend (not serve) physicaly (not LCO) on a weekend. Rock > History > Attendance History. |
| `household.first_lifekids_checkin_campus` | STRING | From Rock attendance tables for NextGen. Family level displayed at person level. The campus code where this person's household first attended LifeKids. NULL if no family LifeKids attendance. |
| `household.first_lifekids_checkin_timestamp` | TIMESTAMP | From Rock attendance tables for NextGen. Family level displayed at person level. The timestamp of the first LifeKids check-in by any member of this person's household. NULL if no family LifeKids attendance. |
| `household.is_legacy_team_prospect` | BOOL | From household_staging table calculated using financial transactions. Household level. Boolean flag indicating whether any non-staff member in this household has contributed at least 20,000 within the past 12 months, making them a prospect for the Legacy Team giving program. This flag is applied to all family members since giving is viewed at the household level - if one family member qualifies based on their giving, the entire household is marked as a prospect. Excludes households where any member is already a Legacy Team member (is_legacy_team_member = TRUE). Rock > Contributions. |
| `household.last_checkin_campus` | STRING | From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in for attendance (not serving). Rock > History > Attendance History. |
| `household.last_checkin_timestamp` | TIMESTAMP | From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in for attendance (not serving). Rock > History > Attendance History. |
| `household.last_financial_transaction_campus` | INT64 | From Data Warehouse, using Rock financial transaction data. Household level. The campus where the family last gave a gift. Rock > Profile > Transactions. Or Rock > Contributions. |
| `household.last_financial_transaction_timestamp` | TIMESTAMP | From Data Warehouse, using Rock financial transaction data. Household level. The date the family last gave a gift. Rock > Profile > Transactions. Or Rock > Contributions. |
| `household.last_household_attendance_campus_short_code_crosstown` | STRING | From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in a child to the Crosstown room. Rock > History > Attendance History. |
| `household.last_household_attendance_campus_short_code_in_the_jungle` | STRING | From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in a child to the In The Jungle room. Rock > History > Attendance History. |
| `household.last_household_attendance_campus_short_code_konnect` | STRING | From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in a child to the Konnect room. Rock > History > Attendance History. |
| `household.last_household_attendance_campus_short_code_let_there_be_light` | STRING | From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in a child to Lifekids. Rock > History > Attendance History. |
| `household.last_household_attendance_campus_short_code_starry_night` | STRING | From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in a child to the Starry Night room. Rock > History > Attendance History. |
| `household.last_household_attendance_campus_short_code_switch_student` | STRING | From Rock attendance tables for Switch. Family level displayed at person level. The campus code where this person's household most recently attended Switch. NULL if no family Switch attendance. |
| `household.last_household_attendance_campus_short_code_the_ark` | STRING | From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in a child to The Ark room. Rock > History > Attendance History. |
| `household.last_household_attendance_campus_short_code_the_garden` | STRING | From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in a child to the In The Garden room. Rock > History > Attendance History. |
| `household.last_household_attendance_campus_short_code_the_loop` | STRING | From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in a child to The Loop room. Rock > History > Attendance History. |
| `household.last_household_attendance_campus_short_code_under_the_sea` | STRING | From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in a child to the Under The Sea room. Rock > History > Attendance History. |
| `household.last_household_attendance_timestamp_crosstown` | TIMESTAMP | From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in a child to the Crosstown room. Rock > History > Attendance History. |
| `household.last_household_attendance_timestamp_in_the_jungle` | TIMESTAMP | From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in a child to the In The Jungle room. Rock > History > Attendance History. |
| `household.last_household_attendance_timestamp_konnect` | TIMESTAMP | From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in a child to the Konnect room. Rock > History > Attendance History. |
| `household.last_household_attendance_timestamp_let_there_be_light` | TIMESTAMP | From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in a child to Lifekids. Rock > History > Attendance History. |
| `household.last_household_attendance_timestamp_starry_night` | TIMESTAMP | From Data Warehosue, using Rock attendance data. Person level. The date the person last checked into serve in Switch. Rock > History > Attendance History. |
| `household.last_household_attendance_timestamp_switch_student` | TIMESTAMP | From Rock attendance tables for Switch. Family level displayed at person level. The timestamp of the most recent Switch check-in by any member of this person's household. NULL if no family Switch attendance. |
| `household.last_household_attendance_timestamp_the_ark` | TIMESTAMP | From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in a child to The Ark room. Rock > History > Attendance History. |
| `household.last_household_attendance_timestamp_the_garden` | TIMESTAMP | From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in a child to the In The Garden room. Rock > History > Attendance History. |
| `household.last_household_attendance_timestamp_the_loop` | TIMESTAMP | From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in a child to The Loop room. Rock > History > Attendance History. |
| `household.last_household_attendance_timestamp_under_the_sea` | TIMESTAMP | From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in a child to the Under The Sea room. Rock > History > Attendance History. |
| `household.last_household_weekend_attendance_campus` | STRING | From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in to attend (not serve) on a weekend. Rock > History > Attendance History. |
| `household.last_household_weekend_attendance_timestamp` | TIMESTAMP | From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in to attend (not serve) on a weekend. Rock > History > Attendance History. |
| `household.last_household_weekend_physical_attendance_campus` | STRING | From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in to attend (not serve) physically (not LCO) on a weekend. Rock > History > Attendance History. |
| `household.last_household_weekend_physical_attendance_timestamp` | TIMESTAMP | From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in to attend (not serve) physicaly (not LCO) on a weekend. Rock > History > Attendance History. |
| `household.last_lifekids_checkin_campus` | STRING | From Rock attendance tables for NextGen. Family level displayed at person level. The campus code where this person's household most recently attended LifeKids. NULL if no family LifeKids attendance. |
| `household.last_lifekids_checkin_timestamp` | TIMESTAMP | From Rock attendance tables for NextGen. Family level displayed at person level. The timestamp of the most recent LifeKids check-in by any member of this person's household. NULL if no family LifeKids attendance. |
| `household.latitude` | FLOAT64 | Extracted from Rock RMS Location.GeoPoint using custom function. Entity level. The latitude coordinate of the entity location in decimal degrees. Used for mapping and distance calculations. |
| `household.longitude` | FLOAT64 | Extracted from Rock RMS Location.GeoPoint using custom function. Entity level. The longitude coordinate of the entity location in decimal degrees. Used for mapping and distance calculations. |
| `household.postal_code` | STRING | From Rock RMS Location.postalcode. Person level. The ZIP code of the person's home address. Used for geographic analysis and drive time calculations. |
| `household.state_province` | STRING | From person_location table. Family-level. Full state/province name. Rock > Person > Address. |
| `hubspot_contact_email` | STRING | From person_hubspot_id intermediate table. Person-level. The validated email address associated with the HubSpot match. Either pulled from HubSpot contact.property_email or falls back to the Rock email used for matching. Must pass email regex validation. |
| `hubspot_contact_id` | STRING | From person_hubspot_id intermediate table. Person-level. The best match identifier linking Rock person to HubSpot contact, determined through complex matching logic using primary/secondary emails and name validation. Can be either a HubSpot contact ID (numeric) or an email address. Prioritizes matches with most accurate name alignment. |
| `is_adult` | BOOL | Boolean indicating whether or not the person is an adult in their family. TRUE indicates the person is an Adult. Rule of thumb defines a person as Adult when older than 18 years old. FALSE indicates the person is a Child or Unknown. |
| `is_app_connection_enabled` | BOOL | Boolean indicating if the person has app connection features enabled. |
| `is_app_scheduling_enabled` | BOOL | Boolean indicating if the person has app scheduling features enabled. |
| `is_app_user` | BOOL | From Data Warehouse, using Segment app data. Person level. Whether the person has ever used the app or not. Segment > Unify > Profile Explorer > Search User (Person Alias Id) > Traits > Computed Traits > first_app_usage. |
| `is_banned_giver` | STRING | String value ('True') indicating the person has been flagged as a banned giver, typically due to fraudulent activity or chargebacks. Person level. From Rock person attribute BannedGiver. Rock > Profile > Person Profile > Attributes > Banned Giver. |
| `is_business` | BOOL | From Rock RMS Person.RecordTypeValueId. Person-level. TRUE if record type is Business (ID=2), FALSE for individual persons. Rock > Person. |
| `is_deceased` | BOOL | From Rock RMS Person.isdeceased. Person level. Boolean flag indicating if the person is marked as deceased in Rock RMS. TRUE if deceased, FALSE if living. Important for data hygiene and filtering. |
| `is_deletion_requested` | BOOL | Calculated field. Person-level. TRUE if person has requested data deletion. FALSE otherwise. |
| `is_legacy_team_member` | BOOL | Boolean indicating whether the person is a Legacy Team member. |
| `is_legacy_team_prospect` | BOOL | From household_staging table calculated using financial transactions. Household level. Boolean flag indicating whether any non-staff member in this household has contributed at least 20,000 within the past 12 months, making them a prospect for the Legacy Team giving program. This flag is applied to all family members since giving is viewed at the household level - if one family member qualifies based on their giving, the entire household is marked as a prospect. Excludes households where any member is already a Legacy Team member (is_legacy_team_member = TRUE). Rock > Contributions. |
| `is_lifegroup_leader` | BOOL | Boolean indicating whether or not the person is a LifeGroup leader. Defaults to FALSE if null. |
| `is_rms_person_inactive` | BOOL | From Rock RMS Person.RecordStatusValueId. Person-level. TRUE if record status is Inactive (matching constant). NULL if active. Rock > Person. |
| `is_staff` | BOOL | Boolean indicating whether or not the person is a staff member for Life.Church. Defaults to FALSE if null. |
| `is_statement_suppressed` | STRING | String value ('True') indicating the person has opted out of receiving printed contribution statements. Person level. From Rock person attribute SuppressSendingContributionStatements. Rock > Profile > Person Profile > Attributes > Suppress Sending Contribution Statements. |
| `is_volunteer` | BOOL | Boolean indicating if the person is currently serving as a volunteer. |
| `job_title` | STRING | The job title from the Employee Sync Information avalable in RMS. Person level. From Rock person attributes. Rock > Profile > Person Profile > Extended Attributes > Employment Information Sync |
| `last_attendance_app_campus` | STRING | From attender_check_in filtered for app check-ins. Person level. The campus code where the person most recently checked in via the app. Rock > Person > History. |
| `last_attendance_app_timestamp` | TIMESTAMP | From attender_check_in filtered for app check-ins. Person level. The timestamp of the person's most recent attendance check-in via the Life.Church mobile app. NULL if never used app check-in. Rock > Person > History. |
| `last_attendance_campus` | STRING | From attendance_combined filtered for non-volunteer attendance. Person level. The campus code where the person most recently attended a weekend experience. Rock > Person > History. |
| `last_attendance_combined_campus` | STRING | From attendance_combined including all attendance types. Person level. The campus code where the person had their most recent check-in of any type. |
| `last_attendance_combined_parent_group` | STRING | From attendance_combined including all attendance types. Person level. The parent group name of the person's most recent check-in. Indicates current engagement area. . |
| `last_attendance_combined_timestamp` | TIMESTAMP | From attendance_combined including all attendance types. Person level. The timestamp of the person's most recent check-in of any type. The latest interaction with Life.Church. |
| `last_attendance_host_team_campus` | STRING | From attender_check_in via parent group pivot. Person level. The campus code where the person most recently served on Host Team. Rock > Person > History. |
| `last_attendance_host_team_timestamp` | TIMESTAMP | From attender_check_in via parent group pivot. Person level. The timestamp of the person's most recent check-in as a Host Team volunteer. NULL if never served. Rock > Person > History. |
| `last_attendance_lifekids_campus_crosstown` | STRING | From attender_check_in via attendance group pivot. Person level. The campus code where the person most recently attended Crosstown LifeKids room. Rock > Person > History. |
| `last_attendance_lifekids_campus_in_the_jungle` | STRING | From attender_check_in via attendance group pivot. Person level. The campus code where the person most recently attended In The Jungle LifeKids room. Rock > Person > History. |
| `last_attendance_lifekids_campus_konnect` | STRING | From attender_check_in via attendance group pivot. Person level. The campus code where the person most recently attended Konnect LifeKids room. Rock > Person > History. |
| `last_attendance_lifekids_campus_let_there_be_light` | STRING | From attender_check_in via attendance group pivot. Person level. The campus code where the person most recently attended Let There Be Light LifeKids room. Rock > Person > History. |
| `last_attendance_lifekids_campus_starry_night` | STRING | From attender_check_in via attendance group pivot. Person level. The campus code where the person most recently attended Starry Night LifeKids room. Rock > Person > History. |
| `last_attendance_lifekids_campus_the_ark` | STRING | From attender_check_in via attendance group pivot. Person level. The campus code where the person most recently attended The Ark LifeKids room. Rock > Person > History. |
| `last_attendance_lifekids_campus_the_garden` | STRING | From attender_check_in via attendance group pivot. Person level. The campus code where the person most recently attended The Garden LifeKids room. Rock > Person > History. |
| `last_attendance_lifekids_campus_the_loop` | STRING | From attender_check_in via attendance group pivot. Person level. The campus code where the person most recently attended The Loop LifeKids room. Rock > Person > History. |
| `last_attendance_lifekids_campus_under_the_sea` | STRING | From attender_check_in via attendance group pivot. Person level. The campus code where the person most recently attended Under The Sea LifeKids room. Rock > Person > History. |
| `last_attendance_lifekids_timestamp_crosstown` | TIMESTAMP | From attender_check_in via attendance group pivot. Person level. The timestamp of the person's most recent check-in to Crosstown LifeKids room. NULL if never attended. Rock > Person > History. |
| `last_attendance_lifekids_timestamp_in_the_jungle` | TIMESTAMP | From attender_check_in via attendance group pivot. Person level. The timestamp of the person's most recent check-in to In The Jungle LifeKids room. NULL if never attended. Rock > Person > History. |
| `last_attendance_lifekids_timestamp_konnect` | TIMESTAMP | From attender_check_in via attendance group pivot. Person level. The timestamp of the person's most recent check-in to Konnect LifeKids room. NULL if never attended. Rock > Person > History. |
| `last_attendance_lifekids_timestamp_let_there_be_light` | TIMESTAMP | From attender_check_in via attendance group pivot. Person level. The timestamp of the person's most recent check-in to Let There Be Light LifeKids room. NULL if never attended. Rock > Person > History. |
| `last_attendance_lifekids_timestamp_starry_night` | TIMESTAMP | From attender_check_in via attendance group pivot. Person level. The timestamp of the person's most recent check-in to Starry Night LifeKids room. NULL if never attended. Rock > Person > History. |
| `last_attendance_lifekids_timestamp_the_ark` | TIMESTAMP | From attender_check_in via attendance group pivot. Person level. The timestamp of the person's most recent check-in to The Ark LifeKids room. NULL if never attended. Rock > Person > History. |
| `last_attendance_lifekids_timestamp_the_garden` | TIMESTAMP | From attender_check_in via attendance group pivot. Person level. The timestamp of the person's most recent check-in to The Garden LifeKids room. NULL if never attended. Rock > Person > History. |
| `last_attendance_lifekids_timestamp_the_loop` | TIMESTAMP | From attender_check_in via attendance group pivot. Person level. The timestamp of the person's most recent check-in to The Loop LifeKids room. NULL if never attended. Rock > Person > History. |
| `last_attendance_lifekids_timestamp_under_the_sea` | TIMESTAMP | From attender_check_in via attendance group pivot. Person level. The timestamp of the person's most recent check-in to Under The Sea LifeKids room. NULL if never attended. Rock > Person > History. |
| `last_attendance_switch_campus` | STRING | From attender_check_in via parent group pivot. Person level. The campus code where the person most recently attended Switch student ministry. Rock > Person > History. |
| `last_attendance_switch_campus_student` | STRING | From attender_check_in via attendance group pivot. Person level. The campus code where the person most recently attended Switch student ministry. Rock > Person > History. |
| `last_attendance_switch_timestamp` | TIMESTAMP | From attender_check_in via parent group pivot. Person level. The timestamp of the person's most recent check-in to Switch student ministry. NULL if never attended. Rock > Person > History. |
| `last_attendance_switch_timestamp_student` | TIMESTAMP | From attender_check_in via attendance group pivot. Person level. The timestamp of the person's most recent check-in to Switch student ministry. NULL if never attended. Rock > Person > History. |
| `last_attendance_timestamp` | TIMESTAMP | From attendance_combined filtered for non-volunteer attendance. Person level. The timestamp of the person's most recent weekend attendance at any campus. Rock > Person > History. |
| `last_conditional_attendance_agreement_status` | STRING | From Rock defined values for standard requirements. Person level. The status of the person's most recent conditional attendance agreement. |
| `last_conditional_attendance_agreement_timestamp` | TIMESTAMP | From Rock attribute matrix for standard requirements. Person level. The timestamp of the person's most recent conditional attendance agreement. NULL if no agreement. Rock > Person > Extended Attributes. |
| `last_connection_request_campus` | STRING | From ConnectionRequest table. Person level. The campus associated with their most recent connection request. |
| `last_connection_request_timestamp` | TIMESTAMP | From ConnectionRequest table. Person level. The most recent timestamp when this person submitted any connection request. |
| `last_digital_invite_timestamp` | TIMESTAMP | From Interaction table filtered by digital invite component. Person level. The most recent timestamp when this person sent a digital invite to someone. |
| `last_financial_transaction_campus` | STRING | The campus short code where the person made their most recent financial contribution. Person level. Retrieved from the campus associated with the last transaction. Rock > Profile > Transactions. |
| `last_financial_transaction_timestamp` | TIMESTAMP | The timestamp of the person's most recent financial contribution to Life.Church. Person level. Calculated as the latest transaction from fact_giving where amount >= 0 and is_successful = TRUE. Rock > Profile > Transactions. |
| `last_form_submission_account_acquisition_timestamp_addiction` | TIMESTAMP | Calculated via PIVOT MAX on form_submission_timestamp. Person level. The most recent timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department. Indicates continued or renewed interest in this topic area and church engagement. |
| `last_form_submission_account_acquisition_timestamp_anxiety` | TIMESTAMP | Calculated via PIVOT MAX on form_submission_timestamp. Person level. The most recent timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department. Indicates continued or renewed interest in this topic area and church engagement. |
| `last_form_submission_account_acquisition_timestamp_burnout` | TIMESTAMP | Calculated via PIVOT MAX on form_submission_timestamp. Person level. The most recent timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department. Indicates continued or renewed interest in this topic area and church engagement. |
| `last_form_submission_account_acquisition_timestamp_finance` | TIMESTAMP | Calculated via PIVOT MAX on form_submission_timestamp. Person level. The most recent timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department. Indicates continued or renewed interest in this topic area and church engagement. |
| `last_form_submission_account_acquisition_timestamp_friendship` | TIMESTAMP | Calculated via GREATEST function combining friendship and friendships form variants. Person level. The most recent timestamp when this person submitted any friendship-related account acquisition form through HubSpot paid marketing campaigns managed by the Reach department, accounting for historical form naming variations. Indicates continued or renewed interest in this topic area and church engagement. |
| `last_form_submission_account_acquisition_timestamp_grief` | TIMESTAMP | Calculated via PIVOT MAX on form_submission_timestamp. Person level. The most recent timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department. Indicates continued or renewed interest in this topic area and church engagement. |
| `last_form_submission_account_acquisition_timestamp_habits` | TIMESTAMP | Calculated via PIVOT MAX on form_submission_timestamp. Person level. The most recent timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department. Indicates continued or renewed interest in this topic area and church engagement. |
| `last_form_submission_account_acquisition_timestamp_parenting` | TIMESTAMP | Calculated via PIVOT MAX on form_submission_timestamp. Person level. The most recent timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department. Indicates continued or renewed interest in this topic area and church engagement. |
| `last_form_submission_email_subscription_campus_lco_service_reminder` | STRING | From form_submitted and campus_staging tables. Person level. The three-letter campus code associated with the person's most recent LCO email subscription form submission. |
| `last_form_submission_email_subscription_timestamp_lco_service_reminder` | TIMESTAMP | From form_submitted table. Person level. The UTC timestamp of when the person most recently submitted the LCO email subscription form. Used to track subscription recency and determine service time preferences. |
| `last_form_submission_next_steps_campus_baptism` | STRING | Filtered for specific form using constants. Person level. The campus where this person most recently submitted this next steps form. |
| `last_form_submission_next_steps_campus_commit_to_christ` | STRING | Filtered for specific form using constants. Person level. The campus where this person most recently submitted this next steps form. |
| `last_form_submission_next_steps_campus_general_question` | STRING | Filtered for specific form using constants. Person level. The campus where this person most recently submitted this next steps form. |
| `last_form_submission_next_steps_campus_im_new_here` | STRING | Filtered for specific form using constants. Person level. The campus where this person most recently submitted this next steps form. |
| `last_form_submission_next_steps_campus_known` | STRING | Filtered for specific form using constants. Person level. The campus where this person most recently submitted this next steps form. |
| `last_form_submission_next_steps_campus_prayer_request` | STRING | Filtered for specific form using constants. Person level. The campus where this person most recently submitted this next steps form. |
| `last_form_submission_next_steps_campus_renewing_commitment_to_christ` | STRING | Filtered for specific form using constants. Person level. The campus where this person most recently submitted this next steps form. |
| `last_form_submission_next_steps_timestamp_baptism` | TIMESTAMP | Filtered for specific form using constants. Person level. The most recent timestamp when this person submitted this next steps form, indicating continued or renewed spiritual engagement. |
| `last_form_submission_next_steps_timestamp_commit_to_christ` | TIMESTAMP | Filtered for specific form using constants. Person level. The most recent timestamp when this person submitted this next steps form, indicating continued or renewed spiritual engagement. |
| `last_form_submission_next_steps_timestamp_general_question` | TIMESTAMP | Filtered for specific form using constants. Person level. The most recent timestamp when this person submitted this next steps form, indicating continued or renewed spiritual engagement. |
| `last_form_submission_next_steps_timestamp_im_new_here` | TIMESTAMP | Filtered for specific form using constants. Person level. The most recent timestamp when this person submitted this next steps form, indicating continued or renewed spiritual engagement. |
| `last_form_submission_next_steps_timestamp_known` | TIMESTAMP | Filtered for specific form using constants. Person level. The most recent timestamp when this person submitted this next steps form, indicating continued or renewed spiritual engagement. |
| `last_form_submission_next_steps_timestamp_prayer_request` | TIMESTAMP | Filtered for specific form using constants. Person level. The most recent timestamp when this person submitted this next steps form, indicating continued or renewed spiritual engagement. |
| `last_form_submission_next_steps_timestamp_renewing_commitment_to_christ` | TIMESTAMP | Filtered for specific form using constants. Person level. The most recent timestamp when this person submitted this next steps form, indicating continued or renewed spiritual engagement. |
| `last_household_attendance_switch_timestamp` | TIMESTAMP | From Rock attendance tables for Switch. Family level displayed at person level. The timestamp of the most recent Switch check-in by any member of this person's household. NULL if no family Switch attendance. |
| `last_lco_engagement_timestamp` | TIMESTAMP | The timestamp of the person's most recent Life.Church Online (LCO) engagement or campus-less interaction. This includes attendance, serving, financial transactions, form submissions, volunteer interest forms, person creation records, baptism attributes, and known attendance records where the campus is NULL or 'INT' (LCO indicator). NULL indicates the person has never had a recorded LCO engagement. |
| `last_name` | STRING | From Data Warehouse, using Rock person data. Person level. The last name of the person. Rock > Profile > Main Contact Details. |
| `last_physical_campus_engagement_timestamp` | TIMESTAMP | The timestamp of the person's most recent engagement at any physical Life.Church campus location. This includes physical attendance, serving, financial transactions, form submissions, volunteer interest forms, person creation records, baptism attributes, and known attendance records where the campus is not NULL and not 'INT' (LCO). NULL indicates the person has never had a recorded physical campus engagement. |
| `last_row_update_timestamp` | TIMESTAMP | From Fivetran, Person._fivetran_synced. Person-level. Timestamp of last Fivetran sync for this record. Format: TIMESTAMP. |
| `last_scheduled_financial_transaction_timestamp` | TIMESTAMP | The timestamp of the most recent transaction that was part of a scheduled/recurring gift. Person level. Latest transaction timestamp where financial_transaction_schedule_id is not null. Rock > Profile > Scheduled Transactions > Transaction History. |
| `last_segment_interaction_timestamp` | TIMESTAMP | From aggregated Segment events. Person level. The latest timestamp across all tracked sources, representing the person's most recent digital interaction with any Life.Church platform. Used to determine overall engagement recency. Calculated as MAX of all source-specific last interactions. |
| `last_segment_interaction_timestamp_chop_prod` | TIMESTAMP | From Segment events table. Person level. The timestamp of the person's most recent interaction with Church Online Platform. Indicates latest online church engagement. |
| `last_segment_interaction_timestamp_finds_life_prod` | TIMESTAMP | From Segment events table. Person level. The timestamp of the person's most recent interaction with finds.life website. Shows latest church finder usage. |
| `last_segment_interaction_timestamp_hubspot_email_events_dev` | TIMESTAMP | From Segment events table. Person level. The timestamp of the person's most recent email interaction tracked through HubSpot. Shows latest email engagement activity. |
| `last_segment_interaction_timestamp_hubspot_form_submission` | TIMESTAMP | From Segment events table. Person level. The timestamp of the person's most recent form submission tracked through HubSpot. Records latest form completion. |
| `last_segment_interaction_timestamp_kotlin_android` | TIMESTAMP | From Segment events table. Person level. The timestamp of the person's most recent interaction with the Life.Church Android app (Kotlin version). Tracks current Android app usage. |
| `last_segment_interaction_timestamp_lc_ios_swift` | TIMESTAMP | From Segment events table. Person level. The timestamp of the person's most recent interaction with the Life.Church iOS app (Swift version). Tracks current iOS app usage. |
| `last_segment_interaction_timestamp_lcweb` | TIMESTAMP | From Segment events table. Person level. The timestamp of the person's most recent interaction with the main Life.Church website. Shows latest web engagement. |
| `last_segment_interaction_timestamp_lifechurch_android` | TIMESTAMP | From Segment events table. Person level. The timestamp of the person's most recent interaction with the legacy Life.Church Android app. Tracks continued usage of older Android version. |
| `last_segment_interaction_timestamp_lifechurch_ios` | TIMESTAMP | From Segment events table. Person level. The timestamp of the person's most recent interaction with the legacy Life.Church iOS app. Tracks continued usage of older iOS version. |
| `last_segment_interaction_timestamp_rms_prod_js` | TIMESTAMP | From Segment events table. Person level. The timestamp of the person's most recent interaction tracked by Rock RMS JavaScript SDK. Shows latest Rock-integrated web activity. |
| `last_served_activity` | STRING | From volunteer_check_in table. Person level. The specific serving role or activity name from the person's most recent volunteer check-in. |
| `last_served_campus` | STRING | The campus where the person last served/volunteered. |
| `last_served_host_team_activity` | STRING | From volunteer_check_in table. Person level. The specific Host Team role from the person's most recent Host Team check-in. |
| `last_served_host_team_campus` | STRING | From Data Warehouse, using Rock attendance data. Person level. The campus where the person last checked in to serve with Host Team. Rock > History > Attendance History. |
| `last_served_host_team_timestamp` | TIMESTAMP | From volunteer_check_in table. Person level. The timestamp when the person most recently served in Host Team ministry. |
| `last_served_operations_activity` | STRING | From Data Warehosue, using Rock attendance data. Person level. The activity for which the person last checked into serve in Operations. Rock > History > Attendance History. |
| `last_served_operations_campus` | STRING | From Data Warehosue, using Rock attendance data. Person level. The campus where the person last checked into serve in Operations. Rock > History > Attendance History. |
| `last_served_operations_timestamp` | TIMESTAMP | From volunteer_check_in table. Person level. The timestamp when the person most recently served in Operations ministry. |
| `last_served_switch_activity` | STRING | From Data Warehosue, using Rock attendance data. Person level. The activity for which the person last checked into serve in Switch. Rock > History > Attendance History. |
| `last_served_switch_campus` | STRING | From Data Warehosue, using Rock attendance data. Person level. The campus where the person last checked into serve in Switch. Rock > History > Attendance History. |
| `last_served_switch_timestamp` | TIMESTAMP | From volunteer_check_in table. Person level. The timestamp when the person most recently served in Switch youth ministry. |
| `last_served_timestamp` | TIMESTAMP | From volunteer_check_in table. Person level. The timestamp of the person's most recent volunteer serving check-in across all ministries. Indicates current volunteer engagement. |
| `last_served_worship_activity` | STRING | From volunteer_check_in table. Person level. The specific Worship Team role from the person's most recent Worship check-in. |
| `last_served_worship_campus` | STRING | From volunteer_check_in and Campus tables. Person level. The three-letter campus code where the person most recently served on Worship Team. |
| `last_served_worship_timestamp` | TIMESTAMP | From volunteer_check_in table. Person level. The timestamp when the person most recently served on Worship Team. |
| `last_step_next_steps_campus_you_said_yes` | STRING | From Step table filtered by YSY step type. Person level. The campus where this person most recently completed the You Said Yes step. |
| `last_step_next_steps_timestamp_you_said_yes` | TIMESTAMP | From Step table filtered by YSY step type. Person level. The most recent timestamp when this person completed the You Said Yes step. |
| `last_volunteer_campus` | STRING | From attendance_combined filtered for volunteer attendance. Person level. The campus code where the person most recently served as a volunteer. |
| `last_volunteer_interest_campus_short_code_host_team` | STRING | From volunteer_interest_forms table. Person level. The three-letter campus code from the person's most recent Host Team volunteer interest submission. |
| `last_volunteer_interest_campus_short_code_lifegroups_lifemissions` | STRING | From volunteer_interest_forms table. Person level. The three-letter campus code from the person's most recent LifeGroups/LifeMissions interest submission. |
| `last_volunteer_interest_campus_short_code_media` | STRING | From volunteer_interest_forms table. Person level. The three-letter campus code from the person's most recent Media/Tech volunteer interest submission. |
| `last_volunteer_interest_campus_short_code_operations_team` | STRING | From volunteer_interest_forms table. Person level. The three-letter campus code from the person's most recent Operations volunteer interest submission. |
| `last_volunteer_interest_campus_short_code_switch` | STRING | From volunteer_interest_forms table. Person level. The three-letter campus code from the person's most recent Switch volunteer interest submission. |
| `last_volunteer_interest_host_team_timestamp` | TIMESTAMP | From volunteer_interest_forms table. Person level. The timestamp when the person most recently submitted a volunteer interest form for Host Team ministry. Used to track renewed or ongoing interest. . |
| `last_volunteer_interest_lifegroups_lifemissions_timestamp` | TIMESTAMP | From volunteer_interest_forms table. Person level. The timestamp when the person most recently submitted a volunteer interest form for LifeGroups/LifeMissions. . |
| `last_volunteer_interest_media_timestamp` | TIMESTAMP | From volunteer_interest_forms table. Person level. The timestamp when the person most recently submitted a volunteer interest form for Media/Tech ministries. |
| `last_volunteer_interest_operations_team_timestamp` | TIMESTAMP | From volunteer_interest_forms table. Person level. The timestamp when the person most recently submitted a volunteer interest form for Operations Team. |
| `last_volunteer_interest_switch_timestamp` | TIMESTAMP | From volunteer_interest_forms table. Person level. The timestamp when the person most recently submitted a volunteer interest form for Switch ministry. |
| `last_volunteer_timestamp` | TIMESTAMP | From attendance_combined filtered for volunteer attendance. Person level. The timestamp of the person's most recent volunteer serving check-in. |
| `latitude` | FLOAT64 | Extracted from Rock RMS Location.GeoPoint using custom function. Entity level. The latitude coordinate of the entity location in decimal degrees. Used for mapping and distance calculations. |
| `legacy_team_approval_date` | DATE | No description |
| `lifegroup` | STRUCT<last_lifegroup_joined_name STRING, last_lifegroup_joined_campus STRING, last_lifegroup_joined_timestamp TIMESTAMP, last_lifegroup_joined_member_role STRING, last_lifegroup_joined_member_status STRING, first_lifegroup_joined_name STRING, first_lifegroup_joined_campus STRING, first_lifegroup_joined_timestamp TIMESTAMP, first_lifegroup_joined_member_role STRING, first_lifegroup_joined_member_status STRING, primary_lifegroup_joined_name STRING, primary_lifegroup_joined_campus STRING, primary_lifegroup_joined_timestamp TIMESTAMP, primary_lifegroup_joined_member_role STRING, primary_lifegroup_joined_member_status STRING, first_lifegroup_inquiry_timestamp TIMESTAMP, first_lifegroup_inquiry_campus STRING, last_lifegroup_inquiry_timestamp TIMESTAMP, last_lifegroup_inquiry_campus STRING> | STRUCT from lifegroup_membership model. Person level. Nested structure containing comprehensive LifeGroup participation history including first/last/primary group details, member roles, and inquiry information. |
| `lifegroup.first_lifegroup_inquiry_campus` | STRING | No description |
| `lifegroup.first_lifegroup_inquiry_timestamp` | TIMESTAMP | No description |
| `lifegroup.first_lifegroup_joined_campus` | STRING | No description |
| `lifegroup.first_lifegroup_joined_member_role` | STRING | No description |
| `lifegroup.first_lifegroup_joined_member_status` | STRING | No description |
| `lifegroup.first_lifegroup_joined_name` | STRING | No description |
| `lifegroup.first_lifegroup_joined_timestamp` | TIMESTAMP | No description |
| `lifegroup.last_lifegroup_inquiry_campus` | STRING | No description |
| `lifegroup.last_lifegroup_inquiry_timestamp` | TIMESTAMP | No description |
| `lifegroup.last_lifegroup_joined_campus` | STRING | No description |
| `lifegroup.last_lifegroup_joined_member_role` | STRING | No description |
| `lifegroup.last_lifegroup_joined_member_status` | STRING | No description |
| `lifegroup.last_lifegroup_joined_name` | STRING | No description |
| `lifegroup.last_lifegroup_joined_timestamp` | TIMESTAMP | No description |
| `lifegroup.primary_lifegroup_joined_campus` | STRING | No description |
| `lifegroup.primary_lifegroup_joined_member_role` | STRING | No description |
| `lifegroup.primary_lifegroup_joined_member_status` | STRING | No description |
| `lifegroup.primary_lifegroup_joined_name` | STRING | No description |
| `lifegroup.primary_lifegroup_joined_timestamp` | TIMESTAMP | No description |
| `lifegroup_leader_campus` | ARRAY<STRING> | From Group and Campus tables. Person level. Array of three-letter campus codes where the person leads Life Groups. Can lead at multiple campuses simultaneously. |
| `lifekids` | STRUCT<total_household_attendance_count INT64, first_household_attendance_timestamp TIMESTAMP, first_household_attendance_campus STRING, last_household_attendance_timestamp TIMESTAMP, last_household_attendance_campus STRING, weekly_household_attendance_count INT64, last_attendance_timestamp TIMESTAMP, last_attendance_campus STRING, first_attendance_timestamp TIMESTAMP, first_attendance_campus STRING, last_served_activity STRING, last_served_campus STRING, last_served_timestamp TIMESTAMP, last_volunteer_interest_timestamp TIMESTAMP, last_volunteer_interest_campus STRING, first_volunteer_interest_timestamp TIMESTAMP, first_volunteer_interest_campus STRING> | Comprehensive LifeKids engagement metrics combining household attendance, personal participation, and volunteer activity. This structure aggregates all children's ministry touchpoints including when children attend, when adults serve, and volunteer interest expressions. Provides a complete view of family engagement with LifeKids programming across all age-appropriate rooms. |
| `lifekids.first_attendance_campus` | STRING | From attender_check_in via parent group pivot. Person level. The campus code where the person first attended any LifeKids room. Rock > Person > History. |
| `lifekids.first_attendance_timestamp` | TIMESTAMP | From attender_check_in via parent group pivot. Person level. The timestamp of the person's first check-in to any LifeKids room (aggregated parent group). NULL if never attended LifeKids. Rock > Person > History. |
| `lifekids.first_household_attendance_campus` | STRING | From Rock attendance tables for NextGen. Family level displayed at person level. The campus code where this person's household first attended LifeKids. NULL if no family LifeKids attendance. |
| `lifekids.first_household_attendance_timestamp` | TIMESTAMP | From Rock attendance tables for NextGen. Family level displayed at person level. The timestamp of the first LifeKids check-in by any member of this person's household. NULL if no family LifeKids attendance. |
| `lifekids.first_volunteer_interest_campus` | STRING | From volunteer_interest_forms table. Person level. The three-letter campus code where the person first expressed interest in LifeKids volunteering. |
| `lifekids.first_volunteer_interest_timestamp` | TIMESTAMP | From volunteer_interest_forms table. Person level. The timestamp when the person first submitted a volunteer interest form for LifeKids ministry. Indicates interest in children's ministry volunteering. |
| `lifekids.last_attendance_campus` | STRING | From attender_check_in via parent group pivot. Person level. The campus code where the person most recently attended any LifeKids room. Rock > Person > History. |
| `lifekids.last_attendance_timestamp` | TIMESTAMP | From attender_check_in via parent group pivot. Person level. The timestamp of the person's most recent check-in to any LifeKids room. NULL if never attended. Rock > Person > History. |
| `lifekids.last_household_attendance_campus` | STRING | From Rock attendance tables for NextGen. Family level displayed at person level. The campus code where this person's household most recently attended LifeKids. NULL if no family LifeKids attendance. |
| `lifekids.last_household_attendance_timestamp` | TIMESTAMP | From Rock attendance tables for NextGen. Family level displayed at person level. The timestamp of the most recent LifeKids check-in by any member of this person's household. NULL if no family LifeKids attendance. |
| `lifekids.last_served_activity` | STRING | From volunteer_check_in table. Person level. The specific LifeKids role or classroom from the person's most recent LifeKids check-in. |
| `lifekids.last_served_campus` | STRING | The campus where the person last served/volunteered. |
| `lifekids.last_served_timestamp` | TIMESTAMP | From volunteer_check_in table. Person level. The timestamp when the person most recently served in LifeKids ministry. |
| `lifekids.last_volunteer_interest_campus` | STRING | From volunteer_interest_forms table. Person level. The three-letter campus code from the person's most recent LifeKids volunteer interest submission. |
| `lifekids.last_volunteer_interest_timestamp` | TIMESTAMP | From volunteer_interest_forms table. Person level. The timestamp when the person most recently submitted a volunteer interest form for LifeKids ministry. |
| `lifekids.total_household_attendance_count` | INT64 | From Rock attendance tables aggregated by family. Family level displayed at person level. The total number of LifeKids check-ins for all members of this person's household. NULL if no family LifeKids attendance. |
| `lifekids.weekly_household_attendance_count` | INT64 | From Rock attendance tables aggregated by family and week. Family level displayed at person level. The number of distinct weeks this person's household has attended LifeKids. NULL if no family LifeKids attendance. |
| `list_of_donor_events` | STRING | From Rock RMS AttributeValue and DefinedValue tables. Person level. Comma-separated list of all donor eventsthe person has participated in or been associated with. Retrieved by parsing the person's donor event attribute which stores multiple event GUIDs, then joining to DefinedValue to get human-readable event names. Each event represents a special giving campaign, capital campaign, or fundraising initiative. NULL if the person has not participated in any tracked donor events. The list is aggregated using STRING_AGG and may contain multiple events separated by commas. Rock > Person Profile > Attributes > Donor Events. Used for campaign attribution and donor segmentation analysis. |
| `list_of_given_funds` | STRING | List of funds the person has given to. |
| `longitude` | FLOAT64 | Extracted from Rock RMS Location.GeoPoint using custom function. Entity level. The longitude coordinate of the entity location in decimal degrees. Used for mapping and distance calculations. |
| `marital_status` | STRING | The marital status according to Rock RMS of the person (i.e. Single, Married, Divorced, Widowed). Defaults to 'Unknown' if null. |
| `middle_name` | STRING | From Rock RMS Person table. Person-level. Middle name with empty strings converted to NULL. Rock > Person. |
| `next_form_submission_email_subscription_timestamp_lco_service_reminder` | TIMESTAMP | Calculated from LCO service reminder form submissions. Person level. The UTC timestamp for when the person's next service reminder email should be sent, calculated by extracting their preferred service day and time from their form submission (assumes submission occurred 30 minutes before preferred service), finding the next occurrence of that day/time, and rounding to 15-minute intervals for batch processing efficiency. Returns NULL if they haven't submitted a service reminder preference form. |
| `nickname` | STRING | From Rock RMS Person table. Person-level. Preferred name or nickname with empty strings converted to NULL. Rock > Person. |
| `percent_scheduled` | STRING | The percent of all the gifts a person has given that have been scheduled, versus one-time. |
| `person_created_by_rms_person_alias_id` | INT64 | From Rock RMS Person.CreatedByPersonAliasId. Person-level. Alias ID of person/system who created this record. Rock > Person > History. |
| `phone_number` | STRING | The main contact phone number for the individual. Returns NULL if phone number is empty string. |
| `postal_code` | STRING | From Rock RMS Location.postalcode. Person level. The ZIP code of the person's home address. Used for geographic analysis and drive time calculations. |
| `predicted_segment_trait_likely_next_step_score_attend` | STRING | From Segment. Person level. A prediction made by Segment, based on the person's data and digital behavior. Is true if Segment has predicted the person is likely (0.5 or greater) to start attending. Segment > Unify > Traits > Computed Traits. |
| `predicted_segment_trait_likely_next_step_score_give` | STRING | From Segment. Person level. A prediction made by Segment, based on the person's data and digital behavior. Is true if Segment has predicted the person is likely (0.5 or greater) to start giving. Segment > Unify > Traits > Computed Traits. |
| `predicted_segment_trait_likely_next_step_score_serve` | STRING | From Segment. Person level. A prediction made by Segment, based on the person's data and digital behavior. Is true if Segment has predicted the person is likely (0.5 or greater) to start serving. Segment > Unify > Traits > Computed Traits. |
| `predicted_segment_trait_likely_next_step_score_stop_attending` | STRING | From Segment. Person level. A prediction made by Segment, based on the person's data and digital behavior. Is true if Segment has predicted the person is likely (0.5 or greater) to stop attending. Segment > Unify > Traits > Computed Traits. |
| `predicted_segment_trait_likely_next_step_score_stop_serving` | STRING | From Segment. Person level. A prediction made by Segment, based on the person's data and digital behavior. Is true if Segment has predicted the person is likely (0.5 or greater) to stop serving. Segment > Unify > Traits > Computed Traits. |
| `preferred_campus` | STRING | The preferred campus as decided by the user's engagement with Life.Church. |
| `preferred_currency` | STRING | The preferred money currency the person likes to give to Life.Church. |
| `preferred_source` | STRING | The preferred way the person likes to give to Life.Church (e.g. card, check, ACH, etc.). |
| `prefix` | STRING | From Rock RMS DefinedValue via Person.TitleValueId. Person-level. Name prefix/title with empty strings converted to NULL. Rock > Person Profile > Title. (e.g., 'Mr', 'Dr'). |
| `previous_attendance_flow_classification` | STRING | From attendance_flow model calculations. Person level (inherited from family level). The attendance stage that the person's family transitioned from to reach their current classification. Indicates the flow pattern (e.g., New to Retained, Retained to Absent). Used to understand attendance transitions and calculate flow metrics. NULL for families in their first classification (New). Example values: 'New', 'Retained', 'Re-engaged', 'Absent', 'Inactive', NULL. |
| `primary_giving_subtype` | STRING | The specific payment method subtype (e.g., 'Visa', 'Mastercard') used in the person's most recent contribution. Person level. From the latest transaction's transaction_subtype, excluding 'unknown' values. Rock > Profile > Transactions. |
| `primary_giving_type` | STRING | The transaction type (e.g., 'Cash', 'Check', 'ACH', 'Credit Card') used in the person's most recent contribution. Person level. From the latest transaction's transaction_type. Rock > Profile > Transactions. |
| `primary_person_alias` | INT64 | From Rock RMS Person.PrimaryAliasId. Person-level. The current primary alias ID for the person, which may change due to merges. Rock > Person > Extendes Attributes. |
| `product_sales` | STRUCT<shopify_customer_id INT64, shopify_total_orders INT64, first_order_timestamp TIMESTAMP, last_order_timestamp TIMESTAMP, most_frequent_bought_product_type STRING, last_frequent_bought_product_type_order_timestamp TIMESTAMP, last_abandoned_checkout_timestamp TIMESTAMP, abandoned_checkout_url STRING> | A STRUCT containing all Shopify-related purchase and customer data for the person. |
| `product_sales.abandoned_checkout_url` | STRING | From Data Warehouse, using Shopify data. Person Level. The recovery URL is only available if the checkout remains abandoned and no later orders were completed by this customer. Shopify > Orders > Abandoned Checkout. |
| `product_sales.first_order_timestamp` | TIMESTAMP | From Shopify order tables. Person level. The timestamp of the person's earliest order across both Shopify stores, converted from Central Time to UTC. Represents when they became a Shopify customer. Shopify > Customers > Customer > Orders. |
| `product_sales.last_abandoned_checkout_timestamp` | TIMESTAMP | From shopify_hubspot_properties table. Person level. The timestamp of the person's most recent abandoned checkout event. Used to trigger recovery campaigns and analyze checkout friction. Shopify > Orders > Abandoned Checkout |
| `product_sales.last_frequent_bought_product_type_order_timestamp` | TIMESTAMP | From shopify_hubspot_properties table. Person level. The timestamp when the person last purchased their most frequently bought product type. Used to track product preference recency. Shopify > Customers > Customer > Orders. |
| `product_sales.last_order_timestamp` | TIMESTAMP | From Shopify order tables. Person level. The timestamp of the person's most recent order across both Shopify stores, converted from Central Time to UTC. Used to determine customer recency and abandoned cart eligibility. Shopify > Customers > Customer > Orders. |
| `product_sales.most_frequent_bought_product_type` | STRING | From Data Warehouse, using Shopify data. Person Level. It is calculated when the same product type is bought at least twice. Shopify > Customer > Timeline. |
| `product_sales.shopify_customer_id` | INT64 | From Shopify customer tables (both main store and Life Store). Person level. The Shopify-assigned customer ID that corresponds to this Rock RMS person, matched by email address. Takes the minimum ID when multiple matches exist. Shopify > Customers. Example: 7516112191660. |
| `product_sales.shopify_total_orders` | INT64 | From Shopify order tables. Person level. The total count of all orders placed by this person across both Shopify stores (main store and Life Store). Calculated by counting all orders associated with the person's email address. Shopify Admin > Customers Example: 2. |
| `rms_family_id` | INT64 | The primary unique identifier for a family or household in Rock RMS. |
| `rms_person_created_timestamp` | TIMESTAMP | From Rock RMS Person.CreatedDateTime. Person-level. Timestamp when person record was created in Rock. Rock > Person > History. |
| `rms_person_id` | INT64 | The unique Rock RMS identifier for the individual. Person-level. Links to Person.Id in Rock RMS. Used to join all person-related data across the system. Rock > Person Profile. |
| `rms_person_inactive_reason` | STRING | From Rock RMS DefinedValue via Person.RecordStatusReasonValueId. Person-level. Reason for inactive status. NULL if active. Rock > Person Profile > Inactivate Reason. |
| `rms_person_inactive_timestamp` | TIMESTAMP | From Rock RMS Person._fivetran_synced. Person-level. Timestamp when marked inactive. NULL if active. |
| `rms_person_type` | STRING | From Rock RMS DefinedValue via Person.ConnectionStatusValueId. Person-level. Connection status (e.g., 'Visitor', 'Attendee', 'Member'). Rock > Person. |
| `scheduled_transaction_count` | INT64 | The number of gifts the person has given using a recurring schedule. |
| `school_grade` | STRING | From Rock RMS DefinedValue lookup based on graduation year. Person level. The current school grade descriptor (e.g., 'Kindergarten', '1st Grade'). Calculated from graduation year and current date. |
| `segment_canonical_id` | ARRAY<STRING> | From external_id_mapping table. Person level. Array of all canonical Segment user IDs associated with this Rock RMS person. Used for identity resolution and cross-device tracking. |
| `staff_end_timestamp` | TIMESTAMP | From Rock RMS AttributeValue. Person-level. Date person stopped being staff. NULL if still active or future date. Rock > Person Profile > Extended Attributes |
| `staff_start_timestamp` | TIMESTAMP | From Rock RMS AttributeValue. Person-level. Date person became staff member. NULL for future dates. Rock > Person > Extended Attributes |
| `state_province` | STRING | From person_location table. Family-level. Full state/province name. Rock > Person > Address. |
| `state_province_code` | STRING | From Rock RMS Location.state. Person level. Two-character state/province code of the person's home address (e.g., 'OK', 'TX'). Used for geographic analysis. |
| `statement_suppressed_timestamp` | TIMESTAMP | The timestamp when the person opted out of printed contribution statements. Person level. CreatedDateTime of the statement suppression attribute. Rock > Profile > Attributes > Suppress Sending Contribution Statements > Created Date. |
| `streaks` | ARRAY<STRUCT<streak_enrolled_timestamp TIMESTAMP, streak_enrolled_type STRING>> | From Rock streak tables. Person level. An array of the person's engagement streaks showing when they enrolled in various streak types. Each streak contains enrollment timestamp and type (Serving, Attendance, Digital Invites, Serving Daily, Weekly Attendance). Ordered by enrollment date. Rock > Person Profile > Streaks. |
| `streaks.streak_enrolled_timestamp` | TIMESTAMP | No description |
| `streaks.streak_enrolled_type` | STRING | No description |
| `suffix` | STRING | From Rock RMS DefinedValue via Person.SuffixValueId. Person-level. Name suffix with empty strings converted to NULL. Rock > Person Profile > Suffix. (e.g., 'Jr', 'III'). |
| `three_month_campus` | STRING | The campus short code where the person committed to the three-month tithe challenge. Person level. From the campus attribute in the Three Month Tithe Challenge matrix. Rock > Profile > Attributes > Three Month Tithe Challenge. |
| `three_month_timestamp` | TIMESTAMP | The start date when the person began their three-month tithe challenge commitment. Person level. Retrieved from Rock attribute matrix for Three Month Tithe Challenge. Format: YYYY-MM-DD HH:MM:SS. Rock > Profile > Person > Attributes > Three Month Tithe Challenge. |
| `total_attendance_app_count` | INT64 | From attendance_combined filtered for app check-ins. Person level. The total number of check-ins made via the Life.Church mobile app. Always <= total_attendance_combined_count. |
| `total_attendance_combined_count` | INT64 | From attendance_combined count aggregation. Person level. The total number of all check-ins (attendance + volunteer) for this person across all campuses and time. Always >= 0. Rock > Person > History. |
| `total_attendance_lco_count` | INT64 | From attendance_combined filtered for Church Online Platform. Person level. The total number of check-ins for Life.Church Online experiences. Always <= total_attendance_combined_count. |
| `total_digital_invite` | INT64 | Count from Interaction table. Person level. The total number of digital invites this person has sent. |
| `total_financial_transaction_count` | INT64 | The total number of successful financial transactions the person has made. Person level. Count of distinct financial_transaction_id from fact_giving where amount >= 0 and is_successful = TRUE. Rock > Profile > Transactions. |
| `total_household_attendance_switch_count` | INT64 | From Rock attendance tables aggregated by family. Family level displayed at person level. The total number of Switch check-ins for all members of this person's household. NULL if no family Switch attendance. |
| `total_household_switch_aged_students` | INT64 | From Person table based on graduation year. Family level displayed at person level only calculated for Adults. The count of Switch-aged students (grades 6-12) currently in this person's household. NULL if no Switch-aged students. |
| `total_scheduled_giving_count` | INT64 | The total number of scheduled giving transactions for the person. |
| `total_serving_check_ins` | INT64 | The total number of serving check-ins for the person. Null if 0. |
| `typical_frequency` | FLOAT64 | The average frequency the person gives to Life.Church. |
| `user_id` | INT64 | The current unique identifier for an individual person or business in Rock RMS, despite merges. Cast as STRING for external system compatibility. |
| `weekly_household_attendance_switch_count` | INT64 | From Rock attendance tables aggregated by family and week. Family level displayed at person level. The number of distinct weeks this person's household has attended Switch. NULL if no family Switch attendance. |
| `weeks_in_current_attendance_flow_classification` | INT64 | From row_number calculation over classification changes. Person level (inherited from family level). The number of consecutive weeks the person's family has been in their current attendance classification. Calculated by detecting when the classification changes and counting weeks since the most recent change. Resets to 1 whenever the family transitions to a new classification. Always >= 1 for families with a classification. |

## Column Details

### `address_1`

- **Type**: STRING
- **Description**: From Rock RMS Location.Street1. Entity level. The primary street address line for the entity physical location.

### `address_2`

- **Type**: STRING
- **Description**: From Rock RMS Location.Street2. Entity level. The secondary address line (suite, building, etc). Returns empty string if NULL.

### `address_to_primary_campus_distance_miles`

- **Type**: FLOAT64
- **Description**: From person_location table. Person-level. Calculated distance in miles from home address to primary campus.

### `age`

- **Type**: INT64
- **Description**: The age in years of the person.

### `age_group`

- **Type**: STRING
- **Description**: The person's age in bucketed groups.

### `background_check_completed_timestamp`

- **Type**: DATE
- **Description**: From Step table. Person level. The date when the person's most recent background check was completed. Used to track expiration and renewal needs.

### `background_check_status`

- **Type**: STRING
- **Description**: The current status of the person's background check.

### `banned_giver_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp when the person was marked as a banned giver. Person level. CreatedDateTime of the BannedGiver attribute value. Rock > Profile > Person Profile > Attributes > Banned Giver > Created Date.

### `birthdate`

- **Type**: DATE
- **Description**: From Rock RMS Person.Birthdate. Person level. The person's date of birth. Format: YYYY-MM-DD. Used for age calculations and age-appropriate room assignments.

### `city`

- **Type**: STRING
- **Description**: From Rock RMS Location. Entity level. The city where the entity is located.

### `country`

- **Type**: STRING
- **Description**: From location.country. Person level. The country of the person's home address. Typically 'US' for most records. Used for international attendee identification.

### `county`

- **Type**: STRING
- **Description**: From person_location table. Family-level. County name. Rock > Person > Address.

### `current_attendance_flow_classification`

- **Type**: STRING
- **Description**: From attendance_flow model calculations. Person level (inherited from family level). The current attendance stage of the person's family based on their check-in patterns. Represents which of the 5 stages (New, Retained, Re-engaged, Absent, or Inactive) the family is currently in. New = first 4 weeks after first check-in, Retained = attending at least once every 4 weeks, Re-engaged = returned after 4+ weeks absence, Absent = no attendance for 4-8 weeks, Inactive = no attendance for 8+ weeks. Example values: 'New', 'Retained', 'Re-engaged', 'Absent', 'Inactive', NULL.

### `decade_of_life`

- **Type**: FLOAT64
- **Description**: The age in years of the person, rounded or truncated to the earliest decade or 10 years.

### `deletion_requested_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS Person where InactiveReasonNote contains deletion request. Person-level. Timestamp of GDPR deletion request. Rock > Person Profile > Inactive Reason Note.

### `email`

- **Type**: STRING
- **Description**: From Rock RMS Person.email. Person level. The person's primary email address as stored in Rock RMS. May be NULL if no email on file. Used for communication and matching.

### `engagement_status_self_identified`

- **Type**: STRING
- **Description**: The engagement status as self-identified by the person.

### `family_position`

- **Type**: STRING
- **Description**: Family hierarchy, whether the person is an Adult or Child in their family.

### `first_attendance_app_campus`

- **Type**: STRING
- **Description**: From attender_check_in filtered for app check-ins. Person level. The campus code where the person first checked in via the app. Rock > Person > History.

### `first_attendance_app_timestamp`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in filtered for app check-ins. Person level. The timestamp of the person's first attendance check-in via the Life.Church mobile app. NULL if never used app check-in. Rock > Person > History.

### `first_attendance_campus`

- **Type**: STRING
- **Description**: From attendance_combined filtered for non-volunteer attendance. Person level. The campus code where the person first attended a experience. Rock > Person > History.

### `first_attendance_combined_campus`

- **Type**: STRING
- **Description**: From attendance_combined including all attendance types. Person level. The campus code where the person had their first check-in of any type. Rock > Person > History.

### `first_attendance_combined_parent_group`

- **Type**: STRING
- **Description**: From attendance_combined including all attendance types. Person level. The parent group name of the person's first check-in (e.g., Host Team, LifeKids, Switch). Indicates their entry point into Life.Church.

### `first_attendance_combined_timestamp`

- **Type**: TIMESTAMP
- **Description**: From attendance_combined including all attendance types. Person level. The timestamp of the person's first check-in of any type (attendance or volunteer). The earliest interaction with Life.Church. Rock > Person > History.

### `first_attendance_host_team_campus`

- **Type**: STRING
- **Description**: From attender_check_in via parent group pivot. Person level. The campus code where the person first served on Host Team. Rock > Person > History.

### `first_attendance_host_team_timestamp`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via parent group pivot. Person level. The timestamp of the person's first check-in as a Host Team volunteer. NULL if never served. Rock > Person > History.

### `first_attendance_lifekids_campus_crosstown`

- **Type**: STRING
- **Description**: From attender_check_in via attendance group pivot. Person level. The campus code where the person first attended Crosstown LifeKids room. Rock > Person > History.

### `first_attendance_lifekids_campus_in_the_jungle`

- **Type**: STRING
- **Description**: From attender_check_in via attendance group pivot. Person level. The campus code where the person first attended In The Jungle LifeKids room. Rock > Person > History.

### `first_attendance_lifekids_campus_konnect`

- **Type**: STRING
- **Description**: From attender_check_in via attendance group pivot. Person level. The campus code where the person first attended Konnect LifeKids room. Rock > Person > History.

### `first_attendance_lifekids_campus_let_there_be_light`

- **Type**: STRING
- **Description**: From attender_check_in via attendance group pivot. Person level. The campus code where the person first attended Let There Be Light LifeKids room. Rock > Person > History.

### `first_attendance_lifekids_campus_starry_night`

- **Type**: STRING
- **Description**: From attender_check_in via attendance group pivot. Person level. The campus code where the person first attended Starry Night LifeKids room. Rock > Person > History.

### `first_attendance_lifekids_campus_the_ark`

- **Type**: STRING
- **Description**: From attender_check_in via attendance group pivot. Person level. The campus code where the person first attended The Ark LifeKids room. Rock > Person > History.

### `first_attendance_lifekids_campus_the_garden`

- **Type**: STRING
- **Description**: From attender_check_in via attendance group pivot. Person level. The campus code where the person first attended The Garden LifeKids room. Rock > Person > History.

### `first_attendance_lifekids_campus_the_loop`

- **Type**: STRING
- **Description**: From attender_check_in via attendance group pivot. Person level. The campus code where the person first attended The Loop LifeKids room. Paired with timestamp - both NULL or both populated. Rock > Person > History.

### `first_attendance_lifekids_campus_under_the_sea`

- **Type**: STRING
- **Description**: From attender_check_in via attendance group pivot. Person level. The campus code where the person first attended Under The Sea LifeKids room. Rock > Person > History.

### `first_attendance_lifekids_timestamp_crosstown`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via attendance group pivot. Person level. The timestamp of the person's first check-in to Crosstown LifeKids room (5th grade). NULL if never attended. Rock > Person > History.

### `first_attendance_lifekids_timestamp_in_the_jungle`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via attendance group pivot. Person level. The timestamp of the person's first check-in to In The Jungle LifeKids room (age 4). NULL if never attended. Rock > Person > History.

### `first_attendance_lifekids_timestamp_konnect`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via attendance group pivot. Person level. The timestamp of the person's first check-in to Konnect LifeKids room (1st-2nd grade). NULL if never attended. Rock > Person > History.

### `first_attendance_lifekids_timestamp_let_there_be_light`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via attendance group pivot. Person level. The timestamp of the person's first check-in to Let There Be Light LifeKids room (age 3). NULL if never attended. Rock > Person > History.

### `first_attendance_lifekids_timestamp_starry_night`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via attendance group pivot. Person level. The timestamp of the person's first check-in to Starry Night LifeKids room (age 5). NULL if never attended. Rock > Person > History.

### `first_attendance_lifekids_timestamp_the_ark`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via attendance group pivot. Person level. The timestamp of the person's first check-in to The Ark LifeKids room. NULL if never attended. Rock > Person > History.

### `first_attendance_lifekids_timestamp_the_garden`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via attendance group pivot. Person level. The timestamp of the person's first check-in to The Garden LifeKids room (3rd-4th grade). NULL if never attended. Rock > Person > History.

### `first_attendance_lifekids_timestamp_the_loop`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via attendance group pivot. Person level. The timestamp of the person's first check-in to The Loop LifeKids room (ages 1-2). NULL if never attended. Rock > Person > History.

### `first_attendance_lifekids_timestamp_under_the_sea`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via attendance group pivot. Person level. The timestamp of the person's first check-in to Under The Sea LifeKids room (kindergarten). NULL if never attended. Rock > Person > History.

### `first_attendance_switch_campus`

- **Type**: STRING
- **Description**: From attender_check_in via parent group pivot. Person level. The campus code where the person first attended Switch student ministry. Rock > Person > History.

### `first_attendance_switch_campus_student`

- **Type**: STRING
- **Description**: From attender_check_in via attendance group pivot. Person level. The campus code where the person first attended Switch student ministry. Rock > Person > History.

### `first_attendance_switch_timestamp`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via parent group pivot. Person level. The timestamp of the person's first check-in to Switch student ministry (parent group level). NULL if never attended. Rock > Person > History.

### `first_attendance_switch_timestamp_student`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via attendance group pivot. Person level. The timestamp of the person's first check-in to Switch student ministry (6th-12th grade). NULL if never attended. Rock > Person > History.

### `first_attendance_timestamp`

- **Type**: TIMESTAMP
- **Description**: From attendance_combined filtered for non-volunteer attendance. Person level. The timestamp of the person's first attendance at any Life.Church campus (excludes volunteer check-ins). Rock > Person > History.

### `first_connection_request_event_interest_campus_baptism`

- **Type**: STRING
- **Description**: From ConnectionRequest filtered by connection opportunity ID. Person level. The campus associated with their first connection request for this event.

### `first_connection_request_event_interest_campus_baptism_class_kids`

- **Type**: STRING
- **Description**: From ConnectionRequest filtered by connection opportunity ID. Person level. The campus associated with their first connection request for this event.

### `first_connection_request_event_interest_timestamp_baptism`

- **Type**: TIMESTAMP
- **Description**: From ConnectionRequest filtered by connection opportunity ID. Person level. The earliest timestamp when this person expressed interest in this event through a connection request.

### `first_connection_request_event_interest_timestamp_baptism_class_kids`

- **Type**: TIMESTAMP
- **Description**: From ConnectionRequest filtered by connection opportunity ID. Person level. The earliest timestamp when this person expressed interest in this event through a connection request.

### `first_event_participation_campus_baptism`

- **Type**: STRING
- **Description**: From Rock Attributes tables. The first recorded Life.Church campus at which the person was baptized. Rock > Extended Attributes > Life Events > Baptism.

### `first_event_participation_campus_child_dedication`

- **Type**: STRING
- **Description**: From Rock Attributes tables. The first recorded Life.Church campus at which the person dedicated a child at Life.Church. Rock > Extended Attributes > Life Events > Child Dedication.

### `first_event_participation_campus_known`

- **Type**: STRING
- **Description**: From Rock Attributes tables and Steps tables. The first recorded Life.Church campus at which the person attended any form of Known Event (previously called 'Open Door'). Rock > Steps > Known.

### `first_event_participation_timestamp_baptism`

- **Type**: TIMESTAMP
- **Description**: From Rock Attributes tables. The first recorded timestamp of when the person was baptized. Rock > Extended Attributes > Life Events > Baptism.

### `first_event_participation_timestamp_child_dedication`

- **Type**: TIMESTAMP
- **Description**: From Rock Attributes tables. The first recorded timestamp of when the person dedicated a child at Life.Church. Rock > Extended Attributes > Life Events > Child Dedication.

### `first_event_participation_timestamp_known`

- **Type**: TIMESTAMP
- **Description**: From Rock Attributes tables and Steps tables. The first recorded timestamp of when the person attended any form of Known Event (previously called 'Open Door'). Rock > Steps > Known.

### `first_financial_transaction_campus`

- **Type**: STRING
- **Description**: The campus short code (e.g., 'EDM', 'STW') where the person made their first financial contribution. Person level. Retrieved from the campus associated with the first transaction. Rock > Profile > Transactions.

### `first_financial_transaction_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp of the person's first ever financial contribution to Life.Church. Person level. Calculated as the earliest transaction from fact_giving where amount >= 0 and is_successful = TRUE. Rock > Profile > Transactions.

### `first_form_submission_account_acquisition_timestamp_addiction`

- **Type**: TIMESTAMP
- **Description**: Calculated via PIVOT MIN on form_submission_timestamp. Person level. The earliest timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department.

### `first_form_submission_account_acquisition_timestamp_anxiety`

- **Type**: TIMESTAMP
- **Description**: Calculated via PIVOT MIN on form_submission_timestamp. Person level. The earliest timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department.

### `first_form_submission_account_acquisition_timestamp_burnout`

- **Type**: TIMESTAMP
- **Description**: Calculated via PIVOT MIN on form_submission_timestamp. Person level. The earliest timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department.

### `first_form_submission_account_acquisition_timestamp_finance`

- **Type**: TIMESTAMP
- **Description**: Calculated via PIVOT MIN on form_submission_timestamp. Person level. The earliest timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department.

### `first_form_submission_account_acquisition_timestamp_friendship`

- **Type**: TIMESTAMP
- **Description**: Calculated via LEAST function combining friendship and friendships form variants. Person level. The earliest timestamp when this person submitted any friendship-related account acquisition form through HubSpot paid marketing campaigns managed by the Reach department, accounting for historical form naming variations.

### `first_form_submission_account_acquisition_timestamp_grief`

- **Type**: TIMESTAMP
- **Description**: Calculated via PIVOT MIN on form_submission_timestamp. Person level. The earliest timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department.

### `first_form_submission_account_acquisition_timestamp_habits`

- **Type**: TIMESTAMP
- **Description**: Calculated via PIVOT MIN on form_submission_timestamp. Person level. The earliest timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department.

### `first_form_submission_account_acquisition_timestamp_parenting`

- **Type**: TIMESTAMP
- **Description**: Calculated via PIVOT MIN on form_submission_timestamp. Person level. The earliest timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department.

### `first_form_submission_next_steps_campus_baptism`

- **Type**: STRING
- **Description**: Filtered for specific form using constants. Person level. The campus where this person first submitted this next steps form.

### `first_form_submission_next_steps_campus_commit_to_christ`

- **Type**: STRING
- **Description**: Filtered for specific form using constants. Person level. The campus where this person first submitted this next steps form.

### `first_form_submission_next_steps_campus_general_question`

- **Type**: STRING
- **Description**: Filtered for specific form using constants. Person level. The campus where this person first submitted this next steps form.

### `first_form_submission_next_steps_campus_im_new_here`

- **Type**: STRING
- **Description**: Filtered for specific form using constants. Person level. The campus where this person first submitted this next steps form.

### `first_form_submission_next_steps_campus_known`

- **Type**: STRING
- **Description**: Filtered for specific form using constants. Person level. The campus where this person first submitted this next steps form.

### `first_form_submission_next_steps_campus_prayer_request`

- **Type**: STRING
- **Description**: Filtered for specific form using constants. Person level. The campus where this person first submitted this next steps form.

### `first_form_submission_next_steps_campus_renewing_commitment_to_christ`

- **Type**: STRING
- **Description**: Filtered for specific form using constants. Person level. The campus where this person first submitted this next steps form.

### `first_form_submission_next_steps_timestamp_baptism`

- **Type**: TIMESTAMP
- **Description**: Filtered for specific form using constants. Person level. The earliest timestamp when this person submitted this particular next steps form representing deeper spiritual engagement.

### `first_form_submission_next_steps_timestamp_commit_to_christ`

- **Type**: TIMESTAMP
- **Description**: Filtered for specific form using constants. Person level. The earliest timestamp when this person submitted this particular next steps form representing deeper spiritual engagement.

### `first_form_submission_next_steps_timestamp_general_question`

- **Type**: TIMESTAMP
- **Description**: Filtered for specific form using constants. Person level. The earliest timestamp when this person submitted this particular next steps form representing deeper spiritual engagement.

### `first_form_submission_next_steps_timestamp_im_new_here`

- **Type**: TIMESTAMP
- **Description**: Filtered for specific form using constants. Person level. The earliest timestamp when this person submitted this particular next steps form representing deeper spiritual engagement.

### `first_form_submission_next_steps_timestamp_known`

- **Type**: TIMESTAMP
- **Description**: Filtered for specific form using constants. Person level. The earliest timestamp when this person submitted this particular next steps form representing deeper spiritual engagement.

### `first_form_submission_next_steps_timestamp_prayer_request`

- **Type**: TIMESTAMP
- **Description**: Filtered for specific form using constants. Person level. The earliest timestamp when this person submitted this particular next steps form representing deeper spiritual engagement.

### `first_form_submission_next_steps_timestamp_renewing_commitment_to_christ`

- **Type**: TIMESTAMP
- **Description**: Filtered for specific form using constants. Person level. The earliest timestamp when this person submitted this particular next steps form representing deeper spiritual engagement.

### `first_name`

- **Type**: STRING
- **Description**: Employee's legal first name from the employee table. Used for official documentation and reporting.

### `first_segment_interaction_timestamp`

- **Type**: TIMESTAMP
- **Description**: From aggregated Segment events. Person level. The earliest timestamp across all tracked sources, representing the person's first known digital interaction with any Life.Church platform. Used to determine overall engagement start date. Calculated as MIN of all source-specific first interactions.

### `first_segment_interaction_timestamp_chop_prod`

- **Type**: TIMESTAMP
- **Description**: From Segment events table. Person level. The timestamp of the person's first interaction with Church Online Platform (CHOP) production environment tracked by Segment. Tracks when they first engaged with online church services.

### `first_segment_interaction_timestamp_finds_life_prod`

- **Type**: TIMESTAMP
- **Description**: From Segment events table. Person level. The timestamp of the person's first interaction with finds.life website. Tracks engagement with the articles.

### `first_segment_interaction_timestamp_hubspot_email_events_dev`

- **Type**: TIMESTAMP
- **Description**: From Segment events table. Person level. The timestamp of the person's first email interaction tracked through HubSpot integration. Captures initial email engagement like opens or clicks.

### `first_segment_interaction_timestamp_hubspot_form_submission`

- **Type**: TIMESTAMP
- **Description**: From Segment events table. Person level. The timestamp of the person's first form submission tracked through HubSpot integration. Records initial form completions across Life.Church properties.

### `first_segment_interaction_timestamp_kotlin_android`

- **Type**: TIMESTAMP
- **Description**: From Segment events table. Person level. The timestamp of the person's first interaction with the Life.Church Android app (Kotlin version). Indicates when they first used the newer Android application.

### `first_segment_interaction_timestamp_lc_ios_swift`

- **Type**: TIMESTAMP
- **Description**: From Segment events table. Person level. The timestamp of the person's first interaction with the Life.Church iOS app (Swift version). Indicates when they first used the newer iOS application.

### `first_segment_interaction_timestamp_lcweb`

- **Type**: TIMESTAMP
- **Description**: From Segment events table. Person level. The timestamp of the person's first interaction with the main Life.Church website. Tracks initial web engagement.

### `first_segment_interaction_timestamp_lifechurch_android`

- **Type**: TIMESTAMP
- **Description**: From Segment events table. Person level. The timestamp of the person's first interaction with the legacy Life.Church Android app. Tracks usage of the older Android application version.

### `first_segment_interaction_timestamp_lifechurch_ios`

- **Type**: TIMESTAMP
- **Description**: From Segment events table. Person level. The timestamp of the person's first interaction with the legacy Life.Church iOS app. Tracks usage of the older iOS application version.

### `first_segment_interaction_timestamp_rms_prod_js`

- **Type**: TIMESTAMP
- **Description**: From Segment events table. Person level. The timestamp of the person's first interaction tracked by Rock RMS JavaScript SDK in production. Captures initial engagement with Rock-integrated web properties.

### `first_serving_check_in_activity`

- **Type**: STRING
- **Description**: From volunteer_check_in table. Person level. The specific serving role or activity name from the person's first volunteer check-in. Provides context for their initial serving experience.

### `first_serving_check_in_campus`

- **Type**: STRING
- **Description**: From volunteer_check_in and Campus tables. Person level. The three-letter campus code where the person first checked in to serve.

### `first_serving_check_in_timestamp`

- **Type**: TIMESTAMP
- **Description**: From volunteer_check_in table. Person level. The timestamp of the person's first ever volunteer serving check-in across all ministries. Marks the transition from interest to action.

### `first_step_next_steps_campus_you_said_yes`

- **Type**: STRING
- **Description**: From Step table filtered by YSY step type. Person level. The campus where this person first completed the You Said Yes step.

### `first_step_next_steps_timestamp_you_said_yes`

- **Type**: TIMESTAMP
- **Description**: From Step table filtered by YSY step type. Person level. The earliest timestamp when this person completed the You Said Yes step.

### `first_three_month_tithe_challenge_requested`

- **Type**: BOOL
- **Description**: Boolean indicating whether the person has ever participated in the three-month tithe challenge. Person level. TRUE if three_month_timestamp exists, FALSE otherwise. Rock > Profile > Attributes > Three Month Tithe Challenge.

### `first_volunteer_campus`

- **Type**: STRING
- **Description**: From attendance_combined filtered for volunteer attendance. Person level. The campus code where the person first served as a volunteer. Rock > Person > History.

### `first_volunteer_interest_campus_short_code_host_team`

- **Type**: STRING
- **Description**: From volunteer_interest_forms table. Person level. The three-letter campus code where the person first expressed interest in Host Team volunteering.

### `first_volunteer_interest_campus_short_code_lifegroups_lifemissions`

- **Type**: STRING
- **Description**: From volunteer_interest_forms table. Person level. The three-letter campus code where the person first expressed interest in LifeGroups/LifeMissions volunteering.

### `first_volunteer_interest_campus_short_code_media`

- **Type**: STRING
- **Description**: From volunteer_interest_forms table. Person level. The three-letter campus code where the person first expressed interest in Media/Tech volunteering.

### `first_volunteer_interest_campus_short_code_operations_team`

- **Type**: STRING
- **Description**: From volunteer_interest_forms table. Person level. The three-letter campus code where the person first expressed interest in Operations volunteering.

### `first_volunteer_interest_campus_short_code_switch`

- **Type**: STRING
- **Description**: From volunteer_interest_forms table. Person level. The three-letter campus code where the person first expressed interest in Switch volunteering.

### `first_volunteer_interest_host_team_timestamp`

- **Type**: TIMESTAMP
- **Description**: From volunteer_interest_forms table. Person level. The timestamp when the person first submitted a volunteer interest form for Host Team ministry. Indicates initial interest in greeting, ushering, or hospitality roles.

### `first_volunteer_interest_lifegroups_lifemissions_timestamp`

- **Type**: TIMESTAMP
- **Description**: From volunteer_interest_forms table. Person level. The timestamp when the person first submitted a volunteer interest form for LifeGroups or LifeMissions ministry. Indicates interest in small group leadership or missions involvement.

### `first_volunteer_interest_media_timestamp`

- **Type**: TIMESTAMP
- **Description**: From volunteer_interest_forms table. Person level. The timestamp when the person first submitted a volunteer interest form for Media, Social Media, Photography, or Tech Team. Indicates interest in creative or technical ministries.

### `first_volunteer_interest_operations_team_timestamp`

- **Type**: TIMESTAMP
- **Description**: From volunteer_interest_forms table. Person level. The timestamp when the person first submitted a volunteer interest form for Operations Team. Indicates interest in facilities, logistics, or technical operations.

### `first_volunteer_interest_switch_timestamp`

- **Type**: TIMESTAMP
- **Description**: From volunteer_interest_forms table. Person level. The timestamp when the person first submitted a volunteer interest form for Switch ministry. Indicates interest in youth ministry volunteering.

### `first_volunteer_interest_timestamp`

- **Type**: TIMESTAMP
- **Description**: Calculated from all volunteer interest forms. Person level. The earliest timestamp across all ministry-specific volunteer interest forms, representing when the person first expressed any volunteer interest. Calculated using LEAST function with null handling.

### `first_volunteer_timestamp`

- **Type**: TIMESTAMP
- **Description**: From attendance_combined filtered for volunteer attendance. Person level. The timestamp of the person's first volunteer serving check-in at any campus or role. Rock > Person > History.

### `frequency`

- **Type**: STRING
- **Description**: The frequency of the scheduled transaction (e.g., 'Weekly', 'Monthly', 'One-Time'). From Rock RMS defined values for transaction frequency.

### `full_name`

- **Type**: STRING
- **Description**: From Rock RMS Person. Person level. The person's full name constructed as nickname (or first name if no nickname) plus last name. Used for human-readable identification in reports.

### `gender`

- **Type**: STRING
- **Description**: Employee gender from employee.gender. Used for diversity analytics. NULL for requisitions.

### `giving`

- **Type**: STRUCT<is_recurring_giver_tithe_offerings BOOL, is_recurring_giver_tithe_offerings_campus STRING, last_financial_transaction_tithes_offerings_campus STRING, last_financial_transaction_tithes_offerings_timestamp TIMESTAMP, number_of_gifts_last_90_tithes_and_offerings INT64, is_recurring_giver_new_locations BOOL, is_recurring_giver_new_locations_campus STRING, last_financial_transaction_new_locations_campus STRING, last_financial_transaction_new_locations_timestamp TIMESTAMP, is_recurring_giver_local_and_global_missions BOOL, is_recurring_giver_local_and_global_missions_campus STRING, last_financial_transaction_local_global_missions_campus STRING, last_financial_transaction_local_global_missions_timestamp TIMESTAMP, is_recurring_giver_free_resources BOOL, is_recurring_giver_free_resources_campus STRING, last_financial_transaction_free_resources_campus STRING, last_financial_transaction_free_resources_timestamp TIMESTAMP, is_recurring_giver_digital_reach BOOL, is_recurring_giver_digital_reach_campus STRING, is_recurring_giver_youversion_and_bible_translation BOOL, is_recurring_giver_youversion_and_bible_translation_campus STRING, last_financial_transaction_digital_reach_campus STRING, last_financial_transaction_digital_reach_timestamp TIMESTAMP, last_financial_transaction_youversion_bible_translation_campus STRING, last_financial_transaction_youversion_bible_translation_timestamp TIMESTAMP, last_financial_transaction_giving_type STRING>
- **Description**: Nested structure containing detailed giving patterns and recurring donation information across all Life.Church funds

### `giving.is_recurring_giver_digital_reach`

- **Type**: BOOL
- **Description**: Boolean indicating if the person has an active recurring gift schedule for Digital Reach fund. Person level. TRUE if active scheduled transaction exists for this fund. Rock > Contributions > Scheduled Transaction List.

### `giving.is_recurring_giver_digital_reach_campus`

- **Type**: STRING
- **Description**: The campus short code associated with the person's recurring Digital Reach gift. Person level. From the campus of the scheduled transaction detail. Rock > Contributions > Scheduled Transaction List.

### `giving.is_recurring_giver_free_resources`

- **Type**: BOOL
- **Description**: Boolean indicating if the person has an active recurring gift schedule for Free Resources fund. Person level. TRUE if active scheduled transaction exists for this fund. Rock > Contributions > Scheduled Transaction List.

### `giving.is_recurring_giver_free_resources_campus`

- **Type**: STRING
- **Description**: The campus short code associated with the person's recurring Free Resources gift. Person level. From the campus of the scheduled transaction detail. Rock > Contributions > Scheduled Transaction List.

### `giving.is_recurring_giver_local_and_global_missions`

- **Type**: BOOL
- **Description**: Boolean indicating if the person has an active recurring gift schedule for Local & Global Missions fund. Person level. TRUE if active scheduled transaction exists for this fund. Rock > Contributions > Scheduled Transaction List.

### `giving.is_recurring_giver_local_and_global_missions_campus`

- **Type**: STRING
- **Description**: The campus short code associated with the person's recurring Local & Global Missions gift. Person level. From the campus of the scheduled transaction detail. Rock > Contributions > Scheduled Transaction List.

### `giving.is_recurring_giver_new_locations`

- **Type**: BOOL
- **Description**: Boolean indicating if the person has an active recurring gift schedule for New Locations fund. Person level. TRUE if active scheduled transaction exists for this fund. Rock > Profile > Scheduled Transactions.

### `giving.is_recurring_giver_new_locations_campus`

- **Type**: STRING
- **Description**: The campus short code associated with the person's recurring New Locations gift. Person level. From the campus of the scheduled transaction detail. Rock > Contributions > Scheduled Transaction List.

### `giving.is_recurring_giver_tithe_offerings`

- **Type**: BOOL
- **Description**: Boolean indicating if the person has an active recurring gift schedule for Tithes & Offerings fund. Person level. TRUE if active scheduled transaction exists for this fund. Rock > Contributions > Scheduled Transaction List.

### `giving.is_recurring_giver_tithe_offerings_campus`

- **Type**: STRING
- **Description**: The campus short code associated with the person's recurring Tithes & Offerings gift. Person level. From the campus of the scheduled transaction detail.Rock > Contributions > Scheduled Transaction List.

### `giving.is_recurring_giver_youversion_and_bible_translation`

- **Type**: BOOL
- **Description**: From Data Warehouse, using Rock financial transaction data. Household level. Whether or not the family has a recurring gift to the Youversion and Bible Translations fund. Rock > Profile > Transactions. Or Rock > Contributions.

### `giving.is_recurring_giver_youversion_and_bible_translation_campus`

- **Type**: STRING
- **Description**: The campus short code associated with the person's recurring YouVersion & Bible Translation gift. Person level. From the campus of the scheduled transaction detail. Rock > Contributions > Scheduled Transaction List.

### `giving.last_financial_transaction_digital_reach_campus`

- **Type**: STRING
- **Description**: The campus short code where the person made their most recent Digital Reach contribution. Person level. Extracted using window function for transactions matching Digital Reach fund descriptions defined in constants. NULL if person has never given to this fund. Rock > Profile > Transactions.

### `giving.last_financial_transaction_digital_reach_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp of the person's most recent Digital Reach contribution. Person level. Calculated using ROW_NUMBER() window function filtering for Digital Reach fund transactions. Format: YYYY-MM-DD HH:MM:SS UTC. NULL if no Digital Reach giving history. Rock > Profile > Transactions.

### `giving.last_financial_transaction_free_resources_campus`

- **Type**: STRING
- **Description**: The campus short code where the person made their most recent Free Resources contribution. Person level. Derived from the latest transaction where fund description matches Free Resources accounts in constants. NULL for non-givers to this fund. Rock > Profile > Transactions.

### `giving.last_financial_transaction_free_resources_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp of the person's most recent Free Resources contribution. Person level. Identified as the top-ranked transaction by timestamp for Free Resources fund type. Format: YYYY-MM-DD HH:MM:SS UTC. NULL if person has never contributed to Free Resources. Rock > Profile > Transactions.

### `giving.last_financial_transaction_giving_type`

- **Type**: STRING
- **Description**: The transaction type (e.g., 'Cash', 'Check', 'ACH', 'Credit Card', 'Non-Cash') of the person's most recent contribution across all fund types. Person level. Extracted using ROW_NUMBER() = 1 ordered by timestamp DESC across all transactions regardless of fund. Indicates the person's most recent giving method. Rock > Profile > Transactions.

### `giving.last_financial_transaction_local_global_missions_campus`

- **Type**: STRING
- **Description**: The campus short code where the person made their most recent Local & Global Missions contribution. Person level. Extracted from transactions matching Local & Global Missions fund descriptions using window function ranking. NULL if no giving history to missions. Rock > Profile > Transactions.

### `giving.last_financial_transaction_local_global_missions_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp of the person's most recent Local & Global Missions contribution. Person level. Calculated as the latest transaction timestamp for Local & Global Missions fund type. Format: YYYY-MM-DD HH:MM:SS UTC. NULL for non-missions givers. Rock > Profile > Transactions.

### `giving.last_financial_transaction_new_locations_campus`

- **Type**: STRING
- **Description**: The campus short code where the person made their most recent New Locations contribution. Person level. Derived using ROW_NUMBER() = 1 for New Locations fund transactions ordered by timestamp DESC. NULL if person has never given to church expansion. Rock > Profile > Transactions.

### `giving.last_financial_transaction_new_locations_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp of the person's most recent New Locations contribution. Person level. Identified as the most recent transaction for New Locations fund type using window function. Format: YYYY-MM-DD HH:MM:SS UTC. NULL for those who haven't given to this fund. Rock > Profile > Transactions.

### `giving.last_financial_transaction_tithes_offerings_campus`

- **Type**: STRING
- **Description**: The campus short code (e.g., 'EDM', 'STW', 'ONL') where the person made their most recent Tithes & Offerings contribution. Person level. Extracted using ROW_NUMBER() window function ordering by timestamp DESC for transactions matching Tithes & Offerings fund descriptions. NULL if person has never given to this fund. Rock > Profile > Transactions.

### `giving.last_financial_transaction_tithes_offerings_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp of the person's most recent Tithes & Offerings contribution. Person level. Identified using ROW_NUMBER() = 1 partitioned by person and fund type, ordered by timestamp DESC. Format: YYYY-MM-DD HH:MM:SS UTC. NULL if person has never given to this fund. Rock > Profile > Transactions.

### `giving.last_financial_transaction_youversion_bible_translation_campus`

- **Type**: STRING
- **Description**: The campus short code where the person made their most recent YouVersion & Bible Translation contribution. Person level. Extracted from the latest transaction matching YouVersion & Bible Translation fund descriptions. NULL if no YouVersion giving history. Rock > Profile > Transactions.

### `giving.last_financial_transaction_youversion_bible_translation_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp of the person's most recent YouVersion & Bible Translation contribution. Person level. Calculated using window function to find the latest YouVersion fund transaction. Format: YYYY-MM-DD HH:MM:SS UTC. NULL for non-YouVersion contributors. Rock > Profile > Transactions.

### `giving.number_of_gifts_last_90_tithes_and_offerings`

- **Type**: INT64
- **Description**: The count of Tithes & Offerings contributions made by the person in the last 90 days. Person level. Calculated by counting transactions where fund description matches Tithes & Offerings and timestamp >= CURRENT_TIMESTAMP - 90 days. COALESCE ensures 0 for non-givers. Used for recent giving activity analysis and donor engagement metrics. Rock > Profile > Transactions.

### `giving_group_id`

- **Type**: INT64
- **Description**: From Rock RMS Person.GivingGroupId. Person-level. ID for grouping family giving together.

### `has_children`

- **Type**: BOOL
- **Description**: Boolean indicating whether or not the Adult person has children in their family, according to Rock RMS.

### `has_children_in_school_grade`

- **Type**: STRUCT<has_children_in_school_grade_kindergarten BOOL, has_children_in_school_grade_1st BOOL, has_children_in_school_grade_2nd BOOL, has_children_in_school_grade_3rd BOOL, has_children_in_school_grade_4th BOOL, has_children_in_school_grade_5th BOOL, has_children_in_school_grade_6th BOOL, has_children_in_school_grade_7th BOOL, has_children_in_school_grade_8th BOOL, has_children_in_school_grade_freshman BOOL, has_children_in_school_grade_sophomore BOOL, has_children_in_school_grade_junior BOOL, has_children_in_school_grade_senior BOOL>
- **Description**: STRUCT containing boolean flags for each school grade level. Person level. Indicates which grades the adult has children enrolled in, based on family relationships and children's school_grade values. Used for parent communication targeting. Data sourced from Rock RMS Person and DefinedValue tables for grades pre-defined.

### `has_children_in_school_grade.has_children_in_school_grade_1st`

- **Type**: BOOL

### `has_children_in_school_grade.has_children_in_school_grade_2nd`

- **Type**: BOOL

### `has_children_in_school_grade.has_children_in_school_grade_3rd`

- **Type**: BOOL

### `has_children_in_school_grade.has_children_in_school_grade_4th`

- **Type**: BOOL

### `has_children_in_school_grade.has_children_in_school_grade_5th`

- **Type**: BOOL

### `has_children_in_school_grade.has_children_in_school_grade_6th`

- **Type**: BOOL

### `has_children_in_school_grade.has_children_in_school_grade_7th`

- **Type**: BOOL

### `has_children_in_school_grade.has_children_in_school_grade_8th`

- **Type**: BOOL

### `has_children_in_school_grade.has_children_in_school_grade_freshman`

- **Type**: BOOL

### `has_children_in_school_grade.has_children_in_school_grade_junior`

- **Type**: BOOL

### `has_children_in_school_grade.has_children_in_school_grade_kindergarten`

- **Type**: BOOL

### `has_children_in_school_grade.has_children_in_school_grade_senior`

- **Type**: BOOL

### `has_children_in_school_grade.has_children_in_school_grade_sophomore`

- **Type**: BOOL

### `has_form_submission_email_subscription_lco_service_reminder`

- **Type**: BOOL
- **Description**: From form_submitted table. Person level. Boolean flag indicating whether the person has submitted the Life.Church Online email subscription form to receive service reminders. TRUE if they've opted in, FALSE if no submission found. Used to determine email eligibility.

### `home_campus`

- **Type**: STRING
- **Description**: Synonymous with Rock Campus. See lc_campus for description.

### `home_campus_region`

- **Type**: STRING
- **Description**: The geographical region or area grouping for the campus (e.g., 'Region 2A - Bryan Hill', 'Region 1B - Oklahoma'). Sourced from Rock RMS Campus Area attribute via campus_staging table. Used for regional analysis and leadership reporting structures.

### `household`

- **Type**: STRUCT<family_name STRING, campus STRING, first_lifekids_checkin_timestamp TIMESTAMP, first_lifekids_checkin_campus STRING, last_lifekids_checkin_timestamp TIMESTAMP, last_lifekids_checkin_campus STRING, first_financial_transaction_timestamp TIMESTAMP, first_financial_transaction_campus INT64, last_financial_transaction_timestamp TIMESTAMP, last_financial_transaction_campus INT64, last_checkin_timestamp TIMESTAMP, last_checkin_campus STRING, first_checkin_timestamp TIMESTAMP, first_checkin_campus STRING, address_1 STRING, address_2 STRING, postal_code STRING, city STRING, state_province STRING, country STRING, county STRING, longitude FLOAT64, latitude FLOAT64, is_legacy_team_prospect BOOL, first_household_weekend_attendance_timestamp TIMESTAMP, first_household_weekend_attendance_campus STRING, last_household_weekend_attendance_timestamp TIMESTAMP, last_household_weekend_attendance_campus STRING, first_household_weekend_physical_attendance_timestamp TIMESTAMP, first_household_weekend_physical_attendance_campus STRING, last_household_weekend_physical_attendance_timestamp TIMESTAMP, last_household_weekend_physical_attendance_campus STRING, last_household_attendance_timestamp_the_loop TIMESTAMP, last_household_attendance_campus_short_code_the_loop STRING, last_household_attendance_timestamp_let_there_be_light TIMESTAMP, last_household_attendance_campus_short_code_let_there_be_light STRING, last_household_attendance_timestamp_in_the_jungle TIMESTAMP, last_household_attendance_campus_short_code_in_the_jungle STRING, last_household_attendance_timestamp_starry_night TIMESTAMP, last_household_attendance_campus_short_code_starry_night STRING, last_household_attendance_timestamp_under_the_sea TIMESTAMP, last_household_attendance_campus_short_code_under_the_sea STRING, last_household_attendance_timestamp_konnect TIMESTAMP, last_household_attendance_campus_short_code_konnect STRING, last_household_attendance_timestamp_the_garden TIMESTAMP, last_household_attendance_campus_short_code_the_garden STRING, last_household_attendance_timestamp_switch_student TIMESTAMP, last_household_attendance_campus_short_code_switch_student STRING, last_household_attendance_timestamp_crosstown TIMESTAMP, last_household_attendance_campus_short_code_crosstown STRING, last_household_attendance_timestamp_the_ark TIMESTAMP, last_household_attendance_campus_short_code_the_ark STRING>
- **Description**: From Data Warehouse, using Rock person data. Household level. The full name of the family. Rock > Profile > Family Attributes.

### `household.address_1`

- **Type**: STRING
- **Description**: From Rock RMS Location.Street1. Entity level. The primary street address line for the entity physical location.

### `household.address_2`

- **Type**: STRING
- **Description**: From Rock RMS Location.Street2. Entity level. The secondary address line (suite, building, etc). Returns empty string if NULL.

### `household.campus`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock person data. Person level. The main, home, primary, or preferred campus of the person. This is the best source for identifing which campus a person belongs to. Rock > Profile > Main Contact Details.

### `household.city`

- **Type**: STRING
- **Description**: From Rock RMS Location. Entity level. The city where the entity is located.

### `household.country`

- **Type**: STRING
- **Description**: From location.country. Person level. The country of the person's home address. Typically 'US' for most records. Used for international attendee identification.

### `household.county`

- **Type**: STRING
- **Description**: From person_location table. Family-level. County name. Rock > Person > Address.

### `household.family_name`

- **Type**: STRING
- **Description**: From household_staging table. Household level. The last name or designated family name for the household. Rock > People > Family.

### `household.first_checkin_campus`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The campus where the family first checked in for attendance (not serving). Rock > History > Attendance History.

### `household.first_checkin_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The date the family first checked in for attendance (not serving). Rock > History > Attendance History.

### `household.first_financial_transaction_campus`

- **Type**: INT64
- **Description**: From Data Warehouse, using Rock financial transaction data. Household level. The campus where the family first gave a gift. Rock > Profile > Transactions. Or Rock > Contributions.

### `household.first_financial_transaction_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Data Warehouse, using Rock financial transaction data. Household level. The date the family first gave a gift. Rock > Profile > Transactions. Or Rock > Contributions.

### `household.first_household_weekend_attendance_campus`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The campus where the family first checked in to attend (not serve) on a weekend. Rock > History > Attendance History.

### `household.first_household_weekend_attendance_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The date the family first checked in to attend (not serve) on a weekend. Rock > History > Attendance History.

### `household.first_household_weekend_physical_attendance_campus`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The campus where the family first checked in to attend (not serve) physically (not LCO) on a weekend. Rock > History > Attendance History.

### `household.first_household_weekend_physical_attendance_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The date the family first checked in to attend (not serve) physicaly (not LCO) on a weekend. Rock > History > Attendance History.

### `household.first_lifekids_checkin_campus`

- **Type**: STRING
- **Description**: From Rock attendance tables for NextGen. Family level displayed at person level. The campus code where this person's household first attended LifeKids. NULL if no family LifeKids attendance.

### `household.first_lifekids_checkin_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock attendance tables for NextGen. Family level displayed at person level. The timestamp of the first LifeKids check-in by any member of this person's household. NULL if no family LifeKids attendance.

### `household.is_legacy_team_prospect`

- **Type**: BOOL
- **Description**: From household_staging table calculated using financial transactions. Household level. Boolean flag indicating whether any non-staff member in this household has contributed at least 20,000 within the past 12 months, making them a prospect for the Legacy Team giving program. This flag is applied to all family members since giving is viewed at the household level - if one family member qualifies based on their giving, the entire household is marked as a prospect. Excludes households where any member is already a Legacy Team member (is_legacy_team_member = TRUE). Rock > Contributions.

### `household.last_checkin_campus`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in for attendance (not serving). Rock > History > Attendance History.

### `household.last_checkin_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in for attendance (not serving). Rock > History > Attendance History.

### `household.last_financial_transaction_campus`

- **Type**: INT64
- **Description**: From Data Warehouse, using Rock financial transaction data. Household level. The campus where the family last gave a gift. Rock > Profile > Transactions. Or Rock > Contributions.

### `household.last_financial_transaction_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Data Warehouse, using Rock financial transaction data. Household level. The date the family last gave a gift. Rock > Profile > Transactions. Or Rock > Contributions.

### `household.last_household_attendance_campus_short_code_crosstown`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in a child to the Crosstown room. Rock > History > Attendance History.

### `household.last_household_attendance_campus_short_code_in_the_jungle`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in a child to the In The Jungle room. Rock > History > Attendance History.

### `household.last_household_attendance_campus_short_code_konnect`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in a child to the Konnect room. Rock > History > Attendance History.

### `household.last_household_attendance_campus_short_code_let_there_be_light`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in a child to Lifekids. Rock > History > Attendance History.

### `household.last_household_attendance_campus_short_code_starry_night`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in a child to the Starry Night room. Rock > History > Attendance History.

### `household.last_household_attendance_campus_short_code_switch_student`

- **Type**: STRING
- **Description**: From Rock attendance tables for Switch. Family level displayed at person level. The campus code where this person's household most recently attended Switch. NULL if no family Switch attendance.

### `household.last_household_attendance_campus_short_code_the_ark`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in a child to The Ark room. Rock > History > Attendance History.

### `household.last_household_attendance_campus_short_code_the_garden`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in a child to the In The Garden room. Rock > History > Attendance History.

### `household.last_household_attendance_campus_short_code_the_loop`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in a child to The Loop room. Rock > History > Attendance History.

### `household.last_household_attendance_campus_short_code_under_the_sea`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in a child to the Under The Sea room. Rock > History > Attendance History.

### `household.last_household_attendance_timestamp_crosstown`

- **Type**: TIMESTAMP
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in a child to the Crosstown room. Rock > History > Attendance History.

### `household.last_household_attendance_timestamp_in_the_jungle`

- **Type**: TIMESTAMP
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in a child to the In The Jungle room. Rock > History > Attendance History.

### `household.last_household_attendance_timestamp_konnect`

- **Type**: TIMESTAMP
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in a child to the Konnect room. Rock > History > Attendance History.

### `household.last_household_attendance_timestamp_let_there_be_light`

- **Type**: TIMESTAMP
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in a child to Lifekids. Rock > History > Attendance History.

### `household.last_household_attendance_timestamp_starry_night`

- **Type**: TIMESTAMP
- **Description**: From Data Warehosue, using Rock attendance data. Person level. The date the person last checked into serve in Switch. Rock > History > Attendance History.

### `household.last_household_attendance_timestamp_switch_student`

- **Type**: TIMESTAMP
- **Description**: From Rock attendance tables for Switch. Family level displayed at person level. The timestamp of the most recent Switch check-in by any member of this person's household. NULL if no family Switch attendance.

### `household.last_household_attendance_timestamp_the_ark`

- **Type**: TIMESTAMP
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in a child to The Ark room. Rock > History > Attendance History.

### `household.last_household_attendance_timestamp_the_garden`

- **Type**: TIMESTAMP
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in a child to the In The Garden room. Rock > History > Attendance History.

### `household.last_household_attendance_timestamp_the_loop`

- **Type**: TIMESTAMP
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in a child to The Loop room. Rock > History > Attendance History.

### `household.last_household_attendance_timestamp_under_the_sea`

- **Type**: TIMESTAMP
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in a child to the Under The Sea room. Rock > History > Attendance History.

### `household.last_household_weekend_attendance_campus`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in to attend (not serve) on a weekend. Rock > History > Attendance History.

### `household.last_household_weekend_attendance_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in to attend (not serve) on a weekend. Rock > History > Attendance History.

### `household.last_household_weekend_physical_attendance_campus`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The campus where the family last checked in to attend (not serve) physically (not LCO) on a weekend. Rock > History > Attendance History.

### `household.last_household_weekend_physical_attendance_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Data Warehouse, using Rock attendance data. Household level. The date the family last checked in to attend (not serve) physicaly (not LCO) on a weekend. Rock > History > Attendance History.

### `household.last_lifekids_checkin_campus`

- **Type**: STRING
- **Description**: From Rock attendance tables for NextGen. Family level displayed at person level. The campus code where this person's household most recently attended LifeKids. NULL if no family LifeKids attendance.

### `household.last_lifekids_checkin_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock attendance tables for NextGen. Family level displayed at person level. The timestamp of the most recent LifeKids check-in by any member of this person's household. NULL if no family LifeKids attendance.

### `household.latitude`

- **Type**: FLOAT64
- **Description**: Extracted from Rock RMS Location.GeoPoint using custom function. Entity level. The latitude coordinate of the entity location in decimal degrees. Used for mapping and distance calculations.

### `household.longitude`

- **Type**: FLOAT64
- **Description**: Extracted from Rock RMS Location.GeoPoint using custom function. Entity level. The longitude coordinate of the entity location in decimal degrees. Used for mapping and distance calculations.

### `household.postal_code`

- **Type**: STRING
- **Description**: From Rock RMS Location.postalcode. Person level. The ZIP code of the person's home address. Used for geographic analysis and drive time calculations.

### `household.state_province`

- **Type**: STRING
- **Description**: From person_location table. Family-level. Full state/province name. Rock > Person > Address.

### `hubspot_contact_email`

- **Type**: STRING
- **Description**: From person_hubspot_id intermediate table. Person-level. The validated email address associated with the HubSpot match. Either pulled from HubSpot contact.property_email or falls back to the Rock email used for matching. Must pass email regex validation.

### `hubspot_contact_id`

- **Type**: STRING
- **Description**: From person_hubspot_id intermediate table. Person-level. The best match identifier linking Rock person to HubSpot contact, determined through complex matching logic using primary/secondary emails and name validation. Can be either a HubSpot contact ID (numeric) or an email address. Prioritizes matches with most accurate name alignment.

### `is_adult`

- **Type**: BOOL
- **Description**: Boolean indicating whether or not the person is an adult in their family. TRUE indicates the person is an Adult. Rule of thumb defines a person as Adult when older than 18 years old. FALSE indicates the person is a Child or Unknown.

### `is_app_connection_enabled`

- **Type**: BOOL
- **Description**: Boolean indicating if the person has app connection features enabled.

### `is_app_scheduling_enabled`

- **Type**: BOOL
- **Description**: Boolean indicating if the person has app scheduling features enabled.

### `is_app_user`

- **Type**: BOOL
- **Description**: From Data Warehouse, using Segment app data. Person level. Whether the person has ever used the app or not. Segment > Unify > Profile Explorer > Search User (Person Alias Id) > Traits > Computed Traits > first_app_usage.

### `is_banned_giver`

- **Type**: STRING
- **Description**: String value ('True') indicating the person has been flagged as a banned giver, typically due to fraudulent activity or chargebacks. Person level. From Rock person attribute BannedGiver. Rock > Profile > Person Profile > Attributes > Banned Giver.

### `is_business`

- **Type**: BOOL
- **Description**: From Rock RMS Person.RecordTypeValueId. Person-level. TRUE if record type is Business (ID=2), FALSE for individual persons. Rock > Person.

### `is_deceased`

- **Type**: BOOL
- **Description**: From Rock RMS Person.isdeceased. Person level. Boolean flag indicating if the person is marked as deceased in Rock RMS. TRUE if deceased, FALSE if living. Important for data hygiene and filtering.

### `is_deletion_requested`

- **Type**: BOOL
- **Description**: Calculated field. Person-level. TRUE if person has requested data deletion. FALSE otherwise.

### `is_legacy_team_member`

- **Type**: BOOL
- **Description**: Boolean indicating whether the person is a Legacy Team member.

### `is_legacy_team_prospect`

- **Type**: BOOL
- **Description**: From household_staging table calculated using financial transactions. Household level. Boolean flag indicating whether any non-staff member in this household has contributed at least 20,000 within the past 12 months, making them a prospect for the Legacy Team giving program. This flag is applied to all family members since giving is viewed at the household level - if one family member qualifies based on their giving, the entire household is marked as a prospect. Excludes households where any member is already a Legacy Team member (is_legacy_team_member = TRUE). Rock > Contributions.

### `is_lifegroup_leader`

- **Type**: BOOL
- **Description**: Boolean indicating whether or not the person is a LifeGroup leader. Defaults to FALSE if null.

### `is_rms_person_inactive`

- **Type**: BOOL
- **Description**: From Rock RMS Person.RecordStatusValueId. Person-level. TRUE if record status is Inactive (matching constant). NULL if active. Rock > Person.

### `is_staff`

- **Type**: BOOL
- **Description**: Boolean indicating whether or not the person is a staff member for Life.Church. Defaults to FALSE if null.

### `is_statement_suppressed`

- **Type**: STRING
- **Description**: String value ('True') indicating the person has opted out of receiving printed contribution statements. Person level. From Rock person attribute SuppressSendingContributionStatements. Rock > Profile > Person Profile > Attributes > Suppress Sending Contribution Statements.

### `is_volunteer`

- **Type**: BOOL
- **Description**: Boolean indicating if the person is currently serving as a volunteer.

### `job_title`

- **Type**: STRING
- **Description**: The job title from the Employee Sync Information avalable in RMS. Person level. From Rock person attributes. Rock > Profile > Person Profile > Extended Attributes > Employment Information Sync

### `last_attendance_app_campus`

- **Type**: STRING
- **Description**: From attender_check_in filtered for app check-ins. Person level. The campus code where the person most recently checked in via the app. Rock > Person > History.

### `last_attendance_app_timestamp`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in filtered for app check-ins. Person level. The timestamp of the person's most recent attendance check-in via the Life.Church mobile app. NULL if never used app check-in. Rock > Person > History.

### `last_attendance_campus`

- **Type**: STRING
- **Description**: From attendance_combined filtered for non-volunteer attendance. Person level. The campus code where the person most recently attended a weekend experience. Rock > Person > History.

### `last_attendance_combined_campus`

- **Type**: STRING
- **Description**: From attendance_combined including all attendance types. Person level. The campus code where the person had their most recent check-in of any type.

### `last_attendance_combined_parent_group`

- **Type**: STRING
- **Description**: From attendance_combined including all attendance types. Person level. The parent group name of the person's most recent check-in. Indicates current engagement area. .

### `last_attendance_combined_timestamp`

- **Type**: TIMESTAMP
- **Description**: From attendance_combined including all attendance types. Person level. The timestamp of the person's most recent check-in of any type. The latest interaction with Life.Church.

### `last_attendance_host_team_campus`

- **Type**: STRING
- **Description**: From attender_check_in via parent group pivot. Person level. The campus code where the person most recently served on Host Team. Rock > Person > History.

### `last_attendance_host_team_timestamp`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via parent group pivot. Person level. The timestamp of the person's most recent check-in as a Host Team volunteer. NULL if never served. Rock > Person > History.

### `last_attendance_lifekids_campus_crosstown`

- **Type**: STRING
- **Description**: From attender_check_in via attendance group pivot. Person level. The campus code where the person most recently attended Crosstown LifeKids room. Rock > Person > History.

### `last_attendance_lifekids_campus_in_the_jungle`

- **Type**: STRING
- **Description**: From attender_check_in via attendance group pivot. Person level. The campus code where the person most recently attended In The Jungle LifeKids room. Rock > Person > History.

### `last_attendance_lifekids_campus_konnect`

- **Type**: STRING
- **Description**: From attender_check_in via attendance group pivot. Person level. The campus code where the person most recently attended Konnect LifeKids room. Rock > Person > History.

### `last_attendance_lifekids_campus_let_there_be_light`

- **Type**: STRING
- **Description**: From attender_check_in via attendance group pivot. Person level. The campus code where the person most recently attended Let There Be Light LifeKids room. Rock > Person > History.

### `last_attendance_lifekids_campus_starry_night`

- **Type**: STRING
- **Description**: From attender_check_in via attendance group pivot. Person level. The campus code where the person most recently attended Starry Night LifeKids room. Rock > Person > History.

### `last_attendance_lifekids_campus_the_ark`

- **Type**: STRING
- **Description**: From attender_check_in via attendance group pivot. Person level. The campus code where the person most recently attended The Ark LifeKids room. Rock > Person > History.

### `last_attendance_lifekids_campus_the_garden`

- **Type**: STRING
- **Description**: From attender_check_in via attendance group pivot. Person level. The campus code where the person most recently attended The Garden LifeKids room. Rock > Person > History.

### `last_attendance_lifekids_campus_the_loop`

- **Type**: STRING
- **Description**: From attender_check_in via attendance group pivot. Person level. The campus code where the person most recently attended The Loop LifeKids room. Rock > Person > History.

### `last_attendance_lifekids_campus_under_the_sea`

- **Type**: STRING
- **Description**: From attender_check_in via attendance group pivot. Person level. The campus code where the person most recently attended Under The Sea LifeKids room. Rock > Person > History.

### `last_attendance_lifekids_timestamp_crosstown`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via attendance group pivot. Person level. The timestamp of the person's most recent check-in to Crosstown LifeKids room. NULL if never attended. Rock > Person > History.

### `last_attendance_lifekids_timestamp_in_the_jungle`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via attendance group pivot. Person level. The timestamp of the person's most recent check-in to In The Jungle LifeKids room. NULL if never attended. Rock > Person > History.

### `last_attendance_lifekids_timestamp_konnect`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via attendance group pivot. Person level. The timestamp of the person's most recent check-in to Konnect LifeKids room. NULL if never attended. Rock > Person > History.

### `last_attendance_lifekids_timestamp_let_there_be_light`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via attendance group pivot. Person level. The timestamp of the person's most recent check-in to Let There Be Light LifeKids room. NULL if never attended. Rock > Person > History.

### `last_attendance_lifekids_timestamp_starry_night`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via attendance group pivot. Person level. The timestamp of the person's most recent check-in to Starry Night LifeKids room. NULL if never attended. Rock > Person > History.

### `last_attendance_lifekids_timestamp_the_ark`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via attendance group pivot. Person level. The timestamp of the person's most recent check-in to The Ark LifeKids room. NULL if never attended. Rock > Person > History.

### `last_attendance_lifekids_timestamp_the_garden`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via attendance group pivot. Person level. The timestamp of the person's most recent check-in to The Garden LifeKids room. NULL if never attended. Rock > Person > History.

### `last_attendance_lifekids_timestamp_the_loop`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via attendance group pivot. Person level. The timestamp of the person's most recent check-in to The Loop LifeKids room. NULL if never attended. Rock > Person > History.

### `last_attendance_lifekids_timestamp_under_the_sea`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via attendance group pivot. Person level. The timestamp of the person's most recent check-in to Under The Sea LifeKids room. NULL if never attended. Rock > Person > History.

### `last_attendance_switch_campus`

- **Type**: STRING
- **Description**: From attender_check_in via parent group pivot. Person level. The campus code where the person most recently attended Switch student ministry. Rock > Person > History.

### `last_attendance_switch_campus_student`

- **Type**: STRING
- **Description**: From attender_check_in via attendance group pivot. Person level. The campus code where the person most recently attended Switch student ministry. Rock > Person > History.

### `last_attendance_switch_timestamp`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via parent group pivot. Person level. The timestamp of the person's most recent check-in to Switch student ministry. NULL if never attended. Rock > Person > History.

### `last_attendance_switch_timestamp_student`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via attendance group pivot. Person level. The timestamp of the person's most recent check-in to Switch student ministry. NULL if never attended. Rock > Person > History.

### `last_attendance_timestamp`

- **Type**: TIMESTAMP
- **Description**: From attendance_combined filtered for non-volunteer attendance. Person level. The timestamp of the person's most recent weekend attendance at any campus. Rock > Person > History.

### `last_conditional_attendance_agreement_status`

- **Type**: STRING
- **Description**: From Rock defined values for standard requirements. Person level. The status of the person's most recent conditional attendance agreement.

### `last_conditional_attendance_agreement_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock attribute matrix for standard requirements. Person level. The timestamp of the person's most recent conditional attendance agreement. NULL if no agreement. Rock > Person > Extended Attributes.

### `last_connection_request_campus`

- **Type**: STRING
- **Description**: From ConnectionRequest table. Person level. The campus associated with their most recent connection request.

### `last_connection_request_timestamp`

- **Type**: TIMESTAMP
- **Description**: From ConnectionRequest table. Person level. The most recent timestamp when this person submitted any connection request.

### `last_digital_invite_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Interaction table filtered by digital invite component. Person level. The most recent timestamp when this person sent a digital invite to someone.

### `last_financial_transaction_campus`

- **Type**: STRING
- **Description**: The campus short code where the person made their most recent financial contribution. Person level. Retrieved from the campus associated with the last transaction. Rock > Profile > Transactions.

### `last_financial_transaction_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp of the person's most recent financial contribution to Life.Church. Person level. Calculated as the latest transaction from fact_giving where amount >= 0 and is_successful = TRUE. Rock > Profile > Transactions.

### `last_form_submission_account_acquisition_timestamp_addiction`

- **Type**: TIMESTAMP
- **Description**: Calculated via PIVOT MAX on form_submission_timestamp. Person level. The most recent timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department. Indicates continued or renewed interest in this topic area and church engagement.

### `last_form_submission_account_acquisition_timestamp_anxiety`

- **Type**: TIMESTAMP
- **Description**: Calculated via PIVOT MAX on form_submission_timestamp. Person level. The most recent timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department. Indicates continued or renewed interest in this topic area and church engagement.

### `last_form_submission_account_acquisition_timestamp_burnout`

- **Type**: TIMESTAMP
- **Description**: Calculated via PIVOT MAX on form_submission_timestamp. Person level. The most recent timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department. Indicates continued or renewed interest in this topic area and church engagement.

### `last_form_submission_account_acquisition_timestamp_finance`

- **Type**: TIMESTAMP
- **Description**: Calculated via PIVOT MAX on form_submission_timestamp. Person level. The most recent timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department. Indicates continued or renewed interest in this topic area and church engagement.

### `last_form_submission_account_acquisition_timestamp_friendship`

- **Type**: TIMESTAMP
- **Description**: Calculated via GREATEST function combining friendship and friendships form variants. Person level. The most recent timestamp when this person submitted any friendship-related account acquisition form through HubSpot paid marketing campaigns managed by the Reach department, accounting for historical form naming variations. Indicates continued or renewed interest in this topic area and church engagement.

### `last_form_submission_account_acquisition_timestamp_grief`

- **Type**: TIMESTAMP
- **Description**: Calculated via PIVOT MAX on form_submission_timestamp. Person level. The most recent timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department. Indicates continued or renewed interest in this topic area and church engagement.

### `last_form_submission_account_acquisition_timestamp_habits`

- **Type**: TIMESTAMP
- **Description**: Calculated via PIVOT MAX on form_submission_timestamp. Person level. The most recent timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department. Indicates continued or renewed interest in this topic area and church engagement.

### `last_form_submission_account_acquisition_timestamp_parenting`

- **Type**: TIMESTAMP
- **Description**: Calculated via PIVOT MAX on form_submission_timestamp. Person level. The most recent timestamp when this person submitted this specific topic-focused account acquisition form through HubSpot paid marketing campaigns managed by the Reach department. Indicates continued or renewed interest in this topic area and church engagement.

### `last_form_submission_email_subscription_campus_lco_service_reminder`

- **Type**: STRING
- **Description**: From form_submitted and campus_staging tables. Person level. The three-letter campus code associated with the person's most recent LCO email subscription form submission.

### `last_form_submission_email_subscription_timestamp_lco_service_reminder`

- **Type**: TIMESTAMP
- **Description**: From form_submitted table. Person level. The UTC timestamp of when the person most recently submitted the LCO email subscription form. Used to track subscription recency and determine service time preferences.

### `last_form_submission_next_steps_campus_baptism`

- **Type**: STRING
- **Description**: Filtered for specific form using constants. Person level. The campus where this person most recently submitted this next steps form.

### `last_form_submission_next_steps_campus_commit_to_christ`

- **Type**: STRING
- **Description**: Filtered for specific form using constants. Person level. The campus where this person most recently submitted this next steps form.

### `last_form_submission_next_steps_campus_general_question`

- **Type**: STRING
- **Description**: Filtered for specific form using constants. Person level. The campus where this person most recently submitted this next steps form.

### `last_form_submission_next_steps_campus_im_new_here`

- **Type**: STRING
- **Description**: Filtered for specific form using constants. Person level. The campus where this person most recently submitted this next steps form.

### `last_form_submission_next_steps_campus_known`

- **Type**: STRING
- **Description**: Filtered for specific form using constants. Person level. The campus where this person most recently submitted this next steps form.

### `last_form_submission_next_steps_campus_prayer_request`

- **Type**: STRING
- **Description**: Filtered for specific form using constants. Person level. The campus where this person most recently submitted this next steps form.

### `last_form_submission_next_steps_campus_renewing_commitment_to_christ`

- **Type**: STRING
- **Description**: Filtered for specific form using constants. Person level. The campus where this person most recently submitted this next steps form.

### `last_form_submission_next_steps_timestamp_baptism`

- **Type**: TIMESTAMP
- **Description**: Filtered for specific form using constants. Person level. The most recent timestamp when this person submitted this next steps form, indicating continued or renewed spiritual engagement.

### `last_form_submission_next_steps_timestamp_commit_to_christ`

- **Type**: TIMESTAMP
- **Description**: Filtered for specific form using constants. Person level. The most recent timestamp when this person submitted this next steps form, indicating continued or renewed spiritual engagement.

### `last_form_submission_next_steps_timestamp_general_question`

- **Type**: TIMESTAMP
- **Description**: Filtered for specific form using constants. Person level. The most recent timestamp when this person submitted this next steps form, indicating continued or renewed spiritual engagement.

### `last_form_submission_next_steps_timestamp_im_new_here`

- **Type**: TIMESTAMP
- **Description**: Filtered for specific form using constants. Person level. The most recent timestamp when this person submitted this next steps form, indicating continued or renewed spiritual engagement.

### `last_form_submission_next_steps_timestamp_known`

- **Type**: TIMESTAMP
- **Description**: Filtered for specific form using constants. Person level. The most recent timestamp when this person submitted this next steps form, indicating continued or renewed spiritual engagement.

### `last_form_submission_next_steps_timestamp_prayer_request`

- **Type**: TIMESTAMP
- **Description**: Filtered for specific form using constants. Person level. The most recent timestamp when this person submitted this next steps form, indicating continued or renewed spiritual engagement.

### `last_form_submission_next_steps_timestamp_renewing_commitment_to_christ`

- **Type**: TIMESTAMP
- **Description**: Filtered for specific form using constants. Person level. The most recent timestamp when this person submitted this next steps form, indicating continued or renewed spiritual engagement.

### `last_household_attendance_switch_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock attendance tables for Switch. Family level displayed at person level. The timestamp of the most recent Switch check-in by any member of this person's household. NULL if no family Switch attendance.

### `last_lco_engagement_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp of the person's most recent Life.Church Online (LCO) engagement or campus-less interaction. This includes attendance, serving, financial transactions, form submissions, volunteer interest forms, person creation records, baptism attributes, and known attendance records where the campus is NULL or 'INT' (LCO indicator). NULL indicates the person has never had a recorded LCO engagement.

### `last_name`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock person data. Person level. The last name of the person. Rock > Profile > Main Contact Details.

### `last_physical_campus_engagement_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp of the person's most recent engagement at any physical Life.Church campus location. This includes physical attendance, serving, financial transactions, form submissions, volunteer interest forms, person creation records, baptism attributes, and known attendance records where the campus is not NULL and not 'INT' (LCO). NULL indicates the person has never had a recorded physical campus engagement.

### `last_row_update_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Fivetran, Person._fivetran_synced. Person-level. Timestamp of last Fivetran sync for this record. Format: TIMESTAMP.

### `last_scheduled_financial_transaction_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp of the most recent transaction that was part of a scheduled/recurring gift. Person level. Latest transaction timestamp where financial_transaction_schedule_id is not null. Rock > Profile > Scheduled Transactions > Transaction History.

### `last_segment_interaction_timestamp`

- **Type**: TIMESTAMP
- **Description**: From aggregated Segment events. Person level. The latest timestamp across all tracked sources, representing the person's most recent digital interaction with any Life.Church platform. Used to determine overall engagement recency. Calculated as MAX of all source-specific last interactions.

### `last_segment_interaction_timestamp_chop_prod`

- **Type**: TIMESTAMP
- **Description**: From Segment events table. Person level. The timestamp of the person's most recent interaction with Church Online Platform. Indicates latest online church engagement.

### `last_segment_interaction_timestamp_finds_life_prod`

- **Type**: TIMESTAMP
- **Description**: From Segment events table. Person level. The timestamp of the person's most recent interaction with finds.life website. Shows latest church finder usage.

### `last_segment_interaction_timestamp_hubspot_email_events_dev`

- **Type**: TIMESTAMP
- **Description**: From Segment events table. Person level. The timestamp of the person's most recent email interaction tracked through HubSpot. Shows latest email engagement activity.

### `last_segment_interaction_timestamp_hubspot_form_submission`

- **Type**: TIMESTAMP
- **Description**: From Segment events table. Person level. The timestamp of the person's most recent form submission tracked through HubSpot. Records latest form completion.

### `last_segment_interaction_timestamp_kotlin_android`

- **Type**: TIMESTAMP
- **Description**: From Segment events table. Person level. The timestamp of the person's most recent interaction with the Life.Church Android app (Kotlin version). Tracks current Android app usage.

### `last_segment_interaction_timestamp_lc_ios_swift`

- **Type**: TIMESTAMP
- **Description**: From Segment events table. Person level. The timestamp of the person's most recent interaction with the Life.Church iOS app (Swift version). Tracks current iOS app usage.

### `last_segment_interaction_timestamp_lcweb`

- **Type**: TIMESTAMP
- **Description**: From Segment events table. Person level. The timestamp of the person's most recent interaction with the main Life.Church website. Shows latest web engagement.

### `last_segment_interaction_timestamp_lifechurch_android`

- **Type**: TIMESTAMP
- **Description**: From Segment events table. Person level. The timestamp of the person's most recent interaction with the legacy Life.Church Android app. Tracks continued usage of older Android version.

### `last_segment_interaction_timestamp_lifechurch_ios`

- **Type**: TIMESTAMP
- **Description**: From Segment events table. Person level. The timestamp of the person's most recent interaction with the legacy Life.Church iOS app. Tracks continued usage of older iOS version.

### `last_segment_interaction_timestamp_rms_prod_js`

- **Type**: TIMESTAMP
- **Description**: From Segment events table. Person level. The timestamp of the person's most recent interaction tracked by Rock RMS JavaScript SDK. Shows latest Rock-integrated web activity.

### `last_served_activity`

- **Type**: STRING
- **Description**: From volunteer_check_in table. Person level. The specific serving role or activity name from the person's most recent volunteer check-in.

### `last_served_campus`

- **Type**: STRING
- **Description**: The campus where the person last served/volunteered.

### `last_served_host_team_activity`

- **Type**: STRING
- **Description**: From volunteer_check_in table. Person level. The specific Host Team role from the person's most recent Host Team check-in.

### `last_served_host_team_campus`

- **Type**: STRING
- **Description**: From Data Warehouse, using Rock attendance data. Person level. The campus where the person last checked in to serve with Host Team. Rock > History > Attendance History.

### `last_served_host_team_timestamp`

- **Type**: TIMESTAMP
- **Description**: From volunteer_check_in table. Person level. The timestamp when the person most recently served in Host Team ministry.

### `last_served_operations_activity`

- **Type**: STRING
- **Description**: From Data Warehosue, using Rock attendance data. Person level. The activity for which the person last checked into serve in Operations. Rock > History > Attendance History.

### `last_served_operations_campus`

- **Type**: STRING
- **Description**: From Data Warehosue, using Rock attendance data. Person level. The campus where the person last checked into serve in Operations. Rock > History > Attendance History.

### `last_served_operations_timestamp`

- **Type**: TIMESTAMP
- **Description**: From volunteer_check_in table. Person level. The timestamp when the person most recently served in Operations ministry.

### `last_served_switch_activity`

- **Type**: STRING
- **Description**: From Data Warehosue, using Rock attendance data. Person level. The activity for which the person last checked into serve in Switch. Rock > History > Attendance History.

### `last_served_switch_campus`

- **Type**: STRING
- **Description**: From Data Warehosue, using Rock attendance data. Person level. The campus where the person last checked into serve in Switch. Rock > History > Attendance History.

### `last_served_switch_timestamp`

- **Type**: TIMESTAMP
- **Description**: From volunteer_check_in table. Person level. The timestamp when the person most recently served in Switch youth ministry.

### `last_served_timestamp`

- **Type**: TIMESTAMP
- **Description**: From volunteer_check_in table. Person level. The timestamp of the person's most recent volunteer serving check-in across all ministries. Indicates current volunteer engagement.

### `last_served_worship_activity`

- **Type**: STRING
- **Description**: From volunteer_check_in table. Person level. The specific Worship Team role from the person's most recent Worship check-in.

### `last_served_worship_campus`

- **Type**: STRING
- **Description**: From volunteer_check_in and Campus tables. Person level. The three-letter campus code where the person most recently served on Worship Team.

### `last_served_worship_timestamp`

- **Type**: TIMESTAMP
- **Description**: From volunteer_check_in table. Person level. The timestamp when the person most recently served on Worship Team.

### `last_step_next_steps_campus_you_said_yes`

- **Type**: STRING
- **Description**: From Step table filtered by YSY step type. Person level. The campus where this person most recently completed the You Said Yes step.

### `last_step_next_steps_timestamp_you_said_yes`

- **Type**: TIMESTAMP
- **Description**: From Step table filtered by YSY step type. Person level. The most recent timestamp when this person completed the You Said Yes step.

### `last_volunteer_campus`

- **Type**: STRING
- **Description**: From attendance_combined filtered for volunteer attendance. Person level. The campus code where the person most recently served as a volunteer.

### `last_volunteer_interest_campus_short_code_host_team`

- **Type**: STRING
- **Description**: From volunteer_interest_forms table. Person level. The three-letter campus code from the person's most recent Host Team volunteer interest submission.

### `last_volunteer_interest_campus_short_code_lifegroups_lifemissions`

- **Type**: STRING
- **Description**: From volunteer_interest_forms table. Person level. The three-letter campus code from the person's most recent LifeGroups/LifeMissions interest submission.

### `last_volunteer_interest_campus_short_code_media`

- **Type**: STRING
- **Description**: From volunteer_interest_forms table. Person level. The three-letter campus code from the person's most recent Media/Tech volunteer interest submission.

### `last_volunteer_interest_campus_short_code_operations_team`

- **Type**: STRING
- **Description**: From volunteer_interest_forms table. Person level. The three-letter campus code from the person's most recent Operations volunteer interest submission.

### `last_volunteer_interest_campus_short_code_switch`

- **Type**: STRING
- **Description**: From volunteer_interest_forms table. Person level. The three-letter campus code from the person's most recent Switch volunteer interest submission.

### `last_volunteer_interest_host_team_timestamp`

- **Type**: TIMESTAMP
- **Description**: From volunteer_interest_forms table. Person level. The timestamp when the person most recently submitted a volunteer interest form for Host Team ministry. Used to track renewed or ongoing interest. .

### `last_volunteer_interest_lifegroups_lifemissions_timestamp`

- **Type**: TIMESTAMP
- **Description**: From volunteer_interest_forms table. Person level. The timestamp when the person most recently submitted a volunteer interest form for LifeGroups/LifeMissions. .

### `last_volunteer_interest_media_timestamp`

- **Type**: TIMESTAMP
- **Description**: From volunteer_interest_forms table. Person level. The timestamp when the person most recently submitted a volunteer interest form for Media/Tech ministries.

### `last_volunteer_interest_operations_team_timestamp`

- **Type**: TIMESTAMP
- **Description**: From volunteer_interest_forms table. Person level. The timestamp when the person most recently submitted a volunteer interest form for Operations Team.

### `last_volunteer_interest_switch_timestamp`

- **Type**: TIMESTAMP
- **Description**: From volunteer_interest_forms table. Person level. The timestamp when the person most recently submitted a volunteer interest form for Switch ministry.

### `last_volunteer_timestamp`

- **Type**: TIMESTAMP
- **Description**: From attendance_combined filtered for volunteer attendance. Person level. The timestamp of the person's most recent volunteer serving check-in.

### `latitude`

- **Type**: FLOAT64
- **Description**: Extracted from Rock RMS Location.GeoPoint using custom function. Entity level. The latitude coordinate of the entity location in decimal degrees. Used for mapping and distance calculations.

### `legacy_team_approval_date`

- **Type**: DATE

### `lifegroup`

- **Type**: STRUCT<last_lifegroup_joined_name STRING, last_lifegroup_joined_campus STRING, last_lifegroup_joined_timestamp TIMESTAMP, last_lifegroup_joined_member_role STRING, last_lifegroup_joined_member_status STRING, first_lifegroup_joined_name STRING, first_lifegroup_joined_campus STRING, first_lifegroup_joined_timestamp TIMESTAMP, first_lifegroup_joined_member_role STRING, first_lifegroup_joined_member_status STRING, primary_lifegroup_joined_name STRING, primary_lifegroup_joined_campus STRING, primary_lifegroup_joined_timestamp TIMESTAMP, primary_lifegroup_joined_member_role STRING, primary_lifegroup_joined_member_status STRING, first_lifegroup_inquiry_timestamp TIMESTAMP, first_lifegroup_inquiry_campus STRING, last_lifegroup_inquiry_timestamp TIMESTAMP, last_lifegroup_inquiry_campus STRING>
- **Description**: STRUCT from lifegroup_membership model. Person level. Nested structure containing comprehensive LifeGroup participation history including first/last/primary group details, member roles, and inquiry information.

### `lifegroup.first_lifegroup_inquiry_campus`

- **Type**: STRING

### `lifegroup.first_lifegroup_inquiry_timestamp`

- **Type**: TIMESTAMP

### `lifegroup.first_lifegroup_joined_campus`

- **Type**: STRING

### `lifegroup.first_lifegroup_joined_member_role`

- **Type**: STRING

### `lifegroup.first_lifegroup_joined_member_status`

- **Type**: STRING

### `lifegroup.first_lifegroup_joined_name`

- **Type**: STRING

### `lifegroup.first_lifegroup_joined_timestamp`

- **Type**: TIMESTAMP

### `lifegroup.last_lifegroup_inquiry_campus`

- **Type**: STRING

### `lifegroup.last_lifegroup_inquiry_timestamp`

- **Type**: TIMESTAMP

### `lifegroup.last_lifegroup_joined_campus`

- **Type**: STRING

### `lifegroup.last_lifegroup_joined_member_role`

- **Type**: STRING

### `lifegroup.last_lifegroup_joined_member_status`

- **Type**: STRING

### `lifegroup.last_lifegroup_joined_name`

- **Type**: STRING

### `lifegroup.last_lifegroup_joined_timestamp`

- **Type**: TIMESTAMP

### `lifegroup.primary_lifegroup_joined_campus`

- **Type**: STRING

### `lifegroup.primary_lifegroup_joined_member_role`

- **Type**: STRING

### `lifegroup.primary_lifegroup_joined_member_status`

- **Type**: STRING

### `lifegroup.primary_lifegroup_joined_name`

- **Type**: STRING

### `lifegroup.primary_lifegroup_joined_timestamp`

- **Type**: TIMESTAMP

### `lifegroup_leader_campus`

- **Type**: ARRAY<STRING>
- **Description**: From Group and Campus tables. Person level. Array of three-letter campus codes where the person leads Life Groups. Can lead at multiple campuses simultaneously.

### `lifekids`

- **Type**: STRUCT<total_household_attendance_count INT64, first_household_attendance_timestamp TIMESTAMP, first_household_attendance_campus STRING, last_household_attendance_timestamp TIMESTAMP, last_household_attendance_campus STRING, weekly_household_attendance_count INT64, last_attendance_timestamp TIMESTAMP, last_attendance_campus STRING, first_attendance_timestamp TIMESTAMP, first_attendance_campus STRING, last_served_activity STRING, last_served_campus STRING, last_served_timestamp TIMESTAMP, last_volunteer_interest_timestamp TIMESTAMP, last_volunteer_interest_campus STRING, first_volunteer_interest_timestamp TIMESTAMP, first_volunteer_interest_campus STRING>
- **Description**: Comprehensive LifeKids engagement metrics combining household attendance, personal participation, and volunteer activity. This structure aggregates all children's ministry touchpoints including when children attend, when adults serve, and volunteer interest expressions. Provides a complete view of family engagement with LifeKids programming across all age-appropriate rooms.

### `lifekids.first_attendance_campus`

- **Type**: STRING
- **Description**: From attender_check_in via parent group pivot. Person level. The campus code where the person first attended any LifeKids room. Rock > Person > History.

### `lifekids.first_attendance_timestamp`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via parent group pivot. Person level. The timestamp of the person's first check-in to any LifeKids room (aggregated parent group). NULL if never attended LifeKids. Rock > Person > History.

### `lifekids.first_household_attendance_campus`

- **Type**: STRING
- **Description**: From Rock attendance tables for NextGen. Family level displayed at person level. The campus code where this person's household first attended LifeKids. NULL if no family LifeKids attendance.

### `lifekids.first_household_attendance_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock attendance tables for NextGen. Family level displayed at person level. The timestamp of the first LifeKids check-in by any member of this person's household. NULL if no family LifeKids attendance.

### `lifekids.first_volunteer_interest_campus`

- **Type**: STRING
- **Description**: From volunteer_interest_forms table. Person level. The three-letter campus code where the person first expressed interest in LifeKids volunteering.

### `lifekids.first_volunteer_interest_timestamp`

- **Type**: TIMESTAMP
- **Description**: From volunteer_interest_forms table. Person level. The timestamp when the person first submitted a volunteer interest form for LifeKids ministry. Indicates interest in children's ministry volunteering.

### `lifekids.last_attendance_campus`

- **Type**: STRING
- **Description**: From attender_check_in via parent group pivot. Person level. The campus code where the person most recently attended any LifeKids room. Rock > Person > History.

### `lifekids.last_attendance_timestamp`

- **Type**: TIMESTAMP
- **Description**: From attender_check_in via parent group pivot. Person level. The timestamp of the person's most recent check-in to any LifeKids room. NULL if never attended. Rock > Person > History.

### `lifekids.last_household_attendance_campus`

- **Type**: STRING
- **Description**: From Rock attendance tables for NextGen. Family level displayed at person level. The campus code where this person's household most recently attended LifeKids. NULL if no family LifeKids attendance.

### `lifekids.last_household_attendance_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock attendance tables for NextGen. Family level displayed at person level. The timestamp of the most recent LifeKids check-in by any member of this person's household. NULL if no family LifeKids attendance.

### `lifekids.last_served_activity`

- **Type**: STRING
- **Description**: From volunteer_check_in table. Person level. The specific LifeKids role or classroom from the person's most recent LifeKids check-in.

### `lifekids.last_served_campus`

- **Type**: STRING
- **Description**: The campus where the person last served/volunteered.

### `lifekids.last_served_timestamp`

- **Type**: TIMESTAMP
- **Description**: From volunteer_check_in table. Person level. The timestamp when the person most recently served in LifeKids ministry.

### `lifekids.last_volunteer_interest_campus`

- **Type**: STRING
- **Description**: From volunteer_interest_forms table. Person level. The three-letter campus code from the person's most recent LifeKids volunteer interest submission.

### `lifekids.last_volunteer_interest_timestamp`

- **Type**: TIMESTAMP
- **Description**: From volunteer_interest_forms table. Person level. The timestamp when the person most recently submitted a volunteer interest form for LifeKids ministry.

### `lifekids.total_household_attendance_count`

- **Type**: INT64
- **Description**: From Rock attendance tables aggregated by family. Family level displayed at person level. The total number of LifeKids check-ins for all members of this person's household. NULL if no family LifeKids attendance.

### `lifekids.weekly_household_attendance_count`

- **Type**: INT64
- **Description**: From Rock attendance tables aggregated by family and week. Family level displayed at person level. The number of distinct weeks this person's household has attended LifeKids. NULL if no family LifeKids attendance.

### `list_of_donor_events`

- **Type**: STRING
- **Description**: From Rock RMS AttributeValue and DefinedValue tables. Person level. Comma-separated list of all donor eventsthe person has participated in or been associated with. Retrieved by parsing the person's donor event attribute which stores multiple event GUIDs, then joining to DefinedValue to get human-readable event names. Each event represents a special giving campaign, capital campaign, or fundraising initiative. NULL if the person has not participated in any tracked donor events. The list is aggregated using STRING_AGG and may contain multiple events separated by commas. Rock > Person Profile > Attributes > Donor Events. Used for campaign attribution and donor segmentation analysis.

### `list_of_given_funds`

- **Type**: STRING
- **Description**: List of funds the person has given to.

### `longitude`

- **Type**: FLOAT64
- **Description**: Extracted from Rock RMS Location.GeoPoint using custom function. Entity level. The longitude coordinate of the entity location in decimal degrees. Used for mapping and distance calculations.

### `marital_status`

- **Type**: STRING
- **Description**: The marital status according to Rock RMS of the person (i.e. Single, Married, Divorced, Widowed). Defaults to 'Unknown' if null.

### `middle_name`

- **Type**: STRING
- **Description**: From Rock RMS Person table. Person-level. Middle name with empty strings converted to NULL. Rock > Person.

### `next_form_submission_email_subscription_timestamp_lco_service_reminder`

- **Type**: TIMESTAMP
- **Description**: Calculated from LCO service reminder form submissions. Person level. The UTC timestamp for when the person's next service reminder email should be sent, calculated by extracting their preferred service day and time from their form submission (assumes submission occurred 30 minutes before preferred service), finding the next occurrence of that day/time, and rounding to 15-minute intervals for batch processing efficiency. Returns NULL if they haven't submitted a service reminder preference form.

### `nickname`

- **Type**: STRING
- **Description**: From Rock RMS Person table. Person-level. Preferred name or nickname with empty strings converted to NULL. Rock > Person.

### `percent_scheduled`

- **Type**: STRING
- **Description**: The percent of all the gifts a person has given that have been scheduled, versus one-time.

### `person_created_by_rms_person_alias_id`

- **Type**: INT64
- **Description**: From Rock RMS Person.CreatedByPersonAliasId. Person-level. Alias ID of person/system who created this record. Rock > Person > History.

### `phone_number`

- **Type**: STRING
- **Description**: The main contact phone number for the individual. Returns NULL if phone number is empty string.

### `postal_code`

- **Type**: STRING
- **Description**: From Rock RMS Location.postalcode. Person level. The ZIP code of the person's home address. Used for geographic analysis and drive time calculations.

### `predicted_segment_trait_likely_next_step_score_attend`

- **Type**: STRING
- **Description**: From Segment. Person level. A prediction made by Segment, based on the person's data and digital behavior. Is true if Segment has predicted the person is likely (0.5 or greater) to start attending. Segment > Unify > Traits > Computed Traits.

### `predicted_segment_trait_likely_next_step_score_give`

- **Type**: STRING
- **Description**: From Segment. Person level. A prediction made by Segment, based on the person's data and digital behavior. Is true if Segment has predicted the person is likely (0.5 or greater) to start giving. Segment > Unify > Traits > Computed Traits.

### `predicted_segment_trait_likely_next_step_score_serve`

- **Type**: STRING
- **Description**: From Segment. Person level. A prediction made by Segment, based on the person's data and digital behavior. Is true if Segment has predicted the person is likely (0.5 or greater) to start serving. Segment > Unify > Traits > Computed Traits.

### `predicted_segment_trait_likely_next_step_score_stop_attending`

- **Type**: STRING
- **Description**: From Segment. Person level. A prediction made by Segment, based on the person's data and digital behavior. Is true if Segment has predicted the person is likely (0.5 or greater) to stop attending. Segment > Unify > Traits > Computed Traits.

### `predicted_segment_trait_likely_next_step_score_stop_serving`

- **Type**: STRING
- **Description**: From Segment. Person level. A prediction made by Segment, based on the person's data and digital behavior. Is true if Segment has predicted the person is likely (0.5 or greater) to stop serving. Segment > Unify > Traits > Computed Traits.

### `preferred_campus`

- **Type**: STRING
- **Description**: The preferred campus as decided by the user's engagement with Life.Church.

### `preferred_currency`

- **Type**: STRING
- **Description**: The preferred money currency the person likes to give to Life.Church.

### `preferred_source`

- **Type**: STRING
- **Description**: The preferred way the person likes to give to Life.Church (e.g. card, check, ACH, etc.).

### `prefix`

- **Type**: STRING
- **Description**: From Rock RMS DefinedValue via Person.TitleValueId. Person-level. Name prefix/title with empty strings converted to NULL. Rock > Person Profile > Title. (e.g., 'Mr', 'Dr').

### `previous_attendance_flow_classification`

- **Type**: STRING
- **Description**: From attendance_flow model calculations. Person level (inherited from family level). The attendance stage that the person's family transitioned from to reach their current classification. Indicates the flow pattern (e.g., New to Retained, Retained to Absent). Used to understand attendance transitions and calculate flow metrics. NULL for families in their first classification (New). Example values: 'New', 'Retained', 'Re-engaged', 'Absent', 'Inactive', NULL.

### `primary_giving_subtype`

- **Type**: STRING
- **Description**: The specific payment method subtype (e.g., 'Visa', 'Mastercard') used in the person's most recent contribution. Person level. From the latest transaction's transaction_subtype, excluding 'unknown' values. Rock > Profile > Transactions.

### `primary_giving_type`

- **Type**: STRING
- **Description**: The transaction type (e.g., 'Cash', 'Check', 'ACH', 'Credit Card') used in the person's most recent contribution. Person level. From the latest transaction's transaction_type. Rock > Profile > Transactions.

### `primary_person_alias`

- **Type**: INT64
- **Description**: From Rock RMS Person.PrimaryAliasId. Person-level. The current primary alias ID for the person, which may change due to merges. Rock > Person > Extendes Attributes.

### `product_sales`

- **Type**: STRUCT<shopify_customer_id INT64, shopify_total_orders INT64, first_order_timestamp TIMESTAMP, last_order_timestamp TIMESTAMP, most_frequent_bought_product_type STRING, last_frequent_bought_product_type_order_timestamp TIMESTAMP, last_abandoned_checkout_timestamp TIMESTAMP, abandoned_checkout_url STRING>
- **Description**: A STRUCT containing all Shopify-related purchase and customer data for the person.

### `product_sales.abandoned_checkout_url`

- **Type**: STRING
- **Description**: From Data Warehouse, using Shopify data. Person Level. The recovery URL is only available if the checkout remains abandoned and no later orders were completed by this customer. Shopify > Orders > Abandoned Checkout.

### `product_sales.first_order_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Shopify order tables. Person level. The timestamp of the person's earliest order across both Shopify stores, converted from Central Time to UTC. Represents when they became a Shopify customer. Shopify > Customers > Customer > Orders.

### `product_sales.last_abandoned_checkout_timestamp`

- **Type**: TIMESTAMP
- **Description**: From shopify_hubspot_properties table. Person level. The timestamp of the person's most recent abandoned checkout event. Used to trigger recovery campaigns and analyze checkout friction. Shopify > Orders > Abandoned Checkout

### `product_sales.last_frequent_bought_product_type_order_timestamp`

- **Type**: TIMESTAMP
- **Description**: From shopify_hubspot_properties table. Person level. The timestamp when the person last purchased their most frequently bought product type. Used to track product preference recency. Shopify > Customers > Customer > Orders.

### `product_sales.last_order_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Shopify order tables. Person level. The timestamp of the person's most recent order across both Shopify stores, converted from Central Time to UTC. Used to determine customer recency and abandoned cart eligibility. Shopify > Customers > Customer > Orders.

### `product_sales.most_frequent_bought_product_type`

- **Type**: STRING
- **Description**: From Data Warehouse, using Shopify data. Person Level. It is calculated when the same product type is bought at least twice. Shopify > Customer > Timeline.

### `product_sales.shopify_customer_id`

- **Type**: INT64
- **Description**: From Shopify customer tables (both main store and Life Store). Person level. The Shopify-assigned customer ID that corresponds to this Rock RMS person, matched by email address. Takes the minimum ID when multiple matches exist. Shopify > Customers. Example: 7516112191660.

### `product_sales.shopify_total_orders`

- **Type**: INT64
- **Description**: From Shopify order tables. Person level. The total count of all orders placed by this person across both Shopify stores (main store and Life Store). Calculated by counting all orders associated with the person's email address. Shopify Admin > Customers Example: 2.

### `rms_family_id`

- **Type**: INT64
- **Description**: The primary unique identifier for a family or household in Rock RMS.

### `rms_person_created_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS Person.CreatedDateTime. Person-level. Timestamp when person record was created in Rock. Rock > Person > History.

### `rms_person_id`

- **Type**: INT64
- **Description**: The unique Rock RMS identifier for the individual. Person-level. Links to Person.Id in Rock RMS. Used to join all person-related data across the system. Rock > Person Profile.

### `rms_person_inactive_reason`

- **Type**: STRING
- **Description**: From Rock RMS DefinedValue via Person.RecordStatusReasonValueId. Person-level. Reason for inactive status. NULL if active. Rock > Person Profile > Inactivate Reason.

### `rms_person_inactive_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS Person._fivetran_synced. Person-level. Timestamp when marked inactive. NULL if active.

### `rms_person_type`

- **Type**: STRING
- **Description**: From Rock RMS DefinedValue via Person.ConnectionStatusValueId. Person-level. Connection status (e.g., 'Visitor', 'Attendee', 'Member'). Rock > Person.

### `scheduled_transaction_count`

- **Type**: INT64
- **Description**: The number of gifts the person has given using a recurring schedule.

### `school_grade`

- **Type**: STRING
- **Description**: From Rock RMS DefinedValue lookup based on graduation year. Person level. The current school grade descriptor (e.g., 'Kindergarten', '1st Grade'). Calculated from graduation year and current date.

### `segment_canonical_id`

- **Type**: ARRAY<STRING>
- **Description**: From external_id_mapping table. Person level. Array of all canonical Segment user IDs associated with this Rock RMS person. Used for identity resolution and cross-device tracking.

### `staff_end_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS AttributeValue. Person-level. Date person stopped being staff. NULL if still active or future date. Rock > Person Profile > Extended Attributes

### `staff_start_timestamp`

- **Type**: TIMESTAMP
- **Description**: From Rock RMS AttributeValue. Person-level. Date person became staff member. NULL for future dates. Rock > Person > Extended Attributes

### `state_province`

- **Type**: STRING
- **Description**: From person_location table. Family-level. Full state/province name. Rock > Person > Address.

### `state_province_code`

- **Type**: STRING
- **Description**: From Rock RMS Location.state. Person level. Two-character state/province code of the person's home address (e.g., 'OK', 'TX'). Used for geographic analysis.

### `statement_suppressed_timestamp`

- **Type**: TIMESTAMP
- **Description**: The timestamp when the person opted out of printed contribution statements. Person level. CreatedDateTime of the statement suppression attribute. Rock > Profile > Attributes > Suppress Sending Contribution Statements > Created Date.

### `streaks`

- **Type**: ARRAY<STRUCT<streak_enrolled_timestamp TIMESTAMP, streak_enrolled_type STRING>>
- **Description**: From Rock streak tables. Person level. An array of the person's engagement streaks showing when they enrolled in various streak types. Each streak contains enrollment timestamp and type (Serving, Attendance, Digital Invites, Serving Daily, Weekly Attendance). Ordered by enrollment date. Rock > Person Profile > Streaks.

### `streaks.streak_enrolled_timestamp`

- **Type**: TIMESTAMP

### `streaks.streak_enrolled_type`

- **Type**: STRING

### `suffix`

- **Type**: STRING
- **Description**: From Rock RMS DefinedValue via Person.SuffixValueId. Person-level. Name suffix with empty strings converted to NULL. Rock > Person Profile > Suffix. (e.g., 'Jr', 'III').

### `three_month_campus`

- **Type**: STRING
- **Description**: The campus short code where the person committed to the three-month tithe challenge. Person level. From the campus attribute in the Three Month Tithe Challenge matrix. Rock > Profile > Attributes > Three Month Tithe Challenge.

### `three_month_timestamp`

- **Type**: TIMESTAMP
- **Description**: The start date when the person began their three-month tithe challenge commitment. Person level. Retrieved from Rock attribute matrix for Three Month Tithe Challenge. Format: YYYY-MM-DD HH:MM:SS. Rock > Profile > Person > Attributes > Three Month Tithe Challenge.

### `total_attendance_app_count`

- **Type**: INT64
- **Description**: From attendance_combined filtered for app check-ins. Person level. The total number of check-ins made via the Life.Church mobile app. Always <= total_attendance_combined_count.

### `total_attendance_combined_count`

- **Type**: INT64
- **Description**: From attendance_combined count aggregation. Person level. The total number of all check-ins (attendance + volunteer) for this person across all campuses and time. Always >= 0. Rock > Person > History.

### `total_attendance_lco_count`

- **Type**: INT64
- **Description**: From attendance_combined filtered for Church Online Platform. Person level. The total number of check-ins for Life.Church Online experiences. Always <= total_attendance_combined_count.

### `total_digital_invite`

- **Type**: INT64
- **Description**: Count from Interaction table. Person level. The total number of digital invites this person has sent.

### `total_financial_transaction_count`

- **Type**: INT64
- **Description**: The total number of successful financial transactions the person has made. Person level. Count of distinct financial_transaction_id from fact_giving where amount >= 0 and is_successful = TRUE. Rock > Profile > Transactions.

### `total_household_attendance_switch_count`

- **Type**: INT64
- **Description**: From Rock attendance tables aggregated by family. Family level displayed at person level. The total number of Switch check-ins for all members of this person's household. NULL if no family Switch attendance.

### `total_household_switch_aged_students`

- **Type**: INT64
- **Description**: From Person table based on graduation year. Family level displayed at person level only calculated for Adults. The count of Switch-aged students (grades 6-12) currently in this person's household. NULL if no Switch-aged students.

### `total_scheduled_giving_count`

- **Type**: INT64
- **Description**: The total number of scheduled giving transactions for the person.

### `total_serving_check_ins`

- **Type**: INT64
- **Description**: The total number of serving check-ins for the person. Null if 0.

### `typical_frequency`

- **Type**: FLOAT64
- **Description**: The average frequency the person gives to Life.Church.

### `user_id`

- **Type**: INT64
- **Description**: The current unique identifier for an individual person or business in Rock RMS, despite merges. Cast as STRING for external system compatibility.

### `weekly_household_attendance_switch_count`

- **Type**: INT64
- **Description**: From Rock attendance tables aggregated by family and week. Family level displayed at person level. The number of distinct weeks this person's household has attended Switch. NULL if no family Switch attendance.

### `weeks_in_current_attendance_flow_classification`

- **Type**: INT64
- **Description**: From row_number calculation over classification changes. Person level (inherited from family level). The number of consecutive weeks the person's family has been in their current attendance classification. Calculated by detecting when the classification changes and counting weeks since the most recent change. Resets to 1 whenever the family transitions to a new classification. Always >= 1 for families with a classification.

