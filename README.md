# Public website (GitHub Pages)

Static site that mirrors the in-app legal copy. Used for the public
**Privacy URL** required by the App Store and Play Store listings.

## Files

- `index.html` — landing page
- `privacy.html` — privacy notice
- `disclaimer.html` — medical disclaimer
- `about.html` — about the project
- `styles.css` — shared styles
- `.nojekyll` — disables Jekyll processing

## Recommended setup (no personal username in the URL)

This gives you the cleanest URL: `https://zambia-anaesthesia-hub.github.io/privacy.html`

### Step 1 — Create a free GitHub organization

1. Go to <https://github.com/account/organizations/new>.
2. Pick the **Free** plan.
3. Organization account name: `zambia-anaesthesia-hub`
   (if taken, try `zambiaanaesthesiahub` or similar — whatever you choose
   will be your URL prefix).
4. Contact email: `zambiaanaesthesiahub@gmail.com`.
5. Skip invitations, skip the survey.

### Step 2 — Create the website repo

In the new org:

1. **New repository**.
2. Repository name: **must exactly match `<org-name>.github.io`**.
   For example: `zambia-anaesthesia-hub.github.io`.
3. Visibility: **Public** (required for free Pages).
4. Do **not** initialize with a README — we will push our own files.
5. Click **Create repository**.

### Step 3 — Push the `website/` folder to that repo

From this project root:

```sh
cd website
git init
git add .
git commit -m "Initial public site"
git branch -M main
git remote add origin git@github.com:<org-name>/<org-name>.github.io.git
git push -u origin main
```

(Replace `<org-name>` with whatever you picked in Step 1.)

### Step 4 — Enable Pages

1. In the new repo: **Settings → Pages**.
2. **Source = Deploy from a branch**.
3. **Branch = main**, **Folder = `/` (root)**.
4. **Save**. Wait ~1 minute.

### Step 5 — Verify

Open the live URLs:

- `https://<org-name>.github.io/`
- `https://<org-name>.github.io/privacy.html`
- `https://<org-name>.github.io/disclaimer.html`
- `https://<org-name>.github.io/about.html`

### Step 6 — Wire the URL into store listings

- **App Store Connect** → App Privacy → **Privacy Policy URL**:
  `https://<org-name>.github.io/privacy.html`
- **Google Play Console** → Store listing → **Privacy Policy**:
  `https://<org-name>.github.io/privacy.html`
- Mark the privacy-URL item as done in `docs/release-checklist.md`.

## Alternative: custom domain

If you later buy a domain (e.g. `zambiaanaesthesiahub.org`):

1. Add a file named `CNAME` in this folder containing just the apex domain.
2. In your DNS provider, add the GitHub Pages `A` records and a `CNAME`
   for `www`. GitHub's docs walk through this.
3. **Settings → Pages → Custom domain** in the repo, paste the domain,
   tick **Enforce HTTPS**.

URL becomes: `https://zambiaanaesthesiahub.org/privacy.html`.

## Keeping copy in sync

The same wording lives in the app at
`app/lib/features/legal/legal_copy.dart`. When you change one, change the
other so the public site and the in-app screens stay aligned.

