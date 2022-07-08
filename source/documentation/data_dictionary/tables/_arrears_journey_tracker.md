## arrears_journey_tracker

Used by medium arrears journey and created when a user embarks on the payment in arrears journey. This is used to track the progress of the users through the arrears journey and relates the progress_update and/or payment_request entities to the funding_application being worked on. 

**Only** one arrears_journey_tracker can exist at a given time and is deleted upon completion of the arrears journey. The funding application is then associated with the funding_application through a completed_arrears_journeys entity.  

```
  id: UUID <<PK>>
  funding_application_id: UUID <<FK>>
  payment_request_id: UUID <<FK>>
  progress_update_id: UUID <<FK>>
  created_at: Timestamp
  updated_at: Timestamp
```