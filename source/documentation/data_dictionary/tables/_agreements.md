##agreements

Used by small and medium legal agreements.  Stores when the
grant and the terms were agreed.  Also stores what the applicant 
was shown when they agreed to the terms and grant - and they
are able to view this afterwards.

```
  id: UUID <<PK>>
  funding_application_id: UUID <<FK>>
  grant_agreed_at: Timestamp
  terms_agreed_at: Timestamp
  project_details_html: text          Stores the details of the project, as html, at the point that the applicant agreed to them
  terms_html: text                    Stores the terms of the project, as html, at the point that the applicant agreed to them
  created_at: Timestamp
  updated_at: Timestamp
```