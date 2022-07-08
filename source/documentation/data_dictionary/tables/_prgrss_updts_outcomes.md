## prgrss_updts_outcomes

Contains information relating to additional grant condition data.

Outcomes are stored as JSON, as each outcome is pulled dynamically from Salesforce as a key, with the user's answers stored as the value. 

A single progress_update can have *many* prgrss_updts_outcomes.

A prgrss_updts_outcomes can **only** be linked to one progress_update

```
  id: UUID **PK**
  progress_update_id: UUID **FK**
  progress_updates: JSONB
  created_at: Timestamp
  updated_at: Timestamp
```