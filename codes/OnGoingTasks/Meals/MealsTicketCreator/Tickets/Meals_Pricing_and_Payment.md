# Task: Meals Pricing & Payment

**Status:** 
**Assignee:** Suleman Naeem
**Related Tickets:** 

**Description:**
(Integrate the cost of selected meals into the overall booking price summary and payment processing flow. This involves updating relevant APIs like `/addons/confirm` and `/payment` as mentioned in the RFC and similar to the Seat Selection feature - FBOWINT-833.)

**Acceptance Criteria:**
- Total cost in price breakdown includes selected meal costs.
- Payment API requests include meal costs.
- Successful payment correctly captures the amount for meals.
- `/addons/confirm` API response reflects total meal amount. 