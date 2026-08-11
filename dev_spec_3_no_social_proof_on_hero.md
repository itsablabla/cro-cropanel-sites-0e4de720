# No social proof on hero — dev spec
Site: allbirds.com · Priority 3 · High · Effort: Medium (2-5 days)

## Problem
The hero lacks any trust signals (review count, rating, or press logos), so first-time visitors may hesitate to click through due to uncertainty about quality and fit.

## Evidence (from the live site)
> Hero H1: 'Wildly Comfortable. Super Natural.' with CTAs 'SHOP MEN' and 'SHOP WOMEN' but no review stars, count, or press mentions in the body sample.

## Current state
h1: Wildly Comfortable. Super Natural.; cta: SHOP MEN / SHOP WOMEN; notes: No social proof visible in hero section.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: SHOP MEN / SHOP WOMEN; notes: Add a line under the CTAs: 'Rated 4.6/5 from 50,000+ reviews' or a press logo strip (e.g., 'As seen in Vogue, GQ, Forbes').

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add a line under the CTAs: 'Rated 4.6/5 from 50,000+ reviews' or a press logo strip (e.g., 'As seen in Vogue, GQ, Forbes').
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_no_social_proof_on_hero` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
