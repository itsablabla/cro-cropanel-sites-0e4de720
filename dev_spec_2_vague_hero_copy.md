# Vague hero copy — dev spec
Site: allbirds.com · Priority 2 · High · Effort: Low (0.5-2 days)

## Problem
The hero headline 'Wildly Comfortable. Super Natural.' is abstract and doesn't directly address the visitor's intent to find comfortable, sustainable shoes, leaving them to infer the value proposition.

## Evidence (from the live site)
> H1: 'Wildly Comfortable. Super Natural.' with CTAs 'SHOP MEN' and 'SHOP WOMEN'.

## Current state
h1: Wildly Comfortable. Super Natural.; cta: SHOP MEN / SHOP WOMEN; notes: The subhead is absent; the hero relies on the brand name and abstract adjectives, not on the visitor's need for comfortable, sustainable footwear.

## Required change
h1: Shoes That Feel Like Nothing Else; cta: Shop Men's Shoes / Shop Women's Shoes; notes: Use a benefit-driven headline that speaks to comfort and natural materials, with CTAs that clearly direct to product categories.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Use a benefit-driven headline that speaks to comfort and natural materials, with CTAs that clearly direct to product categories.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_vague_hero_copy` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
