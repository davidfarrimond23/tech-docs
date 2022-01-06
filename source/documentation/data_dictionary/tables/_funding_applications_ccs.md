## funding_applications_ccs

Join table to cash contributions from funding_applications. 

```
id: UUID <<PK>>
funding_application_id: UUID <<FK>>
cash_contribution_id: UUID <<FK>>
created_at: Timestamp
updated_at: Timestamp
```
