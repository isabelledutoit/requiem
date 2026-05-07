# Requiem — Isabelle du Toit

## 🔗 [isabelledutoit.vercel.app](https://isabelledutoit.vercel.app)

---

![Mentes Extractae — Isabelle du Toit](public/artworks/MentesFull.jpg)

A single-page landing site for Isabelle du Toit's **Requiem** series. Standalone from her main portfolio at [isabelledutoit.com](https://isabelledutoit.com).

The site pairs hyperrealist painting with an interactive tokenizer: each painting carries a cryptic token number (painted directly on the canvas); visitors discover the concept behind it by clicking.

## Running

No build step. Clone the repo, then either open `index.html` in a browser or serve the folder:

```bash
git clone https://github.com/isabelledutoit/requiem.git
cd requiem
python -m http.server 8000
# or
npx serve .
```

Then visit `http://localhost:8000`.

> Internet is required for the Google Font (Patrick Hand) and the background audio. Images are local to the repo and work offline.

## Structure

```
index.html              single-file page — all CSS, JS, HTML
public/artworks/        paintings (Mentes Extractae — full + 3 details)
docs/design-ideas.md    design interview + decisions
```

## Design Language

- **Font**: Patrick Hand (Google Fonts), throughout
- **Palette**: dead dark brown `#15100a`, bone `#f5f0e5`, blood red `#c41e1e`, gold `#a07d30` (accents only)
- **Background**: blood-red and silver orbs on canvas — slow physics, connected by thin silver constellation lines when within 180px
- **Mood**: funerary · visceral · hyperrealist

## Sections

1. **Hero** — ISABELLE DU TOIT / REQUIEM
2. **About** — series statement
3. **Slideshow** — full-screen cinematic, four views (Mentes Extractae + details), paused by default; play/pause toggle advances every 5s
4. **Tokenizer** — scroll-triggered reveal; 8 masked concept pills + custom input
5. **Footer** — links to isabelledutoit.com, the Requiem series page, the GitHub repo, and the build credit

## The Cipher Mechanic

Each painting in the slideshow displays a token number (e.g. `#27891`). Clicking it:

1. Fades the number and reveals the concept word
2. Smooth-scrolls to the tokenizer section
3. Auto-triggers the matching pill → runs the full dissection (tokens → IDs → 1536-dim vector)

Current cipher assignments:

All eight slides display the same title — **Mentes Extractae** — the painting they document. Each slide carries a different cipher token:

| Slide | Cipher | Concept |
|-------|--------|---------|
| 01 | `#27891` | Death |
| 02 | `#34012` | Cruelty |
| 03 | `#22345` | Deception |
| 04 | `#19234` | Oppression |
| 05 | `#38659` | Greed |
| 06 | `#12670` | Apathy |
| 07 | `#12896` | Selfishness |
| 08 | `#8716` | Manipulation |

Isabelle can paint any of the eight token IDs directly onto a work; visitors who arrive here will find the match and decode it.

## Updating Paintings

Swap the image on any slide by changing the `src` on its `<img>` element. The slides currently point at `MentesFull.jpg` and `MentesDetail1/2/3.jpg` in `public/artworks/`.

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

- **Live site** — [isabelledutoit.vercel.app](https://isabelledutoit.vercel.app)
- Isabelle du Toit — [isabelledutoit.com](https://isabelledutoit.com)
- Requiem series — [isabelledutoit.com/requiem](https://isabelledutoit.com/requiem)
- GitHub (Isabelle) — [github.com/isabelledutoit/requiem](https://github.com/isabelledutoit/requiem)

© Isabelle du Toit. All rights reserved.

## Support

If this project helps you, you can support DreamForge Academy here: [Buy Me a Coffee](https://buymeacoffee.com/dreamforgeacademy).
