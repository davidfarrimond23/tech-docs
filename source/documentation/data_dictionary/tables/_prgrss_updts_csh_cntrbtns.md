## prgrss_updts_csh_cntrbtns

Description 

```
  id: UUID **PK**
  progress_update_id: UUID **FK**
  salesforce_project_income_id: String
  display_text: String
  amount_expected: Integer
  amount_received_so_far: Integer
  received_amount_expected: Boolean
  will_receive_total_amount: Boolean
  received_amount_expected: Boolean
  reason_amount_expected_not_received: String
  created_at: Timestamp
  updated_at: Timestamp
```