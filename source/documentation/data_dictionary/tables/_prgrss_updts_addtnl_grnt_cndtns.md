## prgrss_updts_addtnl_grnt_cndtns

Contains infomation relating to additional grant condition data.

A single progress_update can have *many* prgrss_updts_addtnl_grnt_cndtns.

A prgrss_updts_addtnl_grnt_cndtn can **only** be linked to one progress_update


```
  id: UUID **PK**
  progress_update_id: UUID **FK**
  full_date: DateTime
  description: String
  salesforce_additional_grant_condition_id: String
  created_at: Timestamp
  updated_at: Timestamp
```