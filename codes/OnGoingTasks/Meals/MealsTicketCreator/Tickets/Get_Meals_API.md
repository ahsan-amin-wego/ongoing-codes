# Task: Get Meals API

**Status:** Code Complete
**Assignee:** Suleman Naeem
**Related Tickets:** 

**Description:**
(Create the `GetMealsAvailability` API endpoint as defined in the RFC. This API will fetch meal options from integrated providers based on the flight/booking context.)

**Acceptance Criteria:**
- API endpoint `/metasearch/bookings/flights/.../meals-availability` (or similar) is created.
- Accepts `GetMealsAvailabilityRequest`.
- Returns `GetMealsAvailabilityResponse` with meal options, pricing, and metadata.
- Handles scenarios where providers don't support meals or return errors. 