# mridhulsharma.com — portfolio

Two modes, both first-class:

- **Pit lane** — `index.html`. Fast, typographic, zero JavaScript. All five case
  studies as text. This is live now.
- **Race mode** — one scroll-driven WebGL scene in five themed sectors. Phase 1
  onward. See [`BRIEF.md`](./BRIEF.md).

## Run it

No build step, no dependencies. Open `index.html`, or serve the folder:

```bash
python -m http.server 8000
# or
npx serve .
```

## Deploy — Cloudflare Pages

1. Cloudflare dashboard → **Workers & Pages** → **Create** → **Pages** →
   **Connect to Git**, and pick `MridhulSharma/portfolio`.
2. Build settings: **framework preset** `None`, **build command** empty,
   **output directory** `/`.
3. Deploy. Every push to `main` republishes.
4. **Custom domain** → add your domain and follow the DNS step.

Chosen over GitHub Pages for bandwidth: Pages has unlimited static requests,
GitHub Pages has a soft 100 GB/month cap. Single assets must stay under 25 MiB
on Cloudflare, which the Phase 1 budget already requires.

GitHub Pages also works if you would rather not add a service — Settings →
Pages → deploy from `main` / root.

## Structure

```
index.html              pit lane — the content lives here, hand-authored
assets/css/tokens.css   design tokens: colour, type, space, motion
assets/css/pitlane.css  pit lane styles
BRIEF.md                full Phase 1 spec — read before writing 3D code
```

`tokens.css` is the single source of truth for the visual system. Phase 1 imports
it rather than redefining anything.

## Before this goes on an application

- [ ] Add contact details to the footer and the links row in `index.html`
      (search for `TODO`). Left blank deliberately rather than guessed.
- [ ] Add an OG image at 1200×630 and set `og:url`.
- [ ] Point a custom domain at it.
