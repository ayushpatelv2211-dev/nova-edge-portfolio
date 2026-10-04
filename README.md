# NOVA EDGE — Creative Agency Portfolio

> "We make brands impossible to ignore."

Portfolio website for **NOVA EDGE**, a creative agency from Ahmedabad, India —
Video Editing · Graphic Design · Website Design · Social Media Management.

## Tech

- Single-file static site: `index.html` (HTML + CSS + JS inline, zero dependencies)
- Project visuals in `assets/`
- No build step, no framework — works on any static host

## Run locally

```bash
# Python
python3 -m http.server 8000

# or Node
npx serve .
```

Then open http://localhost:8000

## Deploy

Push to GitHub and connect the repo to any of these (no build settings needed):

- **Vercel** — Import repo → Deploy (framework preset: Other)
- **Netlify** — Import repo → Deploy (build command: empty, publish dir: `.`)
- **GitHub Pages** — Settings → Pages → Deploy from branch → `main` / root
- **Cloudflare Pages** — Connect repo → Deploy (no build command)

## Videos

Project films stream from [Mux](https://mux.com). Each project in the `CASES` array
(`index.html`) carries its own `pid` (Mux playback id), `orient` (`landscape` 16:9 or
`portrait` 9:16), `dur`, and `frames` (timecodes for the case-study frame strip).

To swap a film, edit that entry — posters, previews, case players and frame grabs all
follow automatically (frames are served live from `image.mux.com/{pid}/thumbnail.jpg`).
Local posters live in `assets/poster-*.jpg` (regenerate from any frame via
`https://image.mux.com/{pid}/thumbnail.jpg?time={seconds}&width={w}`).

## Structure

```
nova-edge/
├── index.html        # complete site (styles + scripts inline)
├── assets/           # poster frames (Stroom, NemPanth, Elite Sport, Sardardham, LDCE, Ecstacy)
└── README.md
```

© 2026 NOVA EDGE — Ahmedabad, Gujarat, India.
