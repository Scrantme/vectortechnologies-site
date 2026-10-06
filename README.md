# vectortechnologies-site

Public website for **vectortechnologies.ai**, served by GitHub Pages. Plain HTML/CSS, no build step.

| Page | URL | Why it exists |
|---|---|---|
| `index.html` | https://vectortechnologies.ai/ | Landing page with the beta sign-up form |
| `privacy/index.html` | https://vectortechnologies.ai/privacy/ | Privacy policy |
| `terms/index.html` | https://vectortechnologies.ai/terms/ | Terms of service |
| `style.css` | | Shared styles: the app's M18 design system as plain CSS |

**Do not move or remove `/privacy/` or `/terms/`.** Google's OAuth consent screen for the evaluations platform (Google Cloud project `vector-evals`) links to them; breaking them can affect the app's Google Calendar access. If the site moves to another host, keep these URLs working.

## Landing page and beta form

- The wording was approved word for word by the owner (2026-10-06, the "beta landing page messaging" doc). Change it only with the owner's say-so. The statistics cite their source in small print under them.
- Colours and fonts copy the evaluations app's tokens (`src/app/globals.css` in the app repo, where a test checks contrast). Change them there first, then copy them into `style.css`.
- **The form can't save anything by itself** (GitHub Pages serves fixed files only). Its script posts the address to the evaluations app's public endpoint, `https://app.vectortechnologies.ai/api/beta-signup`, which saves it in Supabase (`beta_signups`) and sends the thank-you and the owner's notification. How that works and what to do when it fails: the app repo's `docs/OPERATIONS.md`, section 5d.
- **Changing `style.css`:** also change the `?v=…` date on its `<link>` in **all three** pages (`index.html`, `privacy/`, `terms/`), e.g. `/style.css?v=2026-11-02`. GitHub Pages lets browsers keep a file for 10 minutes, so without a new `?v=` a returning visitor can see the new page with the old styles (it looks unstyled; happened on 2026-10-06).
- The app only accepts the form from `https://vectortechnologies.ai`, `https://www.vectortechnologies.ai` and `http://localhost:8080` (`ALLOWED_ORIGINS` in the app). **If the site's address changes, that list must change too.**

### Previewing locally

1. In the app repo, start the app: `npm run dev` (it serves `http://localhost:3000` and uses the **development** database and email key).
2. In this folder, serve the site: `npx --yes serve -l 8080 .` (downloads a small static server the first time; nothing is added to this repo).
3. Open http://localhost:8080. Opened from `localhost`, the form posts to the local app instead of production, so tests never touch real data.

The privacy policy and terms are **placeholders that need legal review** before real customers or candidates use the platform. Update the "Last updated" date whenever the text changes.

`CNAME` tells GitHub Pages to serve this site at the custom domain.
