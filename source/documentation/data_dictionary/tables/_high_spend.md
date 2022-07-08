## high_spend

Contains information relating to high spend data.

A single payment request can have *many* high_spends.

A high_spend can **only** be linked to one payment_request

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
