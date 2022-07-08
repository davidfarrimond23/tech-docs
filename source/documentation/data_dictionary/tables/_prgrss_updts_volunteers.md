## prgrss_updts_volunteers

Contains infomation relating to volunteer data.

A single progress_update can have *many* prgrss_updts_volunteers.

A prgrss_updts_volunteers can **only** be linked to one progress_update

```
  id: UUID **PK**
  progress_update_id: UUID **FK**
  description: String
  hours: Integer
  created_at: Timestamp
  updated_at: Timestamp
```