## pa_project_enquiries

Table that stores the answers that an applicant gives for a project enquiry form (PEF).

```
  id: UUID **PK**
  pre_application_id: UUID **FK**
  previous_contact_name: text
  heritage_focus: text
  what_project_does: text
  programme_outcomes: text
  project_reasons: text
  project_participants: text
  project_timescales: text
  project_likely_cost: text
  working_title: text
  potential_funding_amount: Integer
  salesforce_project_enquiry_id: character varying    The Salesforce record id for the PEF
  salesforce_pef_reference                            The reference for the PEF in Salesforce
  created_at: Timestamp
  updated_at: Timestamp
```