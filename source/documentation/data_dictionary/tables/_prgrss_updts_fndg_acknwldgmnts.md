## prgrss_updts_fndg_acknwldgmnts

Contains infomation relating to additional grant condition data.

Funding Acknowledgments are stored as JSON, as each achnowledgment is pulled dynamically from Salesforce as a key, with the users answers stored as the value. 

A single progress_update can have *many* prgrss_updts_fndg_acknwldgmnts.

A prgrss_updts_fndg_acknwldgmnts can **only** be linked to one progress_update

```
  id: UUID **PK**
  progress_update_id: UUID **FK**
  acknowledgements: JSONB
  created_at: Timestamp
  updated_at: Timestamp
```