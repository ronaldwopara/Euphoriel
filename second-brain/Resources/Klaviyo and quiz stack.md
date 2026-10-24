---
type: resource
tags:
  - resource
  - klaviyo
  - quiz
---

# Klaviyo and quiz stack

The contract between [[Skin quiz]], [[Bundle builder]], and [[Welcome email]]. If a result, URL, or email looks wrong, start here.

## Profile properties the quiz writes

| Key | What it is |
| --- | --- |
| `skin_quiz_result` | `balance` / `harmonic` / `renewal` / `timeless` |
| `skin_type` | Label of Q1 |
| `skin_concern` | Label of Q2 |
| `skin_after_cleansing` | Label of Q3 |
| `skincare_goal` | Label of Q4 |

Email reads `person.skin_quiz_result` via `person\|lookup:'skin_quiz_result'`.

## What the quiz posts to Klaviyo

Three client calls, in parallel, from `quiz.page.liquid`:

1. `subscriptions` → list `YswWdg`, source `Skin Quiz`
2. `profiles` → name + the properties above (subscription alone does not keep custom props)
3. `events` → metric **Completed Skin Quiz**, same properties, unique id `skin-quiz-{email}-{timestamp}-{result}` so retakes still fire the welcome flow

Company id / public key lives in `quiz.page.liquid` as `KLAVIYO_PUBLIC_KEY`.

## Bundle deep links

Path: `/pages/about?view=build-your-bundle`

| Param | Meaning |
| --- | --- |
| `face` | Quiz result key. Auto-adds that face oil. |
| `add` | One key, or comma-separated keys. Auto-adds those products. |

Keys on the buttons (`data-bundle-key`):

- Face: `balance`, `harmonic`, `renewal`, `timeless`
- Body: `shower` (Radiance Ritual Shower Oil), `shea` (Rejuvenating Shea Body Butter), `mango` (Revitalizing Mango Body Butter), `golden` (Golden Aura Body Oil)

Examples:

- `?face=harmonic&add=mango` → Harmonic + mango butter
- `?add=shower,shea` → shower oil + shea

The quiz does **not** add the oil to the bundle itself. It only passes `face`. Adding it in both places used to duplicate the line item.

## Bundle discounts

- 2 products → 15%
- 3+ → 20%
- Do not stack with other promos
