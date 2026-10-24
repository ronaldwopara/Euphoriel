---
type: project
status: active
started: 2026-10-24
client: Euphoriel
tags:
  - project
  - euphoriel
---

# Euphoriel

Status:: active
Client:: Euphoriel Beauty
Site:: [euphorielbeauty.com](https://euphorielbeauty.com)
Code:: parent folder of this vault. Live Shopify files at the root. Static mockups in `local/`. Emails in `emails/`.

## Outcome

Ship the quiz → personalized result → build-your-bundle → welcome email path so a new subscriber lands on the right face oil and a discounted bundle.

## Now

The live workstreams are [[Skin quiz]], [[Bundle builder]], and [[Welcome email]]. Uncommitted theme files as of 2026-10-24:

- `quiz.page.liquid` — Klaviyo `Completed Skin Quiz` event for retakes
- `sections/bundle-page.liquid` — `face` + `add` deep links via `data-bundle-key`
- `emails/klaviyo-welcome-bundle-email.html` — new welcome that uses both

Contract between the three: [[Klaviyo and quiz stack]]. Calls we already made: [[Decisions]].

## Brand facts that keep coming up

- Tagline: Feed Your Skin
- Vegan, cruelty-free, made in Canada, waterless / concentrated
- Free shipping over $75
- First-order promo on site: 15% off
- Bundle: 15% at 2 products, 20% at 3+
- 30-day satisfaction guarantee; eligible return if 75%+ remaining
- Face oils are $39.99 CAD

## Face oils the quiz maps to

| Result key | Product | For |
| --- | --- | --- |
| `balance` | Balance Elixir | Oily / blemish-prone |
| `harmonic` | Harmonic Elixir | Combination |
| `renewal` | Renewal Elixir | Normal to dry / sensitive |
| `timeless` | Timeless Elixir | Mature / aging |

Quiz answers write `skin_quiz_result`. The welcome email and bundle URL both read that value (`?face=` / `?add=`).

## People

- [[Euphoriel client]]

## Context

- [[2026-10-24 Cursor — second brain]]
- [[2026-10-24 Stretch theme migration]]
- [[2026-10-24 Call — ecom double down]]
- [[Homepage rebuild]]
- [[Stretch migration]]
- [[Brand and audience]]
- [[Tasks]]
