# Executive And Source Authority Guide

Goal: establish what is actually running, what data matters, and what modernization must not break.

## Questions

1. Which Fleetwood executable/version is used in production today?
2. Which source tree corresponds to production: `Fleetwood4`, `Fleetwood5`, standalone `../Fleetwood5`, or another tree?
3. Are the standalone `Fleetwood.Web` and `FleetLive` repos production systems, or are the nested copies under `../Fleetwood` authoritative?
4. What SQL Server instances and databases are active?
5. Which company databases are live, historical, test, or archived?
6. Is there one operational company or multiple companies/regions?
7. Who are the primary user groups: dispatch, order entry, billing, management, sales, customer service, drivers/vendors, customers?
8. What daily work cannot stop during migration?
9. What month-end or billing-cycle work cannot be disrupted?
10. What legal, tax, customer, vendor, or insurance obligations are tied to Fleetwood records?
11. Which integrations are business-critical today?
12. Is FleetLive still used?
13. Is the customer web portal still used?
14. Are checked-in credentials still valid and requiring rotation?
15. What would make the modernization fail from the customer perspective?

## Decisions Needed

| Decision | Options | Notes |
| --- | --- | --- |
| Authoritative source tree | `Fleetwood4`, `Fleetwood5`, standalone repos, running system only, unknown | Required before detailed source tracing. |
| Active data source | Production SQL backup, live read-only DB, exported schema, source-only | Needed for schema and report validation. |
| First modernization scope | Dispatch, order entry, billing, mobile, reports, customer portal | Should be based on risk and value. |
| Migration style | Side-by-side, module replacement, full rewrite after spec, data-first platform | Avoid deciding before critical workflows are known. |

## Source Context

- Main VB6 application project files: `../Fleetwood/Fleetwood4/Fleetwood.vbp`, `../Fleetwood/Fleetwood5/Fleetwood.vbp`, `../Fleetwood5/Fleetwood.vbp`
- Existing customer web portal: `../Fleetwood.Web/Fleetwood.Web.sln`
- Existing mobile stack: `../FleetLive/FleetLive.sln`
- Cloud migration notes: `../FleetwoodTasks/CloudMigration.md`
