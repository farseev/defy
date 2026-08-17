# Defy. Cloud prototype — farseev.github.io/defy

Interactive prototype restyled to the **defy-brand-guideline v2.0**. Two
self-contained pages, no build step, no dependencies beyond the Google Fonts link.

| File | Serves at | Product |
|---|---|---|
| `index.html` | `https://farseev.github.io/defy/` | **DefyDelivery** — social, SEO·AEO·GEO and ads on autopilot |
| `pro.html` | `https://farseev.github.io/defy/pro.html` | **DefyResearch** — audience research, Defy Copilot, DefyProduction |
| `defy_social_preview.png` | — | 1200×630 OG card for `index.html` |
| `defy_research_preview.png` | — | 1200×630 OG card for `pro.html` |

## Deploying

This is a GitHub Pages **project** site, so there is deliberately **no `CNAME`
file** — a CNAME only belongs on a custom domain, and adding one here would
break `farseev.github.io/defy`. Drop these files at the repo root of a repo
named `defy` (or in `/docs`), enable Pages, and the URLs above resolve as-is.

## Sign-in

| Email | Shown as |
|---|---|
| `aleks@defygroup.ai` | Aleks Farseev · Founder · Defy Group |

Password: `123qwe0-=` — English is the default language on both pages.

Credentials are not stored in either file. Each is the SHA-256 digest of
`"<email>|<password>"`, hashed in-browser via Web Crypto at sign-in; the digest
cannot be reversed back into the email or password, and both pages return a
single "Incorrect email or password" so a valid address can't be probed. To
change the roster:

```
python3 -c "import hashlib;print(hashlib.sha256(b'you@defygroup.ai|yourpassword').hexdigest())"
```

then edit `USERS` in `index.html` (digest → name/role) and `AUTH_H` in `pro.html`.

---

## Brand system applied

Run against the guideline's 13-step migration checklist.

### Palette — red + neutrals, nothing else

| Role | Hex |
|---|---|
| Defy Red (accent) | `#CC0000` |
| Red Dark (red on red) | `#990000` |
| Black (surface + display type) | `#0A0A0A` |
| Warm White (default bg) | `#F9F9F7` |
| Cream (secondary surface) | `#F3F1EC` |
| Charcoal (body) | `#2D2D2D` |
| Mid Grey (caption) | `#777777` |
| Border Grey (hairline) | `#E8E6E1` |

No blue, teal, purple, orange or yellow survives in the chrome. The single-purpose
green `#2A9D2A` is not used at all — it is reserved for DO-card borders, and this
prototype has none.

### Red is punctuation, not paragraph

The most consequential decision here. Every primary action in the source was a
filled accent button, which under Defy would put red on far more than 10% of the
page — the guideline calls that out explicitly ("typical mistake is using red as
a button fill"). So **primary actions are black `#0A0A0A`** (`--btn`), and red is
reserved for:

- the wordmark's red-square full stop
- section labels / eyebrows and stat labels
- bullet markers (every checkmark is now an 8px red square)
- the active-nav rule, card left-borders, accent hairlines
- small badges, step numbers, status dots, sparkline and share bars
- one series in each chart — the brand's own

Two panels that were large red fills are now black with a red accent letter: the
ExoStride brand tile and the plan ribbon set.

Measured across all 18 rendered screens, red covers **0.05–4.2%** of pixels; the
50/40/10 ratio holds on every page.

### Type

Playfair Display (800–900, title case, `-0.5px`) for the wordmark, all headings,
stat numbers and page titles. DM Sans for body, labels, captions and every UI
control. Eyebrows are DM Sans Bold caps at `0.4em`; stat labels at `0.28em`.
Long-form article body moves to 16px / 1.85 line-height; dense UI copy stays
tighter than the guideline's 1.85 so tables and cards remain readable — the one
deliberate adaptation. Noto Sans SC is retained for the `zh` locale.

### Wordmark

"Defy" in Playfair Black followed by the red square that replaces the period —
in all four mark positions (DefyDelivery sidebar + login, DefyResearch sidebar +
login, and the nested simple-mode prototype). Title case only; the square is
`0.27em`, sits on the baseline, and stays `#CC0000` on both light and dark.
Favicons are the standalone red square on a black plate, square-cornered.

### Flat and square

- Every `border-radius` is `0` — including pills, avatars, status dots and the
  bubble launchers. Status dots and bullets read as red squares, which is the
  guideline's own bullet pattern.
- Every `box-shadow` became a hairline `0 0 0 1px #E8E6E1` ring, so dropdowns,
  modals and drawers still separate from the page without a blur.
- Every `linear-gradient` / `radial-gradient` collapsed to a flat fill.
- `backdrop-filter` blurs and `text-shadow` glows removed.

### Naming

| Was | Now |
|---|---|
| SOMIN Cloud Suite | DefyDelivery |
| SOMIN PRO | DefyResearch |
| SOWISE | DefyProduction |
| SOMIN Copilot | Defy Copilot |
| SOMIN MCP / -class / -verified | Defy MCP / Defy-class / Defy-verified |
| `/somin-*-deck` | `/defy-*-deck` |
| nav groups `SO`MONITOR / `SO`INSPIRE / `SO`WISE | `▪`MONITOR / `▪`INSPIRE / `▪`PRODUCTION |
| `*@somin.ai` | `*@defygroup.ai` |
| `© 2026 SOMIN · interactive prototype` | `DEFY GROUP LIMITED — INTERACTIVE PROTOTYPE` |
| `somin_auth` / `somin_lang` / `sowiseSrc` | `defy_auth` / `defy_lang` / `prodSrc` |

### Kept off-palette (deliberate)

Real third-party platform identity stays itself inside Defy chrome: LinkedIn
`#0A66C2`, Facebook `#1877F2`, Instagram `#E4405F` / `#C13584`, Google `#4285F4`
/ `#34A853`, Telegram `#229ED9`. The generated ExoStride campaign creatives are
client artwork and are untouched — only the Defy-owned chrome around them was
restyled, per the guideline's carve-out.

---

Verified in headless Chromium: every nav destination on both pages plus the
nested simple-mode prototype, **zero JavaScript errors**, no surviving
`border-radius`, `box-shadow` blur or gradient, and no residual SOMIN, SOWISE,
teal or Montserrat reference.
