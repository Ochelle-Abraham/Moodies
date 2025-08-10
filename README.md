# Moodies — Scripture by Mood (Single‑File Site)

This is a **single‑page** HTML app that surfaces Bible verses based on how someone feels (Sad, Guilt, Anger, Happy, Tired, Anxiety). It’s responsive, touch‑friendly, and includes subtle pink “star” clusters in the page corners.

## What’s inside

- One file: `test.html`
- Sections:
  - **Home** (title typing effect, slogan, Get Started)
  - **Select Mood** (2×3 grid; adapts on small screens)
  - **Verse** (randomized verse + reference, Refresh, Back)
- Theme variables defined with CSS custom properties (purple background, soft pink accents)
- Corner “stars” rendered with `body::before`/`::after` radial‑gradient patterns

## Quick start

1. Download/save `test.html`.
2. Double‑click to open in a browser (Chrome, Edge, Firefox, Safari).
3. Tap **Get Started** → pick a mood → read a verse → tap **Refresh**  to shuffle.

> Tip: For clean local links and caching behavior, you can also serve it from a tiny local server:
>
> - Python 3: `python -m http.server 8080`
> - Node (if installed): `npx serve .`

## Customize

### Colors & theme

Edit CSS variables at the top of the `<style>` block:

```css
:root{
  --bg:#2a0151;       /* deep purple */
  --bg-2:#420a78;     /* secondary purple */
  --text:#f6b1cf;     /* pink text/buttons */
  --dot-1:#f4a5c9;    /* star shades */
  --dot-2:#e48eb9;
  --dot-3:#c47aa6;
}
```

### Corner stars

Tweak size/opacity/spacing in the `body::before`/`body::after` rules:

```css
body::before, body::after{
  width:160px; height:160px;           /* cluster size */
  background-size:30px 30px,45px 45px,60px 60px; /* dot spacing */
  opacity:.4;                          /* visibility */
}
```

To add more corners, duplicate a rule (e.g., `body::after`) and position it at `top:0; right:0;` or `bottom:0; left:0;`.

### Moods

Add/remove mood labels in the `MOODS` array and provide verses in the `VERSES` object (each entry is `{ t: "Text", r: "Reference" }`). Example:

```js
const MOODS=['Sad','Guilt','Anger','Happy','Tired','Anxiety','Hopeful'];
VERSES.Hopeful=[
  { t:"Be strong and courageous...", r:"Joshua 1:9" },
  { t:"May the God of hope fill you with all joy and peace...", r:"Romans 15:13" },
];
```

### Behavior

- Shuffle avoids repeating the same verse back‑to‑back.
- Back buttons invert colors on hover/focus/active for clear affordance.
- Mobile: larger tap targets (`--tap:48px`), grid collapses 3→2→1 columns.

## Deploy

This is a static page—you can host it anywhere:

- **GitHub Pages**: create a repo with `test.html` at the root → Settings → Pages → deploy from `main`/root.
- **Netlify** / **Vercel**: drag‑and‑drop the file/folder or import from Git.
- **Any static host**: upload `test.html`.

## Notes on content & translations

The verse list is embedded directly in the page. If you need alternate translations (e.g., KJV/ESV/NIV) or additional languages, consider splitting the verses into separate JSON blobs and adding a selector.

## Roadmap ideas

- Save favorites (localStorage)
- Copy/share verse button
- Translation toggle
- Daily reminder (requires Push API / simple backend)
- Print/PDF view

---

**License**: You’re free to use this as you wish. If you want to formalize, add an MIT `LICENSE` block.

