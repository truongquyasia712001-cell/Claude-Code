---
name: awesome-design
description: Apply a ready-made design system modeled on a well-known brand (Stripe, Apple, Linear, Vercel, Notion, Airbnb, Figma, Supabase and ~80 others), covering color palette, typography, spacing, radii, shadows, buttons and components. Use when the user wants a UI "like Stripe/Apple/Linear/…", asks for a professional design system, design tokens, or a consistent visual language for a new app or site.
argument-hint: <brand> [what to build]
---

# Awesome Design

A library of DESIGN.md files from [VoltAgent/awesome-design-md](https://github.com/VoltAgent/awesome-design-md) (MIT). Each one breaks down a brand's design language: palette, type scale, spacing, radii, elevation, component styles, and the dos and don'ts.

## Files

`designs/<brand>.md`, one per brand. List them with `ls <skill>/designs`. Common picks:

- **SaaS / dev tools:** `linear.app`, `vercel`, `stripe`, `supabase`, `raycast`, `resend`, `sentry`, `posthog`, `cursor`, `warp`
- **Productivity:** `notion`, `figma`, `miro`, `slack`, `cal`, `superhuman`, `airtable`
- **Consumer / premium:** `apple`, `airbnb`, `spotify`, `nike`, `tesla`, `uber`, `pinterest`
- **Fintech:** `stripe`, `revolut`, `wise`, `mercury`, `coinbase`, `kraken`
- **AI:** `claude`, `mistral.ai`, `cohere`, `elevenlabs`, `replicate`, `x.ai`, `ollama`

## How to use

1. **Pick the brand.** Use the one the user names. If they name none, suggest 2–3 that fit the product (for example, a B2B dashboard maps to `linear.app`, `vercel` or `stripe`) and ask, or pick one and say which.
2. **Read the whole file** `designs/<brand>.md` before writing any UI code.
3. **Turn it into tokens** in the project's own format: CSS custom properties, a Tailwind theme (`tailwind.config` / `@theme`), or a `theme.ts`. Cover colors (including dark mode if the file defines it), font families and type scale, spacing scale, radii, shadows, and motion durations.
4. **Build components from those tokens only.** Avoid hard-coded hex values and magic numbers outside the token file.
5. **Follow the file's dos and don'ts**, such as button shapes, border use and gradient rules.
6. Optionally copy the file into the project as `DESIGN.md` at the repo root, so future sessions and other agents follow the same system.

## Rules

- These files describe a design *language*. Don't copy logos, trademarks, proprietary fonts or brand imagery. If the file names a proprietary typeface (for example Söhne or SF Pro), use the closest free alternative (for example Inter or Geist) and say so.
- When the user mixes brands ("Linear's layout with Stripe's colors"), read both files and state which parts come from which.
- When the project already has a design system, adapt it toward the reference. Don't replace it unless asked.
