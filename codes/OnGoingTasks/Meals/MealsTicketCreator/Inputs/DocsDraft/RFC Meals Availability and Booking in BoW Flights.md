
## Summary

This RFC proposes the integration of a meal selection feature into the BoW flight booking flow. The goal is to provide personalized travel experiences by allowing users to pre-select their meals, thereby improving customer satisfaction and increasing ancillary revenue.

## Background / Problem Context

Meal services are standard ancillary offerings across airlines, typically customized per passenger and per flight segment. Currently, the BoW platform lacks this feature. The absence of meal selection is a missed opportunity to enhance the booking experience and monetize ancillary services more effectively. The foundational systems supporting ancillaries (like database schema, integration framework, and admin tooling) are already in place, allowing for efficient expansion to support meals.

## Why Now

- **Market Alignment**: As competitors roll out meal offerings, Wego must stay competitive in the ancillary space.
    
- **Revenue Growth**: Ancillaries such as meals have a direct positive impact on per-booking revenue.
    
- **System Readiness**: Backend APIs (e.g., Get Meals, Assign Meals) and provider integrations like Air Arabia are operational.
    
- **User Insights**: UX research has shown clear demand and usability potential for this feature in the checkout process.
    

## Goals / Definition of Success

- [Goal 1] Integrate real-time meal availability into the BoW booking flow.
    
- [Goal 2] Allow users to view, select, and edit meal choices for each passenger and segment.
    
- [Goal 3] Include selected meals in booking confirmation, history, and payment breakdown.
    
- [Goal 4] Enable tracking of meal revenue and user interactions through Genzo.
    

## Non-goals

- Does not introduce loyalty program meal redemptions.
    
- Does not apply to mobile app experiences.
    
- Does not handle airport/in-flight upsells or offline modifications.
    
- Post-booking meal cancellation flows are excluded until further clarity.
    

## Proposal

### Proposed Solution

Leverage the BoW Integration Framework to introduce:

1. **Get Meals Availability**: Fetch meal options from providers after passenger details are completed.
    
2. **Assign/Book Meals**: Confirm meal selections upon payment.
    

### Implementation Plan

#### Backend

- Implement API connectors for real-time meal availability.
    
- Define `GetMealsAvailabilityRequest/Response` and `AssignMealRequest/Response` models.
    
- Extend ancillary tables with support for meal metadata (type, dietary, segment, price).
    
- Ensure meals integrate into booking and ticketing lifecycle.
    

#### Frontend

- Inject meal selection UI (MealMap) after passenger details.
    
- Display options with clear pricing (VAT included/excluded as per locale).
    
- Provide editing and skipping options per pax and segment.
    
- Surface selections on confirmation and booking details page.
    

#### Mid Office and Admin Tools

- Display meal details (type, price, passenger info) in booking logs.
    
- Enable manual meal sync/update operations.
    
- Support refund/adjustment UI (planned for future phase).
    

#### Tracking & Metrics

- Capture view, select, skip, and fail events in Genzo.
    
- Report on:
    
    - Total meal revenue (pre/post-VAT)
        
    - Markup and margins
        
    - User conversion per segment
        
    - Drop-off and error rates
        

### Mermaid Diagram

```
flowchart LR
    A[Passenger Info Completed] --> B[Get Meal Availability]
    B --> C[Display Meals in Checkout Flow]
    C --> D[User Selects Meal]
    D --> E[Assign Meal API Call]
    E --> F[Add to Total Price Summary]
    F --> G[Make Payment]
    G --> H[Confirmation Page]
    H --> I[Booking History Updated]
    G --> J[Meal Booking Status Logged]
    J --> K[CS View Meal Info in Mid Office]
```

## Abandoned Ideas

- **Bundling with Fare Families**: Dismissed due to airline inconsistency and limited dynamic configuration.
    
- **Frontend-Only Rendering**: Rejected to preserve API integrity and consistent business logic.
    

## Decision

Move forward with the phased implementation of meal selection in the BoW flight booking process. This mirrors the structure and lifecycle of the seat selection feature and reuses existing ancillary infrastructure.

## Decision Records

- Meals development progress: [Meals Tracker](https://docs.google.com/spreadsheets/d/1fuMakeh0Q_iKBIg-jGuqxUoqq3RkfWmnq5_KkCDttSo)
    
- Schema reference: [Ancillaries DB Design](https://wegomushi.atlassian.net/wiki/spaces/FT/pages/3085074682/Ancillaries+DB+Design)
    

## Appendices

- [Meal Selection UI Specs](https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2892202115/Addons+Meal+Selection)
    
- [Checkout UX Study](https://wegomushi.atlassian.net/wiki/spaces/URT/pages/2282487835/FBOW+Check+Out+Flow+Meals+Selection)
    
- [Air Arabia Integration Summary](https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2892202115/Addons+Meal+Selection)