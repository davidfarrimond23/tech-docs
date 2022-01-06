## funding_applications_nccs

Join table to non-cash contributions from funding_applications. 

```
id: UUID <<PK>>
funding_application_id: UUID <<FK>>
non_cash_contribution_id: UUID <<FK>>
created_at: Timestamp
updated_at: Timestamp
```
