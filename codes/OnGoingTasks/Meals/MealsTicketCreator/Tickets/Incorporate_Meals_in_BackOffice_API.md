# Task: Incorporate Meals in BackOffice API

**Status:** 
**Assignee:** Suleman Naeem
**Related Tickets:** 

**Description:**
(Update the relevant BackOffice/Admin APIs (likely the `/admin/addons` endpoint, similar to FBOWINT-837 for seats) to fetch and display information about booked meals, including meal type, price, passenger, segment, and status.)

**Acceptance Criteria:**
- BackOffice API response includes a `meals` section with detailed assignments.
- Meal details (type, price, status, passenger/segment mapping) are correctly fetched and returned.
- Follows a similar structure to how seats are handled in the BackOffice API. 