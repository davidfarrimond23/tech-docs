## prgrss_updts_procurements

Contains infomation relating to procurement data.

A single progress_update can have *many* prgrss_updts_procurements.

A prgrss_updts_procurements can **only** be linked to one progress_update

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