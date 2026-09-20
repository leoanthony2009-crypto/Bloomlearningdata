# Deploying Bloom Learning Lab 02 to Netlify

## Files
- `Using Data Micro Course (interactive).dc.html` — the course (served at `/`)
- `Verify.dc.html` — public verification page (`/verify?id=…`)
- `forms.html` — registers the `course-rating` Netlify Form (static detection)
- `netlify/functions/issue.js` — POST `/api/issue` → creates `BLL02-XXXXXX`, stores the record (Blobs store `credentials`)
- `netlify/functions/verify.js` — GET `/api/verify?id=` → public record (no IP, no free-text)
- `netlify/functions/revoke.js` — POST `/api/revoke` (header `x-admin-key`) → marks revoked
- `netlify.toml`, `package.json`, `support.js`

## Deploy
1. Push to a Git repo; Netlify → Add new site → Import from Git. Build command empty; publish `.`.
2. Environment variable `ADMIN_KEY` (only for revoking).
3. Deploy. QR/verify URLs follow the site's own origin automatically.

## Behaviour
- On certificate unlock the course POSTs to `/api/issue`; the returned ID prints on the certificate with a QR to `/verify?id=…`.
- Offline / local file: falls back to a device-local ID `BLL02-L0001` and the certificate says "Local record — not registered online".
- Ratings POST to Netlify Forms (`course-rating`): name, stars, useful, text, credId, course. View under Forms in the Netlify dashboard.
- **Route ratings to your inbox:** Netlify → Site → Forms → course-rating → *Form notifications* → add Email (or Slack webhook). Every submission is then forwarded automatically.
- The course confirms "Your feedback has been recorded" only when Netlify returns 200; otherwise it saves the rating on the device and says so.
