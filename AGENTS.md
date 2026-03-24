# AGENTS.md

This repository is a small static personal website hosted on Firebase Hosting.

## Purpose

The repo contains:

- The main personal homepage at `index.html`
- Two static legal pages for the Card Binder app in `card_binder/`
- A separate static World Cup betting microsite in `laporra/`

There is no application backend, no package manager, and no build pipeline beyond Sass compilation that was historically handled with Prepros.

## Repo Layout

- `index.html`: main one-page personal website
- `css/`: compiled CSS for the main site and bundled vendor styles
- `sass/`: Sass source for the main site, including a local Bootstrap Sass tree
- `js/`: main site JavaScript and third-party vendor scripts
- `images/`: images used by the main homepage
- `fonts/`: local icon/bootstrap font assets used by the main homepage
- `card_binder/`: static privacy policy and terms pages for Card Binder
- `laporra/`: standalone static microsite with its own assets, fonts, JS, CSS, and form-related vendor files
- `firebase.json`: Firebase Hosting config
- `prepros-6.config`: historical local Sass compilation config

## Main Site Architecture

The main site is a single static HTML page built from a Colorlib-style portfolio template.

Main content sections in `index.html`:

- sidebar / profile / nav
- hero
- about
- counters
- skills
- education
- experience
- work
- contact

Behavior is driven by `js/main.js` using jQuery plugins:

- smooth scrolling between sections
- viewport-triggered animations
- animated counters
- mobile off-canvas nav
- hero flexslider setup

Styling is authored in `sass/style.scss` and compiled to `css/style.css`.

## Deployment

Deployment is intentionally simple:

- Firebase Hosting serves the repo root as `public`
- all routes rewrite to `/index.html`

Typical deploy flow:

1. Update source files
2. If Sass changed, recompile `sass/style.scss` to `css/style.css`
3. Run `firebase deploy`

Keep exact deploy commands and human-facing setup instructions in `README.md`.

Use `AGENTS.md` for workflow expectations and repository behavior, not as the primary human deployment guide.

See `README.md` for command-level deployment steps and `firebase.json` for hosting behavior.

## Editing Guidance

- Prefer editing `sass/style.scss` instead of hand-editing `css/style.css` when changing main site styles.
- If you change Sass, keep the compiled CSS in sync.
- Treat `index.html` as the source of truth for homepage content.
- Be careful not to break the standalone `card_binder/` and `laporra/` pages when making hosting or path changes.
- Preserve static relative paths unless you are intentionally restructuring the repo.

## Legacy / Template Leftovers

This repo predates AI-assisted development and contains template baggage. Before removing anything, verify it is truly unused.

Known leftovers or suspicious areas:

- `index.html` references `fonts/flaticon/font/flaticon.css`, but that path is not present in the repo.
- `js/main.js` still initializes sticky and owl-carousel behavior even though the main page does not obviously use matching elements.
- `js/google_map.js` appears unused by the main page.
- Large parts of `css/`, `js/`, `sass/bootstrap/`, and `laporra/` are vendor/template assets.
- Some content in `index.html` is historically stale or inconsistent across sections.

Do not remove vendor files aggressively unless the task explicitly includes cleanup and you have confirmed they are not referenced.

## Content Notes

Current homepage content is hardcoded directly in HTML. There is no CMS, no JSON content source, and no server-side rendering.

That means:

- copy changes are direct HTML edits
- new sections usually require both HTML and CSS updates
- SEO/meta improvements require manual updates in `index.html`

## Microsites

### `card_binder/`

Contains:

- `privacyPolicy.html`
- `termsAndConditions.html`

These are plain static legal pages for the Card Binder app.

### `laporra/`

Contains a self-contained promotional/information page for a 2022 betting pool. It has its own:

- HTML
- CSS
- JS
- fonts
- images
- auxiliary vendor files

Treat it as a separate static site living inside the same Firebase-hosted repo.

## Agent Expectations

When working in this repo:

- start by identifying whether the task affects the main homepage, Card Binder pages, or the `laporra` microsite
- avoid introducing unnecessary tooling unless explicitly requested
- prefer minimal static-site changes over framework migrations
- preserve the current deployment model unless the user asks for a larger modernization
- call out stale content, broken links, and unused assets when relevant, but do not clean them up implicitly

## Safe First Checks

Before substantial edits, it is usually worth checking:

- `index.html`
- `sass/style.scss`
- `js/main.js`
- `firebase.json`
- whether referenced assets actually exist

## Out of Scope Assumptions

Do not assume:

- there is a Node-based build
- there are tests
- there is a component system
- there is any runtime other than static hosting in the browser

Keep solutions simple and static by default.
