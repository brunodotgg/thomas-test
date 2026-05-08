# Thomas RS3 Page Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build a single self-contained `index.html` tribute page for Thomas's Audi RS3 8Y with a clean, premium aesthetic.

**Architecture:** One `index.html` file with all CSS in a `<style>` block and all JS inline at the bottom of `<body>`. No build step, no dependencies beyond Google Fonts loaded via `<link>`. Sections built and committed incrementally.

**Tech Stack:** HTML5, CSS3 (custom properties, grid, flexbox), vanilla JS (`IntersectionObserver`), Google Fonts (Inter 300/400/700).

---

## File Map

| File | Action | Responsibility |
|------|--------|----------------|
| `index.html` | Create | Entire page — markup, styles, script |

---

### Task 1: HTML scaffold + feature branch

**Files:**
- Create: `index.html`

- [ ] **Step 1: Create a feature branch**

```bash
git checkout -b feat/thomas-rs3-page
```

- [ ] **Step 2: Create `index.html` with base scaffold**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Thomas's RS3 8Y</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;700&display=swap" rel="stylesheet" />
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --red: #BB0A21;
      --black: #111111;
      --grey: #888888;
      --light: #f5f5f5;
      --white: #ffffff;
      --font: 'Inter', system-ui, sans-serif;
    }

    html { font-size: 16px; }

    body {
      font-family: var(--font);
      color: var(--black);
      background: var(--white);
      -webkit-font-smoothing: antialiased;
    }
  </style>
</head>
<body>
</body>
</html>
```

- [ ] **Step 3: Verify it opens without errors**

Open `index.html` in a browser. Expected: blank white page, no console errors, Inter font loading in Network tab.

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: add HTML scaffold with base styles and fonts"
```

---

### Task 2: Nav

**Files:**
- Modify: `index.html` — add nav markup inside `<body>` and nav CSS inside `<style>`

- [ ] **Step 1: Add nav CSS inside the `<style>` block (after `body { ... }`)**

```css
/* Nav */
nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.5rem 3rem;
  border-bottom: 1px solid #e5e5e5;
  position: sticky;
  top: 0;
  background: var(--white);
  z-index: 100;
}

nav .nav-model {
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--black);
}

nav .nav-name {
  font-size: 0.75rem;
  font-weight: 400;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--grey);
}
```

- [ ] **Step 2: Add nav markup inside `<body>`**

```html
<nav>
  <span class="nav-model">RS3 8Y</span>
  <span class="nav-name">Thomas</span>
</nav>
```

- [ ] **Step 3: Verify**

Reload. Expected: thin nav bar, "RS3 8Y" on the left, "Thomas" on the right, bottom border visible, nav sticks on scroll.

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: add sticky nav"
```

---

### Task 3: Hero section

**Files:**
- Modify: `index.html` — add hero markup and CSS

- [ ] **Step 1: Add hero CSS inside `<style>` (after nav styles)**

```css
/* Hero */
.hero {
  min-height: 100vh;
  background: linear-gradient(160deg, #111111 0%, #1c1c1c 60%, #2a1a1a 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 6rem 2rem;
}

.hero-inner {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.5rem;
}

.hero-badge {
  font-size: 0.7rem;
  font-weight: 700;
  letter-spacing: 0.25em;
  text-transform: uppercase;
  color: var(--grey);
}

.hero-headline {
  font-size: clamp(2.5rem, 6vw, 5rem);
  font-weight: 300;
  line-height: 1.1;
  color: var(--white);
  letter-spacing: -0.02em;
}

.hero-rule {
  width: 3rem;
  height: 2px;
  background: var(--red);
  border: none;
}
```

- [ ] **Step 2: Add hero markup inside `<body>` after `</nav>`**

```html
<section class="hero">
  <div class="hero-inner">
    <span class="hero-badge">Audi RS3 8Y &middot; 2024</span>
    <h1 class="hero-headline">Built to move.<br>Built for Thomas.</h1>
    <hr class="hero-rule" />
  </div>
</section>
```

- [ ] **Step 3: Verify**

Reload. Expected: full-viewport dark gradient section with centered white headline, small grey badge above, short red rule below. Text scales smoothly with `clamp`.

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: add hero section with dark gradient and headline"
```

---

### Task 4: Specs grid

**Files:**
- Modify: `index.html` — add specs markup and CSS

- [ ] **Step 1: Add specs CSS inside `<style>` (after hero styles)**

```css
/* Specs */
.specs {
  padding: 6rem 3rem;
  background: var(--white);
}

.section-title {
  font-size: 0.7rem;
  font-weight: 700;
  letter-spacing: 0.25em;
  text-transform: uppercase;
  color: var(--grey);
  margin-bottom: 3rem;
}

.specs-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 0;
}

.spec-item {
  padding: 2rem 0;
  border-top: 1px solid #e5e5e5;
  padding-right: 2rem;
}

.spec-value {
  font-size: 2.5rem;
  font-weight: 700;
  color: var(--red);
  line-height: 1;
  letter-spacing: -0.03em;
}

.spec-label {
  margin-top: 0.5rem;
  font-size: 0.7rem;
  font-weight: 400;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--grey);
}

@media (max-width: 768px) {
  .specs { padding: 4rem 1.5rem; }
  .specs-grid { grid-template-columns: repeat(2, 1fr); }
  .spec-item { padding-right: 1rem; }
}
```

- [ ] **Step 2: Add specs markup inside `<body>` after the hero `</section>`**

```html
<section class="specs">
  <p class="section-title">The Machine</p>
  <div class="specs-grid">
    <div class="spec-item">
      <div class="spec-value">400</div>
      <div class="spec-label">Horsepower</div>
    </div>
    <div class="spec-item">
      <div class="spec-value">500</div>
      <div class="spec-label">Nm torque</div>
    </div>
    <div class="spec-item">
      <div class="spec-value">3.8s</div>
      <div class="spec-label">0 – 100 km/h</div>
    </div>
    <div class="spec-item">
      <div class="spec-value">290</div>
      <div class="spec-label">km/h top speed</div>
    </div>
    <div class="spec-item">
      <div class="spec-value">2.5L</div>
      <div class="spec-label">5-cyl TFSI</div>
    </div>
    <div class="spec-item">
      <div class="spec-value">AWD</div>
      <div class="spec-label">Quattro</div>
    </div>
    <div class="spec-item">
      <div class="spec-value">7-spd</div>
      <div class="spec-label">S tronic</div>
    </div>
  </div>
</section>
```

- [ ] **Step 3: Verify**

Reload. Expected: 4-column grid on desktop, 2-column on mobile (&le;768px), red large numerals, grey uppercase labels, thin top border on each cell.

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: add specs grid with 7 RS3 stats"
```

---

### Task 5: Favorites section

**Files:**
- Modify: `index.html` — add favorites markup and CSS

- [ ] **Step 1: Add favorites CSS inside `<style>` (after specs styles)**

```css
/* Favorites */
.favorites {
  padding: 6rem 3rem;
  background: var(--light);
}

.favorites-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.5rem;
  margin-top: 3rem;
}

.fav-card {
  background: var(--white);
  padding: 3rem;
  border-top: 3px solid var(--red);
}

.fav-number {
  font-size: 4rem;
  font-weight: 700;
  color: var(--red);
  line-height: 1;
  letter-spacing: -0.04em;
}

.fav-title {
  margin-top: 1rem;
  font-size: 1.25rem;
  font-weight: 700;
  letter-spacing: 0.05em;
  text-transform: uppercase;
  color: var(--black);
}

.fav-tagline {
  margin-top: 0.75rem;
  font-size: 0.9rem;
  font-weight: 300;
  line-height: 1.6;
  color: var(--grey);
}

@media (max-width: 768px) {
  .favorites { padding: 4rem 1.5rem; }
  .favorites-grid { grid-template-columns: 1fr; }
}
```

- [ ] **Step 2: Add favorites markup inside `<body>` after the specs `</section>`**

```html
<section class="favorites">
  <p class="section-title">Why Thomas Loves It</p>
  <div class="favorites-grid">
    <div class="fav-card">
      <div class="fav-number">3.8</div>
      <div class="fav-title">Speed</div>
      <p class="fav-tagline">Zero to 100 in 3.8 seconds. No excuses.</p>
    </div>
    <div class="fav-card">
      <div class="fav-number">400</div>
      <div class="fav-title">Power</div>
      <p class="fav-tagline">400 horses. All four wheels. Always ready.</p>
    </div>
  </div>
</section>
```

- [ ] **Step 3: Verify**

Reload. Expected: light grey section, two white cards side by side, red top border on each card, large red numerals, bold uppercase titles, light grey taglines. Stacks to single column on mobile.

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: add favorites section with Speed and Power cards"
```

---

### Task 6: Footer

**Files:**
- Modify: `index.html` — add footer markup and CSS

- [ ] **Step 1: Add footer CSS inside `<style>` (after favorites styles)**

```css
/* Footer */
footer {
  padding: 2rem 3rem;
  border-top: 1px solid #e5e5e5;
  text-align: center;
  font-size: 0.75rem;
  font-weight: 400;
  letter-spacing: 0.1em;
  color: var(--grey);
}

footer span {
  color: var(--red);
}
```

- [ ] **Step 2: Add footer markup inside `<body>` after the favorites `</section>`**

```html
<footer>
  Thomas <span>&hearts;</span> RS3 8Y &middot; 2026
</footer>
```

- [ ] **Step 3: Verify**

Reload. Expected: minimal footer at the bottom, red heart, grey text, thin top border.

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: add footer"
```

---

### Task 7: Scroll fade-in animations + final responsive pass

**Files:**
- Modify: `index.html` — add fade-in CSS utility and JS at bottom of `<body>`

- [ ] **Step 1: Add fade-in CSS inside `<style>` (at the end, before `</style>`)**

```css
/* Scroll animations */
.fade-in {
  opacity: 0;
  transform: translateY(1.5rem);
  transition: opacity 0.6s ease, transform 0.6s ease;
}

.fade-in.visible {
  opacity: 1;
  transform: translateY(0);
}
```

- [ ] **Step 2: Add `fade-in` class to animatable elements**

Add `class="fade-in"` to each `.spec-item` and each `.fav-card`:

```html
<div class="spec-item fade-in">...</div>
<!-- repeat for all 7 spec-item divs -->

<div class="fav-card fade-in">...</div>
<!-- repeat for both fav-card divs -->
```

- [ ] **Step 3: Add IntersectionObserver script at the bottom of `<body>` before `</body>`**

```html
<script>
  const observer = new IntersectionObserver(
    (entries) => entries.forEach(e => e.isIntersecting && e.target.classList.add('visible')),
    { threshold: 0.15 }
  );
  document.querySelectorAll('.fade-in').forEach(el => observer.observe(el));
</script>
```

- [ ] **Step 4: Verify animations**

Reload and scroll down slowly. Expected: spec items and favorite cards fade up into view as they enter the viewport. No jank, no layout shift.

- [ ] **Step 5: Verify mobile layout**

Resize browser to &le;768px. Expected:
- Nav text readable, no overflow
- Hero headline scales down smoothly via `clamp`
- Specs grid: 2 columns
- Favorites cards: stacked single column
- No horizontal scroll

- [ ] **Step 6: Commit**

```bash
git add index.html
git commit -m "feat: add scroll fade-in animations and verify responsive layout"
```
