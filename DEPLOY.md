# Deploying the Mindbook prototypes (shareable link)

The site is static (no build). The whole thing is `index.html` (the hub) + `prototypes/` + `assets/`. Any static host works. Two easy paths:

## Option A — Netlify Drop (no CLI, ~30 seconds)

1. Open **https://app.netlify.com/drop**
2. Drag the file **`mindbook-prototypes.zip`** (in the repo root) onto the page — or drag the whole `mindbook` folder.
3. Netlify gives you a live link instantly (e.g. `https://something-random.netlify.app`).
4. (Optional) Sign in with GitHub to keep the site, rename it (`mindbook-mvp.netlify.app`), and password-protect it under Site settings → Access.

Share that link with your co-founder. The link is unguessable; it is not indexed unless you make it so.

## Option B — Netlify CLI (one-time login, keeps deploys repeatable)

```bash
cd ~/mindbook
npx netlify-cli login        # opens a browser once to authorize
npx netlify-cli deploy --dir . --prod   # first run: choose "Create & configure a new site"
```

The final `--prod` line prints your live URL each time you run it, so re-deploying after design changes is one command.

## Option C — Vercel CLI

```bash
cd ~/mindbook
npx vercel        # first run: login (browser) + "set up and deploy" → accept defaults
npx vercel --prod # promotes to the production URL
```

## Keeping it private

- Netlify: Site settings → Access & security → **Password protection** (free) or **Visitor access** (Pro) so only people with the password can view.
- Vercel: Project → Settings → **Deployment Protection** (Vercel Authentication / password).

## Custom domain (later)

Point `design.mindbook.africa` (or similar) at the Netlify/Vercel site under Domain settings.
