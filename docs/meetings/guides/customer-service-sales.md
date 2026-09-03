# Customer Service And Sales Guide

Goal: validate customer/consignee records, communications, alerts, sales tracking, callbacks, and account history needs.

## Source Assumptions To Validate

| Assumption | Evidence |
| --- | --- |
| Customer maintenance includes customer edit, advanced settings, email settings, services, vendor rates, weight rates, alerts, visits, and consignees. | `../Fleetwood/Fleetwood4/Forms`, `../Fleetwood/Fleetwood5/Forms`, `../Fleetwood5/Forms` |
| Sales/reporting includes sales calls, callbacks, follow-ups, potential customers, new sales, top sales, sales compared, volume, and contracts termination reports. | `../Fleetwood/Fleetwood4/Forms/Main.frm`, `../Fleetwood/Fleetwood5/Forms/Main.frm` |
| Customer web accounts and groups exist separately from desktop users. | `../Fleetwood/Fleetwood4/Forms/Main.frm`, `../Fleetwood.Web/Fleetwood.Web.Api/Core/Repositories/UsersRepository.cs` |

## Questions

1. What is a customer account in Fleetwood: billing entity, requester, location, company, or all of these?
2. How are consignees used?
3. Which customer fields are critical for dispatch?
4. Which customer fields are critical for billing?
5. What customer alerts exist, and when should they appear?
6. How are credit problems handled?
7. How are customer-specific services and rate permissions managed?
8. Who maintains customer email/contact data?
9. How are customer visits, sales calls, callbacks, and follow-ups used?
10. Which customer history is needed during a phone call?
11. Which customers use the web portal?
12. What do customers ask for that Fleetwood cannot provide easily today?
13. What data should be searchable across customers, orders, notes, emails, and calls?
14. What customer information should be hidden or permission-controlled?

## AI-First Prompts

- Would call/order/customer summaries help customer service?
- Could an assistant draft customer follow-up notes or reminders?
- What would users want to ask in plain English about a customer account?
