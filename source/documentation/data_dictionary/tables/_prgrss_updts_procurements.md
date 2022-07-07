## prgrss_updts_events

Description

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