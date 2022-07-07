## completed_arrears_journeys

Used by medium arrears journey and created when a user completes the payment in arrears journey. This is used to store to store and linke completed data object related to a users previouse arrears journies - relating the completed progress_update and/or payment_request entities to the funding_application. 

*Many* completed_arrears_journeys can exist agast one funding_application. 

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