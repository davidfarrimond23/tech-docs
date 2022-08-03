## funding_applications

Table that contains details specific to a funding application.  The current application table may contain additional fields as originally declaration data was kept on this table.

Funding applications now has a `status` enumerator stored, which is checked by the context to ensure that only application with a status of `payment_can_start` can enter a payment route. This status is set by the `task_controller` when a funding application has completed all legal agreement journeys. 

 An `award_type` enumerator is also present that is set through the `FundingApplicationContext` and `LegalAgreementsContext` when a valid application is found, or, at the start of all application legal agreement journeys - ensuring all application types are set and locked in, regardless of app type specific flows. 

This status and award type lock fix the application into the specific journey flow intended for the application type. This safeguards applications against changing journey flows if there is a grant amount increase/decrease during sensitive legal agreement and payment journeys. 

```
id: UUID <<PK>>                         
project_reference_number: String            Salesforce project reference number
salesforce_case_id: String                  Case ID in Salesforce
salesforce_case_number: String              Case Number in Salesforce
organisation: UUID <<FK>>                   Link to organisation table
submitted_on: Timestamp                     DateTime that the application was submitted
agreement_submitted_on: Timestamp           DateTime that an applicant concludes an agreement journey by clicking submit.
award_type: Enum            Enumerated type used to lock in award_type for future reference. 
status: Enum            Enumerated type used to reflect project status.  At the time of writing, only includes at status of 1 indicating payment can start.
created_at: Timestamp
updated_at: Timestamp
```
