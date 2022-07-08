## payment_requests

Contains information relating to a payment request,
storing selected answers and journey statuses as JSON Key/Values.

```
  id: UUID <<PK>>
  amount_requested: Integer
  answers_json: JSONB
  created_at: Timestamp
  updated_at: Timestamp
  submitted_on: Timestamp
```
