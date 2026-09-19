# Technical Documentation

## 1. Overview
This is a responsive personal portfolio website built with HTML, CSS and JavaScript. It has three main sections (About Me, Projects, Contact) and two interactive features: a time-based greeting and a dark/light mode toggle. It uses no frameworks or backend.

## 2. File Structure
```
id-name-assignment1/
├── README.md
├── index.html
├── css/
│   └── styles.css
├── js/
│   └── script.js
├── assets/
│   └── images/
├── docs/
│   ├── ai-usage-report.md
│   └── technical-documentation.md
└── .gitignore
```

| File | Purpose |
|---|---|
| `index.html` | Page structure and content |
| `css/styles.css` | Colors, layout, responsive design and dark mode styles |
| `js/script.js` | Greeting message and theme toggle |
| `docs/` | Project documentation |

## 3. HTML Structure
The page uses semantic tags to describe its structure:

- `<header>`: site title, navigation links and the theme toggle button
- `<nav>`: links to the three sections using `#about`, `#projects` and `#contact`
- `<main>`: contains the three `<section>` elements
- `<footer>`: copyright line

**Sections**
- **About Me** (`#about`): greeting, tagline and a short introduction.
- **Projects** (`#projects`): two project boxes (`<article class="project-box">`), each with a title, description and placeholder image.
- **Contact** (`#contact`): a form with Name, Email and Message fields. Each field has a `<label>` linked by `for` and `id`, and uses `required` for basic validation.

## 4. CSS Design

### Color variables
Colors are defined once in `:root` as CSS variables (for example `--accent-color`) and reused with `var()`. This makes the theme easy to change and allows dark mode to work by replacing the variables.

### Layout
- **Flexbox** is used for the header (title on the left, navigation on the right) and for the contact form (fields stacked vertically).
- **CSS Grid** is used for the projects. On desktop and tablet they sit in two equal columns (`grid-template-columns: repeat(2, 1fr)`). On mobile (600px and below) a media query changes this to one column (`grid-template-columns: 1fr`).
- Sections use `max-width: 1000px` and `margin: 0 auto` to stay centered on wide screens.
- The contact form uses `max-width: 500px` and `margin: 0 auto` so it stays centered at every screen width.

### Responsive design
Two media queries adapt the layout:

| Breakpoint | Changes |
|---|---|
| `max-width: 768px` (tablet) | Smaller section padding |
| `max-width: 600px` (mobile) | Header stacks vertically, projects switch to one column |

### Dark mode
Dark mode is done with a `dark-mode` class on `<body>`. The rule `body.dark-mode` replaces the color variables with darker values, so the whole page changes at once. A few extra rules adjust heading colors and form fields for readability.

## 5. JavaScript Features
The script is loaded at the end of `<body>` so the HTML elements exist before the code runs.

### Time-based greeting
```js
const hour = new Date().getHours();
```
`getHours()` returns the current hour (0 to 23). An `if / else if / else` chooses "Good morning!" (before 12), "Good afternoon!" (before 18) or "Good evening!". The text is placed in `<p id="greeting">` using `textContent`.

### Dark/light mode toggle
An event listener on the button (`#theme-toggle`) runs when it is clicked. It calls `classList.toggle("dark-mode")` on `<body>`, which adds the class if it is missing and removes it if present. The button text then changes between "Dark Mode" and "Light Mode".

## 6. Testing
- Checked the layout at laptop, tablet and phone sizes using Chrome DevTools device mode.
- Checked that navigation links scroll to the correct sections.
- Checked that the greeting shows and the theme toggle switches correctly.
- Checked the browser console for errors.

## 7. Known Limitations
- The contact form has no backend, so messages are not sent or stored.
- The theme choice is not saved, so the page returns to light mode when refreshed.
- Project images are placeholders from `placehold.co`.