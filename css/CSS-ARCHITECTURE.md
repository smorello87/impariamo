# CSS Architecture Documentation - Impariamo l'Italiano!

## Overview
The CSS architecture for Impariamo l'Italiano has been redesigned using modern CSS best practices to improve maintainability, consistency, and performance across all pages.

## File Structure

```
css/
├── styles.css          # Core styles and common components
├── games.css          # Game-specific styles
└── CSS-ARCHITECTURE.md # This documentation
```

## Core Files

### 1. styles.css
**Purpose:** Contains all common styles, CSS custom properties, and base components shared across all pages.

**Includes:**
- CSS Custom Properties (variables) for theming
- Reset and base styles
- Typography system
- Header, navigation, and footer styles
- Form elements and buttons
- Utility classes
- Responsive breakpoints
- Animations
- Accessibility features

### 2. games.css
**Purpose:** Contains styles specific to game components and interactions.

**Includes:**
- Spinning wheel styles (Tenses & Reflexives)
- Memory game board and cards
- Wordle game tiles and keyboard
- Fiore (Flower) game components
- Crossword puzzle styles
- Game status and scoring displays
- Game-specific animations

## Implementation Guide

### For New HTML Pages

Add these two lines in the `<head>` section of your HTML file:

```html
<link rel="stylesheet" href="css/styles.css">
<link rel="stylesheet" href="css/games.css">
```

Remove all inline `<style>` tags except for page-specific overrides (if absolutely necessary).

### For Existing HTML Pages

1. **Replace inline styles** with the external stylesheets:
   ```html
   <!-- Remove this entire block -->
   <style>
     body { ... }
     /* All other inline styles */
   </style>

   <!-- Add these instead -->
   <link rel="stylesheet" href="css/styles.css">
   <link rel="stylesheet" href="css/games.css">
   ```

2. **Update container structure**:
   ```html
   <!-- Old -->
   <div class="container">

   <!-- New (semantic HTML) -->
   <main class="container">
   ```

3. **Keep page-specific styles minimal**:
   If you need page-specific styles, keep them minimal and in a small `<style>` tag:
   ```html
   <style>
     /* Only page-specific overrides */
     .special-feature {
       /* unique styles for this page only */
     }
   </style>
   ```

## CSS Custom Properties (Variables)

The system uses CSS custom properties for consistent theming. Key variables include:

### Colors
- `--color-italian-green`: #008C45
- `--color-italian-red`: #CE2B37
- `--color-italian-white`: #ffffff
- Extended palette with dark/light variants
- Neutral grays (100-700)

### Typography
- `--font-primary`: System font stack
- `--font-size-base`: 16px (scales down on mobile)
- Size variants: small, large, xlarge, xxlarge
- Font weights: normal (400), medium (500), bold (700)

### Spacing
- `--spacing-xs`: 5px
- `--spacing-sm`: 10px
- `--spacing-md`: 15px
- `--spacing-lg`: 20px
- `--spacing-xl`: 30px
- `--spacing-xxl`: 40px

### Other Properties
- Border radius variants
- Shadow definitions
- Transition durations
- Z-index layers

## Key Features

### 1. Responsive Design
- Mobile-first approach
- Breakpoints at 768px and 600px
- Hamburger menu for mobile navigation
- Flexible grid layouts for games

### 2. Animations
- Smooth transitions on all interactive elements
- Custom animations for game interactions:
  - Card flips for Memory game
  - Tile reveals for Wordle
  - Wheel spinning animation
  - Flower blooming effect

### 3. Accessibility
- Focus visible states for keyboard navigation
- Reduced motion support
- High contrast mode compatibility
- Screen reader-only utility class
- Semantic color usage

### 4. Performance Optimizations
- CSS custom properties for efficient theming
- Minimal specificity for faster parsing
- Hardware-accelerated animations
- Optimized selector efficiency

## Utility Classes

Common utility classes available:

### Text Alignment
- `.text-center`, `.text-left`, `.text-right`

### Spacing
- `.mt-[0-5]`: Margin top
- `.mb-[0-5]`: Margin bottom
- `.p-[0-5]`: Padding

### Visibility
- `.hidden`: Hide element
- `.sr-only`: Screen reader only

## Migration Checklist

For each HTML file that needs updating:

- [ ] Remove all inline `<style>` tags
- [ ] Add links to `styles.css` and `games.css`
- [ ] Replace `<div class="container">` with `<main class="container">`
- [ ] Test navigation dropdown functionality
- [ ] Test mobile hamburger menu
- [ ] Verify game-specific functionality
- [ ] Check responsive behavior
- [ ] Validate accessibility features

## Customization Guide

### Adding New Colors
Add to the `:root` selector in styles.css:
```css
:root {
  --color-custom: #hexvalue;
}
```

### Creating New Game Styles
Add to games.css following the existing pattern:
```css
.new-game-board {
  /* Use existing CSS variables */
  margin: var(--spacing-xl) auto;
  border-radius: var(--border-radius-medium);
}
```

### Page-Specific Overrides
Only when absolutely necessary, add minimal overrides:
```html
<style>
  .page-specific-class {
    /* Minimal overrides using CSS variables */
    color: var(--color-italian-green);
  }
</style>
```

## Visual Improvements

The new CSS architecture includes:

1. **Gradient backgrounds** on buttons and headers for depth
2. **Subtle animations** on hover and interaction
3. **Box shadows** for elevation and hierarchy
4. **Smooth transitions** for all state changes
5. **Consistent spacing** using the spacing scale
6. **Modern card designs** with hover effects
7. **Enhanced form elements** with focus states
8. **Loading states** and skeleton screens
9. **Success/error messaging** with appropriate styling

## Browser Support

The CSS is compatible with:
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+
- Mobile browsers (iOS Safari 14+, Chrome Mobile)

Fallbacks are provided for:
- CSS Grid (flexbox fallback)
- Custom properties (static values)
- Modern animations (graceful degradation)

## Maintenance Tips

1. **Always use CSS variables** for colors, spacing, and common values
2. **Follow BEM-like naming** for new components
3. **Group related properties** in logical order
4. **Comment complex techniques** or browser workarounds
5. **Test on multiple devices** and browsers
6. **Keep specificity low** - avoid deep nesting
7. **Use semantic class names** that describe purpose, not appearance

## Future Enhancements

Potential improvements to consider:

1. **CSS Modules** or **CSS-in-JS** for component isolation
2. **PostCSS** for automatic vendor prefixing
3. **CSS Grid** for more complex layouts
4. **Dark mode** theme variant
5. **Print stylesheets** for educational materials
6. **Animation library** for consistent micro-interactions
7. **Component library** documentation
8. **Performance budgets** for CSS file size

## Contact

For questions or suggestions about the CSS architecture, please refer to the main project documentation or contact the development team.