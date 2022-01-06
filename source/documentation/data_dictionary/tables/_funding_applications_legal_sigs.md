## funding_applications_legal_sigs

Join table to legal_signatories from funding_applications. 

```
id: UUID <<PK>>
funding_application_id: UUID <<FK>>
legal_signatory_id: UUID <<FK>>
created_at: Timestamp
updated_at: Timestamp
```
