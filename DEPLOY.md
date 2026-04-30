# Deploy the deck to GitHub Pages

The deck is a single static `index.html` plus an `assets/` folder. GitHub Pages serves static sites for free with a one-time setup.

## What you'll get

A public URL you can share with attendees:

```
https://<your-github-username>.github.io/<repo-name>/
```

Anyone with the URL can open the deck. No login, no install. Works on phones, laptops, projector machines.

## One-time setup (~5 minutes)

### 1 · Create a GitHub repo for the deck

```bash
cd "/Users/Ismail/Documents/Keeta/docs/Agentic AI Session/presenation"
git init
git add .
git commit -m "Initial deck"
```

Create an empty public repo on github.com (e.g. `agentic-design-system-masterclass`). Don't add a README or .gitignore — just an empty repo.

Then:

```bash
git branch -M main
git remote add origin https://github.com/<your-username>/agentic-design-system-masterclass.git
git push -u origin main
```

### 2 · Enable GitHub Pages

On the repo page in GitHub:

1. **Settings** → **Pages** (left sidebar)
2. **Source**: *Deploy from a branch*
3. **Branch**: `main` · **Folder**: `/ (root)` · **Save**

GitHub builds the site within ~30 seconds. The Pages URL appears at the top of the same Settings → Pages page once ready.

### 3 · Visit your URL

```
https://<your-username>.github.io/agentic-design-system-masterclass/
```

The deck loads, all assets work (logos, welcome-bg.jpg, welcome-logo.png, qr-menti.png once you add it).

## Updating the deck

Every push to `main` triggers a redeploy in ~30 seconds:

```bash
git add .
git commit -m "Tweak slide 42"
git push
```

Refresh the live URL — changes appear after the rebuild finishes (watch *Actions* tab in GitHub for status).

## Custom domain (optional)

If you have a domain (e.g. `masterclass.keeta.app`), add a `CNAME` file with one line containing the domain, push, then point your DNS `CNAME` record at `<your-username>.github.io`. GitHub Pages handles HTTPS automatically.

## Day-of-session checklist

- [ ] Public URL works on the venue's machine (test before presenting)
- [ ] `assets/qr-menti.png` is in the repo and committed (the QR points to the live Menti URL)
- [ ] Mentimeter placeholders in `index.html` are replaced with the real values
- [ ] Open the deck URL on the projector machine in the morning, advance through it once

## Trade-off vs `file://`

| | `file://` (open locally) | GitHub Pages |
|---|---|---|
| Open with one click | ✓ | (requires URL) |
| Works offline | ✓ | (requires internet) |
| Shareable URL | ✗ | ✓ |
| Fonts, popups, third-party iframes | ⚠ flaky | ✓ |
| Mentimeter iframe | broken | still walled (Free tier) |

Hosting fixes the file:// quirks. The Menti embed is *still* walled because that's a Mentimeter Free-tier policy, not a browser issue. The mint *"Open live results in Mentimeter"* button on slide 5.5 is the production path either way.

## Backup plan

Always have the deck folder cached locally too — if conference wifi dies, you can still open `index.html` directly from your laptop. The deck is fully offline-capable except for the live Menti results (which need the internet anyway).
