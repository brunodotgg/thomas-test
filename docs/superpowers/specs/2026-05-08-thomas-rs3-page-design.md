# Thomas's RS3 8Y — Tribute Page Design

**Date:** 2026-05-08
**Status:** Approved

## Summary

A single self-contained HTML page celebrating Thomas's Audi RS3 8Y. Clean, premium aesthetic inspired by Audi's own design language. No build step, no dependencies beyond Google Fonts.

## Visual Design

- **Palette:** White background (`#ffffff`), near-black text (`#111111`), Audi red (`#BB0A21`) as accent
- **Typography:** Inter via Google Fonts — light weight for headlines, regular for body
- **Feel:** Audi.com-adjacent: lots of white space, thin lines, restrained use of color

## Sections

### 1. Nav
Minimal top bar. "RS3 8Y" on the left, "Thomas" on the right. Thin bottom border. No links.

### 2. Hero
Full-viewport height. Dark gradient background (`#111` to `#1a1a1a`). Centered content:
- Small all-caps label: "Audi RS3 8Y · 2024"
- Large headline: "Built to move. Built for Thomas."
- Thin red horizontal rule beneath

### 3. Specs Grid
Section title: "The Machine". 4-column grid (collapses to 2 on mobile). Each cell:
- Large number in Audi red
- Short label below in grey uppercase
- Thin top border

Specs to include: 400 HP · 500 Nm · 0–100 in 3.8s · 290 km/h · 2.5L 5-cyl TFSI · Quattro AWD · 7-speed S tronic

### 4. Favorites
Section title: "Why Thomas Loves It". Two equal-width cards side by side:
- **Speed** — tagline: "Zero to 100 in 3.8 seconds. No excuses."
- **Power** — tagline: "400 horses. All four wheels. Always ready."
Each card has a large numeral in Audi red (Speed: "3.8", Power: "400"), the Audi red accent line, and ample padding.

### 5. Footer
Minimal single line: `Thomas ♥ RS3 8Y · 2026`

## Technical

- Single `index.html` file
- Styles in `<style>` block in `<head>`
- Google Fonts: Inter (300, 400, 700)
- Vanilla JS: `IntersectionObserver` for fade-in on scroll
- Fully responsive (mobile breakpoint at 768px)
- No images required — hero uses CSS gradient
