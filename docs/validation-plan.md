# Validation Plan

This plan turns source-derived assumptions into focused customer validation sessions.

## Validation Status Labels

- `source-proven`: directly supported by source files.
- `inferred`: likely based on names, routes, data fields, or partial code paths.
- `validated`: confirmed by user/customer.
- `contradicted`: user/customer says source no longer reflects reality.
- `obsolete`: source feature exists but is no longer used.
- `unknown`: not yet validated.

## Pre-Meeting Preparation

1. Ask Lazar for source authority and deployment answers.
2. Request a read-only production schema export or backup plan.
3. Ask customer to identify users for each session.
4. Prepare examples: recent orders, invoices, settlements, reports, and mobile deliveries.
5. Confirm whether screenshots or recordings are allowed during workflow validation.

## Workflow Validation Checklist

| Workflow | Source Confidence | Participants | Validate |
| --- | --- | --- | --- |
| Order entry | medium | order takers, dispatchers | Required fields, customer lookup, consignee reuse, service selection, pieces/weight/COD, notes, timing, rate preview. |
| Dispatch assignment | medium | dispatchers, operations manager | Queue views, vendor choice, status changes, tabs, route logic, exceptions, reassignment. |
| Pickup execution | medium | drivers/vendors, dispatchers | Notification, pickup queue, pickup proof, status transition, missed/failed pickup. |
| Delivery execution | medium | drivers/vendors, dispatchers | Delivery queue, signatures, images, barcodes, POD, failed delivery, status transition. |
| Billing/invoicing | medium | billing/accounting | Billable rules, invoice batch creation, adjustments, no-charge, credits, customer delivery. |
| Payments/credits | low | billing/accounting | Payment application, credit approval, aging, reconciliation. |
| Vendor/employee settlement | low | billing/accounting, managers | Settlement formulas, commission, reimbursement, exceptions, approvals. |
| Reports | medium | managers, billing, dispatch, sales | Required outputs, external reports, Excel exports, exact-format needs, obsolete reports. |
| Customer web portal | medium | customer service, customers, managers | Current usage, order placement, tracking, reports, customer permissions. |
| FleetLive mobile | medium | drivers/vendors, dispatchers | Current usage, devices, field workflow, offline needs, notification reliability. |

## Session Outputs

Each session should produce:

- Validated/corrected workflow summary.
- Required reports and outputs touched by the workflow.
- Known exceptions and manual workarounds.
- Data fields that must be preserved.
- Permission and audit requirements.
- AI opportunities with user value and risk.
- Open questions added or resolved in `docs/open-questions.md`.

## Post-Meeting Processing

1. Update the relevant domain doc.
2. Convert confirmed facts into requirements.
3. Add contradictions against source to a decision log.
4. Add examples and test cases for later migration validation.
5. Keep unresolved questions in `docs/open-questions.md`.
