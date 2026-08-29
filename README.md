# HoniOra site

Marketing site for HoniOra. Single-page, static HTML.

## Structure

- `index.html` — the full desktop/tablet build. All CSS and JS are inline (no separate `.css` or `.js` files).
- `lite.html` — a lighter build for phones: no hero video (a static poster image instead), no GSAP/ScrollTrigger, the ingredient rail stacks instead of pinning and scrolling horizontally. Same content and copy otherwise.
- `index.html` redirects phone-width visitors (`max-width:760px`) to `lite.html` automatically, via a small inline script at the top of `<head>`. Add `?full=1` to the URL to stay on the full build on a phone.
- Everything else in this folder, flat, no subfolders, is an image or video asset referenced by `index.html` / `lite.html` via relative path.

## Running locally

No build step. From this folder:

```
python3 -m http.server 8000
```

Then open `http://localhost:8000`.

## Deploying (e.g. GitHub Pages)

Push this whole folder as-is, keeping every asset in its current relative location. Nothing needs to be split out or bundled. The phone redirect (`index.html` → `lite.html`) works the same way on GitHub Pages since it's plain client-side JavaScript, no server config needed.

The only external dependency is GSAP + ScrollTrigger, loaded from the public cdnjs CDN in the `<head>`:

```
https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js
https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollTrigger.min.js
```

They power the pinned horizontal ingredient scroll and the scroll-reveal animations. Everything else on the page works with no dependencies.
