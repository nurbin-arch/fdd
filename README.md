# CulturalWeb

Static website for an international student community focused on social activities and cultural awareness. The site showcases events, galleries, team info, FAQs, and a culture blog. Forms are present for contact, newsletter signup, and volunteering.

## Project Structure

```
e:\fdd\
  ├─ index.html            # Home (hero, welcome video, nav)
  ├─ about.html            # Mission, membership, team
  ├─ events.html           # Events dashboard + details
  ├─ gallery.html          # Photos + cultural highlights
  ├─ blog.html             # Culture & International blog (recipes, music, festivals, stories)
  ├─ contact.html          # Contact, newsletter, volunteer registration
  ├─ faq.html              # Frequently asked questions
  ├─ legal.html            # Policies
  ├─ 404.html              # Not found
  ├─ css/                  # Styles (shared + per-page)
  ├─ js/                   # JavaScript (shared + per-page)
  └─ images/               # Assets used across pages
```

## Key Pages and Features

- Home (`index.html`)
  - Nepali hero animation with CTA
  - Embedded welcome/highlights video
  - Navigation cards and global footer

- About (`about.html`)
  - Explicit statement that membership is primarily international students
  - Purpose: social activities, cultural awareness, international-student support
  - Team section with roles and social links

- Events (`events.html`)
  - Upcoming list + month grid
  - Event details with imagery and descriptions
  - Includes cultural events: International Food Day, Cultural Dance Night, Dashain, Christmas Carol, Hackathon, Talent

- Gallery (`gallery.html`)
  - Filterable grid with lazy-loaded images
  - Lightbox viewer
  - Cultural Highlights section for short clips/spotlights

- Blog (`blog.html`)
  - Categories: Recipes, Music, Festivals, Stories
  - Seed articles as content examples

- Contact (`contact.html`)
  - General contact form
  - Newsletter signup form (handled client-side)
  - Inline volunteer registration form (plus an optional volunteer modal on home)

- FAQ (`faq.html`)
  - Accordion-driven Q&A
  - Entries clarifying membership (primarily international students) and purpose

Note: Health & Wellness was removed per requirements, and the language selector was removed; the site currently uses static English copy.

## JavaScript Overview

- `js/main.js` (shared)
  - Utilities: debounce, throttle, smooth scroll, viewport checks, date formatting
  - Navigation: active link highlighting, mobile menu toggle
  - Theme: dark/light mode with `localStorage` persistence
  - FAQ accordion behavior
  - Notification system (toast-like)
  - Form handling: prevents default submit, shows loading state, simulates async response, resets forms
  - Lazy loading for images via IntersectionObserver
  - Search helpers (if `.search-input` is present)
  - Back-to-top button, keyboard shortcuts, simple performance log

- `js/home.js` (home-specific)
  - Hero animations and particles
  - Interactive navigation cards
  - Newsletter signup client-side validation and feedback
  - Stats counter animations
  - Testimonials slider (if present in markup)
  - Quick actions (e.g., open volunteer modal)
  - Volunteer and donation modal helpers

Other page scripts (e.g., `js/events.js`, `js/gallery.js`) provide page-level enhancements and are loaded only where needed.

## Styles

- `css/style.css` contains shared variables, layout, utilities, and base components.
- Each page has an additional stylesheet for page-specific layout and components.

## Development

This is a static site and can be viewed locally in any web server or directly opened in a browser. For improved routing and asset caching in development, use a lightweight server.

### Quick Start

1. Open `index.html` in your browser, or
2. Serve the folder (examples):
   - Node: `npx serve .`
   - Python: `python -m http.server 8080`

### Editing Content

- Add events: edit `events.html` in both the Upcoming list and the Event Details grid. Reference existing entries for structure.
- Add blog posts: append new `<article>` blocks under a category in `blog.html` or create category anchors similar to current sections.
- Update gallery: add new `div.gallery-item` blocks in `gallery.html` and place images under `images/`.
- Update team/membership: edit copy in `about.html` under the hero text.
- Update FAQs: add new `.faq-item` groups in `faq.html`.

### Forms and Handling

- All forms are currently client-side only. Submission is simulated in `js/main.js` and `js/home.js` with a timeout and a success notification.
- To wire up a real backend:
  - Replace the simulated `setTimeout` handlers with `fetch()` calls to your API endpoint.
  - Handle success and error states (update button state, show notifications).

### Theming

- Dark/light theme toggled via the header button in each page using `data-theme` on `<html>` and persisted to `localStorage`.

## Accessibility & Performance Notes

- Semantic HTML, labels for inputs, and `aria` attributes in controls where appropriate.
- Lazy loading and throttled scroll handlers to avoid jank.
- SVG icons inline for crisp rendering.

## Extending the Site

- Add a new section/page: copy an existing page, adjust the nav link, and include `css/style.css` plus any page stylesheet. Keep shared interactions in `js/main.js` and page-specific logic in a dedicated script.
- Internationalization: currently disabled; if needed, reintroduce a selector and key-based `data-i18n` attributes as shown in the removed `setupLanguageSelector` approach.

## License

This project is provided as-is for educational/community purposes. Add your preferred license terms here if needed.
