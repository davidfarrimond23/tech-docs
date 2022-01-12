## pa_expressions_of_interest

Table that stores the answers that an applicant gives for an expression of interest (EOI).

```
  id: UUID **PK**
  pre_application_id: UUID **FK**
  heritage_focus: text
  what_project_does: text
  project_outcomes: text
  project_reasons: text
  project_timescales: text
  overall_cost: text
  working_title: text
  potential_funding_amount: Integer
  likely_submission_description: text
  previous_contact_name: text
  salesforce_expression_of_interest_id: character varying     The Salesforce record id for the EOI
  salesforce_eoi_reference: character varying                 The reference for the EOI in Salesforce
  created_at: Timestamp
  updated_at: Timestamp
```