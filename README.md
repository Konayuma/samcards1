# Samcards — Consultation (static site)

Simple static landing page for Samcards offering consultations. The site is a plain static site (no build step).

Cloudflare Pages (recommended):

- Git-based: Push this folder to a GitHub or GitLab repo, then create a new Pages project in the Cloudflare dashboard and connect the repo. Set the "Build command" empty and "Build output directory" to the project root ("./").
- Wrangler CLI (direct publish): Install the Cloudflare Wrangler CLI and publish directly from the local directory. This requires a Cloudflare API token with Pages permissions.

Wrangler publish example:

```bash
npm install -g wrangler
wrangler login                # opens browser to authenticate
wrangler pages publish . --project-name=samcards
```

Notes:
- If using Git integration, Cloudflare Pages will build and publish on each push to the connected branch.
- If you prefer me to deploy from this environment, I can run the `wrangler pages publish` command here — I'll need a Cloudflare API token or to run `wrangler login` interactively.

Existing Netlify instructions (left for reference):

- Netlify CLI quick deploy:

```bash
npm install -g netlify-cli
netlify login
netlify deploy --dir=.         # creates a draft URL
netlify deploy --prod --dir=.  # publish to production
```
