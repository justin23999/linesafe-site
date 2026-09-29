# LineSafe website

The official V1 website for **LineSafe — Pipeline Survey & Longitudinal Profile**.

## 1. Purpose

This is the public website for the LineSafe app. It provides:

- Product information and the V1 feature list
- The Privacy Policy (to be linked from the Google Play listing)
- User support information
- A place for the Google Play download link once the app is published

It is a plain static site (HTML and CSS only, no JavaScript, no build step) designed to be hosted for free on GitHub Pages.

## 2. File structure

```
linesafe website/
├── index.html        Home page: hero, features, workflow
├── privacy.html      Privacy Policy
├── support.html      Support page
├── styles.css        Shared stylesheet for all pages
├── README.md         This file
└── assets/
    └── linesafe-icon.png   App icon (header, favicon, hero)
```

All internal links and asset paths are **relative** (`privacy.html`, `assets/linesafe-icon.png`), so the site works both from a local folder and from a GitHub Pages sub-path such as `/linesafe-site/`. Do not change them to root-absolute paths like `/privacy.html`.

## 3. Preview locally

Option A: open the file directly. Double-click `index.html`, or run in PowerShell:

```powershell
Start-Process "D:\linesafe website\index.html"
```

Option B: run a small local web server (closer to how GitHub Pages serves it). If Python is installed:

```powershell
cd "D:\linesafe website"
python -m http.server 8000
```

Then open <http://localhost:8000/> in a browser. Press `Ctrl+C` to stop the server.

## 4. Support email

The support address is `linesafe.app.support@gmail.com`. It appears in `privacy.html` and `support.html`, both as visible text and inside `mailto:` links.

To change it, use VS Code's **Replace in Files** (`Ctrl+Shift+H`): search for the current address, enter the new one, and click **Replace All**. Then search again to confirm no occurrences of the old address remain.

## 5. Update screenshots and assets

- Put images in the `assets/` folder and reference them with relative paths, e.g. `<img src="assets/screenshot-profile.png" alt="Longitudinal profile screen">`.
- Always include meaningful `alt` text.
- Keep file names lowercase with hyphens, no spaces (GitHub Pages URLs are case-sensitive).
- Keep images reasonably small (under about 500 KB each). PNG suits UI screenshots.
- To change the icon, replace `assets/linesafe-icon.png` with a new file of the same name. The originals live in the Flutter project at `assets/branding/`; copy from there and never edit those originals.
- The hero on the home page currently shows a schematic SVG illustration (drawn in `index.html`), not a screenshot. You can replace the `<figure class="profile-figure">` block with a real app screenshot later.

## 6. Create a GitHub repository named `linesafe-site`

1. Sign in to <https://github.com>.
2. Click **+** (top right), then **New repository**.
3. Repository name: `linesafe-site`.
4. Visibility: **Public** (GitHub Pages on a free account requires a public repository).
5. Do **not** add a README, `.gitignore` or licence (this folder already has a README).
6. Click **Create repository**.

## 7. Push this folder to GitHub

Requires Git for Windows. In PowerShell:

```powershell
cd "D:\linesafe website"
git init
git add .
git commit -m "LineSafe website V1"
git branch -M main
git remote add origin https://github.com/justin23999/linesafe-site.git
git push -u origin main
```

If your GitHub username is different, change `justin23999` in the remote URL.

## 8. Enable GitHub Pages from the `main` branch

1. Open the repository on GitHub.
2. Go to **Settings**, then **Pages** (left sidebar).
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
4. Set **Branch** to `main` and folder to `/ (root)`, then click **Save**.
5. Wait a minute or two, then refresh the Pages settings screen. It will show the live URL.

Later changes are published by committing and pushing again:

```powershell
git add .
git commit -m "Describe the change"
git push
```

## 9. Final URL

With the username `justin23999` and repository `linesafe-site`, the site will be at approximately:

- Home: <https://justin23999.github.io/linesafe-site/>
- Privacy Policy: <https://justin23999.github.io/linesafe-site/privacy.html>
- Support: <https://justin23999.github.io/linesafe-site/support.html>

Use the Privacy Policy URL in the Google Play Console.

## Before publishing

- Review `privacy.html` against the final production Android build and your Google Play Data Safety answers (see the comment at the top of that file).
- Add the Google Play download link to `index.html` once the listing is live.
