# Glass Studio

A browser-based generator for translucent glass form imagery — built for brand and marketing teams to create on-brand 3D visuals without leaving the browser.

Real WebGL rendering with refraction, attenuation, anisotropy, iridescence, and bloom post-processing. No build step, no dependencies beyond the Three.js CDN.

## Live demo

After deploying, your studio will be available at:

```
https://<your-username>.github.io/<repo-name>/
```

## Features

- **5 shapes**: disc, pill (rounded rectangle), rectangle, square, rounded square
- **6 compositions**: spiral, twist, tower, scatter, grid, ring
- **3 material styles**: layered (default — core+shell for inter-plate refraction), crystal (chunky polished), frosted (lightly etched)
- **14-step brand-blue palette** plus a free custom color picker
- **Slider controls** for element count, twist, taper, spacing, thickness, color depth, refraction (IOR), polish, bloom intensity, and exposure
- **Drag to orbit**, scroll to zoom, randomize button for ideation
- **PNG export** at HD / QHD / 4K / 8K landscape, HD / 4K portrait, or 2K / 4K square — with aspect-correct camera reframing

## Deploying to GitHub Pages

### Option A — push to a new repo

1. Create a new repository on GitHub (public or private with Pages enabled).
2. Clone it locally and copy this `index.html` into the root.
3. Commit and push:

   ```bash
   git add index.html README.md
   git commit -m "Deploy Glass Studio"
   git push origin main
   ```

4. In the repo on GitHub: **Settings → Pages**. Under "Source", choose **Deploy from a branch**, pick `main` and `/ (root)`, click Save.
5. Wait ~30 seconds. The URL appears at the top of the Pages settings page.

### Option B — upload via the GitHub web UI (no command line)

1. Create a new repository on GitHub.
2. On the empty-repo page, click **uploading an existing file**.
3. Drag `index.html` and `README.md` into the upload zone.
4. Commit directly to `main`.
5. Go to **Settings → Pages**, set source to `main` / `/ (root)`, save.

## Local preview

The file works directly from disk in any modern browser — just open `index.html`. For best results (some browsers restrict `file://` for ES modules), use any static server:

```bash
# Python 3
python3 -m http.server 8000

# Node.js
npx serve .
```

Then open `http://localhost:8000`.

## Browser support

Requires a browser with WebGL 2 and ES module support. Tested on Chrome, Edge, Safari, and Firefox (last two major versions of each). Mobile Safari and Chrome Android work but performance scales with the device — drop the element count slider on lower-end hardware.

## Tech notes

- Three.js r160 loaded via ES module from `jsdelivr` (with `unpkg` fallback baked in)
- `MeshPhysicalMaterial` with `transmission`, `attenuationColor`, `iridescence`, `anisotropy`, and (where supported) `dispersion`
- Procedural studio environment baked via `PMREMGenerator` — no external HDR needed
- `UnrealBloomPass` post-processing for highlight glow
- Core + shell dual-mesh technique so each glass plate visibly refracts the other plates around it

## License

Add a license file (MIT, Apache 2.0, etc.) before publishing if you intend others to reuse this.
