## legal_signatories

Contains legal signatory information for the up to 
two legal signatories that are assigned to an 
organisation.

Currently used in the small and medium legal
agreements process.

```
  id: UUID <<PK>>
  name: String - name of signatory
  email_address: String
  phone_number: String
  organisation_id: UUID <<FK>> - FK to the organisation table
  created_at: Timestamp
  updated_at: Timestamp
```
