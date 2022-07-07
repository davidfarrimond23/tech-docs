## low_spend

Contains infomation relating to low spend data.

A single payment request can have *many* low_spends.

A low_spend can **only** be linked to one payment_request

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
