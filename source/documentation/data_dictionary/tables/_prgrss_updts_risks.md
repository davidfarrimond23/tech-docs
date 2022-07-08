## prgrss_updts_risks

Contains information relating to additional grant condition data.

A single progress_update can have *many* prgrss_updts_risks.

A prgrss_updts_risks can **only** be linked to one progress_update

```
  id: UUID **PK**
  progress_update_id: UUID **FK**
  description: String
  likelihood: Integer
  Impact: Integer
  is_risk: Boolean
  is_still_risk_description: String
  created_at: Timestamp
  updated_at: Timestamp
```