Page URL: https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2892202115/Addons+Meal+Selection
## ![direct hit](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f3af/path?scale=MDPI) Objective

**Meal Selection** feature will allow users to select meals for their flights during the booking process (Phase 1) or post-booking management (Phase 2).

## ![bar chart](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f4ca/path?scale=MDPI) Success metrics

|   |   |
|---|---|
|**Goal**|**Metric**|
|Adoption Rate|- % booking with selected meal (denominator = booking with view meal selection)<br>    <br>- % booking with selected meal (denominator = overall booking)|
|Revenue Growth|- ==Meal Revenue (total or per booking)==<br>    <br>- Meal Contribution Margin (total or per booking)<br>    <br>- Overall Gross Revenue (total or per booking)<br>    <br>- Overall Contribution Margin (total or per booking)|
|Booking Growth|- # bookings<br>    <br>- CVR (# bookings / # BoW clicks)|

## ![thinking face](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f914/path?scale=MDPI) Assumptions

TBD

## Phase Summary

- Phase 1: Meal selection during booking, pricing configuration in CMS, back office tool to support meal cancellation/change
    
- Phase 2: Meal selection in post booking, support meal cancellation/change in manage my booking
    
- Phase 3: Upsell opportunities (highlight premium meal options, display discounts or offers for certain meal types)
    

## User Stories Phase 1

- **As a user**, I want to select a meal for my flight during the booking process, so I can ensure my dietary preferences are met.
    
- **As a pricing manager**, I want to optimize meal pricing based on certain breakdowns
    
- **As a CS**, I can support customer in cancelling/changing their meal preferences
    

## Functional Requirement Phase 1

**High Level Requirement**

1. Display meal options based on airline’s offering in booking flow
    
2. ==Develop pricing logic that is configured via CMS (Pennyworth)==
    
3. Display selected meal details in Back Office tool, grant ability to process cancellation/change
    

### Front-End Requirements (Booking Flow)

1. After filling passenger details, display meal availability for each leg
    
    1. Highlight any savings for pre-booking meal
        
    2. Hide meal selection if none of the legs have meal selection)
        
2. Users can select meals per pax and per leg
    
    - User can see the meal price before VAT
        
    - Users can input notes (e.g. dietary restrictions or allergies)
        
    - Users can skip meal selection
        
3. User can see the total meal price after VAT (and the breakdown) in price summary & payment
    
4. User can see the selected meal in booking confirmation page, email confirmation, and booking history
    

### Back-End Requirements

1. Store list of provider with meal selection (Help FE to decide to show/not show meal selection per leg)
    
2. Integrate provider API to fetch real-time meal options, availability, and price
    
    - Ensure real-time updates for changes in meal policies
        
3. Pricing logic to markup base meal price, configured via Pennyworth
    
    - Some airlines may provide free meal (e.g. Full Service Carriers), in this case we won’t add markup price.
        
    - [MVP] Breakdown by POS, Integration, Carrier
        
    - [Next phase] Breakdown by trip category (domestic/international), passenger type, cabins, iPCC, trip type, locale, schedule date
        
4. Book selected meal per leg per pax to provider
    
5. Update meal booking status in the ticket (success / fail)
    
    - Send notification to CS if meal booking failed after payment
        

### CS & Mid Office Requirements

1. Enable CS to view and (manually) modify meal selections upon user request.
    
2. Enable CS to cancel non-refundable meal upon user request
    
3. Enable CS to refund for failed meal booking
    
4. Add FAQs for common meal selection issues
    

### Tracking Requirements

1. Booking flow:
    
    1. # view meal selection, # BoW click with view meal selection, # booking with view meal selection
        
    2. # click meal selection, # BoW click with view meal selection, # booking with click meal selection
        
    3. # purchased meal selection, # BoW click with selected meal selection, # booking with selected meal selection
        
    4. # skip meal selection, # BoW click with skip meal selection, # booking with skip meal selection
        
2. Pricing & sales:
    
    1. gross revenue
        
    2. contribution margin
        
    3. total base meal price
        
    4. total meal price after markup before VAT
        
    5. total meal VAT
        
    6. total meal price after markup and VAT
        
3. Post booking:
    
    1. # of meal cancellations
        
    2. # of failed meal booking vs # of successful meal booking
        

**Data structure**

- Meal is stored at segment level (Hierarchy: Booking > Leg > Meal)
    
- Meal as a separate product item and revenue item to flights
    

## Non-Functional Requirements

- Latency: Meal selection should load within 2 seconds (TBC)
    
- Scalability: Handle concurrent meal selection requests during peak times (RPS up to xx)
    
- Reliability: Ensure 99% uptime for meal-related features.
    
- Error states: track various error reasons
    
- Compatibility: since all suppliers treat meals differently, integration framework will have to standardize dealing with all suppliers in flow of offering ancillaries
    
    - [Integration Framework](https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2078638156 "https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2078638156")
        
        - (TBC) - If FareRule has seats included boolean
            
        - Search/Revalidation - Add meals element
            
        - Booking/Validate Booking - Add meals element
            
        - Ticketing - Add meals element
            
        - Cancellation - (non refundable)
            
    - Ability for WegoPro to also consume service requesting & booking a meal (pricing, etc)
        
- Extensibility
    
    - Extend to other ancillaries a.k.a Special Service Request
        
- Testability
    
    - Unit testing
        
    - Automated end-to-end testing for all flows
        

## Risks and Mitigations

1. Risk: Airline APIs may fail or provide inconsistent data.  
    Mitigation: Implement caching and fallback options.
    
2. Risk: Users may misunderstand meal options.  
    Mitigation: Use clear descriptions and tooltips.
    
3. Risk: Last-minute meal changes may not be accommodated.  
    Mitigation: Notify users of airline cut-off times.
    