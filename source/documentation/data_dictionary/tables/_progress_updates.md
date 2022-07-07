## progress_updates

Contains information relating to a progress updates journey, storing selected asnswers as JSON Key/Values.

This entitiy relates all the answers objects to the current arrears_journey_tracker or (upon completion) the completed_arrears_journey.

```
  id: UUID <<PK>>
  submitted_on: Timestamp
  answers_json: JSONB 
  created_at: Timestamp
  updated_at: Timestamp
```