# Dispatch And Orders Guide

Goal: validate how orders enter the system, become dispatch work, move through statuses, and get resolved.

## Source Assumptions To Validate

| Assumption | Evidence |
| --- | --- |
| The desktop app has order entry, view orders, copy orders, dispatch orders, today's prescheduled orders, and after-hours orders. | `../Fleetwood/Fleetwood4/Forms/Main.frm`, `../Fleetwood/Fleetwood5/Forms/Main.frm` |
| Core status codes include hold, ready, notify, up, down, and cancel. | `../Fleetwood/Fleetwood4/Modules/Main.bas`, `../Fleetwood/Fleetwood5/Modules/Main.bas` |
| Mobile pickup work is selected by pickup vendor and `NTF` status; delivery work is selected by delivery vendor and `UP` status. | `../FleetLive/FleetLive.Web.Api/Controllers/PickupOrdersController.cs`, `../FleetLive/FleetLive.Web.Api/Controllers/DeliveryOrdersController.cs` |
| Mobile status updates move picked-up orders to `UP` and delivered orders to `DWN`. | `../FleetLive/FleetLive.Web.Api/Controllers/OrdersController.cs` |

## Questions

1. What are the real-world meanings of `HLD`, `RDY`, `NTF`, `UP`, `DWN`, and `CNL`?
2. What is the normal path from a new order to completed delivery?
3. Who can create orders, edit orders, cancel orders, and reopen orders?
4. What information is mandatory before an order can be dispatched?
5. What information is commonly missing at order-entry time?
6. How are pickup and delivery vendors chosen?
7. Can pickup and delivery vendors be different?
8. What does "ready to notify" mean operationally?
9. What does "up" mean: driver en route, picked up, or something else?
10. How are late, failed, refused, wrong-address, or partially completed orders handled?
11. How are after-hours and weekend orders handled?
12. How are prescheduled and contract orders used?
13. Are routes used daily or only for certain customers?
14. How do dispatch tabs work, and what do they represent?
15. How are notes used, and who sees them?
16. What information do dispatchers need but cannot see quickly today?
17. What mistakes cause the most operational damage?
18. Which order changes require audit history?

## Workflow To Validate

1. Customer requests delivery.
2. Order taker enters billing, pickup, delivery, service, pieces, weight, COD, notes, and requested/actual time.
3. System calculates mileage and charges.
4. Order becomes ready for dispatch.
5. Dispatcher assigns pickup/delivery vendor.
6. Vendor is notified.
7. Pickup happens.
8. Delivery happens.
9. Proof of delivery, signature, images, barcodes, and notes are recorded.
10. Order becomes billable or no-charge/exception.

## AI-First Prompts

- Could an assistant draft an order from a phone transcript, email, or text message?
- What should an assistant warn about before dispatching an order?
- What dispatch decisions depend on experience rather than explicit rules?
- What data would make ETA or late-risk prediction useful?
