# Impariamo l'Italiano! 🇮🇹

An interactive Italian language learning website featuring educational games and exercises, designed for use in college and high school language classrooms.

**Created by Beatrice Carnelutti**

[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)

## 📚 About

Impariamo l'Italiano! is a collection of interactive web-based games designed to help students practice Italian vocabulary, verb conjugations, and language skills in an engaging way. The games are suitable for classroom use or independent study.

### Available Games

- **Memory Game** - Match Italian words with their English translations across different topics (food, daily activities, family, school, work)
- **Wordle** - Italian word guessing game with three difficulty levels (Facile, Medio, Difficile)
- **Spin the Wheel - Verb Tenses** - Practice conjugating Italian verbs in different tenses with a spinning wheel interface
- **Spin the Wheel - Reflexive Verbs** - Focus specifically on reflexive verb conjugations
- **Fiore** - Flower-based word guessing game with visual progression
- **Crossword Puzzle** - Italian vocabulary crosswords

## 🎯 Educational Use

This project was built specifically for language classroom environments:

- **No installation required** - Works directly in any web browser
- **No dependencies** - Pure HTML, CSS, and JavaScript
- **Mobile-friendly** - Responsive design works on tablets and phones
- **Self-contained** - Can be hosted on any web server or run locally
- **Customizable content** - Word lists and vocabulary can be easily modified

## 🏗️ Architecture

### Technology Stack

- **HTML5** - Semantic markup for each game page
- **CSS3** - Custom properties for theming, responsive design
- **Vanilla JavaScript** - No frameworks or libraries required
- **Static hosting** - No server-side processing needed

### File Structure

```
impariamo/
├── index.html              # Landing page
├── memory.html             # Memory card game
├── wordle.html             # Italian Wordle
├── tenses.html             # Verb tense wheel
├── reflexives.html         # Reflexive verbs wheel
├── fiore.html              # Flower word game
├── crosswords.html         # Crossword puzzle
├── css/
│   ├── styles-v2.css       # Main stylesheet (navigation, layout, forms)
│   └── games-v2.css        # Game-specific styles (cards, tiles, wheels)
├── flower/                 # Image assets for fiore game
└── .htaccess               # Server configuration (for Apache hosting)
```

### Design Principles

1. **Standalone pages** - Each game is self-contained in a single HTML file
2. **Consistent theming** - Italian flag colors (green #008C45, red #CE2B37, white #ffffff)
3. **Mobile-first** - Responsive design with hamburger menu for small screens
4. **No build process** - Direct editing of HTML/CSS/JavaScript

## 🚀 Getting Started

### Running Locally

1. Clone or download this repository
2. Open any HTML file in a web browser, or
3. Start a local server:

```bash
# Python 3
python3 -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000

# PHP
php -S localhost:8000
```

4. Navigate to `http://localhost:8000`

### Deploying to a Web Server

1. Upload all files to your web server via FTP/SFTP
2. Ensure the `.htaccess` file is uploaded (required for cache control)
3. Navigate to your domain

**Note:** This project is configured for Reclaim Hosting but works with any Apache-based hosting.

## 🌍 Adapting for Other Languages

This project can be easily adapted for teaching other languages. Here's how:

### 1. Update Color Scheme

In `css/styles-v2.css`, change the CSS custom properties to match your target language's flag or theme:

```css
:root {
  /* Example: Spanish flag colors */
  --color-primary: #AA151B;      /* Red */
  --color-secondary: #F1BF00;    /* Yellow */
  --color-tertiary: #ffffff;     /* White */

  /* Update references throughout */
  --color-italian-green: var(--color-primary);
  --color-italian-red: var(--color-secondary);
  /* etc. */
}
```

### 2. Update Vocabulary and Content

Each game stores its data in JavaScript arrays within the HTML file:

**Memory Game** (`memory.html`):
```javascript
const topics = {
  food: [
    { italian: "pane", english: "bread" },
    // Change to your target language
    { spanish: "pan", english: "bread" },
  ],
  // Add more topics
};
```

**Wordle** (`wordle.html`):
```javascript
const facileWords = [
  "PANE", "CASA", "MARE",
  // Replace with 5-letter words in your target language
];
```

**Verb Games** (`tenses.html`, `reflexives.html`):
```javascript
const verbs = [
  { infinitive: "essere", conjugations: { /* ... */ } },
  // Replace with verbs in your target language
];
```

### 3. Update Text and Labels

Search and replace Italian text throughout the HTML files:

- Page titles (e.g., "Impariamo l'Italiano!" → "¡Aprendamos Español!")
- Button labels (e.g., "Inizia" → "Comenzar")
- Instructions and feedback messages
- Navigation menu items

### 4. Update Metadata

- Change `<title>` tags in each HTML file
- Update the Google Analytics ID in the tracking code (or remove if not needed)
- Update the footer attribution to credit your adaptation

### 5. Rename the Project

- Update `index.html` header and title
- Change references to "Italian" in all files
- Update `README.md` 

## 🎨 Customization

### Adding New Vocabulary Topics

To add a new topic to the Memory Game:

1. Open `memory.html`
2. Find the `topics` object in the JavaScript section
3. Add a new key with word pairs:

```javascript
const topics = {
  // Existing topics...
  animals: [
    { italian: "gatto", english: "cat" },
    { italian: "cane", english: "dog" },
    // Add at least 10-14 pairs for best gameplay
  ]
};
```

4. Add the topic to the dropdown:

```html
<select id="topicSelect">
  <option value="food">Food</option>
  <!-- Add new option -->
  <option value="animals">Animals</option>
</select>
```

### Modifying Game Difficulty

**Wordle** - Add words to different difficulty arrays:
- `facileWords` - Easy 5-letter words
- `medioWords` - Medium difficulty
- `difficileWords` - Advanced vocabulary

**Memory Game** - Adjust grid size by changing the number of pairs (max 14 pairs = 28 cards)

**Fiore** - Modify difficulty by changing word length in the word arrays

## 📱 Mobile Optimization

The site is fully responsive and optimized for mobile devices:

- Touch targets are minimum 44px for easy tapping
- Hamburger menu for navigation on screens < 600px
- Memory cards adapt to smaller grids on mobile
- Input fields use 16px font to prevent iOS auto-zoom

## 🔧 Technical Notes

### CSS Versioning

CSS files use version numbers (`styles-v2.css`) to handle aggressive server caching on Reclaim Hosting:

- When updating CSS, increment the version number
- Update all HTML `<link>` tags to reference the new version
- Upload both new CSS and updated HTML files

### Browser Compatibility

- Modern browsers (Chrome, Firefox, Safari, Edge)
- Internet Explorer is not supported
- Mobile browsers (iOS Safari, Chrome Mobile, Firefox Mobile)

## 📄 License

This work is licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-nc-sa/4.0/).

**You are free to:**
- Share — copy and redistribute the material in any medium or format
- Adapt — remix, transform, and build upon the material

**Under the following terms:**
- **Attribution** — You must give appropriate credit to Beatrice Carnelutti
- **NonCommercial** — You may not use the material for commercial purposes
- **ShareAlike** — If you remix or adapt the material, you must distribute your contributions under the same license

## 🤝 Contributing

This project is designed for educational use and adaptation. If you adapt this for another language or add new games, consider sharing your work with the educational community under the same CC BY-NC-SA license.

## 👩‍🏫 About the Creator

Created by **Beatrice Carnelutti** for use in college and high school Italian language classrooms.

## 📞 Support

For questions about using or adapting this project for your classroom, please open an issue in the repository.

---

**Buon divertimento! (Have fun!)**
