## funding_applications_eos

Join table to evidence_of_support from funding_applications. 

```
id: UUID <<PK>>
funding_application_id: UUID <<FK>>
evidence_of_support_id: UUID <<FK>>
created_at: Timestamp
updated_at: Timestamp
```
