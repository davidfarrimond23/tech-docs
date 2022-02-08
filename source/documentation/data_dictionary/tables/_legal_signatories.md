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
  organisation_id: UUID <<FK>>              FK to the organisation table
  role: String                              The role of the signatory in the organisation
  salesforce_legal_signatory_id: String     The ID of the corresponding legal signatory record in Salesforce
  created_at: Timestamp
  updated_at: Timestamp
```
