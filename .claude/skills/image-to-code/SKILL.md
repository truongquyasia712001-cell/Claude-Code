---
name: image-to-code
description: Turn a screenshot, mockup, Figma export or design reference image into faithful frontend code, then verify it visually against the reference in a real browser. Use when the user shares or points to an image of a UI and wants it built, cloned or matched.
argument-hint: <image-path> [framework]
---

# Image to Code

Rebuild the UI in a reference image as clean, production-quality code that matches it closely.

## 1. Analyze the image

Open the image with the Read tool. Write short notes covering:

- **Canvas:** approximate viewport width (desktop ~1440, laptop ~1280, mobile ~390) and the page background.
- **Layout:** regions from top to bottom (nav, hero, sections, footer, or app shell / sidebar / content). For each one, note the grid (column count, alignment, max content width).
- **Palette:** 4–8 colors with estimated hex values (background, surface, text primary/secondary, border, accent, states).
- **Typography:** serif, sans or mono; the closest free font (Google Fonts or system); size, weight, line-height and letter-spacing for each level (display, h1–h3, body, caption).
- **Spacing:** the base unit (4 or 8 px), section gaps, card padding, gaps between elements.
- **Components:** buttons, inputs, cards, badges, tabs, tables, icons, with radius, border, shadow and state.
- **Signature details:** the 2–3 things that give the design its character. Missing these is what makes a clone look "off".

If parts of the image are unclear, crop or zoom them mentally region by region, and note what you inferred versus what you saw.

## 2. Plan

- Detect the project's stack (package.json, framework, Tailwind, component library) and use it. With no project, default to a single HTML file with modern CSS.
- Write a 5–10 line outline of the component tree, plus the tokens you will define.

## 3. Build

- Put the palette, type scale, spacing and radii into tokens (CSS variables or the Tailwind theme) first.
- Build structure, then layout and spacing, then type and color, then details (shadows, borders, icons, hover states).
- Use semantic HTML, flex/grid, and real text (not images of text). Use an icon set that is close to the original (for example lucide).
- Make it responsive. Match the reference at its own width and degrade gracefully on other sizes.
- Don't copy copyrighted assets (logos, photos, illustrations). Use labeled placeholders or similar free assets.

## 4. Verify visually (required)

Use `playwright-cli` (see the playwright-cli skill) to render the result:

```bash
playwright-cli open <file-or-local-url>
playwright-cli resize <width> <height>   # match the reference viewport
playwright-cli screenshot
```

Read the screenshot and the reference side by side, then compare region by region: alignment, sizes, spacing, colors, font weight, line breaks, borders and shadows. List the visible differences, fix them, and screenshot again. Repeat until the remaining differences are negligible (usually 2–3 passes). Close the browser when done.

## 5. Report

Briefly state what matches, any deliberate deviations (fonts substituted, assets replaced with placeholders), and anything ambiguous in the reference.
