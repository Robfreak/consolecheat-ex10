# HDR- und Helligkeits-Hilfe

Schwarzwert-, Weiß- und Graustufen-Muster für die Bildeinstellung, lokal im Browser. Teil der inoffiziellen consolecheat-Werkzeuge rund um [consolecheat.com](https://consolecheat.com). German is the primary language, English is the other. Light and dark theme, self-hosted fonts, footer, Impressum, and Datenschutz are included. There is no Webmail link.

No account, no tracking, nothing uploaded. Fonts (Outfit, Source Sans 3) are self-hosted from `@fontsource`, so the page makes no request to Google or any other third party. The Impressum fields are placeholders until the operator fills them in. No name or address was invented.

Site: <https://robfreak.github.io/consolecheat-ex10/>

Inoffiziell. Nicht von Sony.

## What it does

A local brightness and black-level helper that complements the screen test. Open it at `/consolecheat-ex10/`. German is the default. English is the other language. Light and dark follow `consolecheat-theme`.

The short guide says what a browser page can check (near-black steps from 0% to 5%, a PLUGE-style black-crush check, near-white and white-clipping steps, a 256-step grayscale with 20% / 50% / 80% patches for a tint) and what it cannot. True HDR peak luminance in nits and the PQ curve (PQ EOTF, SMPTE ST 2084) cannot be verified from a normal web page. CSS white is the browser’s SDR white. The page does not certify HDR10, Dolby Vision, or HLG.

Patterns are drawn in the browser with CSS and one canvas ramp. No image is fetched. Open a pattern from the list or with the keys `1`–`6`. Arrows move between patterns. `Esc` leaves fullscreen first; the next `Esc` returns to the list. If the Fullscreen API is missing or refused, the pattern still fills the window. A strong link points at `https://robfreak.github.io/consolecheat-ex7/` for color, pixels, motion, and sharpness.

`matchMedia('(dynamic-range: high)')` is shown on the page when the browser supports it. The result is informational only, not a measurement and not a certification. `high`, `standard`, and `unknown` are all expected outcomes.

The last opened pattern is remembered only in `sessionStorage`, key `consolecheat-hdr-pattern` (a pattern id such as `near-black`, this tab only). The page reads that key once on load, writes it only after a pattern is opened, and removes it when you return to the list. Closing the tab drops it. Language and appearance reuse `consolecheat-lang` and `consolecheat-theme`.

## Storage

- `consolecheat-hdr-pattern` (sessionStorage, only this tab)
- `consolecheat-lang` and `consolecheat-theme` (localStorage, shared with the other consolecheat tools on robfreak.github.io)

The Datenschutz page has a button that removes this page's keys. Nothing else is stored.

## Run and test

```bash
npm install
npm test        # node --experimental-strip-types --test src/hdr/*.test.ts
npm run dev     # http://127.0.0.1:5173/consolecheat-ex10/
npm run build   # typecheck, Vite build (base /consolecheat-ex10/), offline check of dist/
npm run preview # http://127.0.0.1:4173/consolecheat-ex10/
```

Node `>=22.6` (`package.json` `engines`).

## Files

- `index.html` — the HTML entry (Vite input)
- `src/hdr/` — React + TypeScript source, styles, and tests
- `src/hdr/tools.ts` + `src/hdr/tool-links.tsx` — the footer list **Weitere Werkzeuge** (keep it identical across the consolecheat repos)
- `public/` — `favicon.svg`, `FONT-OFL.txt`, `.nojekyll`
- `scripts/check-dist.mjs` — offline check of `dist/` (no third-party hosts, no `.woff` fallback, woff2 fonts present)
- `.github/workflows/pages.yml` — test, build, and deploy to `gh-pages`

## Other tools

The footer group **Weitere Werkzeuge** (English: **Other tools**) links to the other consolecheat tools: Title-ID-Finder (ex1), PS-Plus-Archiv (ex2), Controller-Tester (ex3), Save-Info-Leser (ex4), Fehlercode-Nachschlager (ex5), the [Spiele-Merkliste](https://robfreak.github.io/consolecheat-ex6/), and [Bildschirm-Test](https://robfreak.github.io/consolecheat-ex7/), [Download-Zeit-Rechner](https://robfreak.github.io/consolecheat-ex8/), [Tastenbelegung](https://robfreak.github.io/consolecheat-ex9/), [Audio-Kanal-Test](https://robfreak.github.io/consolecheat-ex11/), [USB-Stick-Checkliste](https://robfreak.github.io/consolecheat-ex12/), [Combo-Trainer](https://robfreak.github.io/consolecheat-ex13/), [Sprite-Animator](https://robfreak.github.io/consolecheat-ex14/). These are ordinary links. The page does not request those sites.

This tool was moved here from [Robfreak/consolecheat-ex6](https://github.com/Robfreak/consolecheat-ex6).

## GitHub Pages

`.github/workflows/pages.yml` runs install, test, and build on pull requests and on every push. A push to `main` also pushes `dist/` to the orphan branch `gh-pages` (`peaceiris/actions-gh-pages`, Jekyll off). Vite `base` is `/consolecheat-ex10/`, which matches the project site <https://robfreak.github.io/consolecheat-ex10/>.

Enable once in the repository settings:

1. **Settings → Actions → General → Workflow permissions → Read and write permissions.** Save.
2. **Settings → Pages → Build and deployment → Source: Deploy from a branch.** Branch: **`gh-pages`**, folder: **`/ (root)`.** Save.

After that, every push to `main` updates the site.

## Credits

Outfit and Source Sans 3 are bundled from `@fontsource` under the SIL Open Font License; see `public/FONT-OFL.txt` and `THIRD_PARTY_NOTICES.md`.

Replace the Impressum placeholders with the operator’s real details before treating that page as a legal notice.
