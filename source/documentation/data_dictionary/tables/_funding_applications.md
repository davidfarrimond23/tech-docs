## funding_applications

Table that contains details specific to a funding application.  The current application table may contain additional fields as originally declaration data was kept on this table.

```
id: UUID <<PK>>                         
project_reference_number: String            Salesforce project reference number
salesforce_case_id: String                  Case ID in Salesforce
salesforce_case_number: String              Case Number in Salesforce
organisation: UUID <<FK>>                   Link to organisation table
submitted_on: Timestamp                     DateTime that the application was submitted
agreement_submitted_on: Timestamp           DateTime that an applicant concludes an agreement journey by clicking submit.
created_at: Timestamp
updated_at: Timestamp
```
