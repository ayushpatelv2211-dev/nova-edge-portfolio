# NOVA EDGE — Portfolio Page Review

_Analyzed: clone of `novaedge73/nova-edge-portfolio` (index.html, 1,470 lines, 6 image assets) — Oct 2026_

---

## 1. What the site is today

- **Stack:** one self-contained `index.html` (CSS + JS inline), zero dependencies, 6 JPEGs in `assets/`. Deployable anywhere static.
- **Art direction:** black / bone / neon `#D6FF3F`, Anton + Instrument Serif + Space Grotesk. Editorial "brutalist + neon" look. Very consistent.
- **Sections:** preloader → hero → marquee → manifesto → work ("select a world") → services → about/founders → process → why → receipts → status terminal → contact → footer, plus a case-study overlay and a showreel modal.
- **Motion already in place:** preloader counter + clip-path exit, word-split reveals, fade-up reveals, tilted marquee, magnetic buttons, custom cursor (VIEW/PLAY/DRAG/EXPLORE/LET'S TALK), hero glow-follow + depth parallax, hero word-roller, hover-driven work/services stages with per-project mood color, case-study wipe transition + drag-scroll frames + next-project flow, process line that fills on scroll, WebAudio UI sounds (off by default).
- **A11y/SEO already in place:** `prefers-reduced-motion` support, noscript fallbacks, skip link, aria labels, JSON-LD Organization, OG text, semantic HTML.

**Verdict:** the foundation and motion craft are already above average. The gap is not "more polish on the code" — it is **graphics credibility** and a handful of **signature motion upgrades**.

---

## 2. Findings — graphics & assets (highest priority)

The tagline literally says *"the website is the portfolio"*, so the visuals are the pitch. Right now they undercut it:

| Project | Case study says | Image shows | Problem |
|---|---|---|---|
| Stroom | Energy label identity | STROOM drink branding mockup | ✅ Fits |
| Ecstacy | Experimental motion/type | Chrome/fluid abstract | ⚠️ Fits subject, but AI-garbled lettering ("RAWE MOTION FORMS") is readable at full width |
| NemPanth | Community storytelling, warm & human | Athlete with neon speed lines | ❌ Reads as sports ad — wrong project |
| Elite Sport | Sports advertising, match-day hype | Sci-fi HUD dashboard | ❌ Wrong subject entirely |
| Sardardham | Prestige film for a Gujarati landmark | Thai temple at dusk | ❌ Wrong country's landmark |
| LDCE | Tech-fest website/UI | Illuminated royal palace | ❌ Wrong subject entirely |

Specific issues:

1. **Image ↔ project mismatches** (4 of 6). A prospective client scrolling the work wall will notice the runner isn't "community storytelling" and the Thai temple isn't Sardardham. For a design agency, this is the single biggest trust risk.
2. **AI-generation artifacts are visible** — garbled pseudo-text in `work-ecstacy.jpg` and `work-elite.jpg`. Fine as mood-boards, not fine as "selected work".
3. **Fake frame variety** — each case study's "Selected frames 01/02/03" are the same JPEG with CSS `scale(1.25)` + `object-position` shifts.
4. **No `og:image`** — shares on WhatsApp / Instagram / LinkedIn (the studio's actual channels, listed in the footer) render with no preview card. For an Ahmedabad agency where projects get shared on WhatsApp, this is real lost reach.
5. **Founder visuals are placeholders** — the `A` / `M` initial cards look intentional but are stand-ins for real portraits.
6. **Showreel promise mismatch** — hero says "SHOWREEL '26 — PRESS PLAY" but `SHOWREEL_SRC` is empty and the modal says "in production". Honest, but the CTA over-promises; either ship the reel or reword the hero CTA.
7. **No optimized variants** — no WebP/AVIF/srcset yet (fine at today's weight ≈ 1.2 MB, will matter once real frames/videos land).

---

## 3. Findings — animation upgrades (on top of the existing system)

In order of impact vs effort:

1. **Scroll-velocity marquee** — marquee speed (and slight skew) reacts to scroll velocity. Classic "brutalist" signature move; pure JS on the existing CSS track.
2. **Count-up on "receipts"** — 06 / 04 / 02 / 4.9★ animate from zero when scrolled into view.
3. **Terminal typing effect** — the STATUS terminal already has a blinking caret; make its lines type in.
4. **Hero frame 3D tilt** — hero stage images get subtle mouse-tilt (rotateX/Y) to pair with the existing glow/depth parallax.
5. **Scroll-scrubbed giant type** — footer "NOVA EDGE" and the manifesto ghost "ATTENTION ✦" translate on scroll; extend `data-px` ghost parallax to more section titles.
6. **Work-row hover thumbnails** — desktop: a small preview follows the cursor on world rows; later, replace with short video loops per project.
7. **Case overlay entrance stagger** — content blocks stagger in after the wipe; "next project" name gets a hover marquee.
8. **Micro-interactions** — click-to-copy email with toast, nav-link glitch/scramble hover (fits "impossible to ignore"), magnetic effect extended to `stage-open`.
9. **Optional:** hand-rolled smooth-scroll inertia (Lenis-style) — nice feel, but weigh perf/complexity.

---

## 4. Findings — structure, conversion & tech

1. **Desktop nav is missing SERVICES / PROCESS** — mobile menu has 5 links, desktop has 3 (WORK/ABOUT/CONTACT). Section 03 and 05 are unreachable from the desktop chrome.
2. **Six identical case "result" paragraphs** ("Shipped as NOVA EDGE selected work…") — reads templated; write one real outcome sentence per project.
3. **All "FULL PROJECT" buttons point to the same Behance profile** — deep-link per project if the pieces live separately.
4. **Launch hygiene:** no `robots.txt`, no `sitemap.xml`, no canonical URL, no `twitter:card`, no analytics (Plausible/GA4/umami) — needed before promoting the site.
5. **WhatsApp-first CTA** — consider a sticky mobile "WhatsApp us" bar; the contact section is already WhatsApp-forward, which suits the market.
6. **A11y polish:** focus trap + `aria-modal` focus management inside the case overlay / reel modal; the cursor rAF loop runs forever (minor battery cost on desktop).
7. **Maintainability:** 1,470 lines is fine for zero-dep, but before adding reel + more cases consider splitting into `styles.css` / `main.js` (still no build step).

---

## 5. Suggested rollout

**Phase 1 — trust & conversion** (needs assets from you)
- Replace work images with real project frames (fix all 4 mismatches), unique frames per case study
- Add `og:image` (we can design one), fix hero showreel CTA wording until the reel exists
- Desktop nav links, per-project Behance URLs, unique case "result" copy

**Phase 2 — motion upgrades** (fully buildable by us, no assets needed)
- Velocity marquee, receipts count-up, terminal typing, hero 3D tilt, scrubbed giant type, copy-email toast

**Phase 3 — depth**
- Real showreel video (`SHOWREEL_SRC`), founder portraits, hover video loops on work rows, WebP/srcset pipeline, robots/sitemap/analytics

**What we need from the team:**
- Real frame exports per project (or the videos to pull frames from)
- Showreel `.mp4` URL
- Founder photos (or approval to design illustrated portraits)
- Per-project Behance links
