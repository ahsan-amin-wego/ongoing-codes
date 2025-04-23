-  [![scroll](https://pf-emoji-service--cdn.us-east-1.prod.public.atl-paas.net/standard/ef8b0642-7523-4e13-9fd3-01b65648acf6/32x32/1f4dc.png) Changelog](https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2676654131/Seats#%F0%9F%93%9C-Changelog)
-  [![waving hand](https://pf-emoji-service--cdn.us-east-1.prod.public.atl-paas.net/standard/ef8b0642-7523-4e13-9fd3-01b65648acf6/32x32/1f44b.png) Intro](https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2676654131/Seats#%F0%9F%91%8B-Intro)
-  [![key](https://pf-emoji-service--cdn.us-east-1.prod.public.atl-paas.net/standard/ef8b0642-7523-4e13-9fd3-01b65648acf6/32x32/1f511.png) Key Lifecycle Phases](https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2676654131/Seats#%F0%9F%94%91-Key-Lifecycle-Phases)        
-  [![magnifying glass tilted right](https://pf-emoji-service--cdn.us-east-1.prod.public.atl-paas.net/standard/ef8b0642-7523-4e13-9fd3-01b65648acf6/32x32/1f50e.png) Providers Integration Framework Comparison](https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2676654131/Seats#%F0%9F%94%8E-Providers-Integration-Framework-Comparison)
    - [How to solve when seat selection is not available after payment](https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2676654131/Seats#How-to-solve-when-seat-selection-is-not-available-after-payment)
-  [![electric plug](https://pf-emoji-service--cdn.us-east-1.prod.public.atl-paas.net/standard/ef8b0642-7523-4e13-9fd3-01b65648acf6/32x32/1f50c.png) Integrations Overview](https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2676654131/Seats#%F0%9F%94%8C-Integrations-Overview)
-  [![airplane](https://pf-emoji-service--cdn.us-east-1.prod.public.atl-paas.net/standard/ef8b0642-7523-4e13-9fd3-01b65648acf6/32x32/2708.png) WegoFares Backend Overview](https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2676654131/Seats#%E2%9C%88%EF%B8%8F-WegoFares-Backend-Overview)
-  [![framed picture](https://pf-emoji-service--cdn.us-east-1.prod.public.atl-paas.net/standard/ef8b0642-7523-4e13-9fd3-01b65648acf6/32x32/1f5bc.png) Frontend Overview](https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2676654131/Seats#%F0%9F%96%BC%EF%B8%8F-Frontend-Overview)
    - [Questions](https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2676654131/Seats#Questions)

# ![scroll](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f4dc/path?scale=MDPI) Changelog

History

Doc Url: https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2676654131/Seats
# ![waving hand](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f44b/path?scale=MDPI) Intro

This is the high level / overview / TLDR document. It should give a good enough overview of how the seating workflow should work.

**This is doc is not indicative of the final implementation or tech specifications – Please refer to the Jira below**

![](https://wegomushi.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10507)

[FBOWINT-733: Quicket.io Seat Map & Seat Selection Implementation](https://wegomushi.atlassian.net/browse/WF-3710)

In Progress

Updated on 27 Feb 2025

PRD: Problem Statement & Objective BoW currently does not offer seat selection as part of the booking flow Offering seat selection can help grow our revenue per booking As a work around, our users are

![](https://wegomushi.atlassian.net/secure/attachment/10417/page_next.gif)Normal

Jira

Open preview

[[RFC] Seats Availability and Booking in BoW Flights](https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2707128322)

archived

- ![](https://wegomushi.atlassian.net/wiki/aa-avatar/603c5477ee11770070414612)
    

Owned by Liang JunUpdated on 2 Oct 2024

[RFC] Seats Availability and Booking in BoW Flights Summary: Implementation of Seats booking in BoW Flights Created Sep 23, 2024 PRD: :cross_mark:https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2676654131 Status: Work in progress | In-review | Approved | Obsolete Owner: @Liang Jun Contributors: Other stakeholders: Approvers: Background Seating

3

Confluence

Open preview

# ![key](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f511/path?scale=MDPI) Key Lifecycle Phases        

For seating – we will have **three key phases** that will be added to the existing workflow of booking.

This new phases should **map 1:1** to:

1. Integration framework functionality / connectors
    
2. Wego-fares APIs
    
3. Frontend API calls
    
    1. Quicket Component Props Requirements
        

|   |   |   |
|---|---|---|
|**Phase**|**Purpose**|**Jira**|
|**Get Seats Availability**|Retrieve the seat information for a particular itinerary.  <br>It will provide mapping for:<br><br>- of seat classes [business \| first \| premium eco \| eco \| etc]<br>    <br>- availability of seat<br>    <br>- price of seat|\|Type\|Key\|Summary\|Assignee\|Priority\|Status\|Updated\|<br>\|---\|---\|---\|---\|---\|---\|---\|<br>\|![Sub-task](https://wegomushi.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10516?size=medium)\|[FBOWINT-729](https://wegomushi.atlassian.net/browse/FBOWINT-729)\|CreateGetSeatRequest/ResponseModel\|![](https://secure.gravatar.com/avatar/4c77ebca6284b11355510a7959e54b27?d=https%3A%2F%2Favatar-management--avatars.us-west-2.prod.public.atl-paas.net%2Finitials%2FRK-1.png)<br><br>Rajesh Kanna\|![Normal](https://wegomushi.atlassian.net/secure/attachment/10417/page_next.gif)<br><br>Normal\|Closed\|4 Apr 2025, 07:39\|<br>\|![Sub-task](https://wegomushi.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10516?size=medium)\|[FBOWINT-728](https://wegomushi.atlassian.net/browse/FBOWINT-728)\|Create the GetSeatsAvailabilityView / Helpers\|![](https://secure.gravatar.com/avatar/4c77ebca6284b11355510a7959e54b27?d=https%3A%2F%2Favatar-management--avatars.us-west-2.prod.public.atl-paas.net%2Finitials%2FRK-1.png)<br><br>Rajesh Kanna\|![Normal](https://wegomushi.atlassian.net/secure/attachment/10417/page_next.gif)<br><br>Normal\|Closed\|4 Apr 2025, 07:39\|<br>\|![Sub-task](https://wegomushi.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10516?size=medium)\|[FBOWINT-727](https://wegomushi.atlassian.net/browse/FBOWINT-727)\|Create GetSeatsAvailabilityService / Client\|![](https://secure.gravatar.com/avatar/4c77ebca6284b11355510a7959e54b27?d=https%3A%2F%2Favatar-management--avatars.us-west-2.prod.public.atl-paas.net%2Finitials%2FRK-1.png)<br><br>Rajesh Kanna\|![Normal](https://wegomushi.atlassian.net/secure/attachment/10417/page_next.gif)<br><br>Normal\|Closed\|4 Apr 2025, 07:39\|<br>\|![Sub-task](https://wegomushi.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10516?size=medium)\|[FBOWINT-726](https://wegomushi.atlassian.net/browse/FBOWINT-726)\|Create GetSeatsAvailabilityResource\|![](https://avatar-management--avatars.us-west-2.prod.public.atl-paas.net/603c5477ee11770070414612/447a90fc-6622-4005-a529-0ba8b8934d84/48)<br><br>Liang Jun\|![Normal](https://wegomushi.atlassian.net/secure/attachment/10417/page_next.gif)<br><br>Normal\|Production\|4 Apr 2025, 07:39\|<br>\|![Sub-task](https://wegomushi.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10516?size=medium)\|[FBOWINT-725](https://wegomushi.atlassian.net/browse/FBOWINT-725)\|Create GetSeatsConnector\|![](https://secure.gravatar.com/avatar/d5a2fd1c4a90b91861f7da5cf7e3f6ca?d=https%3A%2F%2Favatar-management--avatars.us-west-2.prod.public.atl-paas.net%2Finitials%2FNG-4.png)<br><br>Nishant Gautam\|![Normal](https://wegomushi.atlassian.net/secure/attachment/10417/page_next.gif)<br><br>Normal\|Production\|21 Jan 2025, 21:03\|<br>\|![Sub-task](https://wegomushi.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10516?size=medium)\|[WF-4901](https://wegomushi.atlassian.net/browse/WF-4901)\|[not rdy] Create BookSeat models\|Unassigned\|![Normal](https://wegomushi.atlassian.net/secure/attachment/10417/page_next.gif)<br><br>Normal\|On Hold\|7 Mar 2025, 07:27\|<br>\|![Sub-task](https://wegomushi.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10516?size=medium)\|[FBOWINT-724](https://wegomushi.atlassian.net/browse/FBOWINT-724)\|Create GetSeatsAvailability models\|![](https://secure.gravatar.com/avatar/d5a2fd1c4a90b91861f7da5cf7e3f6ca?d=https%3A%2F%2Favatar-management--avatars.us-west-2.prod.public.atl-paas.net%2Finitials%2FNG-4.png)<br><br>Nishant Gautam\|![Normal](https://wegomushi.atlassian.net/secure/attachment/10417/page_next.gif)<br><br>Normal\|QA TESTING\|17 Jan 2025, 13:07\|<br>\|![Task](https://wegomushi.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10518?size=medium)\|[FBOWINT-722](https://wegomushi.atlassian.net/browse/FBOWINT-722)\|4. [Integration Framework] Add GetSeats\|![](https://secure.gravatar.com/avatar/d5a2fd1c4a90b91861f7da5cf7e3f6ca?d=https%3A%2F%2Favatar-management--avatars.us-west-2.prod.public.atl-paas.net%2Finitials%2FNG-4.png)<br><br>Nishant Gautam\|![Normal](https://wegomushi.atlassian.net/secure/attachment/10417/page_next.gif)<br><br>Normal\|QA TESTING\|5 Mar 2025, 15:27\|<br>\|![Task](https://wegomushi.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10518?size=medium)\|[FBOWINT-716](https://wegomushi.atlassian.net/browse/FBOWINT-716)\|3. [Backend] Get Seats Endpoint\|![](https://secure.gravatar.com/avatar/d5a2fd1c4a90b91861f7da5cf7e3f6ca?d=https%3A%2F%2Favatar-management--avatars.us-west-2.prod.public.atl-paas.net%2Finitials%2FNG-4.png)<br><br>Nishant Gautam\|![Normal](https://wegomushi.atlassian.net/secure/attachment/10417/page_next.gif)<br><br>Normal\|Production\|7 Mar 2025, 07:25\|<br><br>[<br><br>###### 9 items<br><br>](https://wegomushi.atlassian.net/issues/?jql=text%20~%20%22getseats*%22%20or%20summary%20~%20%22getseats*%22%20ORDER%20BY%20created%20DESC)<br><br>Synced 5 minutes ago|
|**Book Seat**|This reserves or books the seat for a Booking||
|**Cancel Seat**|This releases the seat for a booking.||

# ![magnifying glass tilted right](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f50e/path?scale=MDPI) Providers Integration Framework Comparison

Overview of the key components business logic with each provider.

|   |   |   |   |   |
|---|---|---|---|---|
|**Feature**|**Sabre**|**Flyadeal**|**Flynas**|**TravelPort**|
|**Compare**<br><br>Retrieves latest Provider Branded Fares – applies filters and pricing logics|![Check Mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/atlassian-check_mark/path?scale=MDPI)<br><br>Sabre `Revalidation`<br><br>v4 REST|![Check Mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/atlassian-check_mark/path?scale=MDPI)<br><br>Flyadeal `getQoute`|![Check Mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/atlassian-check_mark/path?scale=MDPI)<br><br>NavitaireXML `GetServiceBundleOffers`|![question mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/2753/path?scale=MDPI)|
|**Fare Rules**<br><br>Retrieve rules / conditions / restrictions for the selected fare.  <br>  <br>This might include Baggage allowance and penalties for example|![Check Mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/atlassian-check_mark/path?scale=MDPI)<br><br>Sabre `AirFareRules`|![Check Mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/atlassian-check_mark/path?scale=MDPI)<br><br>Get Fare rules from Airline service and phrase|![Check Mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/atlassian-check_mark/path?scale=MDPI)<br><br>Get Fare rules from Airline service and phrase|![question mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/2753/path?scale=MDPI)|
|**Dynamic Forms**<br><br>Retrieves any dynamic forms that are will be used by frontend|![Check Mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/atlassian-check_mark/path?scale=MDPI)<br><br>Default setup or no forms|![Check Mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/atlassian-check_mark/path?scale=MDPI)<br><br>Default setup or no forms|![Check Mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/atlassian-check_mark/path?scale=MDPI)<br><br>Default setup or no forms|![question mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/2753/path?scale=MDPI)|
|**Revalidate**<br><br>Checks if selected fare is still valid before booking|![Check Mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/atlassian-check_mark/path?scale=MDPI)<br><br>Sabre `Revalidation`<br><br>v4 REST|![Check Mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/atlassian-check_mark/path?scale=MDPI)<br><br>Flyadeal `getQoute`|![Check Mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/atlassian-check_mark/path?scale=MDPI)<br><br>NavitaireXML `GetItineraryPrice`|![question mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/2753/path?scale=MDPI)|
|**Booking**<br><br>Creates a “booking“ by recording the passenger info and itineraries.|![Check Mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/atlassian-check_mark/path?scale=MDPI)<br><br>Does nothing.<br><br>PNR created at ticketing after payment|![Check Mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/atlassian-check_mark/path?scale=MDPI)<br><br>Flyadeal `Trip`<br><br>Note: No gdsREF / PNR|![Check Mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/atlassian-check_mark/path?scale=MDPI)<br><br>Flynas:<br><br>1. `Sell`<br>    <br>2. `addInfant(sellSSR)`<br>    <br>3. `updateContact`<br>    <br><br>Note: No gdsREF / PNR|![question mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/2753/path?scale=MDPI)|
|**Get Seat Map / Availability** new|![construction](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f6a7/path?scale=MDPI)<br><br>- Via separate API<br>    <br>    - [**REST**](https://developer.sabre.com/docs/rest_apis/air/getseats "https://developer.sabre.com/docs/rest_apis/air/getseats") **(Get Seat 2.0)** ![backhand index pointing left](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f448/path?scale=MDPI)<br>        <br>        - Stateless API only need PNR<br>            <br>    - [**SOAP**](https://developer.sabre.com/docs/soap_apis/air/book/seat_map "https://developer.sabre.com/docs/soap_apis/air/book/seat_map") **(Seat Map 8.0.0)**<br>        <br>    - [**REST**](https://developer.sabre.com/docs/rest_apis/digital_connect/stateless_services/seats/v100/reference-documentation "https://developer.sabre.com/docs/rest_apis/digital_connect/stateless_services/seats/v100/reference-documentation") **(Stateless Seats API 1.2)**<br>        <br>- Need Segment Reference (id)<br>    <br>- Need Passenger Information<br>    <br>- Optional: Fare Component<br>    <br>- Optional: Passenger Loyalty|![question mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/2753/path?scale=MDPI)|![construction](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f6a7/path?scale=MDPI)<br><br>- Via separate API<br>    <br>    - **SOAP (GetSeatAvaibilityRequest)**<br>        <br>- Need Segment details<br>    <br>    - Dep Date<br>        <br>    - Origin<br>        <br>    - Destination<br>        <br>- Need PassengerID from getItinerary price Response<br>    <br>- Optional Seat Filters|![construction](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f6a7/path?scale=MDPI)<br><br>- Via separate API<br>    <br>    - [**REST**](https://support.travelport.com/webhelp/JSONAPIs/Airv11/Content/Air11/Seats/APIRef_SeatMap.htm?Highlight=seat "https://support.travelport.com/webhelp/JSONAPIs/Airv11/Content/Air11/Seats/APIRef_SeatMap.htm?Highlight=seat") **(Seat Map)**<br>        <br>- Perform after “revalidate“ (AirPrice?)<br>    <br>- Need AirPrice offerID<br>    <br>- Optional: AirPrice product identifier to filter product only<br>    <br>- Optional: AirPrice segment sequence (no.) to filter segment only|
|**Book Seat** new<br><br>Save seat selection to PassengerEntity<br><br>Recalculate Fare Price with Seat Pricing.|![construction](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f6a7/path?scale=MDPI)<br><br>- Via create PNR<br>    <br>    - Add AirSeat section and specify seat (& other params)<br>        <br>- Via Separate API<br>    <br>    - [REST](https://developer.sabre.com/docs/rest_apis/digital_connect/stateless_services/seats/v100/reference-documentation "https://developer.sabre.com/docs/rest_apis/digital_connect/stateless_services/seats/v100/reference-documentation") (Stateless Seats API 1.2)<br>        <br>        - Provide PNR and seat selection<br>            <br>    - [SOAP](https://developer.sabre.com/docs/soap_apis/management/itinerary/Passenger_Details "https://developer.sabre.com/docs/soap_apis/management/itinerary/Passenger_Details") (Passenger Details API) or (Passenger Records API mode = update)<br>        <br>        - Add AirSeat Section and modify PNR<br>            <br>- Technically for integration framework – sabre does nothing.|![question mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/2753/path?scale=MDPI)|![construction](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f6a7/path?scale=MDPI)<br><br>- Via Separate API<br>    <br>    - **SOAP (AssignSeatRequest)**<br>        <br>- Need Segment(s) seat details<br>    <br>    - Flight and seat designation<br>        <br>- PassengerIDs|![construction](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f6a7/path?scale=MDPI)<br><br>- Via Separate API<br>    <br>    - [**REST**](https://support.travelport.com/webhelp/JSONAPIs/Airv11/Content/Air11/Seats/APIRef_SeatBook.htm "https://support.travelport.com/webhelp/JSONAPIs/Airv11/Content/Air11/Seats/APIRef_SeatBook.htm") **(Seat Book)**<br>        <br>- Performed before “create PNR“ (commit workbench)<br>    <br>    - Called for each segment.<br>        <br>- Need CatalogOfferingIdentifier (from seatmap response)<br>    <br>- Need TravellerIdentifier (from AddTravellerResponse)|
|**UnBook Seat**<br><br>User unselects the seat? (or can cancel PNR and create new PNR)|||||
|**Fare Available**<br><br>This checks for availability before authorising the payment.<br><br>(Basically a revalidate)|![Check Mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/atlassian-check_mark/path?scale=MDPI)<br><br>Returns `true` by default|![Check Mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/atlassian-check_mark/path?scale=MDPI)<br><br>Return `true` by default<br><br>Performs Flyadeal Refresh (booking) Token|![Check Mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/atlassian-check_mark/path?scale=MDPI)<br><br>Return `true` by default<br><br>Performs Flynas Refresh (booking) Token|![question mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/2753/path?scale=MDPI)|
|**Ticketing (Book)**<br><br>This retrieves or updates PNR after booking is validated (fare available) and payment is made (captured).<br><br>new _**Might need to check if seat pricing , selection etc is valid**_|![construction](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f6a7/path?scale=MDPI)<br><br>Create PNR with AirSeat section<br><br>Seat availability will fail the PNR creation here|![construction](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f6a7/path?scale=MDPI)<br><br>Flyadeal:<br><br>1. `confirmPayment`<br>    <br>2. `commitBooking`<br>    <br>3. `getRecordLocator` – return PNR|![construction](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f6a7/path?scale=MDPI)<br><br>Flynas:<br><br>1. `AddPaymentToBooking`<br>    <br>2. `commitBooking` – Return PNR|![question mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/2753/path?scale=MDPI)|
|**Qct Get Booking Details (Validation)**<br><br>This is the final check with a provider to confirm a booking is valid and successful.<br><br>new _**Might need to check if seat pricing , selection etc is valid**_|![construction](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f6a7/path?scale=MDPI)<br><br>Builds e-tickets from previous steps data and validates e-tickets and pricing.|![construction](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f6a7/path?scale=MDPI)<br><br>Builds e-tickets from previous steps data and validates e-tickets and pricing.|![construction](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f6a7/path?scale=MDPI)<br><br>Builds e-tickets from previous steps data and validates e-tickets and pricing.|![question mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/2753/path?scale=MDPI)|
|**Cancel Seat** new|- Via separate API<br>    <br>    - [**SOAP**](https://developer.sabre.com/docs/soap_apis/air/book/Cancel_Air_Seat "https://developer.sabre.com/docs/soap_apis/air/book/Cancel_Air_Seat") **(Cancel Air Seat 2.1.0)**<br>        <br>- Requires GetReservationRq to be called first to set session  <br>      <br>    <br><br>![Warning](https://pf-emoji-service--cdn.us-east-1.prod.public.atl-paas.net/atlassian/productivityEmojis/exclamation-32px.png)<br><br>Not using PNR so not sure if possible|![question mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/2753/path?scale=MDPI)|- Via separate API to cancel SSR:<br>    <br>    - **SOAP (CancelSSR Request)**<br>        <br>- Provide segment / passenger details and SSR type to cancel<br>    <br>    - *SEAT or SEAT<br>        <br><br>![Warning](https://pf-emoji-service--cdn.us-east-1.prod.public.atl-paas.net/atlassian/productivityEmojis/exclamation-32px.png)<br><br>API docs is not complete|![question mark](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/2753/path?scale=MDPI)|

### How to solve when seat selection is not available after payment

For Sabre:

- Seat selection is added during Create PNR
    
    - PNR can fail if seat selection not available?
        

For others:

- Seat selection is done prior to Create PNR / Create Booking
    
    - It can fail before payment.
        

---

# ![electric plug](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f50c/path?scale=MDPI) Integrations Overview

|   |   |   |
|---|---|---|
|**Feature** Effort Level|**Implementation**|**Remarks**|
|**Get Seat Map / Availability** high|- Call respective provider API to retrieve seat map||
|**Book Seat** high|- Booking seat might be done via PNR creation or separate API<br>    <br>    - If separate API, return API results for Wegofares to process<br>        <br>    - If not just return 201.||
|**Ticketing** Medium|- PNR creation should include seat selection unless already done in previous step||
|**Cancel Seat** Medium|- Call provider to cancel a seat.<br>    <br>    - This is post booking||

---

# ![airplane](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/2708/path?scale=MDPI) WegoFares Backend Overview

- Calls Integration Framework
    
- Updates DB entities
    

|   |   |   |
|---|---|---|
|**Feature** effort level|**Implementation**|**Remarks**|
|**Get Seat Map / Availability** high|- API endpoint to retrieve seat map<br>    <br>- Calls integration framework to retrieve seat map|- Need to determine what info required to request for seat map<br>    <br>- Some providers might need custom params|
|**Book Seat** Medium|- API endpoint to select/book a seat for a given “segment“<br>    <br>- Calls integration framework to Book Seat<br>    <br>    - If success,<br>        <br>        - update Segment Entity with seat selection information<br>            <br>        - update PriceEntity with amounts*||
|**Price*** Medium|- Add new (segment_seat_id) to PriceEntity|- Need better way to identify segment linked price entities. Creating a seat selection entity just to link might be overkill.|
|**Ticketing** Medium|- Ticketing should retrieve seat selection if provided and add to ticketing call.|- Sabre might have race condition if two bookings select the same seat. Travel port doesn't have this problem as it books the seat before PNR creation|
|**Cancel Seat** medium|- API endpoint to remove seat||

---

# ![framed picture](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/1f5bc/path?scale=MDPI) Frontend Overview

- Calls backend for Seat Map and Seat Selection (Book Seat)
    
- Displays Seat Map in Quicket Component
    
- Seat Selection via Quicket Component
    
- Fare Display to include selected Seat Pricing
    

|   |   |   |
|---|---|---|
|**Feature** Effort level|**Implementation**|**Remarks**|
|**Get Seat Map / Availability** high|- Add component to house Quicket component<br>    <br>- Display component only if GetSeatMap API call successful<br>    <br>- Feed API call data to quicket component||
|**Book Seat** MEDium|- Seat Selection on Quicket component will trigger Book seat api call<br>    <br>    - Trigger on change<br>        <br>    - Trigger on save and submit|- Race conditions during seat selection?<br>    <br>- Need to “revalidate“ seatmap?|
|**Payment** Low|- Fare calculation to show seat pricing||
|**Ticketing** na|- No change||
|**Confirmation** High|- Show seat selection in confirm page<br>    <br>- Show seat selection in confirm email||
|**Cancel Seat** na|- Cancel seat not part of FE scope*||

## Questions

1. **What happen if Partner unable to confirm / reserve Seat?**
    
    1. Depends on partner workflow (when do we reserve the seat)
        
        1. Currently only Sabre is problematic because the seat reservation occurs during PNR creation
            
    2. For other LCC / TRAVELPORT, seat reservation should be is a separate API call.
        
        2. LCC should be able to confirm / reserve.
            
        3. Integrations will verify with more LCC partners
            
2. **Per Partner amenities availability**
    
    1. `canSelectSeat`-- not implemented etc
        
        1. default false in integration framework when calling `GetSeatAvailability`
            
3. **How to calculate or store Seat fare?**
    
    1. Check with product
        
    2. Concerns:
        
        1. Future pricing logic and margins
            
    3. Suggestions:
        
        1. Separate (same as VAS insurance)
            
        2. Allow independent pricing of seating
            
4. Are we storing seat map?
    
    4. no. integration provider log is enough
        
5. **SooW Seat Selection?????????????????????**
    
    1. Seat selection per Segment
        
6. **Post Booking**
    
    2. Not yet.
        
    3. Portal Seat Change? SC Task