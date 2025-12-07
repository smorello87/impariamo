# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

"Impariamo l'Italiano!" is an Italian language learning website featuring interactive educational games. It's a static HTML/CSS/JavaScript site with no build process or dependencies.

## Development Commands

```bash
# Start local server
python3 -m http.server 8000

# Open directly (no server needed for basic testing)
open index.html
```

## Architecture

### CSS Versioning (CRITICAL)

CSS files use version numbers for cache-busting due to aggressive Reclaim Hosting caching:
- Current: `styles-v3.css`, `games-v3.css`
- When updating CSS: increment version (v3 → v4) and update ALL HTML `<link>` tags

### CSS Design System (v3 - "La Dolce Lingua")

**Color Palette (Tuscan-inspired):**
- Primary: `--color-terracotta` (#C65D3B), `--color-olive` (#5B7355), `--color-burgundy` (#722F37)
- Neutrals: `--color-parchment` (#F5F0E8), `--color-cream` (#FDFBF7), `--color-warm-white` (#FFFDF9)
- Earth tones: `--color-earth-100` through `--color-earth-800`
- Accents: `--color-gold` (#C4A35A)

**Typography:**
- Display: `Cormorant Garamond` (serif)
- Body: `Source Sans 3` (sans-serif)

**Spacing:** `--spacing-xs` (0.25rem) through `--spacing-4xl` (6rem)

### File Structure

**HTML Pages** (each standalone with embedded JS):
- `index.html` - Landing page with game descriptions (includes EN/IT translation toggle)
- `wordle.html` - Italian Wordle with difficulty levels
- `memory.html` - Vocabulary matching game
- `tenses.html` - Verb tense wheel spinner
- `reflexives.html` - Reflexive verbs wheel spinner
- `fiore.html` - Hangman-style flower game
- `crosswords.html` - Italian crossword puzzles

**Assets:**
- `images/logo.png` - Site logo (speech bubble with Italian flag + "Impariamo l'Italiano!")
- `images/favicon-*.png` - Favicon in multiple sizes (16, 32, 48, 64, 128, 180, 192, 512)
- `images/apple-touch-icon.png` - iOS home screen icon
- `favicon.ico` - Multi-size ICO file in root
- `flower/` - Flower images (flower0-8.jpg) for fiore game

### Common Patterns

**Page Structure:**
```html
<header>
  <img src="images/logo.png" alt="Impariamo l'Italiano!" class="logo">
  <h1>Impariamo l'Italiano!</h1>
</header>
<nav><!-- Navigation with hamburger menu for mobile --></nav>
<main class="container"><!-- Content --></main>
<footer><!-- CC BY-NC-SA 4.0 license --></footer>
```

**CSS & Favicon Linking:**
```html
<link rel="icon" type="image/x-icon" href="favicon.ico">
<link rel="icon" type="image/png" sizes="32x32" href="images/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="images/favicon-16x16.png">
<link rel="apple-touch-icon" sizes="180x180" href="images/apple-touch-icon.png">
<link rel="stylesheet" href="css/styles-v3.css">
<link rel="stylesheet" href="css/games-v3.css">
```

**Navigation:** Duplicated in every HTML file. When adding/removing pages, update ALL files.

### Game Data

Game word lists and data are hardcoded in inline `<script>` tags within each HTML file:
- Wordle: `facileWords`, `medioWords`, `difficileWords` arrays
- Memory: `topics` object with Italian/English word pairs
- Tenses/Reflexives: Verb arrays with conjugation data

### Homepage Translation Feature

Tool cards on index.html have EN/IT translation toggle:
- Button with class `translate-btn` in each `.tool` div
- Overlay with class `translation-overlay` contains English text
- `toggleTranslation(btn)` function handles toggle

### Mobile Considerations

- Breakpoint: 600px for mobile layout
- Hamburger menu: `.menu-items.show-menu` class toggles visibility
- Input font-size: 16px minimum to prevent iOS auto-zoom
- Touch targets: 44px minimum
