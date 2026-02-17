# James Tartaglia Personal Website

Personal website for James Tartaglia — British philosopher at the Slovak Academy of Sciences and jazz musician making Jazz-Philosophy Fusion.

**Stack:** HTML5 · CSS3 · Bootstrap 5 · SASS · Parcel 2 · vanilla JS

---

## Quick Start

```bash
# Install dependencies
npm install

# In one terminal: compile SASS and watch for changes
npm run sass

# In another terminal: start the Parcel dev server
npm run dev
```

The dev server will open automatically at `http://localhost:1234`.

---

## Build for Production

```bash
# Compile SASS first
npm run sass:build

# Then bundle all pages
npm run build
```

Output goes to `dist/`. The `dist/` folder is gitignored — deploy its contents to your host.

---

## Content Editing

### Updating the Bio (index.html)

The intro text is in the `<!-- Section: Introduction -->` block around line 80. Edit the `<p>` tag inside `.col-md-5`.

### Adding a Book Quote (index.html)

Copy an existing `<figure>` block inside a book section and update the `<blockquote>` text and `<figcaption>` attribution.

### Adding a Jazz Recording (jazz.html)

Copy an existing `<div class="accordion-item">` block inside `#magazineAccordian` and update:
- The `id` attributes (heading and collapse must match and be unique)
- The accordion button text (album title and year)
- The album cover `<img>` and description `<p>`
- Each `<audio>` source `src` path pointing to an MP3/M4A in the `audio/` directory

> **Note:** Audio files are gitignored due to size (~205 MB). They must be deployed separately — copy the `audio/` directory manually to your host alongside the built site files.

### Adding a Publication (philosophy.html)

Add a new `<div class="accordion-item">` inside the relevant accordion (`#journalAccordian`, `#bookChaptersAccordian`, etc.). Follow the pattern of existing items — include the citation in the button and a short summary + PDF link in the body.

### Adding a Media Link (media.html)

Add a new `<li class="media-link">` inside `<ul class="media-list">`:

```html
<li class="media-link">
    <a href="https://example.com/article" target="_blank" rel="noopener noreferrer">
        Article Title
    </a>
</li>
```

---

## Project Structure

```
/
├── sass/                  # SASS source files (edit these, not css/)
│   ├── style.scss         # Manifest — imports all partials
│   ├── _bootstrapTheme.scss  # Bootstrap 5 colour customisation
│   ├── _common.scss       # Global body/element styles
│   ├── _header.scss       # Navigation bar
│   ├── _footer.scss       # Footer
│   ├── _home.scss         # Home page specific
│   ├── _cards.scss        # Feature cards
│   ├── _books.scss        # Book sections
│   ├── _articles.scss     # Media/publications lists
│   ├── _jazz.scss         # Jazz page audio player
│   ├── _animations.scss   # Keyframes + prefers-reduced-motion
│   ├── _colors.scss       # Colour palette variables
│   └── _variables.scss    # Breakpoint strings
├── css/
│   ├── main.css           # HTML5 Boilerplate base (do not edit)
│   └── style.css          # Compiled SASS output (do not edit directly)
├── img/                   # Images
├── audio/                 # Audio files — gitignored, deploy manually
├── doc/                   # PDFs (sample chapters etc.)
├── font/                  # Flaticon icon font
├── js/                    # (Legacy directory — no custom JS currently)
├── index.html
├── jazz.html
├── philosophy.html
├── media.html
└── 404.html
```

---

## Deployment

The site is currently hosted on Apache shared hosting. To deploy:

1. Run `npm run sass:build && npm run build`
2. Upload the contents of `dist/` to the server root via FTP/SFTP
3. Upload the `audio/` directory separately (it is gitignored and not part of the build)

**Security headers** are configured in `.htaccess` for Apache. If you ever move to Netlify, Vercel, or Cloudflare Pages, create a `netlify.toml` / `vercel.json` / `_headers` file with equivalent headers — `.htaccess` is ignored by those platforms.

---

## Design Decisions

- **Bootstrap 5** with a custom colour theme defined in `sass/_bootstrapTheme.scss` via `$theme-colors` merge
- **Flaticon** custom icon font for the three feature card icons (saxophone, philosophy, fusion)
- **Rufina** (Google Fonts) for headings; system font stack (`Gill Sans → Calibri → sans-serif`) for body
- **AOS** (Animate On Scroll) v2.3.4 pinned via unpkg — used on the home page only
- **Bootstrap JS** loaded from jsDelivr CDN (required for navbar collapse, accordions, and modals)
- No framework, no build-time templating — the repeated nav/footer across pages is intentional given the small page count; a templating solution (e.g., Eleventy) would be warranted if more pages are added

---

## Node Version

Node 20 LTS is required. Use `nvm use` (reads `.nvmrc`) or install Node 20 directly.
