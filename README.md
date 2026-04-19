# Requiem — Isabelle du Toit

A single-page landing site for Isabelle du Toit's **Requiem** series. Standalone from her main portfolio at [isabelledutoit.com](https://isabelledutoit.com).

The site pairs hyperrealist painting with an interactive tokenizer: each painting carries a cryptic token number (painted directly on the canvas); visitors discover the concept behind it by clicking.

## Running

No build step. Open `index.html` in a browser, or serve the folder:

```bash
python -m http.server 8000
# or
npx serve .
```

Then visit `http://localhost:8000`.

## Structure

```
index.html              single-file page — all CSS, JS, HTML
public/artworks/        paintings (placeholder: memento.webp)
docs/design-ideas.md    design interview + decisions
```

## Design Language

- **Font**: Patrick Hand (Google Fonts), throughout
- **Palette**: dead dark brown `#15100a`, bone `#f5f0e5`, blood red `#c41e1e`, gold `#a07d30`
- **Background**: slow bouncing orb physics on canvas
- **Mood**: funerary · visceral · hyperrealist

## Sections

1. **Hero** — ISABELLE DU TOIT / REQUIEM
2. **About** — series statement
3. **Slideshow** — full-screen cinematic, three works, auto-advance every 7s
4. **Tokenizer** — scroll-triggered reveal; 8 masked concept pills + custom input
5. **Footer** — links back to isabelledutoit.com

## The Cipher Mechanic

Each painting in the slideshow displays a token number (e.g. `#27891`). Clicking it:

1. Fades the number and reveals the concept word
2. Smooth-scrolls to the tokenizer section
3. Auto-triggers the matching pill → runs the full dissection (tokens → IDs → 1536-dim vector)

Current cipher assignments:

| Slide | Cipher | Concept |
|-------|--------|---------|
| 01 Memento | `#27891` | Death |
| 02 The Wound Does Not Heal | `#34012` | Cruelty |
| 03 Evidence | `#22345` | Deception |

Isabelle can paint any of the eight token IDs directly onto a work; visitors who arrive here will find the match and decode it.

## Updating Paintings

Swap the image on any slide by changing the `src` on its `<img>` element. All three currently point at `public/artworks/memento.webp` as a placeholder.

```html
<div class="slide-art">
    <img src="public/artworks/your-new-painting.webp" alt="…">
</div>
```

To change the cipher for a slide, edit its `<button class="slide-cipher-btn" data-word="…" data-mask="#…">…</button>`.

## The Tokenizer

- **Tokenization**: faithful simulation (hand-crafted BPE-like rules, no dependencies)
- **Embeddings**: pre-computed realistic vectors for the eight curated words (32 of 1536 dimensions shown). Custom-input words receive generated illustrative vectors
- **Animation**: three phases — raw word → token chips with IDs → vector stream

The eight pre-computed concepts are: Greed, Apathy, Selfishness, Manipulation, Oppression, Deception, Death, Cruelty.

## Links

- Isabelle du Toit — [isabelledutoit.com](https://isabelledutoit.com)
- Requiem series — [isabelledutoit.com/requiem](https://isabelledutoit.com/requiem)

© Isabelle du Toit. All rights reserved.
