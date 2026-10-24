---
type: project
status: active
parent: Euphoriel
tags:
  - project
  - euphoriel
  - quiz
---

# Skin quiz

Parent:: [[Euphoriel]]
Files:: `quiz.page.liquid`, `quiz.html`

## What it does

Four questions, about one minute. Scores four result keys and shows a matched face oil. Lead capture (name, email, optional phone, SMS consent) happens before results.

The matched product is **not** added to the bundle on the quiz itself. The result page's "Add To My Bundle" button goes to `/pages/about?view=build-your-bundle&face={result}`. [[Bundle builder]] reads `face` on arrival.

On submit, the quiz writes profile properties and fires a **Completed Skin Quiz** event so the welcome flow can run on retakes. Full contract: [[Klaviyo and quiz stack]].

## Questions (short)

1. Skin type → oily / combo / dry / mature (`skin_type`)
2. Biggest concern → breakouts / dullness / lines / redness (`skin_concern`)
3. After cleansing → oily fast / mixed / needs moisture / tight (`skin_after_cleansing`)
4. Goal → clearer / balance / firmer / soothe (`skincare_goal`)

## In flight (uncommitted)

`quiz.page.liquid` now posts three Klaviyo calls: subscribe to list `YswWdg`, upsert profile properties, and send the `Completed Skin Quiz` event with a unique id each time.

## Watch

- Scoring ties and how the winner is chosen
- Event unique id must change on every completion or Klaviyo may drop retakes
- Bundle CTA still passing `face=` only (do not add the oil here)

## Open

See [[Tasks]]
