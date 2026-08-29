# JADA Landscaping — spec demo

Concept one-page lead-gen site to pitch **JADA Landscaping & Construction LLC** (El Paso, TX).
Prospect #3 (Priority A) on `El-Paso-Website-Prospects.xlsx`. Adapted from the Best AirR demo.

```
jada-landscaping-demo/
├── index.html    markup + inline SVG (logo, icons, map)
├── styles.css    JADA-blue palette, before/after slider, gallery
├── script.js     EN/ES toggle, before/after slider, financing calc, form validation
└── assets/       originals + web-optimized copies
```

**Preview:** open `index.html`, or
`cd jada-landscaping-demo && python3 -m http.server 8901` → <http://localhost:8901>

---

## Why the page is built this way

JADA's problem isn't a *bad* website — it's **no website at all**. They post constantly on
Instagram (@jadalandscaping_), Facebook (~1,359 likes) and TikTok, run Meta ads, and are
A+ with the BBB — but their BBB profile's "website" link just points to their Facebook page.
Every ad click lands in Messenger. A homeowner who Googles "JADA Landscaping El Paso" finds
only social profiles.

Landscaping sells on **visuals** and **speed of response**, so this build leans into both:

- **Interactive before/after slider** up top (their real dirt-lot → finished front yard).
  This is the single strongest conversion tool for a landscaper — it's not in the Best AirR
  version.
- **Photo-forward everywhere** — hero photo, 6-tile gallery of real jobs.
- **Lead form tailored to landscaping** — project type, which yard, rough size. Better
  qualification means Daniel walks into every call already knowing the job.
- **"Text Daniel" as a primary action** everywhere (header, form, sticky bar, final CTA),
  because replying in minutes is their edge — the page says so and makes it one tap.
- **Financing estimator** ($3k–$45k range) — full-yard remodels get financed.
- **EN/ES toggle** — bilingual business.

---

## ⚠️ Verified vs. placeholder

**Real — safe to keep:**

| Fact | Source |
|---|---|
| Jada Landscaping & Construction LLC, El Paso TX 79928 | BBB |
| Owner / management: **Jose Daniel Simental** ("Daniel") | BBB |
| Founded 2021 · **4 years in business** | BBB (business started 12/13/2021) |
| **A+ BBB rating** (NOT accredited — page says "A+ with the BBB", not "BBB Accredited") | BBB |
| Insured & bonded | their Instagram bio |
| (915) 218-1222 — call or text | IG bio, BBB, their ads |
| IG @jadalandscaping_ · FB /JADALANDSCAPE · TikTok @jada.landscape | verified live |
| Replies "within minutes", next-day scheduling | Thumbtack review |
| Services in the photos: turf, stamped concrete, pavers, steel & wood pergolas, stone & retaining walls, xeriscape | the 9 client photos |
| Also runs "JADA Skid Steer Rental" | IG bio link |

**Placeholder — fix before this goes live:**

- **Financing APR/terms.** `script.js` line ~11: `APR = 0.0999`, terms 3/5/10 yr. Invented.
  The page carries a "not an offer of credit" disclaimer; get JADA's real finance partner
  numbers (or drop the section if they don't offer financing).
- **Hours.** Footer says "Mon–Sat" with a visible `(confirm hours)` flag. Confirm, then
  delete the `.demo-inline` span.
- **No reviews / star ratings anywhere** — deliberate. Couldn't verify a Google rating.
  Add real ones (they have Thumbtack + Facebook reviews) once Daniel provides them.
- **Logo** is a hand-built SVG approximation of the real "JꓷD" monogram + JADA wordmark.
  Replace with their actual logo file when he sends it.
- **Before/after photos** are slightly different aspect ratios (before 3:2, after 4:3), so
  the horizon doesn't line up perfectly across the wipe. Crop both to the same ratio for a
  clean match.
- **Form has no backend.** Submitting shows a success state and says so on screen. Wire to
  Formspree / email before launch.
- Footer keeps "Concept site prepared for JADA — not an official page." until he buys.

---

## Photos

`assets/` has the 9 originals plus optimized copies the page uses:

| file | used as | from |
|---|---|---|
| `hero.jpg` | hero background | `pergola2.jpg` (black pergola, mountain, sky) |
| `before.jpg` / `after.jpg` | before/after slider | `before_pic.jpg` / `after-pic.jpg` |
| `g1-backyard.jpg` | gallery (wide) | `landscaping3.jpg` |
| `g2-patio.jpg` | gallery | `landscaping2.jpg` |
| `g3-sideyard.jpg` | gallery | `landscaping.jpg` |
| `g4-design.jpg` | gallery | `landscaping4.jpg` |
| `g5-pergola.jpg` | gallery | `pergola.jpg` |
| `g6-under.jpg` | gallery | `pergola-fan.jpg` |

Re-optimize a swap with:
`sips -Z 1400 -s formatOptions 56 new.jpg --out g5-pergola.jpg`

---

## Palette (from the JADA logo)

Sampled from the logo: brand blue `#015198`. Set as CSS custom properties at the top of
`styles.css` — swap these to reskin:

```css
--blue:#015198;        /* their exact brand blue — buttons, links */
--navy:#04345F;         /* darker — headings, dark sections, footer */
--blue-bright:#2E7CC5;   /* lighter monogram blue — accents */
--sky:#E9F1F8;           /* tinted section backgrounds */
--turf:#3E9B48;          /* green — checkmarks, success (nature cue) */
```

---

## Repo & hosting

Same setup as `best-airr-demo`: private repo, hosted free on GitHub Pages (which needs the
repo public). To publish:

```
gh repo edit Kassandra-Rodriguez/jada-landscaping-demo --visibility public --accept-visibility-change-consequences
gh api --method POST /repos/Kassandra-Rodriguez/jada-landscaping-demo/pages -f "source[branch]=main" -f "source[path]=/"
```

Live at `https://kassandra-rodriguez.github.io/jada-landscaping-demo/` (~1 min after).
`noindex` is set so it won't be indexed as a competing JADA page.

---

## Talk track

> "Hi Daniel — I'm Kassandra, a web designer in El Paso. Your Instagram and TikTok are doing
> the hard part, getting people interested. But your ads all land in Messenger and there's no
> website, so anyone who Googles 'JADA Landscaping' just finds your social pages. I built you
> a sample — a drag-to-compare before/after of one of your front yards, your gallery, and a
> quote form that asks what they want done and which yard, so you walk into every call already
> knowing the job. English and Spanish. Want the link?"

Lead with "your social is working, there's just nowhere for it to land." It's a compliment
plus a gap, not a criticism.
