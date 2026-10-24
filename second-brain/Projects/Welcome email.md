---
type: project
status: active
parent: Euphoriel
tags:
  - project
  - euphoriel
  - klaviyo
---

# Welcome email

Parent:: [[Euphoriel]]
File:: `emails/klaviyo-welcome-bundle-email.html`

## What it does

Klaviyo welcome that sells the bundle around the quiz result.

- Headline: Get 20% Off / On what pairs with your face oil
- Hero and CTAs deep-link to the bundle with `face` and `add` from `person.skin_quiz_result`
- Shows the matched elixir: Balance, Harmonic, Renewal, or Timeless
- Pairing links use `add=shower` / `shea` / `mango` / `golden` (needs the uncommitted bundle deep-link work)
- States the 30-day guarantee
- Legal: bundle savings 15% at 2, 20% at 3+; cannot combine with other promos

Welcome flow trigger should be the **Completed Skin Quiz** event, not "profile created once." Retakes need a fresh unique id. [[Klaviyo and quiz stack]]

## Watch

- Klaviyo `person|lookup:'skin_quiz_result'` must match the quiz keys exactly
- Dark-mode / light-mode locks (email forces light)
- Fallback when the profile has no quiz result
- Pairing CTAs only work after `data-bundle-key` ships on the bundle page

## Open

See [[Tasks]]
