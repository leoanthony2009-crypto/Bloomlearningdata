# Bloom Learning Lab 02 — Using Data to Direct School Improvement

Single-file build: every image, script and style is baked into the HTML. No `assets/` folder needed.

- `index.html` — the course (served at `/`)
- `verify.html` — credential verification page (`/verify?id=…`)
- `forms.html` — registers the Netlify `course-rating` form
- `netlify/functions/` — issue / verify / revoke credential functions
- `netlify.toml`, `package.json` — Netlify config

## Deploy
Push to GitHub → Netlify "Import from Git" → build command empty, publish `.`.
Ratings arrive under Netlify → Forms → course-rating; enable *Form notifications* there to route them to your email/Slack.

## GitHub Pages (images only, no credentials/ratings)
Settings → Pages → deploy from `main` / root. `index.html` works as-is.
