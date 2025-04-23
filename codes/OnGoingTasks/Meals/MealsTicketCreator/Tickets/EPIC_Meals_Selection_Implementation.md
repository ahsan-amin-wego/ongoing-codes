# Epic: Meals Selection Implementation

**Key:** FBOWINT-XXX (To be created)
**URL:** (Link to Jira Epic once created)
**Summary:** Meals Selection Implementation
**Project:** Flight BoW Integrations (FBOWINT)
**Issue Type:** Epic
**Status:** To Do
**Priority:** Normal
**Reporter:** (Your Name/Requester)
**Assignee:** Unassigned
**Created:** (Current Date)
**Updated:** (Current Date)
**Labels:** Meals, Ancillary

---

## Description

h2. RFC: [RFC Meals Availability and Booking in BoW Flights](Inputs/DocsDraft/RFC Meals Availability and Booking in BoW Flights.md) 

h2. Problem Statement & Objective

* BoW currently does not offer meal selection as part of the booking flow.
* Offering meal selection can help grow our revenue per booking and improve customer satisfaction by providing personalized travel experiences.
* The foundational systems supporting ancillaries (database schema, integration framework, admin tooling) are already in place from features like Seat Selection, allowing for efficient expansion to support meals.
* Goal is to allow users to view and pre-select meals during the booking process.

h2. Feature Breakdown: Functional

* *Meal selection*
** Meal availability
*** Call relevant provider APIs (e.g., Air Arabia initially) via the Integration Framework to get meal options, descriptions, dietary information, and pricing per passenger/segment. Utilize `Get Meals API`.
*** Handle providers that do not offer meals or specific meal types.
*** Consider provider specific details (e.g., SSR codes, API specifics) - TBC per provider integration.
** Take meal inventory availability from supplier.
** Allow users to select a meal, and unselect a meal, updating the total price accordingly.
** Display meal options clearly (name, description, price, dietary info if available).
** View cost per meal type/option.
** Allow user to skip selecting meals per segment or for specific passengers.
** (TBC) If user did not select meals, consider adding a reminder if the user is sure they don't want to select a meal (can be configured for experimentation).
** Add selected meal cost to the payment summary. Utilize `Assign Meals API` upon payment confirmation.
** (TBC) Order of when the meal selection is shown in the checkout flow (e.g., after passenger details, as per RFC).
** For multi-pax booking:
*** (TBC) Allow selecting meals for all passengers at once or individually.
*** (TBC) Allow booking meals for a subset of passengers in the booking.
** For Fare family:
*** If fare family already includes a meal, user should not be charged extra (or logic TBC based on airline rules).
** Sum of One Way & Virtual Interline:
*** Ability to select meals per leg/segment as appropriate.
** Booking confirmation page, booking history in my account, reflects payment and selected meals.
** Payment to supplier includes meal details/cost as required by the provider.
* (TBC) If meal inventory is unavailable after selection but before confirmation/payment.
* *Pricing, Data & Tracking*
** *Pricing & Sourcing*
*** Ability to set a target margin per meal per segment/route.
*** Pricing rule implementation.
*** Add in upfront commission & back end commission if applicable.
*** Breakdown VAT component of markup/markdown, and VAT component of offering the meal itself (Refer to `Meals Tax Handling` task).
*** CMS/Admin tool to configure which airlines/integrations offer meals.
** *Data*
*** Meal selection is stored at segment and passenger level, rolling up to the booking.
*** Meal as a separate product item and revenue item in reporting.
*** Markup/markdown is calculated separately.
*** VAT is calculated separately.
** *Tracking* (via Genzo)
*** Meal selection UI impressions.
*** Users who viewed meals but did not select.
*** Users who selected meals but did not complete purchase.
*** Users who explicitly skipped meal selection.
*** Log when supplier API calls for meals fail or return errors/no availability.
*** Track `Get Meals API` and `Assign Meals API` calls.
* *CS & BO*
** Per booking, segment, and passenger, reflect if user selected a meal, which meal, price, and status.
** Reflect breakdown in BO tool (Mid Office) (Refer to `Display Meals Info & Status in Mid Office Tool` task).
** Define refund/change policy for meals (TBC, likely non-refundable initially).
* *Experimentation:*
** Baseline: No meal selection offered.
** Variant A: Meal selection offered.

h2. Feature Breakdown: Non-Functional

* Error states
** Flight Suppliers - if unavailable, elegantly skip meal selection and track when skipped, and error reasons. Handle API errors gracefully.
* Compatibility
** Standardise handling meals across different suppliers via the Integration Framework.
*** Review/Update [Integration Framework|https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2078638156/Integration+guidelines] for meals.
*** Consider meal elements in Search/Revalidation, Booking/Validate Booking, Ticketing, Cancellation flows as needed.
** Ability for WegoPro to also consume service requesting & booking a meal (pricing, etc) (Marked as Next Phase).
* Response time & latency
** (TBC) Define acceptable max loading time for meal options (e.g., < 3-5 seconds).
* Caching
** Cache meal *definitions* (descriptions, dietary info) where possible, but availability/pricing requires real-time checks.
* Extensibility
** Ensure framework can support other ancillaries (luggage, seats, etc.).
* Testability
** Unit testing for backend logic (pricing, API calls).
** Automated end-to-end testing for meal selection flow.

h2. Outstanding Questions (Adapted from Seats Epic / RFC)

* Is meal selection per segment or per leg (e.g., for connecting flights)? How should it be presented?
* For connecting flights, what is the desired response structure for multiple segments (e.g., single meal choice for whole journey vs. per segment)?
* For carriers with multiple suppliers, if meals are unavailable in one, do we fail over? Can we book a flight from supplier A and meal from supplier B?
* How do we handle flights with stopovers regarding meal selection/pricing?
* What happens when a selected meal becomes unavailable before payment/confirmation?
* What happens when a meal booking fails but the flight is confirmed? (Relates to CS notification task)
* Can we reserve meal allocation temporarily during the checkout flow?
* How does Wenrix optimization affect meal selection/availability?
* How are meal prices quoted (base, tax, total)?
* How do we verify if a selected Fare Family already includes a meal? Where does this info come from?
* Post-booking meal selection/modification (Marked as Non-goal for now).
* Dietary restrictions handling - how is this data received from providers and presented to users? Are filters needed?
* Meal serving times/conditions - any specific information to display?

*Supporting Documents* (Referenced from Meals RFC):

* [Meals Tracker](https://docs.google.com/spreadsheets/d/1fuMakeh0Q_iKBIg-jGuqxUoqq3RkfWmnq5_KkCDttSo)
* [Ancillaries DB Design](https://wegomushi.atlassian.net/wiki/spaces/FT/pages/3085074682/Ancillaries+DB+Design)
* [Meal Selection UI Specs](https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2892202115/Addons+Meal+Selection)
* [Checkout UX Study](https://wegomushi.atlassian.net/wiki/spaces/URT/pages/2282487835/FBOW+Check+Out+Flow+Meals+Selection)
* [Air Arabia Integration Summary](https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2892202115/Addons+Meal+Selection) (Note: Link seems duplicated in RFC, verify correct link)

*(TBC) Phase 2:*

* Post Booking flow for meals.
* Offering meals after booking (My account, email, etc.).
* Storing user meal preferences.

*References*
* (Add any specific provider documentation links here as integrations happen)

---

## Attachments
*(Add relevant mockups or diagrams if available)*

*(Note: Comments are not included in this summary)* 