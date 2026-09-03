# Fleetwood Reverse-Engineering Plan

This plan is for deriving modern successor requirements from source code, databases, reports, integrations, and targeted user validation. It intentionally avoids implementing the replacement application until the business model is understood.

## Principles

- Treat legacy repositories as read-only evidence.
- Write new findings only in `FleetwoodAI/docs/`.
- Separate source-proven facts from inferences and user-validated requirements.
- Prefer database, report, and business-rule evidence over manual screen transcription.
- Validate important workflows with users after source analysis narrows the questions.
- Redact secrets from documentation.

## Documentation Structure

Planned docs:

- `docs/legacy-inventory/initial-survey.md`
- `docs/legacy-inventory/repository-map.md`
- `docs/legacy-inventory/technology-map.md`
- `docs/legacy-inventory/data-access-map.md`
- `docs/legacy-data-model.md`
- `docs/domain-orders.md`
- `docs/domain-dispatch.md`
- `docs/domain-rating-pricing.md`
- `docs/domain-billing-ar.md`
- `docs/domain-settlements-ap.md`
- `docs/domain-customers.md`
- `docs/domain-vendors-drivers.md`
- `docs/domain-reports.md`
- `docs/domain-mobile-fleetlive.md`
- `docs/domain-customer-web.md`
- `docs/integrations.md`
- `docs/open-questions.md`
- `docs/validation-plan.md`
- `docs/modern-successor-spec.md`

## Work Plan

1. Establish source authority.
   - Reconcile Lazar's answers with repo layout.
   - Decide which code trees are production, historical, duplicated, or abandoned.
   - Mark each source directory with confidence.

2. Build a data catalog.
   - Extract table, view, stored procedure, and column references from VB SQL strings, EF models, SQL scripts, and reports.
   - Identify global/config tables, company tables, FleetLive tables, log tables, and cross-company sync tables.
   - Produce an entity glossary with source references.

3. Map modules to domains.
   - Use VB menu structure, form names, modules, classes, web routes, and mobile controllers.
   - Build one domain page per major business area.
   - For each domain, list screens/forms, data entities, reports, roles, and known workflows.

4. Extract business rules.
   - Mine rules from modules such as shipment, invoice, payroll/settlement, rate sheet, sync, and report code.
   - Label each rule as `source-proven`, `inferred`, or `needs-validation`.
   - Capture source file and line references for every significant rule.

5. Analyze reports as requirements.
   - Inventory Crystal `.rpt` and `.ttx` files.
   - Link each report to source forms/modules, parameters, datasets, and output audience.
   - Ask users to classify each report as required, useful, obsolete, or unknown.

6. Trace critical workflows.
   - Produce sequence docs for order entry, dispatch, mobile pickup, mobile delivery, proof of delivery, invoicing, payment, settlement, customer web order, and reporting.
   - Include happy path and known exceptions.
   - Validate only high-value or ambiguous steps with users.

7. Identify integrations and operational jobs.
   - Inventory email, text messaging, MapPoint/mileage, Office automation, exports, backup tooling, mobile push, and any client-specific sync.
   - Classify each as replace, preserve temporarily, retire, or unknown.

8. Define the modern successor.
   - Convert validated domain docs into a product specification.
   - Propose a modern domain model and API boundaries.
   - Identify AI-first opportunities only where they support real workflows: dispatch assistance, natural-language order intake, customer support context, report explanation, anomaly detection, route optimization, and document/voice search.
   - Produce phased MVP and migration plan.

## Validation Strategy

Target user validation should happen after source analysis produces focused questions:

- Dispatchers validate order state transitions, assignment decisions, exception handling, and priority signals.
- Billing/accounting validates invoice, payment, credit, COD, fuel, settlement, and commission rules.
- Customer service validates customer records, consignees, alerts, callbacks, follow-ups, and order history usage.
- Managers validate required reports, KPIs, permissions, audit expectations, and migration priorities.
- Drivers/vendors validate FleetLive usage, signatures, images, barcodes, notifications, and mobile pain points.

## Initial Deliverables

The next documentation deliverables should be:

1. Source authority decision record after Lazar's answers.
2. Database/data-access map.
3. Domain map with forms/controllers/reports grouped by workflow.
4. Open questions register for user validation.
