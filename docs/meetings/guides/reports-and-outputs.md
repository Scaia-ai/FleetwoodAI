# Reports And Outputs Guide

Goal: classify legacy reports and outputs by business value, compliance need, and replacement priority.

## Source Assumptions To Validate

| Assumption | Evidence |
| --- | --- |
| The VB6 app has many Crystal Reports templates for customer, vendor, order, accounting, sales, manager, POD, route, ticket, and settlement outputs. | `../Fleetwood/Fleetwood4/Templates`, `../Fleetwood/Fleetwood5/Templates`, `../Fleetwood5/Templates` |
| The customer web portal exposes aged invoices, on-time percent, cost summary, and delivery summary reports. | `../Fleetwood.Web/Fleetwood.Web/App/config.js`, `../Fleetwood.Web/Fleetwood.Web.Api/Api/Controllers/ReportsController.cs` |
| Desktop menus group reports by customer, vendor, order, accounting, sales, manager, preprint tickets, radio inventory, MapPoint lookup, shipments log, and mailing labels. | `../Fleetwood/Fleetwood4/Forms/Main.frm`, `../Fleetwood/Fleetwood5/Forms/Main.frm` |

## Report Classification

For each report/output, classify:

- `required`: must be preserved because customers, vendors, accounting, tax, management, or contracts depend on it.
- `useful`: used regularly but can be redesigned.
- `replace-with-dashboard`: better expressed as interactive data.
- `combine`: overlaps with other reports.
- `obsolete`: no longer used.
- `unknown`: needs follow-up.

## Questions

1. Which reports are run daily?
2. Which reports are run weekly, monthly, quarterly, or annually?
3. Which reports are sent outside the company?
4. Which reports must match legacy formatting exactly?
5. Which reports are used for billing or payment reconciliation?
6. Which reports are required by specific customers?
7. Which reports are management KPIs?
8. Which reports are exported to Excel and manipulated manually?
9. Which reports are printed versus emailed versus viewed on screen?
10. Which reports are trusted, and which require manual checking?
11. Which outputs are not reports but still critical: tickets, invoices, PODs, labels, exports, emails, text messages?

## Capture Table

| Report/Output | Audience | Frequency | Purpose | Format Needed | Classification | Notes |
| --- | --- | --- | --- | --- | --- | --- |
| | | | | | | |
