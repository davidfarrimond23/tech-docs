## funding_applications_legal_sigs

Join table to legal_signatories from funding_applications.
Also stores when the signed terms were uploaded back to the service.

```
  id: UUID **PK**
  funding_application_id: UUID **FK**
  legal_signatory_id: UUID **FK**
  signed_terms_submitted_on: Timestamp
  created_at: Timestamp
  updated_at: Timestamp
```
