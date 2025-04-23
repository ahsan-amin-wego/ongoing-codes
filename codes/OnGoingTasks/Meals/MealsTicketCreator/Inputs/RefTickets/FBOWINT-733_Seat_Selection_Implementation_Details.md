# Jira Ticket Details: FBOWINT-733

**Key:** FBOWINT-733
**URL:** https://wegomushi.atlassian.net/browse/FBOWINT-733
**Summary:** Quicket.io Seat Map & Seat Selection Implementation
**Project:** Flight BoW Integrations (FBOWINT)
**Issue Type:** Epic
**Status:** In Progress
**Priority:** Normal
**Reporter:** Manoj Kumar Sundararajan (manoj@wego.com)
**Assignee:** Unassigned
**Created:** 2023-04-25T13:38:09.432+0800
**Updated:** 2025-02-27T14:19:09.567+0800
**Labels:** None

---

## Description

h2. PRD: [https://docs.google.com/document/d/1D2xjs_huz4CJLj65Cflqt050uZi7EvkHnqUe9P6a0Xo/edit?usp=sharing|https://docs.google.com/document/d/1D2xjs_huz4CJLj65Cflqt050uZi7EvkHnqUe9P6a0Xo/edit?usp=sharing|smart-link] 

h2. Problem Statement & Objective

* BoW currently does not offer seat selection as part of the booking flow
* Offering seat selection can help grow our revenue per booking 
* As a work around, our users are currently calling BoW CS to get their PNR (since they don't immediately receive it due to fare being optimised by Wenrix) so they can book seats and additional luggage directly with the airlines after booking with us
* Speed to market in offering seat selection without having to rebuild each aircraft's configuration by partnering with Quicket
* Quicket's seatmaps also include a 360 view of the cabin (depending on their airline and flight availability)

h2. Feature Breakdown: Functional

* *Seat selection*
** Wego to have the ability to configure quicket's colour scheme of seat map
** Call Quicket for seatmap based on carrier, flight number, o&d
** Insert Quicket's UI into our checkout flow
*** iFrame [Integration docs|https://seatmaps.quicket.io/aircrafts/SEATMAP-INTEGRATION.htm#ios-integration]
*** React [Integration docs|https://github.com/Kwiket/jets-seatmap-react-lib-pub/blob/version-2/SEATMAP-INTEGRATION.md]
** Seat availability
*** [Flyadeal|https://wegomushi.atlassian.net/wiki/spaces/FT/pages/1994522729/F3+API+Intro]
**** Seats attachment, taxes, total
**** Search - Response will have a seatMapReference
**** Fare Quote - seatAssignment, seatMapCode, seatInformation, seatSet, cost (total, tax, adjustments, charges - SellerChargeable)
*** [Flynas|https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2020999179/Onboarding+Flynas]
*** [Sabre (whole flow)|https://developer.sabre.com/guides/travel-agency]
**** Specs for [BFM Search|https://developer.sabre.com/docs/rest_apis/air/search/bargain_finder_max/versions/v500] & [BFM Revalidate|https://developer.sabre.com/docs/rest_apis/air/search/revalidate_itinerary/reference-documentation]
**** [Current Sabre flow diagram|https://wegomushi.atlassian.net/wiki/spaces/FT/pages/303267936/Sabre+API+Integration+Flow] & API list being used
**** FreeSeatSelection - boolean 
**** Seat Preference - (min/max size of pitch, seat type)
**** Seat Amenity Type - value include ((middle seat free)|(standard legroom)|(below average legroom)|(above average legroom)|(skycouch)|(recliner seat)|(full flat seat)|(full flat pod)|(private suite)|(angle flat seat)|(cradle recliner)
*** 
**** Create PNR
**** Specify seat number
**** ? Details on Seat Preference
*** [Travelport|https://support.travelport.com/webhelp/uapi/uAPI.htm#Air/Air_Shopping_and_Booking.htm?TocPath=Air%257CAir%2520Shopping%2520and%2520Booking%257C_____0]
** Preselect a seat if available (logic of finding the front most, aisle or window seat)
** If booking has children included, offer to users bassinet seats
** Take seat inventory availability from supplier, not Quicket
** Allow users to select a seat, and unselect a seat, at the same time updating total price to be paid
** View cost per seat type e.g. exit seat = $10; middle seat seat = $0
** Allow user to skip selecting seats per segment
** (TBC) If user did not select seats, add a reminder if the user is sure they don't want to select a seat (that can be configured for experimentation)
** Add seat selected in payments
** (TBC) Order of when the seat selection is showed e.g. before passenger details or after
** For multi-pax booking
*** (TBC) select all passenger's seats 
*** (TBC) not require user to select seats for all passengers e.g. Booking has 3 pax, only book seat for 1
** For Fare family
*** If fare family already includes seat selection, user should not be charged extra cost
** Sum of One Way & Virtual Interline
*** Ability to select seats per leg
** Booking confirmation page, booking history in my account,  reflects payment on 
** Payment to supplier includes
* (TBC) If seat inventory is unavailable
** For 1 pax booking THEN
*** For GDS
*** LCC Carrier
** For N pax booking AND seat unavailable < N THEN
*** For GDS
*** LCC Carrier
* *Pricing, Data & Tracking*
** *Pricing & Sourcing*
*** Ability to set a target margin per seat per leg
*** Pricing rule is added per "rule number"
*** Add in upfront commission & back end commission (Performance linked bonus)
*** Breakdown VAT component of markup/markdown, and VAT component of offering seat itself
*** CMS to decide which airlines, which integration type (provider) we will call for seats
** *Data*
*** Seat is stored at segment level, that rolls up to booking e.g. Booking has 3 legs, it's possible to have leg 1 to have seat selected, and not legs 2 & 3
*** Seat as a separate product item and revenue item to flights
*** Markup/markdown is calculated separately
*** VAT is calculated separately
** *Tracking*
*** Impressions
*** Users who have selected seat but not purchased
*** Users who selected skip e.g. Possible for user to select "skip" multiple times since we will offer seat selection per leg
*** Log when we call supplier and seat inventory unavailable/no response/error
*** # of times called Quicket
* *CS & BO*
** Per booking and per segment, reflect if user selected a seat, which seat number per flight, per leg
** Reflect breakdown in BO tool
** Seats are non-refundable in case of refund/change request
* *Experimentation:*
** Baseline: No seat
** Variant A: Seat selection


h2. Feature Breakdown: Non-Functional

* Error states
** Quicket - Cache all seat maps. Track their uptime before considering a plan C
** Flight Suppliers - if unavailable, elegantly skip seat selection and track when we have skipped, and error reasons
* Compatibility
** Since all suppliers treat seats differently, integration framework will have to standardise dealing with all suppliers in flow of offering ancillaries like seats
*** [Integration Framework|https://wegomushi.atlassian.net/wiki/spaces/FT/pages/2078638156/Integration+guidelines]
**** (TBC) - If FareRule has seats included boolean
**** Search/Revalidation - Add seats element
**** Booking/Validate Booking - Add seats element
**** Ticketing - Add seats element
**** Cancellation - (non refundable)
** Ability for WegoPro to also consume service requesting & booking a seat (pricing, etc)
* Response time & latency
** (TBC) Max loading time to user for 3 seconds
** Quicket's rich content may require CDN & caching
* Caching
** Quicket allows caching of content but inventory availability is still required real time
* Extensibility
** (TBC) For other ancillaries like luggage, meals, etc. (specific to airline SSR aka Special Service Request), have a single service
* Testability
** Unit testing
** Automated end-to-end testing for all flows



h2. Outstanding Questions

* Is seat selection per segment or per leg? e.g. connecting flight
* For connecting flights, what is the response structure for multiple segments?
* For carriers with multiple suppliers, if seat is unavailable in 1, do we do a fail over and shop another? Can we book a flight from 1 supplier, and seat from another?
* How do we deal with flights with stop over --- e.g. seat selection, pricing, etc.?
* what happens when seat is unavailable?
* what happens when seat error but flight confirmed? How about vice versa?
* can we reserve seat allocation first before while going through payment? Then release if user didn't go through after a certain time period?
* what happens with seat during Wenrix optimisation?
* where to get quote for seat price?
* for fare family, where to check if seat is included in selected FF?
* for post booking seat price, inventory availability & adding, which docs should I refer to?
* for booking the seat post booking, does it have to be the same supplier/GDS?
* (For Travelport) is Indigo considered "API connection" or "LCC Carrier connection"?


*Supporting Documents*:

* (last updated Oct 2022) [Airline coverage and API Documentation link|https://docs.google.com/spreadsheets/d/1kXuJ5JT6u02M0nePZ_RcHQoKHEK8HCg1/edit?usp=sharing&ouid=114659634605101019515&rtpof=true&sd=true]. 
* Updated list of airlines with examples:[https://seatmaps.com/airlines/f3-flyadeal/airbus-a320/#255ea887b8bca36797426dfb35a809cc|https://seatmaps.com/airlines/f3-flyadeal/airbus-a320/#255ea887b8bca36797426dfb35a809cc|smart-link] 

!image-20230425-054247.png|width=898,height=734!





*(TBC) Phase 2:*

* Post Booking flow
** [Sabre post booking flow|https://developer.sabre.com/guides/travel-agency/workflows/air-extras-search-and-book]
* Offering seat after booking in My account, flight status (home page), email, push notification
* Setup a reusable checkout page
* In users my account, ask for seat preference so we can use it for pre-selection
* Give helpful & value-adding insights a.k.a. "Captain Dean's Hacks"
** Legroom: Seats near the exit rows or at the bulkheads generally offer more legroom.
** Quietness: Seats towards the middle of the plane are typically quieter as they are farther from the engines. Consider bassinets
** Boarding/Deplaning: Seats closer to the front of the economy cabin generally make for quicker boarding and deplaning.
** e.g.
** !image-20240906-023521.png|width=721,height=298,alt="image-20240906-023521.png"!


*References*

* Quicket
** Theme editor (to change colour scheme of cabin) [https://theme-editor.jets.kwiket.com/|https://theme-editor.jets.kwiket.com/|smart-link] 
** Test query[https://seatmaps.quicket.io/aircrafts/test.htm|https://seatmaps.quicket.io/aircrafts/test.htm|smart-link] 
** Example 360 view of cabin [https://viewer.quicket.io/?image=https://files.sandbox.quicket.io/api/public/dl/3nkaAJ9d/AA_B787_8_d20748bdbe06179aa486ba0157b6d700_orig.jpg|https://viewer.quicket.io/?image=https://files.sandbox.quicket.io/api/public/dl/3nkaAJ9d/AA_B787_8_d20748bdbe06179aa486ba0157b6d700_orig.jpg|smart-link] 

---

## Attachments

*   `image-20230425-054247.png` (URL: https://wegomushi.atlassian.net/rest/api/2/attachment/content/72257)
*   `image-20240906-023521.png` (URL: https://wegomushi.atlassian.net/rest/api/2/attachment/content/87255)

*(Note: Comments are not included in this summary as they were not requested in the initial fetch)* 