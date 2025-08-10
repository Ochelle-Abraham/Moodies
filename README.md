# Moodies 

This is a **single‑page** HTML app that surfaces Bible verses based on how someone feels (Sad, Guilt, Anger, Happy, Tired, Anxiety). It’s responsive, touch‑friendly, and includes subtle pink “star” clusters in the page corners.

## What’s inside

- One file: `test.html`
- Sections:
  - **Home** (title typing effect, slogan, Get Started)
  - **Select Mood** (2×3 grid; adapts on small screens)
  - **Verse** (randomized verse + reference, Refresh, Back)
- Theme variables defined with CSS custom properties (purple background, soft pink accents)
- Corner “stars” rendered with `body::before`/`::after` radial‑gradient patterns


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

``

### Behavior

- Shuffle avoids repeating the same verse back‑to‑back.
- Back buttons invert colors on hover/focus/active for clear affordance.
- Mobile: larger tap targets (`--tap:48px`), grid collapses 3→2→1 columns.



## Roadmap ideas

- Stay tuned to find out

---

**License**: You’re free to use this as you wish. If you want to formalize, add an MIT `LICENSE` block.

