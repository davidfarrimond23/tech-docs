## prgrss_updts_demographics

Contains information relating to additional grant condition data.

A single progress_update can have *many* prgrss_updts_demographics.

A prgrss_updts_demographics can **only** be linked to one progress_update

```
  id: UUID **PK**
  progress_update_id: UUID **FK**
  explanation: String
  created_at: Timestamp
  updated_at: Timestamp
```