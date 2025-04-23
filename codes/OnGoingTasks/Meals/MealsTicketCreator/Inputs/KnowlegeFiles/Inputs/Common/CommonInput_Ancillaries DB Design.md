Page URL: https://wegomushi.atlassian.net/wiki/spaces/FT/pages/3085074682/Ancillaries+DB+Design
## ✈️ Real-World Behaviour First: How Ancillaries Work

|   |   |   |
|---|---|---|
|Behavior|Who it Applies To|Granularity|
|**Seats**|Per passenger, per segment|🎯 Passenger + Segment|
|**Meals**|Often selected per segment, for each passenger|🎯 Passenger + Segment|
|**Baggage**|May apply across multiple segments (or specific ones)|⚠️ Sometimes segment-level, sometimes trip-level, Consider Sum of all ways ~|
|**WiFi ??**|May be per journey, not segment|Booking-level or passenger-level|

# Team Proposal

The proposed design structured ancillaries using `ancillaries`, `ancillary_prices`, `ancillary_margins` & `refund_items` table

==Ancillaries Table==

**Note:** ![warning](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/26a0/path?scale=MDPI) This table is no longer needed. Please refer to the next one. ![warning](https://wegomushi.atlassian.net/gateway/api/emoji/a7e53b72-ded0-45e3-8d7c-fd3573f46f1d/26a0/path?scale=MDPI)

`CREATE TABLE ancillaries ( id INT PRIMARY KEY AUTO_INCREMENT, ancillary_type ENUM('seat', 'meal', 'baggage') NOT NULL, booking_id INT NOT NULL, ancillary_margin_id INT, created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP, updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP, FOREIGN KEY (booking_id) REFERENCES bookings(id), FOREIGN KEY (ancillary_margin_id) REFERENCES ancillary_margins(id) );`

====Ancillary Table====

`CREATE TABLE ancillaries ( id INT PRIMARY KEY AUTO_INCREMENT, ancillary_type ENUM('seat', 'meal', 'baggage') NOT NULL, itinerary_id INT NOT NULL, ancillary_margin_id INT, segment_id INT NOT NULL, passenger_id INT NOT NULL, payment_status ENUM('pending', 'captured', 'confirmed', 'refunded') NOT NULL, status ENUM('selected', 'booked', 'failed', 'cancelled', 'refunded') NOT NULL, details JSON NOT NULL, -- its contain following info for seat: -- label -- position ENUM('window', 'aisle', 'middle'), -- description -- extraInfo: Store partner related details -- its contain following info for meal: -- meal_type ENUM('vegetarian', 'non-vegetarian', 'vegan', 'gluten-free', 'halal', 'kosher') NOT NULL, -- meal_description VARCHAR(255), -- its contain following info for baggage: -- baggage_type ENUM('carry-on', 'checked', 'oversized', 'fragile') NOT NULL, -- weight DECIMAL(10,2), created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP, updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP, booked_at TIMESTAMP DEFAULT NULL, failed_at TIMESTAMP DEFAULT NULL, cancelled_at TIMESTAMP DEFAULT NULL, refunded_at TIMESTAMP DEFAULT NULL, FOREIGN KEY (itinerary_id) REFERENCES itineraries(id), FOREIGN KEY (segment_id) REFERENCES segments(id), FOREIGN KEY (passenger_id) REFERENCES passengers(id), FOREIGN KEY (ancillary_margin_id) REFERENCES ancillary_margins(id) );`

Sample Seat details json

`{ "label": "6E", "position": "MIDDLE", "description": "Others", "extraInfo": {"6E": "Y", "femaleOnly": false} }`

==Ancillary Prices Table==

`CREATE TABLE ancillary_prices ( id INT PRIMARY KEY AUTO_INCREMENT, ancillary_id INT NOT NULL, -- Vendor Pricing. vendor_base_amount DECIMAL(15,3), vendor_tax_amount DECIMAL(15,3), vendor_currency_code VARCHAR(3), --prices table its called currency_code vendor_total_amount_usd DECIMAL(15,3), -- Booking ancillary Pricing base_amount DECIMAL(15,3), tax_amount DECIMAL(15,3), total_amount DECIMAL(15,3), --base_amount + tax_amount + margin_amount currency_code VARCHAR(3), --prices table its called user_currency_code total_amount_usd DECIMAL(15,3), --Margin amount margin_amount_usd DECIMAL(15,4), -- Other Details created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP, updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP, FOREIGN KEY (ancillary_id) REFERENCES ancillaries(id), );`

==Ancillary Margins Table:==

``CREATE TABLE `ancillary_margins` ( `id` bigint NOT NULL AUTO_INCREMENT, `ancillary_type` ENUM("seat", "meal" or "baggage") `pos` text NOT NULL, `airline_codes` text NOT NULL, `trip_types` varchar(255) NOT NULL, `rbd` text NOT NULL, `sale_from` datetime NOT NULL, `sale_by` datetime NOT NULL, `outbound_from` datetime NOT NULL, `outbound_by` datetime NOT NULL, `inbound_from` datetime NOT NULL, `inbound_by` datetime NOT NULL, `direct_services_only` boolean NOT NULL, `passenger_types` text NOT NULL, `device_types` varchar(255) NOT NULL, `wego_profile` text NOT NULL, `created_at` datetime NOT NULL, `updated_at` datetime NOT NULL, `cabins` varchar(255) DEFAULT '["*"]' NOT NULL, `ipccs` text NOT NULL, `enabled` boolean DEFAULT TRUE NOT NULL, `priority` int NOT NULL, `excluded_rbd` text, `trip_categories` varchar(255), `segment_counts` varchar(255), `included_routes` text, `excluded_routes` text, `ts_codes` text, `locales` varchar(255) DEFAULT '["*"]', `app_types` varchar(255) DEFAULT '["*"]', `booking_types` varchar(255) DEFAULT '["*"]', `wg_internal_campaign` varchar(255), `margin_details` JSON, PRIMARY KEY (`id`) ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;``

Sample `==margin_details==` JSON for seat:

`[ { "seatPosition": "WINDOW", "seatType": "EMERGENCY", "value": 10, "capAmount": 100, "useFeePercentage": true } ]`

Note: Meals and baggages can have fields like below in `margin_details`

`meal_type STRING, -- 'vegetarian', 'non-vegetarian', 'vegan', 'gluten-free', 'halal', 'kosher' baggage_type STRING, -- 'carry-on', 'checked', 'oversized', 'fragile'`

==Refund Items Table== (This is an **existing table** used for booking refunds)

``CREATE TABLE `refund_items` ( `id` bigint NOT NULL AUTO_INCREMENT, `item_type` enum('PNR','INSURANCE', 'ANCILLARY') COLLATE utf8_unicode_ci DEFAULT NULL, --Add new type in enum (ANCILLARY) `refund_id` bigint NOT NULL, `itinerary_id` bigint DEFAULT NULL, `insurance_id` bigint DEFAULT NULL, `ancillary_id` bigint DEFAULT NULL, --Added this column. #TODO: Erwin will confirm if this is sufficient to calculate the refund. `vendor_amount` decimal(15,3) DEFAULT NULL, `amount` decimal(15,3) DEFAULT NULL, `refund_amount` decimal(15,3) DEFAULT NULL, `refund_fee_amount` decimal(15,3) DEFAULT NULL, `user_refund_amount` decimal(15,3) DEFAULT NULL, `currency_code` varchar(3) COLLATE utf8_unicode_ci DEFAULT NULL, `charged_currency_code` varchar(4) COLLATE utf8_unicode_ci DEFAULT NULL, `charged_refund_amount` decimal(15,3) DEFAULT NULL, `requested_by` varchar(100) COLLATE utf8_unicode_ci DEFAULT NULL, `created_at` timestamp NULL DEFAULT NULL, `updated_at` timestamp NULL DEFAULT NULL, PRIMARY KEY (`id`), KEY `refund_item_refund_id_fk` (`refund_id`), KEY `refund_item_itinerary_id_fk` (`itinerary_id`), KEY `refund_item_insurance_id_fk` (`insurance_id`), CONSTRAINT `refund_item_insurance_id_fk` FOREIGN KEY (`insurance_id`) REFERENCES `insurances` (`id`), CONSTRAINT `refund_item_itinerary_id_fk` FOREIGN KEY (`itinerary_id`) REFERENCES `itineraries` (`id`), CONSTRAINT `refund_item_refund_id_fk` FOREIGN KEY (`refund_id`) REFERENCES `refunds` (`id`) FOREIGN KEY (ancillary_id) REFERENCES ancillaries(id) ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8_unicode_ci;``

Below is a proposal to track status changes (event log). This is an **existing table** used for bookings, and we plan to reuse it by incorporating ancillary-related changes as well. @Liang Jun will revisit this after discussing with the Data team.

==Booking Life Cycle Events Table==

Note: This table is no longer needed. We've added `booked_at`, `failed_at`, `cancelled_at`, and `refunded_at` columns to the ancillary table

``CREATE TABLE `booking_life_cycle_events` ( `id` BIGINT AUTO_INCREMENT PRIMARY KEY, `booking_id` BIGINT NOT NULL, `type` ENUM('booking', 'seat', 'meal', 'baggage') NOT NULL, --Added this column `ref_id` BIGINT NOT NULL, `event_type` VARCHAR(50) NOT NULL, `new_status` VARCHAR(50) NOT NULL, `created_at` TIMESTAMP DEFAULT CURRENT_TIMESTAMP, PRIMARY KEY (`id`), KEY `idx_booking_life_cycle_events_ref_event` (`ref_id`,`event_type`), KEY `idx_booking_life_cycle_events_compound` (`booking_id`,`ref_id`,`event_type`,`new_status`), CONSTRAINT `booking_life_cycle_events_booking_id_fk` FOREIGN KEY (`booking_id`) REFERENCES `bookings` (`id`) ON DELETE CASCADE ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3 COLLATE=utf8_unicode_ci;``
  
**Open Questions:**

==How to calculate the attachment rate?== @Liang Jun  
If we cancel the booking, ancillaries also get canceled, and we return ==any money related to the ancillary==. @Fredick Alvin Setiawan

how do we design the DB relation between booking and ancillaries table? 1 booking many ancillaries?@Erwin

can we have standarized `details` on ancillary_items?@Erwin

should we keep using vendor_ prefix for the price? to avoid using different terminology @Erwin

Audit log for ancillary - @ahsan.amin @Suleman Naeem