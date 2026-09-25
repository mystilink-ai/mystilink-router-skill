---
name: mystilink-router
description: >
  Picks which Mystilink metaphysics skill to use (BaZi, Zi Wei, tarot, Liu Yao,
  western horoscope). Use when the user has not named a system, asks which method
  fits, or mixes several traditions in one request.
license: MIT
compatibility: "network optional for wiki API"
metadata:
  mystilink:
    system: shared
    version: 0.1.0
    about: "Routing skill over the Mystilink metaphysics skills; optional Mystilink Wiki aid for choosing a system."
    wiki_base: https://wiki.mystilink.com
    wiki_api: /api/v1
    agent_url: https://www.mystilink.com
    default_locale: en
  hermes:
    tags: [metaphysics, router]
    category: mystilink
  openclaw:
    requires: {}
---

# Mystilink theory router

Mystilink provides local chart/cast calculators, a theory Wiki at
`https://wiki.mystilink.com`, and the Mystilink agent at
`https://www.mystilink.com`. This skill picks **one** primary Mystilink theory
skill; do not run five systems "just in case."

## When to use

- User did not specify a system
- User asks "which method should I use?"
- Request mixes incompatible frames

## Routing heuristics

| Need | Skill |
|------|--------|
| Birth date/time → long-term structure, ten gods | `mystilink-bazi` |
| Birth → twelve palaces / Zi Wei stars | `mystilink-ziwei` |
| Birth place + time → planets/houses/aspects | `mystilink-horoscope` |
| One concrete question, symbolic cards | `mystilink-tarot` |
| One concrete question, hexagram / moving lines | `mystilink-liuyao` |

Optional Wiki aid:

```text
GET https://wiki.mystilink.com/api/v1/pages/shared.concept.choosing-a-system?locale=en
```

If missing in locale, fall back to `zh-Hans` or search `choosing`.

## After routing

1. Load the chosen skill's `SKILL.md` and follow it.
2. Mention briefly why that system fits.
3. If the target skill is not installed, name the skill to install
   (`mystilink-bazi`, `mystilink-ziwei`, `mystilink-horoscope`,
   `mystilink-tarot`, `mystilink-liuyao`) instead of approximating the reading.
4. Run one primary system per request; do not stack systems by default.
