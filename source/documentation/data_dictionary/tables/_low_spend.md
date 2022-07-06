## low_spend

Low spend descition

```
  id: UUID <<PK>>
  payment_request_id: UUID <<FK>>
  cost_heading: Sting
  vat_amount: Integer
  total_amount: Integer
  spend_threshold: Integer
  created_at: Timestamp
  updated_at: Timestamp
```
