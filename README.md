# Prism

Browser-based brand imagery generator. Produces abstract translucent glass forms — fanned rings, stacks, scatters, and grids — rendered in real-time WebGL with photorealistic glass material.

Single self-contained `index.html`. No build step. Three.js loaded from CDN.

---

## Deploy to GitHub Pages

### One-time setup

1. **Create a new repository on GitHub** (public, or private on a paid plan).

2. **Upload these files to the repo.** Either drag-and-drop in the GitHub web UI, or push from your machine:

   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<your-repo>.git
   git push -u origin main
   ```

3. **Enable GitHub Pages** in repo settings:
   - Go to **Settings** → **Pages**
   - Under **Source**, select **GitHub Actions**
   - Save.

4. **Wait for the first deploy.** Pushing to `main` triggers `.github/workflows/deploy.yml`, which builds and publishes. You can watch progress under the **Actions** tab.

5. **Open your site** at:
   `https://<your-username>.github.io/<your-repo>/`

Subsequent pushes to `main` redeploy automatically.

---

## Local preview

Just open `index.html` in a browser. No server needed — it's pure HTML/JS, modules loaded from CDN.

If your browser blocks ES modules from `file://` URLs (some configurations do), serve it with any static server:

```bash
# Python 3
python3 -m http.server 8000

# Node
npx serve .
```

Then visit `http://localhost:8000`.

---

## What's in the package

```
prism/
├── index.html              ← the whole app
├── README.md               ← this file
├── .gitignore
├── .nojekyll               ← stops GitHub Pages from running Jekyll
└── .github/workflows/
    └── deploy.yml          ← auto-deploys to Pages on push to main
```

The `.nojekyll` file is required. Without it, GitHub Pages tries to process the site through Jekyll, which will silently break files and folders starting with underscores.

---

## Using the app

- **Left panel** — Material & Light (color picker, brand palette, light-direction dial, color depth, refraction, polish, bloom, exposure) and Background.
- **Middle** — 3D viewport. Drag to orbit, scroll to zoom.
- **Right panel** — Shape (5 options), Composition (4 layouts), Material style, Form parameters.
- **Top-right** — Theme toggle (light / dark UI), Randomize, and Export (PNG, 8 resolutions from HD to 8K).

The light-direction dial controls where the key softbox falls from — drag the puck around the circle to reposition the harsh side lighting.

Each composition has its own tuned defaults — clicking Tower, Scatter, etc. auto-adjusts sliders to a look that doesn't clip. Sliders stay usable afterwards for fine-tuning.

---

## Browser support

- **Chrome / Edge / Brave / Arc** — full support
- **Firefox** — full support
- **Safari 16+** — full support
- **Mobile** — works but plate count should be reduced on low-end devices

WebGL2 and ES2020 modules required.

---

## Tech notes

- **No backend.** Everything runs in the browser.
- **No persistence.** Each session starts fresh.
- **No analytics, no tracking.** Pure static HTML.
- **Three.js r160** loaded from jsDelivr with unpkg fallback.

---

## License

Add your own — this scaffold is yours to modify.
