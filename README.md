# www.nicoyuste.es

Static personal website hosted on Firebase Hosting.

This repository contains a small personal site for Nicolas Yuste plus a couple of standalone static pages and microsites that live in the same hosting project.

## What Is In This Repo

- `index.html`: main one-page personal website
- `sass/`: Sass source for the main site
- `css/`: compiled CSS and bundled vendor styles for the main site
- `js/`: homepage behavior and bundled vendor scripts
- `images/`: images used by the main homepage
- `card_binder/`: legal pages for the Card Binder app
- `laporra/`: standalone static betting-pool microsite and its assets
- `firebase.json`: Firebase Hosting configuration
- `AGENTS.md`: repository guidance for coding agents and automation

## Main Site

The main website is a static single-page site built around:

- hardcoded HTML content in `index.html`
- Sass styling in `sass/style.scss`
- compiled CSS in `css/style.css`
- jQuery-based interactions in `js/main.js`

There is no backend, no CMS, and no package-based frontend toolchain in this repo.

## Editing Workflow

For most homepage changes:

1. Update content in `index.html`
2. Update styles in `sass/style.scss` if needed
3. Recompile Sass so `css/style.css` stays in sync
4. Test locally in a browser
5. Deploy to Firebase Hosting

When changing styles, prefer editing the Sass source instead of only changing the compiled CSS.

## Deployment

Everything is hosted in Firebase.

### Prerequisites

Install the Firebase CLI if you do not already have it:

```bash
curl -sL firebase.tools | bash
```

You also need to be authenticated with the correct Firebase account before deploying.

### Deploy

Run:

```bash
firebase deploy
```

## Hosting Behavior

Firebase Hosting is configured to:

- serve the repository root as the public directory
- ignore hidden files and `node_modules`
- rewrite all routes to `/index.html`

That configuration lives in `firebase.json`.

## Notes

- This repo includes legacy template/vendor assets. Not every file is hand-authored.
- `card_binder/` and `laporra/` should be treated as separate static surfaces inside the same hosted project.
- For agent-specific workflow guidance, assumptions, and repository boundaries, see `AGENTS.md`.
