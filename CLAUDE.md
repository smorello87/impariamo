# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an Italian language learning website called "Impariamo l'Italiano!" featuring interactive educational games and exercises. The project is a static HTML/CSS/JavaScript website with no build process or dependencies.

## Architecture

### CSS Architecture (IMPORTANT)

**CSS Versioning System:**
- CSS files use version numbers in filenames: `styles-v2.css`, `games-v2.css`
- When updating CSS, increment version number (v2 → v3) and update ALL HTML `<link>` tags
- This is required because the site is hosted on Reclaim Hosting which has aggressive server-side caching
- The `.htaccess` file forces no-cache headers, but version numbers provide additional cache-busting

**CSS Structure:**
- `css/styles-v2.css` - Main stylesheet with navigation, forms, layout, Italian flag color variables
- `css/games-v2.css` - Game-specific styles (memory cards, wordle tiles, wheel, crosswords)
- Each HTML file has inline `<style>` block for page-specific overrides
- All pages use `.game-section { text-align: center; margin: var(--spacing-lg) 0; }` for centered selection screens

**CSS Custom Properties (in styles-v2.css):**
- Italian flag colors: `--color-italian-green: #008C45`, `--color-italian-red: #CE2B37`, `--color-italian-white: #ffffff`
- Spacing: `--spacing-xs` through `--spacing-xxl` (5px to 40px)
- Z-index layers: `--z-dropdown: 10`, `--z-mobile-menu: 50`, `--z-modal: 100`, `--z-notification: 200`

### File Structure
- **HTML Game Pages**: Each game is a standalone HTML file with embedded JavaScript
  - `index.html` - Main landing page
  - `wordle.html` - Italian Wordle with difficulty levels
  - `memory.html` - Memory card matching game with topics (food, daily activities, family, school, work)
  - `tenses.html` - Verb tense wheel spinner
  - `reflexives.html` - Reflexive verbs wheel spinner
  - `crosswords.html` - Italian crossword puzzle
  - `fiore.html` - Flower-based word guessing game
  - `deep.html` - Deep learning exercises (uses Tailwind CSS, different architecture)
- **Assets**: `flower/` directory contains images (flower0-8.jpg)
- **Server Config**: `.htaccess` with aggressive cache prevention for Reclaim Hosting

### Common Patterns

1. **Page Structure Template**:
   - Header with Italian green background
   - Navigation bar with Italian red background and dropdown menus
   - Responsive hamburger menu for mobile (<600px)
   - Main content in `.container` class
   - Footer with Italian green background
   - Google Analytics tracking (G-QJL9EQGT3Y)

2. **CSS Linking Pattern** (all HTML files except deep.html):
   ```html
   <link rel="stylesheet" href="css/styles-v2.css">
   <link rel="stylesheet" href="css/games-v2.css">
   <style>
     /* Page-specific overrides */
     .game-section {
       text-align: center;
       margin: var(--spacing-lg) 0;
     }
   </style>
   ```

3. **Mobile Responsive Design**:
   - Desktop: Horizontal navigation with dropdown hovers
   - Mobile (<600px): Hamburger menu with vertical layout, 30px navigation padding
   - Touch targets: Minimum 44px for all interactive elements
   - Input fields use 16px font-size to prevent iOS auto-zoom

## Development Commands

Since this is a static website with no build process:

```bash
# Open the site locally
open index.html

# Start a simple HTTP server (if Python is available)
python -m http.server 8000
# or
python3 -m http.server 8000

# For PHP users
php -S localhost:8000
```

## Key Implementation Details

### CSS Updates (CRITICAL WORKFLOW)

When updating CSS:
1. **Increment version number** in filename: `styles-v2.css` → `styles-v3.css`
2. **Update ALL HTML files** to reference new version in `<link>` tags
3. **Upload both** new CSS file and updated HTML files to server
4. This is necessary due to Reclaim Hosting's aggressive caching

### Adding New Games
1. Copy structure from existing game HTML file (e.g., `memory.html` or `wordle.html`)
2. Link to current CSS versions: `<link rel="stylesheet" href="css/styles-v2.css">` and `css/games-v2.css`
3. Add inline `<style>` block with `.game-section { text-align: center; margin: var(--spacing-lg) 0; }`
4. Maintain header/navigation/footer structure
5. Include Google Analytics snippet (G-QJL9EQGT3Y)
6. Update navigation in ALL HTML files (see below)

### Navigation Updates
Navigation appears in every HTML file. When adding/removing pages:
- Update `<nav>` section in ALL HTML files
- Maintain dropdown structure: `<div class="dropdown">` with `<div class="dropdown-content">`
- Add `class="active"` to current page link
- Navigation has single arrow via CSS: `nav .dropdown > a::after { content: '\25BC'; }`

### Select Dropdowns (Important Styling Note)
All `<select>` elements have custom styling in `styles-v2.css`:
- Browser default arrow is hidden with `-webkit-appearance: none; -moz-appearance: none; appearance: none;`
- Custom SVG arrow added via background-image
- Do not add additional CSS arrows to select elements

### Game Data Structure
Game-specific data is hardcoded in JavaScript arrays within each HTML file:
- **Wordle**: `facileWords`, `medioWords`, `difficileWords` arrays (5-letter Italian words)
- **Memory**: `topics` object with word pairs (Italian/English) for food, daily activities, family, school, work
- **Tenses/Reflexives**: Verb arrays and conjugation data in inline scripts
- **Crosswords**: Grid layout and clues defined in JavaScript

### Mobile-Specific Considerations
- Navigation bar: 30px padding on mobile (`var(--spacing-xl)`)
- Z-index stacking: Mobile menu uses `--z-mobile-menu: 50` to appear above all content
- Hamburger menu: `.menu-items.show-menu` triggers dropdown visibility
- All interactive elements: Minimum 44px touch targets
- Input/select font-size: 16px minimum to prevent iOS auto-zoom
- Memory cards: Smaller grid (70px minimum) on mobile with tighter spacing (5px gap)