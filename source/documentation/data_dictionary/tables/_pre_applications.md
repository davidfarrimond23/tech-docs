## pre_applications

Contains metadata data about pre_applications - which are:

- Project enquiry forms (PEF)
- Expressions of interest (EOI)

```
  id: UUID **PK**
  user_id: integer **FK** 
  organisation_id: UUID **FK**
  project_reference_number: text
  salesforce_case_id: text
  salesforce_case_number: text
  submitted_on: text
  submitted_payload
  created_at: Timestamp
  updated_at: Timestamp
```