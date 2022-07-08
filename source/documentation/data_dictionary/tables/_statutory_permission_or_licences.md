## statutory_permission_or_licences

Contains information about a statutory permission or licence captured within
the permission to start process.

Has a FK, and therefore dependency on, sfx_pts_payments.


```
  id: UUID <<PK>>
  details_json: jsonb               Stores detail as JSON.
  sfx_pts_payment_id: UUID <<FK>>
  created_at: Timestamp
  updated_at: Timestamp
```
