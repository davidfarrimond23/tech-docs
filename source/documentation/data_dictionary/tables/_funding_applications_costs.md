## funding_applications_costs

Join table to project_costs from funding_applications. 

```
id: UUID <<PK>>
funding_application_id: UUID <<FK>>
project_cost_id: UUID <<FK>>
created_at: Timestamp
updated_at: Timestamp
```
