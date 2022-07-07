## prgrss_updts_apprvd_prpss

Contains infomation relating to additional grant condition data.

A single progress_update can have *many* prgrss_updts_apprvd_prpss.

A prgrss_updts_apprvd_prps can **only** be linked to one progress_update

```
  id: UUID **PK**
  progress_update_id: UUID **FK**
  progress: String
  description: String
  salesforce_approved_purpose_id: String
  created_at: Timestamp
  updated_at: Timestamp
```