# Bloom Learning Lab 02 — Using Data to Direct School Improvement

Interactive 30-minute micro-course for principals and school leaders. Static site + Netlify Functions.

## Run locally
Open `Using Data Micro Course (interactive).dc.html` in a browser (or `npx serve .`). Credential issue/verify and rating submission need the Netlify deploy.

## Deploy
See `DEPLOY.md`. Push this folder to GitHub → Netlify "Import from Git" → publish `.`; functions auto-detected from `netlify/functions`.

## Where feedback goes
- **Course ratings** → Netlify Forms, form name `course-rating` (fields: name, stars, useful, text, credId, course).
  Netlify dashboard → Forms → course-rating. Turn on **Form notifications** (email/Slack) there so each rating is routed to you.
- **Credentials** → Netlify Blobs store `credentials` (issue.js). Public lookup via `/verify?id=…`.
- Nothing else leaves the learner's device; lesson notes and progress stay in localStorage.

## Files
| Path | Purpose |
| --- | --- |
| `Using Data Micro Course (interactive).dc.html` | The course |
| `Verify.dc.html` | Credential verification page |
| `Using Data Micro Course.dc.html` + `deck-stage.js` | Facilitator slide deck (22 slides) |
| `support.js` | Runtime for `.dc.html` pages |
| `assets/` | Hero image, silver badge |
| `forms.html` | Registers the Netlify form |
| `netlify/functions/` | issue / verify / revoke |
| `netlify.toml`, `package.json` | Netlify config |
