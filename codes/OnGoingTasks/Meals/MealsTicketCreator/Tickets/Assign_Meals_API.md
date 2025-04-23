# Task: Assign Meals API

**Status:** In Progress
**Assignee:** Suleman Naeem
**Related Tickets:** 

**Description:**
(Create the `AssignMealRequest/Response` API endpoint as defined in the RFC. This API will be called to confirm and book the selected meals, typically after successful payment.)

**Acceptance Criteria:**
- API endpoint `/metasearch/bookings/flights/.../assign-meals` (or similar) is created.
- Accepts `AssignMealRequest` containing selected meals per passenger/segment.
- Interacts with the provider's booking API to confirm meal selections.
- Returns `AssignMealResponse` indicating success or failure of meal booking.
- Handles errors during meal assignment (e.g., meal no longer available, provider error). 