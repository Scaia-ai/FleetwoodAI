# Open Questions Register

This register tracks business facts that source code cannot establish with enough confidence. Status values: `open`, `answered`, `validated`, `deferred`.

| ID | Area | Question | Why It Matters | Source Context | Status | Answer |
| --- | --- | --- | --- | --- | --- | --- |
| OQ-001 | Source authority | Which Fleetwood executable/source tree is production today? | Requirements tracing depends on the authoritative version. | `../Fleetwood/Fleetwood4`, `../Fleetwood/Fleetwood5`, `../Fleetwood5` | open | |
| OQ-002 | Source authority | Are standalone repos or nested copies under `../Fleetwood` authoritative? | Prevents documenting stale duplicate code. | `../Fleetwood`, `../Fleetwood.Web`, `../FleetLive`, `../Fleetwood5` | open | |
| OQ-003 | Database | What SQL Server instances and databases are active? | Needed for schema extraction and migration planning. | `../Fleetwood/Fleetwood4/Modules/Main.bas`, web/mobile configs | open | |
| OQ-004 | Database | Which company databases are live, historical, test, or archived? | Determines multi-company requirements and data migration scope. | `DATMST` usage in `Main.bas`; example `StarAustin` configs | open | |
| OQ-005 | Operations | What workflow cannot be interrupted during migration? | Defines MVP and rollout risk. | Menus show orders, dispatch, billing, settlement. | open | |
| OQ-006 | Dispatch | What are the real-world meanings of `HLD`, `RDY`, `NTF`, `UP`, `DWN`, and `CNL`? | Status semantics drive workflow design. | `../Fleetwood/Fleetwood4/Modules/Main.bas` | open | |
| OQ-007 | Dispatch | How are vendors selected and assigned to pickup/delivery? | Dispatch assistant and workflow requirements depend on this. | `frmDispatch.frm`, `frmDispatchNew.frm`, FleetLive controllers | open | |
| OQ-008 | Orders | How are after-hours, weekend, prescheduled, return, and contract orders used today? | These may be high-risk edge workflows. | `Main.frm`, `OrdersRepository.cs` | open | |
| OQ-009 | Pricing | Which rate sheet types are actively used? | Rating model scope and migration tests depend on usage. | `SMRSheets`, `SARSheets`, `SPMRSheets`, bobtail variants | open | |
| OQ-010 | Billing | What makes an order billable or not billable? | Core revenue workflow. | invoice forms/modules and no-charge codes | open | |
| OQ-011 | Billing | Which financial values can be manually overridden, and who approves them? | Audit and permissions requirements. | charge, invoice, payment, settlement forms | open | |
| OQ-012 | Settlement | How are vendor and employee settlements calculated? | Critical AP/pay workflow. | `modPayroll.bas`, settlement forms/reports | open | |
| OQ-013 | Reports | Which reports must be preserved exactly? | Determines reporting rebuild scope. | Crystal reports under `Templates` | open | |
| OQ-014 | Customer portal | Is the existing customer web portal still in production use? | Determines replacement priority and customer-facing migration. | `../Fleetwood.Web` | open | |
| OQ-015 | Mobile | Is FleetLive still in production use? | Determines mobile replacement priority. | `../FleetLive` and FleetLive admin forms | open | |
| OQ-016 | Integrations | Which integrations are live today? | Needed for architecture and rollout. | SMTP, MapPoint, Office, GCM, exports, backup tools | open | |
| OQ-017 | Security | What are the actual operational roles and permissions? | Needed for authorization model. | desktop menu permissions and web/mobile privilege bits | open | |
| OQ-018 | Data quality | What manual workarounds and data cleanup happen today? | Reveals hidden requirements. | Not reliably derivable from source. | open | |
| OQ-019 | Compliance | What data retention, audit, customer, tax, insurance, or legal obligations exist? | Needed before replacing reports and records. | Not reliably derivable from source. | open | |
| OQ-020 | Secrets | Are checked-in credentials still valid? | Security risk and remediation priority. | legacy config files with credentials | open | |
