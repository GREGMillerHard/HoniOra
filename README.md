# HoniOra site

Marketing site for HoniOra. Single-page, static HTML.

## Structure

- `index.html` — the entire page. All CSS and JS are inline (no separate `.css` or `.js` files).
- Everything else in this folder is an image or video asset referenced by `index.html` via relative path (`ingredients/` holds the per-active ingredient photos).

## Running locally

No build step. From this folder:

```
python3 -m http.server 8000
```

Then open `http://localhost:8000`.

## Deploying (e.g. GitHub Pages)

Push this whole folder as-is, keeping every asset in its current relative location. Nothing needs to be split out or bundled.

The only external dependency is GSAP + ScrollTrigger, loaded from the public cdnjs CDN in the `<head>`:

```
https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js
https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollTrigger.min.js
```

They power the pinned horizontal ingredient scroll and the scroll-reveal animations. Everything else on the page works with no dependencies.
