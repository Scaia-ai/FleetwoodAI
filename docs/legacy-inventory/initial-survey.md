# Fleetwood Legacy Initial Survey

Date: 2026-09-03

This is a source-derived first pass over the sibling Fleetwood repositories. The legacy repositories are treated as read-only inputs. Conclusions here should be validated against the running production system and users before becoming product requirements.

## Repositories Found

| Repository | Appears To Contain | Supporting Sources |
| --- | --- | --- |
| `../Fleetwood` | Aggregated legacy source tree after pull. It now contains `Fleetwood4`, `Fleetwood5`, `Fleetwood.Web`, `FleetLive`, `BackupTool`, and `FleetwoodBilling`. | `../Fleetwood/README.md`, `../Fleetwood/Fleetwood4/Fleetwood.vbp`, `../Fleetwood/Fleetwood5/Fleetwood.vbp`, `../Fleetwood/Fleetwood.Web/Source/Fleetwood.Web.sln`, `../Fleetwood/FleetLive/Source/FleetLive.sln`, `../Fleetwood/BackupTool/Source/BackupTool.sln`, `../Fleetwood/FleetwoodBilling/Source/FleetwoodBilling.sln` |
| `../Fleetwood5` | Standalone VB6 desktop Fleetwood 5 tree, likely a later or alternate desktop variant. | `../Fleetwood5/Fleetwood.vbp`, `../Fleetwood5/README.md` |
| `../Fleetwood.Web` | ASP.NET MVC/Web API customer web portal with AngularJS frontend. | `../Fleetwood.Web/Fleetwood.Web.sln`, `../Fleetwood.Web/Fleetwood.Web/Fleetwood.Web.csproj`, `../Fleetwood.Web/Fleetwood.Web.Api/Fleetwood.Web.Api.csproj`, `../Fleetwood.Web/Fleetwood.Web/App/config.js` |
| `../FleetLive` | Mobile/driver system: Web API, EF data project, notification Windows service, Angular/Cordova-style client. | `../FleetLive/FleetLive.sln`, `../FleetLive/FleetLive.Web.Api/FleetLive.Web.Api.csproj`, `../FleetLive/FleetLive.Web.Data/FleetLive.Web.Data.csproj`, `../FleetLive/FleetLive.NotificationService/FleetLive.NotificationService.csproj`, `../FleetLive/FleetLive/scripts/config.js` |
| `../FleetwoodTasks` | Planning and presentation material for cloud migration. | `../FleetwoodTasks/CloudMigration.md`, `../FleetwoodTasks/HOWTO.md` |

## Technologies And Languages

| Area | Technologies | Supporting Sources |
| --- | --- | --- |
| Legacy desktop | VB6, ADO, DAO, SQL Server DMO, Crystal Reports, Word/Excel automation, OstroSoft SMTP, Microsoft MapPoint, ActiveX/OCX controls. | `../Fleetwood/Fleetwood4/Fleetwood.vbp`, `../Fleetwood/Fleetwood5/Fleetwood.vbp`, `../Fleetwood5/Fleetwood.vbp` |
| Customer web portal | .NET Framework 4.5.1, ASP.NET MVC 5, ASP.NET Web API, Entity Framework 5, AngularJS, jQuery, Bootstrap, NLog. | `../Fleetwood.Web/Fleetwood.Web/Fleetwood.Web.csproj`, `../Fleetwood.Web/Fleetwood.Web.Api/Fleetwood.Web.Api.csproj`, `../Fleetwood.Web/Fleetwood.Web/App/config.js` |
| Driver/mobile system | .NET Framework 4.0/4.5, ASP.NET Web API, Entity Framework 6, AngularJS mobile UI, Cordova/PhoneGap-style app assets, Google Cloud Messaging. | `../FleetLive/FleetLive.Web.Api/FleetLive.Web.Api.csproj`, `../FleetLive/FleetLive.Web.Data/FleetLive.Web.Data.csproj`, `../FleetLive/FleetLive/FleetLive.csproj`, `../FleetLive/FleetLive.NotificationService/Services/AndroidPushService.cs` |
| Operations utilities | C# backup utility and C# billing helper under the aggregated `Fleetwood` repo. | `../Fleetwood/BackupTool/Source/BackupTool/BackupTool.csproj`, `../Fleetwood/FleetwoodBilling/Source/FleetwoodBilling.csproj` |

## Database And Data Access

Fleetwood is SQL Server-centered. The VB6 app uses global ADO connections for a selected company database, a default/config Fleetwood database, a FleetLive database, and a log database.

Supporting sources:

- `../Fleetwood/Fleetwood4/Modules/Main.bas`
- `../Fleetwood/Fleetwood5/Modules/Main.bas`
- `../Fleetwood5/Modules/Main.bas`

The source suggests a multi-database model:

- Global/config database, commonly named `Fleetwood`.
- Company databases, with examples such as `StarAustin` in web configs.
- `FleetLive` database for mobile account/log state.
- Optional per-company log database configured through `DATMST.LogDatabase`.

Supporting sources:

- `../Fleetwood/Fleetwood4/Modules/Main.bas`
- `../Fleetwood/Fleetwood.Web/Source/Fleetwood.Web.Api/Web.config`
- `../Fleetwood.Web/Fleetwood.Web.Api/Web.config`
- `../FleetLive/FleetLive.Web.Api/Web.config`
- `../FleetLive/FleetLive.Web.Data/App.config`

Important: several checked-in config files contain database credentials. They should be treated as secrets during modernization and not copied into new docs except as redacted evidence references.

Known data-access locations:

| Location | Role |
| --- | --- |
| `../Fleetwood/Fleetwood4/Modules/Main.bas`, `../Fleetwood/Fleetwood5/Modules/Main.bas`, `../Fleetwood5/Modules/Main.bas` | Connection setup and global ADO recordsets. |
| `../Fleetwood/Fleetwood4/Forms`, `../Fleetwood/Fleetwood5/Forms`, `../Fleetwood5/Forms` | Many forms directly run SQL and bind ADO recordsets. |
| `../Fleetwood/Fleetwood4/Modules/modShipments.bas`, `../Fleetwood/Fleetwood5/Modules/modShipments.bas`, `../Fleetwood5/Modules/modShipments.bas` | Shipment/order business logic and SQL. |
| `../Fleetwood/Fleetwood4/Modules/CustomerSync.bas`, `../Fleetwood/Fleetwood5/Modules/CustomerSync.bas`, `../Fleetwood5/Modules/CustomerSync.bas` | Customer and shipment synchronization across databases. |
| `../Fleetwood.Web/Fleetwood.Web.Api/Core/Context/*.edmx` | Entity Framework model of Fleetwood and company databases. |
| `../Fleetwood.Web/Fleetwood.Web.Api/Core/Repositories` | Web API SQL/EF repositories for users, orders, address book, reports. |
| `../FleetLive/FleetLive.Web.Data/Context` and `../FleetLive/FleetLive.Web.Data/Entities` | EF contexts/entities for FleetLive and company shipment data. |
| `../FleetLive/FleetLive.Web.Data/Scripts/StoredProcedures.sql` | Stored procedure for counting vendor pickup/delivery work. |
| `../Fleetwood/Fleetwood4/Scripts`, `../Fleetwood/Fleetwood5/Scripts`, `../Fleetwood5/Scripts` | SQL migration scripts. |

## Likely Business Domains

| Domain | What Source Shows | Supporting Sources |
| --- | --- | --- |
| Order lifecycle | Order entry, view/copy orders, dispatch orders, load today's prescheduled orders, after-hours orders, hidden prescheduled/contract order menu entries. | `../Fleetwood/Fleetwood4/Forms/Main.frm`, `../Fleetwood/Fleetwood5/Forms/Main.frm`, `../Fleetwood5/Forms/Main.frm` |
| Dispatch | Status codes include hold, ready, notify, up, down, cancel. Dispatch menus include driver sign-in/sign-out, set status, change location, and move orders to tabs. | `../Fleetwood/Fleetwood4/Modules/Main.bas`, `../Fleetwood/Fleetwood4/Forms/Main.frm`, `../Fleetwood/Fleetwood4/Forms/frmDispatch.frm`, `../Fleetwood/Fleetwood4/Forms/frmDispatchNew.frm` |
| Customer/vendor/employee master data | Maintenance for customers, vendors, employees, users, services, GL codes, status codes, service failure codes, no-charge codes, order number prefixes. | `../Fleetwood/Fleetwood4/Forms/Main.frm`, `../Fleetwood/Fleetwood5/Forms/Main.frm` |
| Pricing/rating | Mileage, area, per-mile, bobtail rate sheets, custom service times, weight rates, fuel charges, customer-vendor rates. | `../Fleetwood/Fleetwood4/Forms/Main.frm`, `../Fleetwood.Web/Fleetwood.Web.Api/Core/Repositories/OrdersRepository.cs` |
| Billing and AR/AP | Create/view invoices, apply payments, view payments/credits, create/view settlements, sales commissions, aging and credit reports. | `../Fleetwood/Fleetwood4/Forms/Main.frm`, `../Fleetwood/Fleetwood4/Modules/modInv.bas`, `../Fleetwood/Fleetwood4/Modules/modPayroll.bas` |
| Reports | Customer, vendor, order, accounting, sales, manager, POD, radio inventory, mailing labels, many Crystal templates. | `../Fleetwood/Fleetwood4/Forms/Main.frm`, `../Fleetwood/Fleetwood4/Templates`, `../Fleetwood/Fleetwood5/Templates`, `../Fleetwood5/Templates` |
| Customer web portal | Order entry, return order, track orders, address book, aged invoices, on-time percent, cost summary, delivery summary. | `../Fleetwood.Web/Fleetwood.Web/App/config.js`, `../Fleetwood.Web/Fleetwood.Web.Api/Api/Controllers/OrdersController.cs`, `../Fleetwood.Web/Fleetwood.Web.Api/Api/Controllers/ReportsController.cs` |
| Driver/mobile execution | Vendor authentication, pickup/delivery queues, status updates from picked up to delivered, barcodes, images, signatures, push notifications. | `../FleetLive/FleetLive.Web.Api/Controllers/AccountController.cs`, `../FleetLive/FleetLive.Web.Api/Controllers/PickupOrdersController.cs`, `../FleetLive/FleetLive.Web.Api/Controllers/DeliveryOrdersController.cs`, `../FleetLive/FleetLive.Web.Api/Controllers/OrdersController.cs`, `../FleetLive/FleetLive.NotificationService/Services/FleetLiveNotificationService.cs` |
| Cloud migration | Prior plan considered hosting Fleetwood in the cloud or linking desktop workstations to cloud databases, then gradually replacing functionality. | `../FleetwoodTasks/CloudMigration.md` |

## Repository Relationships

- `../Fleetwood` is now the broadest source package. It includes embedded copies of `Fleetwood4`, `Fleetwood5`, `Fleetwood.Web`, `FleetLive`, `BackupTool`, and `FleetwoodBilling`.
- `../Fleetwood5` appears to duplicate or overlap with `../Fleetwood/Fleetwood5`; production authority is not yet established.
- `../Fleetwood.Web` overlaps with `../Fleetwood/Fleetwood.Web/Source`; production authority is not yet established.
- `../FleetLive` overlaps with `../Fleetwood/FleetLive/Source`; production authority is not yet established.
- Web and mobile systems both depend on the legacy SQL database model rather than replacing it.
- Desktop Fleetwood appears to administer FleetLive vendor access from forms such as `frmVendorEditFleetLive.frm`.

## What Is Not Yet Understood

- Which tree/version is actually running in production: `Fleetwood4`, `Fleetwood5`, standalone `../Fleetwood5`, embedded copies under `../Fleetwood`, or another deployment.
- Which source tree should be treated as authoritative for requirements.
- The active company database list and whether company databases share identical schema.
- Full SQL schema, including views, indexes, constraints, stored procedures, jobs, and triggers outside the checked-in scripts/models.
- Which reports are required versus unused historical artifacts.
- Exact end-to-end dispatch workflows, including exceptions, reassignments, route handling, and after-hours behavior.
- Exact financial rules for invoicing, credits, settlements, commissions, COD, fuel, no-charge orders, and recalculation.
- Which integrations are live today: email, text messaging, maps, accounting exports, phone/call systems, mobile push, client systems, backup jobs.
- Current security roles, privilege meanings, and operational access controls.
- Data quality issues and manual workarounds users rely on.

## Immediate Questions For Lazar Or Users

1. Which executable/source tree is production today?
2. Are the standalone repos authoritative, or are the nested copies under `../Fleetwood` authoritative?
3. What company databases are active?
4. Is FleetLive still used in production? If yes, by whom and on what devices?
5. Which reports must be preserved for customers, vendors, accounting, tax, or management?
6. What daily workflow must never be interrupted during migration?
7. Are any checked-in credentials still valid and therefore needing immediate rotation?
