# NYXE — SPHEREx Time-Domain Astronomy & Citizen Science Console

NASA Space Apps Challenge prototype ("Planet X and SPHEREx" challenge), built by **Elif Turut**.

- **Live demo:** served from this repo via GitHub Pages — see the "About" link on the repository page once Pages is enabled.
- **`index.html`** — the complete, self-contained app (bundled React + Tailwind + icons, no CDN dependencies). Open it directly in any browser, or host it as a static site.
- **`App.jsx`** — the React source.

## Real data
NYXE queries live NASA/IPAC IRSA (SPHEREx), CDS (SIMBAD, VizieR, Sesame), IMCCE (SkyBoT) and CADC (NEOSSat) from the viewer's own browser. If a primary service is blocked on a given network, it automatically retries official mirrors (e.g. SIMBAD via the Harvard and IDIA mirrors, Sesame via the CfA mirror) before giving up; each service's route can also be overridden to a custom address in the app's "Data routes" panel. A built-in Connection test diagnoses *why* a network is blocked (CSP, offline, iframe sandbox, or every host refused too fast to have reached a server) and a downloadable Python script (`nyxe_fetch.py`, generated from inside the app) can fetch the same cutouts from the user's own machine as a fallback.

## Why this needs a normal static host
This app's real-data tab performs outbound `fetch` calls to third-party astronomy services. A sandboxed hosting environment that blocks all outbound network requests (many "AI artifact" preview sandboxes do this by design) will never be able to reach them — GitHub Pages serves plain static files with ordinary browser network rules, so these calls work exactly as they would from any other website.

## Use of AI tools (Super Intelligence)
This project's code was developed with the help of an AI coding assistant (Claude, by Anthropic) working under the author's direction throughout — writing and revising the React/JS implementation, the automated Playwright regression suite, and this documentation. All data-source integrations, scientific content, UI/UX decisions and the project's scope were specified and reviewed by the author. No NASA branding, logos, flags or mission identifiers were AI-generated, and no AI image/video generation was used anywhere in the app. The same disclosure is shown in-app under "About NYXE".

---
© Elif Turut — NASA Space Apps Challenge prototype. Not an official NASA or SPHEREx product.
