## fndng_applctns_prgrss_updts

Contains information relating to a fndng_applctns_prgrss_updts.

```
  id: UUID <<PK>>
  funding_application_id: UUID <<FK>>
  progress_update_id: UUID <<FK>>
  created_at: Timestamp
  updated_at: Timestamp
```