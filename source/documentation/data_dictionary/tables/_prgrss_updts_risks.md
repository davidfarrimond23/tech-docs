## prgrss_updts_risks

Description 

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