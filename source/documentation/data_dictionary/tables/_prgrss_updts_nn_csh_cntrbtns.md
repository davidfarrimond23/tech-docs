## prgrss_updts_nn_csh_cntrbtns

Contains infomation relating to additional grant condition data.

A single progress_update can have *many* prgrss_updts_nn_csh_cntrbtns.

A prgrss_updts_nn_csh_cntrbtns can **only** be linked to one progress_update


```
  id: UUID **PK**
  progress_update_id: UUID **FK**
  description: String
  value: Integer
  created_at: Timestamp
  updated_at: Timestamp
```