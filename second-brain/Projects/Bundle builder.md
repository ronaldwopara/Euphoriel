---
type: project
status: active
parent: Euphoriel
tags:
  - project
  - euphoriel
  - bundle
---

# Bundle builder

Parent:: [[Euphoriel]]
Files:: `sections/bundle-page.liquid`, `templates/page.build-your-bundle.liquid`, `bundle.html`

## What it does

Build-your-bundle page on `/pages/about?view=build-your-bundle`. Shoppers pick face oils plus body products (shower oil, shea butter, mango butter, and the golden / glow option used in the email).

Discount rule (also stated in the welcome email footer):

- 2 products → 15% off
- 3+ products → 20% off
- Cannot stack with other promos

URL params from the quiz / email: `face` and `add`. `add` can be comma-separated. Buttons now carry `data-bundle-key` (`shower`, `shea`, `mango`, `golden`, plus the four face keys). See [[Klaviyo and quiz stack]].

## In flight (uncommitted)

`sections/bundle-page.liquid` auto-adds every key in `face` and `add` on load, not just the quiz face oil. That is what the welcome email pairing links need.

## Watch

- Sticky add-to-bundle CTA width on mobile vs desktop
- Slot styling fighting the theme's card/image rules
- `?face=harmonic&add=mango` must add both, once each

## Open

See [[Tasks]]
