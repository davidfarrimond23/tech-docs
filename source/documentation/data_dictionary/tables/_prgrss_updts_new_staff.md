## prgrss_updts_new_staff

Contains information relating to additional grant condition data.

A single progress_update can have *many* prgrss_updts_new_staff.

A prgrss_updts_new_staff can **only** be linked to one progress_update

```
  id: UUID **PK**
  progress_update_id: UUID **FK**
  name: String
  description: String
  date: DateTime
  amount: Integer
  lowest_tender: Boolean
  supplier_justification: String
  created_at: Timestamp
  updated_at: Timestamp
```