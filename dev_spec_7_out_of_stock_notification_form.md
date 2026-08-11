# Out-of-stock notification form — dev spec
Site: allbirds.com · Priority 7 · High · Effort: Medium (2-5 days)

## Problem
The product page for Anytime Ankle Sock shows a 'Get Notified' CTA, which is a lead capture form, but the form's field set is unknown and may be too long, causing drop-off.

## Evidence (from the live site)
> The product page has a CTA 'Get Notified' and the body sample includes 'Get Notified' but no form details are visible in the crawl.

## Current state
h1: Anytime Ankle Sock; cta: Get Notified; notes: The form likely asks for email and possibly size, but the exact fields are not visible in the crawl. The lack of a trust layer (e.g., 'We'll notify you when back in stock') may reduce signups.

## Required change
h1: Anytime Ankle Sock; cta: Notify Me When Available; notes: Ensure the form only asks for email (and optionally size) and include a trust message like 'We'll email you the moment it's back in stock. No spam.'

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Ensure the form only asks for email (and optionally size) and include a trust message like 'We'll email you the moment it's back in stock. No spam.'
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_out_of_stock_notification_form` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
