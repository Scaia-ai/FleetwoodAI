# Customer Meeting Preparation

Date: 2026-09-03

Purpose: prepare focused customer meetings that validate source-derived findings and expose business requirements for the modern Fleetwood successor. These meetings should not become full screen-by-screen walkthroughs of the legacy app.

## Meeting Objectives

1. Confirm which Fleetwood source tree and deployed application are authoritative.
2. Validate the critical daily workflows that must survive modernization.
3. Identify reports, invoices, settlements, and operational outputs that are contractually or financially important.
4. Discover manual workarounds, exception handling, and pain points not visible in source code.
5. Prioritize modernization phases around operational risk and business value.
6. Identify AI-first opportunities grounded in real work, not novelty.

## Evidence We Are Bringing

| Topic | Current Source-Derived Understanding | Evidence |
| --- | --- | --- |
| Business context | Fleetwood is for hotshot delivery operations. | `../Fleetwood/README.md` |
| Main operational app | VB6 desktop app covers orders, dispatch, billing, settlement, reporting, master data, and maintenance. | `../Fleetwood/Fleetwood4/Fleetwood.vbp`, `../Fleetwood/Fleetwood5/Fleetwood.vbp`, `../Fleetwood/Fleetwood4/Forms/Main.frm`, `../Fleetwood/Fleetwood5/Forms/Main.frm` |
| Data model | SQL Server with global/config DB, company DBs, FleetLive DB, and optional log DB. | `../Fleetwood/Fleetwood4/Modules/Main.bas`, `../Fleetwood/Fleetwood5/Modules/Main.bas`, `../Fleetwood.Web/Fleetwood.Web.Api/Web.config`, `../FleetLive/FleetLive.Web.Api/Web.config` |
| Customer web portal | Existing web app supports order entry, order return, order tracking, address book, and selected reports. | `../Fleetwood.Web/Fleetwood.Web/App/config.js`, `../Fleetwood.Web/Fleetwood.Web.Api/Api/Controllers/OrdersController.cs`, `../Fleetwood.Web/Fleetwood.Web.Api/Api/Controllers/ReportsController.cs` |
| Driver/mobile workflow | FleetLive supports vendor login, pickup/delivery queues, status updates, signatures, images, barcodes, and push notifications. | `../FleetLive/FleetLive.Web.Api/Controllers`, `../FleetLive/FleetLive.Web.Data/Context/CompanyContext.cs`, `../FleetLive/FleetLive.NotificationService/Services/FleetLiveNotificationService.cs` |
| Cloud migration history | Prior thinking favored gradual cloud replacement after hosting/linking existing Fleetwood. | `../FleetwoodTasks/CloudMigration.md` |

## Recommended Meeting Sequence

| Session | Participants | Length | Goal |
| --- | --- | --- | --- |
| 1. Executive/source authority | Owner, Lazar, operations manager, technical contact | 45 min | Confirm production version, databases, risks, and modernization guardrails. |
| 2. Dispatch and order operations | Dispatchers, order takers, operations manager | 90 min | Validate order intake, assignment, status changes, exceptions, and daily dispatch rhythms. |
| 3. Billing, AR, settlement | Billing/accounting users, manager | 90 min | Validate invoices, payments, credits, COD, fuel, vendor settlement, commissions, and month-end needs. |
| 4. Customer service and sales | Customer service, sales/manager users | 60 min | Validate customer records, consignees, alerts, callbacks, follow-ups, rate communication, and customer history. |
| 5. Drivers/vendors and mobile | Drivers/vendors using FleetLive, dispatcher, manager | 60 min | Validate mobile workflows, proof of delivery, notifications, images, signatures, and field constraints. |
| 6. Reports and outputs | Management, billing, dispatch, sales | 75 min | Classify required reports and outputs: keep, replace, combine, retire, unknown. |

## Meeting Ground Rules

- Start from source-derived findings and ask users to confirm, correct, or explain.
- Capture examples: real order numbers, customer types, edge cases, report names, and timing constraints.
- Avoid designing screens in the first meetings. Focus on decisions, rules, exceptions, and outcomes.
- Ask what users do when the system cannot express reality.
- Ask what must be auditable.
- Mark each answer as `validated`, `contradicts-source`, `new-requirement`, or `needs-follow-up`.

## Artifacts To Bring

- Initial survey: `docs/legacy-inventory/initial-survey.md`
- Reverse-engineering plan: `docs/reverse-engineering-plan.md`
- Role guides:
  - `docs/meetings/guides/executive-source-authority.md`
  - `docs/meetings/guides/dispatch-and-orders.md`
  - `docs/meetings/guides/billing-and-settlement.md`
  - `docs/meetings/guides/customer-service-sales.md`
  - `docs/meetings/guides/drivers-vendors-mobile.md`
  - `docs/meetings/guides/reports-and-outputs.md`
- Open questions register: `docs/open-questions.md`
- Workflow validation checklist: `docs/validation-plan.md`

## AI-First Topics To Test Carefully

These are candidate opportunities only. Validate need and risk before treating them as requirements.

| Opportunity | Who To Ask | Validation Question |
| --- | --- | --- |
| AI-assisted order entry | Order takers, dispatchers | Can calls/emails/texts be converted into draft orders faster than manual entry without losing required details? |
| Dispatch assistant | Dispatchers | What decisions are hardest: vendor selection, ETA risk, grouping, route changes, after-hours coverage, or exception handling? |
| Customer support context | Customer service | Would instant order/customer history summaries reduce call time or missed details? |
| Report explanation | Management, accounting | Which reports require interpretation, reconciliation, or repeated follow-up questions? |
| Anomaly detection | Billing, dispatch | What mistakes are costly: wrong rate, wrong vendor, missed pickup, late delivery, missing POD, duplicate invoice? |
| Search over calls/documents | Managers, customer service | Is there a business need to search conversations, emails, PODs, images, or notes by order/customer? |

## Capture Format

Use this format during meetings:

```text
Topic:
Source assumption:
User correction/confirmation:
Example:
Business impact:
Frequency:
Risk if wrong:
Requirement candidate:
Follow-up owner:
Status: validated | contradicts-source | new-requirement | needs-follow-up
```
