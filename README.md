# HONIORA site — deployment notes

## What's in this package

- `index.html` — the entire site (markup, CSS, and JS all in one file).
- Every image, video, and icon file — hero shots, nav hex buttons, pillar icons, the Mānuka vista banner, and all 13 ingredient photos used in the Stack section — sits flat in the same folder as `index.html`, referenced as plain filenames like `hero-glass.jpg` or `cGP-Pro_blackcurrant.jpg`. There is no `ingredients/` subfolder — everything is one level, beside `index.html`.

## How to host it

This is a static site with no build step. Upload the whole folder as one flat directory — `index.html` and every image/video file beside it, no subfolders. If any image lands in a different folder than `index.html`, or in a subfolder, it will fail to load even though the page itself renders fine, since every image path in the HTML is relative to where `index.html` lives.

For GitHub Pages specifically: commit the folder as-is, flat, to the repo (or the branch/folder GitHub Pages is configured to serve from). Do not nest the images into subfolders or rename files — the HTML references exact filenames.

## Version

This package corresponds to HONIORA_site_v104, updated 2026-08-31.

Recent changes in this version:
- Pillar icon images (NZ map, mitochondria, heart, H2O droplet) reverted to their original size after a temporary doubling.
- "4D" nav link moved to the right of the HONIORA logo in the nav bar; nav spacing re-verified across desktop widths.
- Braincurrant® copy in the Stack section rewritten.
- Ingredient images moved out of the `ingredients/` subfolder and flattened into the same folder as `index.html`; all `src` paths updated to match.
