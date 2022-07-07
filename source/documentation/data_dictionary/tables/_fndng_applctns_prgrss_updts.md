## fndng_applctns_prgrss_updts

Captures the link between funding applications andprogress_updates.

A single funding application can have *many* progress_updates.

A payment request can **only** be linked to one funding application.

```
  id: UUID <<PK>>
  funding_application_id: UUID <<FK>>
  progress_update_id: UUID <<FK>>
  created_at: Timestamp
  updated_at: Timestamp
```