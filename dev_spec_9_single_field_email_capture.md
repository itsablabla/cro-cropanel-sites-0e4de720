# Single-field email capture — dev spec
Site: allbirds.com · Priority 9 · High · Effort: Medium (2-5 days)

## Problem
The homepage email signup form asks only for an email address, which is the minimum viable field set, but the lack of a trust layer (e.g., privacy note, incentive) may reduce opt-in rates.

## Evidence (from the live site)
> The homepage has a form with 1 input, no labels, and submit button 'Sign Up'. The body sample shows 'Subscribe to our emails Sign Up'.

## Current state
h1: Wildly Comfortable. Super Natural.; cta: Sign Up; notes: Single email field, no visible privacy policy link or incentive (e.g., discount) near the form.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: Sign Up for 10% Off; notes: Add a privacy note ('We respect your inbox') and a clear incentive (e.g., 'Get 10% off your first order') to increase signup conversion.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add a privacy note ('We respect your inbox') and a clear incentive (e.g., 'Get 10% off your first order') to increase signup conversion.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_single_field_email_capture` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
