# Drivers, Vendors, And Mobile Guide

Goal: validate vendor/driver workflow, FleetLive usage, proof of delivery, notifications, mobile constraints, and field exceptions.

## Source Assumptions To Validate

| Assumption | Evidence |
| --- | --- |
| Vendors and employees are represented in the legacy system, with vendor-specific FleetLive access. | `../Fleetwood/Fleetwood4/Forms/frmVendorEditFleetLive.frm`, `../Fleetwood/Fleetwood4/Forms/frmVendorEditAdvanced.frm`, `../Fleetwood/Fleetwood4/Modules/Main.bas` |
| FleetLive accounts are tied to database name and vendor number. | `../FleetLive/FleetLive.Web.Data/Entities/Account.cs` |
| Mobile app exposes pickup orders, delivery orders, order detail, logout, signatures, images, and barcodes. | `../FleetLive/FleetLive/scripts/config.js`, `../FleetLive/FleetLive.Web.Api/Controllers` |
| Notification service watches pickup/delivery order changes and sends mobile notifications. | `../FleetLive/FleetLive.NotificationService/Services/FleetLiveNotificationService.cs`, `../FleetLive/FleetLive.NotificationService/Services/AndroidPushService.cs` |

## Questions

1. Is FleetLive currently used in production?
2. Who uses it: employees, contractors, vendors, dispatchers, or all?
3. What devices are used?
4. What are the most common mobile actions?
5. Are signatures, images, and barcodes mandatory for any customers or order types?
6. What happens if mobile data is missing or uploaded late?
7. How do drivers/vendors know they have new work?
8. What information should drivers/vendors see or not see?
9. Can drivers reject, delay, transfer, or comment on orders?
10. What should happen offline or with bad signal?
11. How are vendor availability, current location, status, and lunch/breakdown represented?
12. What mobile workflow causes the most calls back to dispatch?
13. Are vendor insurance, license, orientation, or expired-date warnings operationally important?

## Workflow To Validate

1. Vendor signs in or becomes available.
2. Dispatcher assigns pickup or delivery work.
3. Vendor receives notification.
4. Vendor views pickup queue.
5. Vendor marks pickup complete.
6. Vendor views delivery queue.
7. Vendor captures signature, images, barcodes, or notes.
8. Vendor marks delivery complete.
9. Dispatcher and billing see final proof/status.

## AI-First Prompts

- Could a mobile assistant reduce calls to dispatch?
- Which field exceptions should be easy to report by voice or quick actions?
- Would ETA prediction or route sequencing help vendors or dispatchers?
