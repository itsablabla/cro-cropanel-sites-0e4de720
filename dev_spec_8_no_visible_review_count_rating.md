# No visible review count/rating — dev spec
Site: allbirds.com · Priority 8 · High · Effort: Low (0.5-2 days)

## Problem
The product page shows a 'Reviews' section heading but no aggregate rating or review count near the price, so buyers cannot quickly validate quality and may abandon.

## Evidence (from the live site)
> H2 'Reviews for Anytime Ankle Sock' exists, but the body sample does not show a star rating or review count near the product title or price.

## Current state
h1: Anytime Ankle Sock; cta: Get Notified; notes: No rating or review count visible in the extracted content.

## Required change
h1: Anytime Ankle Sock; cta: Get Notified; notes: Add a star rating and review count (e.g., '★★★★★ 1,200+ reviews') directly under the product title or above the price.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add a star rating and review count (e.g., '★★★★★ 1,200+ reviews') directly under the product title or above the price.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_no_visible_review_count_rating` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
