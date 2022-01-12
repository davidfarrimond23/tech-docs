## sfx_pts_payments

The permission to start (PTS) journey in Funding Frontend (FFE) requires the applicant to
answer questions.  This table stores those answers as JSON until they are rendered 
to a PDF at the end of the journey and submitted to Salesforce. 

```
  id: UUID <<PK>>
  salesforce_case_id: text                            The case id for the application assigned tp and referred to by Salesforce
  email_address: character varying                    Email address of the user/contact in Salesforce.  Must match FFE account
  pts_answers_json: jsonb                             A collection of PTS informatoion provided by the applicant, stored as JSON
  application_type: integer                           0 = large_delivery, 1 = large_development, 2 = unknown
  salesforce_pts_form_record_id: character varying    when the PTS answers are submitted, this is the form id returned from SF
  submitted_on: Timestamp                             Timestamp of when the PTS answers were submitted
  created_at: Timestamp
  updated_at: Timestamp
```
