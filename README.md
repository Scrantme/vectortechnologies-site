# vectortechnologies-site

Public website for **vectortechnologies.ai**, served by GitHub Pages. Plain HTML/CSS, no build step.

| Page | URL | Why it exists |
|---|---|---|
| `index.html` | https://vectortechnologies.ai/ | Company home page |
| `privacy/index.html` | https://vectortechnologies.ai/privacy/ | Privacy policy |
| `terms/index.html` | https://vectortechnologies.ai/terms/ | Terms of service |

**Do not move or remove `/privacy/` or `/terms/`.** Google's OAuth consent screen for the evaluations platform (Google Cloud project `vector-evals`) links to them; breaking them can affect the app's Google Calendar access. If the site moves to another host (e.g. Lovable), keep these URLs working.

The privacy policy and terms are **placeholders that need legal review** before real customers or candidates use the platform. Update the "Last updated" date whenever the text changes.

`CNAME` tells GitHub Pages to serve this site at the custom domain.
