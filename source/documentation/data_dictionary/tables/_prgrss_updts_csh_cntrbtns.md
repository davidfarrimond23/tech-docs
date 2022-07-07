## prgrss_updts_csh_cntrbtns

Contains infomation relating to additional grant condition data.

A single progress_update can have *many* prgrss_updts_csh_cntrbtns.

A prgrss_updts_csh_cntrbtns can **only** be linked to one progress_update

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