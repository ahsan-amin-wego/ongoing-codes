Doc URL: https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2892235204/Addons+Seat+Selection

|   |   |
|---|---|
|**Target release**|Feb 2025|
|**Epic**|Type /Jira to add Jira epics and issues|
|**Document status**|DRAFT|
|**Document owner**|@Fredick Alvin Setiawan @Richard Nasser Kua|
|**Designer**|@Herajeng Gustiayu @Hafizh Sallam|
|**Tech lead**|@Rajesh Kanna @Viet Tran|
|**Technical writers**|@ writers|
|**QA**||

## ![direct hit](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f3af/path?scale=MDPI) Objective

**Seat Selection** feature will allow users to select seats for their flights during the booking process (Phase 1) or post-booking management (Phase 2).

## ![bar chart](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f4ca/path?scale=MDPI) Success metrics

|   |   |
|---|---|
|**Goal**|**Metric**|
|Adoption Rate|- % booking with selected seat (denominator = booking with view seat selection)<br>    <br>- % booking with selected seat (denominator = overall booking)|
|Revenue Growth|- Seat Revenue (total or per booking)<br>    <br>- Seat Contribution Margin (total or per booking)<br>    <br>- Overall Gross Revenue (total or per booking)<br>    <br>- Overall Contribution Margin (total or per booking)|
|Booking Growth|- # bookings with selected seat<br>    <br>- # bookings<br>    <br>- CVR (# bookings / # BoW clicks)|

## ![chart increasing](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f4c8/path?scale=MDPI)  Tracking

event.id = `page_view_id`

event.category = `addon_flights`

event.object = `seats`

|   |   |   |   |   |   |   |   |   |
|---|---|---|---|---|---|---|---|---|
|event.action|view_section|select_leg|skip_section|edit_leg|submit|next_seat|confirm_seat||
|screenshot|Open image-20250304-152623.png<br><br>![image-20250304-152623.png](blob:https://wegomushi.atlassian.net/9676a284-e5f6-4f42-ace2-e312afaa02d6#media-blob-url=true&id=177f86e8-419a-4c44-9a0f-00d702e3a2f6&collection=contentId-2892235204&contextId=2892235204&mimeType=image%2Fpng&name=image-20250304-152623.png&size=41897&width=346&height=276&alt=image-20250304-152623.png)|Open image-20250304-152734.png<br><br>![image-20250304-152734.png](blob:https://wegomushi.atlassian.net/44d51880-26aa-495d-a872-c5f1cbd7ec64#media-blob-url=true&id=4f23a590-ebd7-4785-8df8-7645570f09d8&collection=contentId-2892235204&contextId=2892235204&mimeType=image%2Fpng&name=image-20250304-152734.png&size=45432&width=344&height=274&alt=image-20250304-152734.png)|Open image-20250304-161252.png<br><br>![image-20250304-161252.png](blob:https://wegomushi.atlassian.net/73327eb5-b3d1-4076-8483-59ea6605f7d8#media-blob-url=true&id=7a92dd1e-7569-46a6-bc45-8e0e01965282&collection=contentId-2892235204&contextId=2892235204&mimeType=image%2Fpng&name=image-20250304-161252.png&size=48518&width=336&height=273&alt=image-20250304-161252.png)|Open image-20250304-161033.png<br><br>![image-20250304-161033.png](blob:https://wegomushi.atlassian.net/c48d2623-7962-4482-94eb-cddb90ea86e6#media-blob-url=true&id=e9252732-92b2-48e9-a10e-ce850726a1be&collection=contentId-2892235204&contextId=2892235204&mimeType=image%2Fpng&name=image-20250304-161033.png&size=46825&width=334&height=316&alt=image-20250304-161033.png)|Open image-20250304-161337.png<br><br>![image-20250304-161337.png](blob:https://wegomushi.atlassian.net/7302e6d3-315a-47b4-95a9-84cf94227c36#media-blob-url=true&id=df184185-95d7-483c-a67e-e34c61f4262f&collection=contentId-2892235204&contextId=2892235204&mimeType=image%2Fpng&name=image-20250304-161337.png&size=52676&width=339&height=314&alt=image-20250304-161337.png)|Open image-20250304-160848.png<br><br>![image-20250304-160848.png](blob:https://wegomushi.atlassian.net/e4f64794-928d-439e-a4e2-bec1db0d8c21#media-blob-url=true&id=2156dc8b-aa59-4d76-80a8-671a54769235&collection=contentId-2892235204&contextId=2892235204&mimeType=image%2Fpng&name=image-20250304-160848.png&size=157365&width=341&height=740&alt=image-20250304-160848.png)|Open image-20250304-160935.png<br><br>![image-20250304-160935.png](blob:https://wegomushi.atlassian.net/6d53cd8a-8caa-4e1e-aa03-a50e7d0d87c7#media-blob-url=true&id=cc6dae92-5e39-49f9-9fe0-cfb0f362bf00&collection=contentId-2892235204&contextId=2892235204&mimeType=image%2Fpng&name=image-20250304-160935.png&size=154907&width=347&height=739&alt=image-20250304-160935.png)||
|trigger condition|view|click|click|click|click|click|click||
|event.value|- booking_ref<br>    <br>- ==# passenger==<br>    <br>- total legs<br>    <br>- # leg with available seat selection|- segment_id<br>    <br>- depart/return flight||- segment_id<br>    <br>- depart/return flight|- booking_ref<br>    <br>- # passenger<br>    <br>- total legs<br>    <br>- # leg with **selected** seats  <br>    # leg with **available** seat selection  <br>    # **selected** seats  <br>    # total **available** seats<br>    <br>- ====total seat price====||- booking_ref<br>    <br>- # passenger<br>    <br>- total legs<br>    <br>- ==# leg with selected seats==<br>    <br>- ==# leg with available seat selection==  <br>    ==# selected seats==  <br>    ==# total available seats==||
||   |   |   |   |   |   |   ||
|event.action|==view_seatmap==|click_seat|select_seat|unselect_seat|remove_seat|exit_seatmap|skip_seat|==error_quicket==|
|screenshot|Open image-20250304-152653.png<br><br>![image-20250304-152653.png](blob:https://wegomushi.atlassian.net/b7648e01-1d9d-4861-bb12-52d51bb34dc7#media-blob-url=true&id=2d05df18-b441-4108-8618-f1a9927f7d04&collection=contentId-2892235204&contextId=2892235204&mimeType=image%2Fpng&name=image-20250304-152653.png&size=123548&width=340&height=734&alt=image-20250304-152653.png)|Open image-20250304-153124.png<br><br>![image-20250304-153124.png](blob:https://wegomushi.atlassian.net/d72d278f-52d3-4e2e-8f2e-defba66962cd#media-blob-url=true&id=a00b7f31-04f7-49ea-a42c-778f71d8094c&collection=contentId-2892235204&contextId=2892235204&mimeType=image%2Fpng&name=image-20250304-153124.png&size=160147&width=348&height=737&alt=image-20250304-153124.png)|Open image-20250304-153738.png<br><br>![image-20250304-153738.png](blob:https://wegomushi.atlassian.net/645e1bb2-8a30-4b9e-8eea-d6601a43d730#media-blob-url=true&id=75906936-e253-4d10-86a8-035874b3b8ec&collection=contentId-2892235204&contextId=2892235204&mimeType=image%2Fpng&name=image-20250304-153738.png&size=174864&width=344&height=737&alt=image-20250304-153738.png)|Open image-20250304-153811.png<br><br>![image-20250304-153811.png](blob:https://wegomushi.atlassian.net/9f9b1e65-014d-4d45-b6ef-bafd93fae7cb#media-blob-url=true&id=cd750081-828e-4c59-8181-cf19eea8bf51&collection=contentId-2892235204&contextId=2892235204&mimeType=image%2Fpng&name=image-20250304-153811.png&size=170454&width=343&height=739&alt=image-20250304-153811.png)|Open image-20250304-153841.png<br><br>![image-20250304-153841.png](blob:https://wegomushi.atlassian.net/7af83ede-2420-43c5-af41-dead70958874#media-blob-url=true&id=c137e8d1-210e-4f7d-985f-0d2ef8b6fa19&collection=contentId-2892235204&contextId=2892235204&mimeType=image%2Fpng&name=image-20250304-153841.png&size=164826&width=343&height=739&alt=image-20250304-153841.png)|Open image-20250304-154502.png<br><br>![image-20250304-154502.png](blob:https://wegomushi.atlassian.net/535d1762-6017-434b-82f2-e6fb7b7458b4#media-blob-url=true&id=bd399ff5-56c4-458b-b078-1cbfed18122d&collection=contentId-2892235204&contextId=2892235204&mimeType=image%2Fpng&name=image-20250304-154502.png&size=169609&width=344&height=741&alt=image-20250304-154502.png)|Open image-20250304-160600.png<br><br>![image-20250304-160600.png](blob:https://wegomushi.atlassian.net/29cba44e-8260-45d4-9f03-ad964fe274bf#media-blob-url=true&id=1296c879-b5f2-479c-b7ad-8098ffb2542e&collection=contentId-2892235204&contextId=2892235204&mimeType=image%2Fpng&name=image-20250304-160600.png&size=174038&width=343&height=738&alt=image-20250304-160600.png)|Open image-20250327-044455.png<br><br>![image-20250327-044455.png](blob:https://wegomushi.atlassian.net/a851f7ef-a521-4e28-aa81-c7c2041f6867#media-blob-url=true&id=33768ebe-0fe6-419a-84a2-b9d3eae3cb42&collection=contentId-2892235204&contextId=2892235204&mimeType=image%2Fpng&name=image-20250327-044455.png&size=64901&width=321&height=665&alt=image-20250327-044455.png)|
|trigger condition|view|click|click|click|click|click|click|view|
|event.value|- segment_id<br>    <br>- passenger_id<br>    <br>- depart/return flight<br>    <br>- # of available **standard** seats<br>    <br>- # of available extra **legroom** seats<br>    <br>- # of total available seats|- segment_id<br>    <br>- passenger_id<br>    <br>- depart/return flight<br>    <br>- seat_number<br>    <br>- seat_price<br>    <br>- currency<br>    <br>- seat_price_usd<br>    <br>- seat_category (standard/legroom)<br>    <br>- ==seat_passenger_type==<br>    <br>- passenger_type|- segment_id<br>    <br>- passenger_id<br>    <br>- depart/return flight<br>    <br>- seat_number<br>    <br>- seat_price<br>    <br>- currency<br>    <br>- seat_price_usd<br>    <br>- seat_category (standard/legroom)<br>    <br>- seat_passenger_type<br>    <br>- passenger_type|- segment_id<br>    <br>- passenger_id<br>    <br>- depart/return flight<br>    <br>- seat_number<br>    <br>- seat_price<br>    <br>- currency<br>    <br>- seat_price_usd<br>    <br>- seat_category (standard/legroom)<br>    <br>- seat_passenger_type<br>    <br>- passenger_type|- segment_id<br>    <br>- passenger_id<br>    <br>- depart/return flight<br>    <br>- seat_number<br>    <br>- seat_price<br>    <br>- currency<br>    <br>- seat_price_usd<br>    <br>- seat_category (standard/legroom)<br>    <br>- seat_passenger_type<br>    <br>- passenger_type|- segment_id<br>    <br>- passenger_id<br>    <br>- depart/return flight|- segment_id<br>    <br>- passenger_id<br>    <br>- depart/return flight|- segment_id<br>    <br>- passenger_id<br>    <br>- depart/return flight<br>    <br>- error reason = quicket error response (e.g. schedule not found)|

## Phase Summary

- Phase 1: Seat selection during booking, pricing configuration in CMS, back office tool to support seat ==cancellation==/change
    
- Phase 2: Seat selection in post booking, support seat cancellation/change in manage my booking
    
- Phase 3: Upsell opportunities (promote premium seats with added benefits like extra legroom, early boarding, or better locations)
    

## User Stories Phase 1

[![](https://developers.google.com/drive/images/drive_icon.png)https://drive.google.com/file/d/1mo4A82WXGgn27HLHzXP0R9EqyZ44KY6k/view?usp=sharing](https://drive.google.com/file/d/1mo4A82WXGgn27HLHzXP0R9EqyZ44KY6k/view?usp=sharing)Connect your Google account

- **As a user**, I want to choose my seat during flight booking to ensure comfort and convenience
    
- **As a pricing manager**, I want to optimize seat pricing based on certain breakdowns
    
- **As a CS**, I can support customer in cancelling/changing their seat preferences
    

## Functional Requirement Phase 1

**High Level Requirement**

1. Display seat maps with real-time availability based on the provider data
    
2. Develop pricing logic that is configured via CMS (Pennyworth)
    
3. Display selected seat details in Back Office tool, enable CS to process cancellation/change
    

### Front-End Requirements (Booking Flow)

1. After filling passenger details, display seat availability for each leg
    
    - Hide seat selection if none of the legs have seat selection)
        
2. Users can select seats per pax and per leg (using Quicket Seatmap UI)
    
    - User see 3 different seat colors: Standard (Blue), Extra Leg room (Green), Unavailable (darker color)
        
        - Show Legend: Standard (Blue), Extra Leg room (Green)
            
    - User can see the seat price before VAT (For fare family that already includes seat selection, user should not be charged extra cost)
        
    - Users can skip seat selection for certain leg or certain passenger
        
    - Users can see the summary of selected seat and confirm (or edit again)
        
    - After confirmation, if seat is not available, user will be informed to either change seat or proceed without seat selection
        
3. User can see the total seat price after VAT (and the breakdown) in price summary & payment
    
4. User can see the selected seat in booking confirmation page, email confirmation, and booking history
    

### Back-End Requirements

1. Store list of provider with seat selection (to help FE in deciding to show/not show seat selection per leg)
    
2. Integrate provider API to fetch real-time seat availability and price
    
    - Ensure the data structure returned to FE is similar to Quicket Seatmap structure
        
    - Ensure real-time updates for changes in seat policies
        
3. Pricing logic to markup base seat price, configured via Pennyworth
    
    - Some airlines may provide free seat (e.g. Full Service Carriers), in this we won’t add markup price.
        
    - [MVP] Breakdown by POS, Integration, Carrier
        
    - [Next phase] Breakdown by trip category (domestic/international), passenger type, cabins, iPCC, trip type, locale, schedule date
        
4. Book selected seat per leg per pax to provider
    
5. Update seat booking status in the ticket (success / fail / partially fail = flight success, but seat fail)
    
    - Send notification to CS if seat booking failed after payment (Note: failure messages must be clear so that the CS team understands the reason, e.g. failure because the selected seat was unavailable.)
        
6. ==Enable AB test between baseline (no seat selection) and variant with seat selection==
    

### ==Post-Booking CX - Manage My Account==

1. @khaled.elkalla to fill this in.
    

### ==CS & MO Tool Requirements==

CS team needs to support customers that booked seats in various cases. The below requirements are for the cases that may rise and the information needed for the CS team to be able to provide proper support.

**==Use Cases==**

|   |   |   |
|---|---|---|
|**As a**|**I want to**|**So that**|
|As a CS agent|I want to view the selected seats.|So that I have the seat number information and can assist the customers with their selected seats|
|As a CS agent|I want to view the basic information of the customer that purchased a seat. Customer first name, last name, type (adult/child), PNR, Segment).|So that I can assist them with any request from their end|
|As a CS agent|I want to view the selected seat status|So that I can know if it is successfully booked or if it has failed|
|As a CS agent|I want to see the price of the seat that the customer purchased|So that I can know how much the seat costs when a customer asks|
|As a CS agent|I want to see the seat category.|So that I can know if the customer paid an amount for which type of seat.|
|As a CS agent|I want to receive a notification when a seat purchase fails|So that I can try to book it again manually and provide the service to the customer|
|As a CS agent|I want to see the price of the seat that Wego paid to the vendor.|So that I can know how much we were supposed to make and rebook a seat to the customer while making the same profit for Wego.|
|As a CS agent|I want to see the price breakdown in the current price breakdown details.|So that I can know the breakdown of the total price paid.|
|As a CS agent|I want to be able to remove a selected seat from showing in the Add-ons.|So that if I have to refund a customer with a successfully selected seat, I can make sure that future agents know that the customer no longer has a selected seat from our end.|
|As a CS agent|I want to view selected seats history|So that there is no confusion between myself and the customer if they call and ask questions about the selected seats|

**Requirements**

Sample Booking: [https://backoffice.wego.net/flights/bookings/v2/WFZV33MCTH624](https://backoffice.wego.net/flights/bookings/v2/WFZV33MCTH624 "https://backoffice.wego.net/flights/bookings/v2/WFZV33MCTH624")

1. Introduce a new section under “Add ons” that will display the Seat Selection.
    
2. New section will be above “Insurance” (if found).
    
3. Items to be displayed
    
    1. Tick box
        
    2. ==Passenger Title==
        
    3. Passenger Type
        
        1. Adult
            
        2. Child
            
        3. Infant
            
    4. Passenger First Name
        
    5. Passenger Last Name
        
    6. ==Flight PNR==
        
    7. Flight Segment
        
    8. ==Selected Seat Number==
        
        1. This NEEDS to be shown whether the seat is confirmed or failed so that the CS team can re-book the seat for the customer if it fails.
            
    9. Selected Seat Category
        
        1. Standard Seat
            
        2. Extra Legroom
            
    10. Selected Seat Status
        
        1. Success - Seat selection is confirmed.
            
        2. Failed - Seat selection failed and needs action from CS side.
            
        3. Pending - API response is unavailable and the confirmation of the seat is stuck somewhere.
            
        4. Refunded - Seat price successfully refunded to customer.
            
        5. Refund Failed - Initiated a refund but the refund failed.
            
        6. Manual Refund - Had to manually refund the customer from the payment gateway since the refund CTA failed to do it automatically.
            
    11. Selected Seat Price
        
    12. ======Selected Seat Payment Status======
        
        1. ==Authorized - Payment is authorized but is yet to be captured by Wego.==
            
        2. ==Captured - Payment is captured by Wego.==
            
        3. ==Failed - Payment is unsuccessful.==
            
        4. ==Pending - Payment is pending authorization.==
            
4. ==New section will be sorted by the Flight Segment names.==
    
5. Sync CTA - ==When the CS modifies anything with regard to the seats==, then the sync will be used to be able to show the latest status from the airline. Clicking sync CTA will refresh all selected seats within the booking.
    
6. Refund CTA - Will be used to refund the customer in the following cases. Need to use the Tick Box to enable this CTA to choose the exact customers that will be refunded. Refund will trigger automatically through the same payment method the customer used for the booking.
    
    1. Eligibility Criteria
        
        1. Single Passenger: Seat selection failed and the seat is no longer available. CS reached out to the customer and they ==do not want another seat.==
            
        2. Multiple Passengers: Seat selection failed and the seat is no longer available. CS reached out to the customer and they do not want another seat and they want to refund all seats because they are no longer sitting together.
            
            1. CS CANNOT cancel a seat once the booking is confirmed. If the seat selection fails for one member within a group and we end up refunding EVERYONE. The ones that their seats were successfully booked, will keep the same seats on the system and will be refunded the money.
                
            2. In the event that we do refund customers for the above mentioned cases, Wego will still be charged for the selected seats because they are non-refundable.
                
    2. Clicking the “Refund CTA” to refund a customer will trigger a confirmation that will display the total amount that will be refunded.
        
        1. Two CTAs to show
            
            1. Confirm Refund - Will trigger the refund process.
                
            2. Cancel - Will close the dialog and will not trigger the refund.
                
    3. Clicking the disabled “Refund CTA” will trigger a notification that the CS need to select a passenger first.
        
7. ==When a customer selects a seat and pays for it but the seat fails to reflect in the system, this will result in an email being triggered to the CS BO BOWF team.==
    
8. Pricing Display
    
    1. Show in “Price Details” section.
        
        1. Show in the section that has “Total Booking Fee”
            
        2. Show above “Total Booking Fee”
            
        3. Show the total amount of seats selected for all legs and all passengers.
            
        4. Title should be “Total Seats Selected”
            
        5. Open image-20250302-101224.png
            
            ![image-20250302-101224.png](blob:https://wegomushi.atlassian.net/fdfdf916-0631-45d2-8035-f134df32c43f#media-blob-url=true&id=759e192d-2b36-4b8b-988b-01be3977eb74&collection=contentId-2892235204&contextId=2892235204&mimeType=image%2Fpng&name=image-20250302-101224.png&size=85333&width=1373&height=798&alt=image-20250302-101224.png)
            
    2. Show in “Payments” section.
        
        6. Show in the table.
            
        7. Breakdown Addons Total Price to show Insurance and Seat Selection.
            
            1. Header to be “Addons” and it will not have a price next to it.
                
            2. Beneath the header there will be the following with its respective price:
                
                1. Total Seats Selected
                    
                2. Insurance
                    
                3. Open image-20250302-101823.png
                    
                    ![image-20250302-101823.png](blob:https://wegomushi.atlassian.net/f2a5de68-1d75-4762-86c7-858cae9892b4#media-blob-url=true&id=421a5d7b-20be-478d-b8f5-fd57b58a927f&collection=contentId-2892235204&contextId=2892235204&mimeType=image%2Fpng&name=image-20250302-101823.png&size=61437&width=1574&height=594&alt=image-20250302-101823.png)
                    
9. ==FAQs==
    
    1. Are seats refundable?
        
        1. No. Once you select a seat and pay for it, the seat is no longer refundable.
            
    2. Can I finish my booking and come back later to select a seat?
        
        2. This feature is coming soon but for now, if you skip the seat selection and book your flight, a random seat will be assigned to you upon checking in. You can opt for purchasing the seat directly from the airline later.
            
    3. ==After I have selected a seat and paid for it, can I change it?==
        
        1. NEED ANSWER
            
    4. If my flight is canceled, would my seats be refundable at that time?
        
        2. Each airline has its own cancelation policy.
            
            1. Flynas: Yes, you receive the full amount paid for your seat along with your flight as credit. The credit amount will expire after 1 year.
                
10. ==If available seat price is higher than initial seat price, then (where applicable) we will send the customer a payment link with the additional amount and book their new seat for them. Otherwise, we will process a refund.==
    

### Tracking Requirements

1. Booking flow:
    
    1. # view seat selection, # BoW click with view seat selection, # booking with view seat selection
        
    2. # click seat selection, # BoW click with view seat selection, # booking with click seat selection
        
    3. # purchased seat selection, # BoW click with selected seat selection, # booking with selected seat selection
        
    4. # skip seat selection, # BoW click with skip seat selection, # booking with skip seat selection
        
    5. # of times called Quicket
        
2. Pricing & sales:
    
    6. gross revenue
        
    7. contribution margin
        
    8. total base seat price
        
    9. total seat price after markup before VAT
        
    10. total seat VAT
        
    11. total seat price after markup and VAT
        
3. Post booking:
    
    1. # of seat cancellations
        
    2. # of failed seat booking (due to inventory supplier unavailable/not yet integrated/no response/error)
        
    3. # of successful seat booking
        

**Data structure**

- seat is stored at segment level (Hierarchy: Booking > Leg > seat)
    
- seat as a separate product item and revenue item to flights
    

## Non-Functional Requirements

- Latency: seat selection should load within 2 seconds (TBC)
    
- Scalability: Handle concurrent seat selection requests during peak times (RPS up to xx)
    
- Reliability: Ensure 99% uptime for seat-related features.
    
- Error states: track various error reasons
    
- Compatibility: since all suppliers treat seats differently, integration framework will have to standardize dealing with all suppliers in flow of offering ancillaries
    
    - [Integration Framework](https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2078638156 "https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2078638156")
        
        - (TBC) - If FareRule has seats included boolean
            
        - Search/Revalidation - Add seats element
            
        - Booking/Validate Booking - Add seats element
            
        - Ticketing - Add seats element
            
        - Cancellation - (non refundable)
            
    - Ability for WegoPro to also consume service requesting & booking a seat (pricing, etc)
        
- Extensibility
    
    - Extend to other ancillaries a.k.a Special Service Request
        
- Testability
    
    - Unit testing
        
    - Automated end-to-end testing for all flows
        

## Risks and Mitigations

1. Risk: Airline APIs may fail or provide inconsistent seat data.  
    Mitigation: track number of failures or inconsistent data
    
2. Risk: Users may be unclear about seat features or charges.  
    Mitigation: Provide clear descriptions and tooltips for seat options.
    
3. Risk: Last-minute changes may not sync with airline systems.  
    Mitigation: Notify users of airline cut-off times.
    

## **Timeline Phase 1 (TBC)**

|   |   |
|---|---|
|Milestone|Target Date|
|Requirements Finalized|31 December, 2025|
|Design Completion|Jan 2025|
|Development Start|Jan 2025|
|AB Testing Start|Feb 2025|
|Launch|March 2025|

## Competitor Research

Competitor Analysis by UX Research:[![](https://developers.google.com/drive/images/drive_icon.png)https://docs.google.com/presentation/d/1rv4kIsV56sF21ArvkQPk88hHNSE4DE0dJbtmnzvUOcE/edit#slide=id.g1aecf2e90d3_0_204](https://docs.google.com/presentation/d/1rv4kIsV56sF21ArvkQPk88hHNSE4DE0dJbtmnzvUOcE/edit#slide=id.g1aecf2e90d3_0_204)Connect your Google account

Prior Attempt (2022):[![](https://static.figma.com/app/icon/1/favicon.ico)https://www.figma.com/design/Ku3Kv5jSCe2lejghfd7VJy/%5BAndroid%5D-Flights?node-id=10116-126867&node-type=canvas&t=tK2vu2id9dM9X0p4-0](https://www.figma.com/design/Ku3Kv5jSCe2lejghfd7VJy/%5BAndroid%5D-Flights?node-id=10116-126867&node-type=canvas&t=tK2vu2id9dM9X0p4-0)Connect your Figma account

Traveloka

|   |   |   |   |
|---|---|---|---|
|**Seat Entry Point**|**Seat Availability per Leg**|**Seat Selection UI**|**Seat Confirmation**|
|Open IMG_6064.PNG<br><br>![IMG_6064.PNG](blob:https://wegomushi.atlassian.net/d2f08229-098f-4eb7-ae9f-a187157f0807#media-blob-url=true&id=bf9867d4-aee0-4459-af20-5d5c5a878120&collection=contentId-2892235204&contextId=2892235204&mimeType=image%2Fpng&name=IMG_6064.PNG&size=934491&width=1170&height=2532&alt=IMG_6064.PNG)|Open AD_4nXdzFmk_t7f7tlNeUPDkdWv7HpiHllBHv_EhM2NGbIcmlGGUdEjF-Jr_HaJtgd9iP9tijlghLh3WIJr-1W4qMazYPljJEeXdYa4yOhikDKx4UdM1HmFNq5jceELt-hVexZYCCB1tPQ?key=Ny-Fho-JJLezgrL_Se1qvDbA<br><br>![](blob:https://wegomushi.atlassian.net/41a92a31-98f2-4b09-8e9a-a1d78f427147#media-blob-url=true&id=61f09028-4fb0-45cb-883f-d5ca9d8e5627&collection=contentId-2892235204&contextId=2892235204&mimeType=image%2Fpng&name=AD_4nXdzFmk_t7f7tlNeUPDkdWv7HpiHllBHv_EhM2NGbIcmlGGUdEjF-Jr_HaJtgd9iP9tijlghLh3WIJr-1W4qMazYPljJEeXdYa4yOhikDKx4UdM1HmFNq5jceELt-hVexZYCCB1tPQ%3Fkey%3DNy-Fho-JJLezgrL_Se1qvDbA&size=114715&width=773&height=1600&alt=)|Open AD_4nXewPkPLod9McqyIJL0JU1a_7hB4C1JWWuwcwMHJuFj-lujWEy4gJHEdA7A3b51_6lSmDoJIF0Bt4_SqyjUJrUWNqse0QCrtSmRl2MdYAIk8-f-_szLgeg54cANbGWL5gV9fuKIXAA?key=Ny-Fho-JJLezgrL_Se1qvDbA<br><br>![](blob:https://wegomushi.atlassian.net/270886c8-e831-48e9-b4ec-993436038eaa#media-blob-url=true&id=dc87a02a-eb04-43d4-89e4-6dfea32aab82&collection=contentId-2892235204&contextId=2892235204&mimeType=image%2Fpng&name=AD_4nXewPkPLod9McqyIJL0JU1a_7hB4C1JWWuwcwMHJuFj-lujWEy4gJHEdA7A3b51_6lSmDoJIF0Bt4_SqyjUJrUWNqse0QCrtSmRl2MdYAIk8-f-_szLgeg54cANbGWL5gV9fuKIXAA%3Fkey%3DNy-Fho-JJLezgrL_Se1qvDbA&size=318026&width=788&height=1600&alt=)|Open AD_4nXdyvvUnMwhq6QI1n0duqY32J6v5vQIyVxRkXVqIPW0t5aGPqOtgC2JVBEKgH687Mi5HnVZGaioipL3I9LPDR_m0C4y3U8LXV50VNHMdRFzle1KR54kqK52U8t2L2aZwTXSR4a26Tg?key=Ny-Fho-JJLezgrL_Se1qvDbA<br><br>![](blob:https://wegomushi.atlassian.net/05263c2b-57e5-48e7-9bd0-b1a2684546a7#media-blob-url=true&id=208bc826-46b4-41b9-b122-28c486d6b3ea&collection=contentId-2892235204&contextId=2892235204&mimeType=image%2Fpng&name=AD_4nXdyvvUnMwhq6QI1n0duqY32J6v5vQIyVxRkXVqIPW0t5aGPqOtgC2JVBEKgH687Mi5HnVZGaioipL3I9LPDR_m0C4y3U8LXV50VNHMdRFzle1KR54kqK52U8t2L2aZwTXSR4a26Tg%3Fkey%3DNy-Fho-JJLezgrL_Se1qvDbA&size=160095&width=765&height=1600&alt=)|

## Questions

1. Is seat selection availability dependent on the flight's supplier?
    
    - Answer: yes, for example if user get Flynas from aggregator, then no seat selection (because we get seat selection directly from airline)
        
2. Post-booking cases
    
    - split booking?
        
    - change the schedule
        
    - change the seat selection
        
    - force reschedule, handled by Sabre?
        
    - airline cancel ticket, refund seat payment or not
        
3. Where to get quote for seat price?
    
4. [Phase 1.1] For carriers with multiple suppliers, if seat is unavailable in 1, do we do a fail over and shop another? Can we book a flight from 1 supplier, and seat from another?
    
5. How to optimize content selection after considering flight & seat cost?
    

## Appendix

|   |   |
|---|---|
|**Partner**|**Docs**|
|Quicket Seatmap|- All in one: [![](https://a.slack-edge.com/80588/marketing/img/meta/favicon-32.png)https://wego.slack.com/archives/C05NF3NQ5LJ/p1726646278793599](https://wego.slack.com/archives/C05NF3NQ5LJ/p1726646278793599)Connect your Slack account  <br>    <br>- Demo link: [Webpack App](https://quicket.io/react-lib-storybook/?path=/story/demo--basic) OR [![](https://dev.quicket.io/favicon.ico)React App](https://dev.quicket.io/)  <br>    <br>- Configure Color: [Theme editor](https://theme-editor.jets.kwiket.com/)  <br>    <br>- Integration docs: [![](https://github.githubassets.com/favicon.ico)https://github.com/Kwiket/jets-seatmap-react-lib-pub/blob/version-3/SEATMAP-INTEGRATION.md](https://github.com/Kwiket/jets-seatmap-react-lib-pub/blob/version-3/SEATMAP-INTEGRATION.md)Connect your Github account<br>    <br>- Call Quicket for seatmap based on carrier, flight number, o&d<br>    <br>- Insert Quicket’s UI into our checkout flow<br>    <br>    - iFrame [Integration docs](https://seatmaps.quicket.io/aircrafts/SEATMAP-INTEGRATION.htm#ios-integration "https://seatmaps.quicket.io/aircrafts/SEATMAP-INTEGRATION.htm#ios-integration")<br>        <br>    - React [Integration docs](https://github.com/Kwiket/jets-seatmap-react-lib-pub/blob/version-2/SEATMAP-INTEGRATION.md "https://github.com/Kwiket/jets-seatmap-react-lib-pub/blob/version-2/SEATMAP-INTEGRATION.md")<br>        <br>- Updated list of airlines with examples :[![](https://seatmaps.com/img/favicon16x16.png)Flyadeal Airbus A320-200 version flight](https://seatmaps.com/airlines/f3-flyadeal/airbus-a320/#255ea887b8bca36797426dfb35a809cc)<br>    <br>- (last updated Oct 2022) [Airline coverage and API Documentation link](https://docs.google.com/spreadsheets/d/1kXuJ5JT6u02M0nePZ_RcHQoKHEK8HCg1/edit?usp=sharing&ouid=114659634605101019515&rtpof=true&sd=true "https://docs.google.com/spreadsheets/d/1kXuJ5JT6u02M0nePZ_RcHQoKHEK8HCg1/edit?usp=sharing&ouid=114659634605101019515&rtpof=true&sd=true").<br>    <br><br>Q&A:<br><br>1. For multiple passengers, during seat selection, can users see the mapping between their name/ID and their selected seats?<br>    <br>    1. Answer: not supported by Seatmap, Wego need to build the component<br>        <br>2. It seems some of the seats are available to book only for adults. How are we going to handle this?<br>    <br>    1. Answer: supported by Seatmap<br>        <br>3. how to cater  serve child/infant seats?<br>    <br>    1. Answer: Partner will give info which seat is available for child/infant, and we will send this info to Seatmap<br>        <br>4. What are the customization provided by SeatMap?<br>    <br>    1. Answer: Wego can change color, while for icon: only can change exit door<br>        <br>5. Does Seatmap support grid view?<br>    <br>    1. Answer: Older version support, but newest version doesn’t|
|Airline/GDS|- [Flyadeal](https://wegomushi.atlassian.net/wiki/spaces/FT/pages/1994522729 "https://wegomushi.atlassian.net/wiki/spaces/FT/pages/1994522729")<br>    <br>    - Seats attachment, taxes, total<br>        <br>    - Search - Response will have a seatMapReference<br>        <br>    - Fare Quote - seatAssignment, seatMapCode, seatInformation, seatSet, cost (total, tax, adjustments, charges - SellerChargeable)<br>        <br>- [Flynas](https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2020999179 "https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2020999179")<br>    <br>- [Sabre (whole flow)](https://developer.sabre.com/guides/travel-agency "https://developer.sabre.com/guides/travel-agency")<br>    <br>    - Specs for [BFM Search](https://developer.sabre.com/docs/rest_apis/air/search/bargain_finder_max/versions/v500 "https://developer.sabre.com/docs/rest_apis/air/search/bargain_finder_max/versions/v500") & [BFM Revalidate](https://developer.sabre.com/docs/rest_apis/air/search/revalidate_itinerary/reference-documentation "https://developer.sabre.com/docs/rest_apis/air/search/revalidate_itinerary/reference-documentation")<br>        <br>    - [Current Sabre flow diagram](https://wegomushi.atlassian.net/wiki/spaces/FT/pages/303267936 "https://wegomushi.atlassian.net/wiki/spaces/FT/pages/303267936") & API list being used<br>        <br>    - FreeSeatSelection - boolean <br>        <br>    - Seat Preference - (min/max size of pitch, seat type)<br>        <br>    - Seat Amenity Type - value include ((middle seat free)\|(standard legroom)\|(below average legroom)\|(above average legroom)\|(skycouch)\|(recliner seat)\|(full flat seat)\|(full flat pod)\|(private suite)\|(angle flat seat)\|(cradle recliner)<br>        <br>    - Create PNR<br>        <br>    - Specify seat number<br>        <br>    - ? Details on Seat Preference<br>        <br>- [Travelport](https://support.travelport.com/webhelp/uapi/uAPI.htm#Air/Air_Shopping_and_Booking.htm?TocPath=Air%257CAir%2520Shopping%2520and%2520Booking%257C_____0 "https://support.travelport.com/webhelp/uapi/uAPI.htm#Air/Air_Shopping_and_Booking.htm?TocPath=Air%257CAir%2520Shopping%2520and%2520Booking%257C_____0")<br>    <br>    - Question: Is Indigo considered an “API connection” or “LCC Carrier connection”?|

|   |   |   |
|---|---|---|
|**Problem**|**Issue**|**Opportunity**|
|BOWF currently does not offer seat selection as part of the booking flow.|Currently, If a traveller wants to find out if their ticket includes baggage, or add baggage or book a specific seat number they need to contact our CS to do so manually.<br><br>The main issue comes from Low Cost Carriers in fact Flynas, Flyadeal, Jazeera and AirArabia group make up 86% of the issue.  Our primary focus is these 4 LCC's from our core markets (GCC).|- Offering seat selection enhance booking experience and grow our revenue per booking<br>    <br>- Speed to market in offering seat selection without having to rebuild each aircraft’s configuration by partnering with Quicket|
|BOWF cannot integrate with some airlines|Pegasus and AirAsia integrations to BoW are blocked since seat selection are compulsory elements|Scaling more airline integrations|

## User Stories Phase 2

- **As a user**, I want to choose my seat after booking a flight
    
- **As a user**, I want to modify my seat selection after booking if my preferences change.
    

|                               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| ----------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Feature**                   | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Post Booking                  | - User can chance/cancel selected seat in Manage My Booking ([Sabre post booking flow](https://developer.sabre.com/guides/travel-agency/workflows/air-extras-search-and-book "https://developer.sabre.com/guides/travel-agency/workflows/air-extras-search-and-book"))<br>    <br>- User can see seat offering in checkout page, my account, flight status, email, push notification (if they haven’t purchased seat)<br>    <br>- For booking the seat in post booking, does it have to be the same supplier/GDS?<br>    <br>- For post booking seat price, inventory availability & adding, which docs should I refer to? |
| Preselect Seat                | - In users my account, ask for seat preference so we can use it for pre-selection                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Insight during Seat Selection | - Legroom: Seats near the exit rows or at the bulkheads generally offer more legroom.<br>    <br>- Quietness: Seats towards the middle of the plane are typically quieter as they are farther from the engines. Consider bassinets<br>    <br>- Boarding/Deplaning: Seats closer to the front of the economy cabin generally make for quicker boarding and deplaning.                                                                                                                                                                                                                                                       |