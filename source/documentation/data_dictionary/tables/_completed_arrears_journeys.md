## completed_arrears_journeys

Completed arrears journey descriptions

```
  id: UUID <<PK>>
  funding_application_id: UUID <<FK>>
  payment_request_id: UUID <<FK>>
  progress_update_id: UUID <<FK>>
  submitted_on: Timestamp
  created_at: Timestamp
  updated_at: Tmestamp
  salesforce_form_id: String
```