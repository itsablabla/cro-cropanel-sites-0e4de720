# Path bypass via Get Notified — dev spec
Site: allbirds.com · Priority 6 · Urgent · Effort: Medium (2-5 days)

## Problem
The 'Get Notified' CTA on a product page that has a size selector and price visible creates a bypass that may lead users to abandon the purchase path if the product is actually in stock or available for pre-order.

## Evidence (from the live site)
> CTAs: 'Get Notified', 'Learn More', 'Sign Up'. Direct signals: size_selector: true, n_prices: 42 (on homepage, but product page likely has price).

## Current state
h1: Anytime Ankle Sock; cta: Get Notified; notes: Product page shows 'Get Notified' as a primary CTA, which may be appropriate for out-of-stock items, but if the product is available, it diverts from adding to cart.

## Required change
h1: Anytime Ankle Sock; cta: Add to Cart; notes: If the product is in stock, replace 'Get Notified' with 'Add to Cart' to keep users on the purchase path. If out of stock, ensure 'Get Notified' is clearly secondary and not the only CTA.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN If the product is in stock, replace 'Get Notified' with 'Add to Cart' to keep users on the purchase path. If out of stock, ensure 'Get Notified' is clearly secondary and not the only CTA.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_path_bypass_via_get_notified` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 118,817 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; 40 days

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
