## high_spend

High spend descition

```
    id: UUID <<PK>>
    payment_request_id: UUID <<FK>>
    cost_heading: Sting
    description: String
    vat_amount: Integer
    amount: Integer
    date_of_spend: Timestamp
    spend_threshold: Integer
    created_at: Timestamp
    updated_at: Timestamp
```
