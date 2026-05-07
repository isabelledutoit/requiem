# Design Interview — Isabelle du Toit / Requiem Landing Page

## Decisions Made

| # | Question | Choice |
|---|----------|--------|
| 1 | Tokenizer fidelity | **B — Faithful simulation** (hand-crafted BPE-like rules, zero dependency) |
| 2 | Vector embeddings | **A — Pre-computed real-looking vectors** (hardcoded 32 of 1536 dims, text-embedding-3-small style) |
| 3 | Background animation | **C — Bouncing physics balls**, subtle and slow |
| 4 | Gallery presentation | **B — Full-screen slideshow** (one work at a time, cinematic) |
| 5 | Tokenizer position | **C — Separate section with dramatic scroll reveal** |

## Visual Direction

- **Colors**: Dead dark brown (`#0e0a05`), blood red (`#6b0e0e` / `#991414`), bone/cream (`#f0ebe0`)
- **Font**: Patrick Hand throughout
- **Aesthetic**: Funerary, visceral, hyperrealist — matches Isabelle's practice
- **Background**: Slow bouncing orbs in dark reds and browns, blurred, ~18 balls
- **Thematic thread**: Tokenizer framed as "Language as Anatomy" — paralleling how Isabelle dissects matter, the LLM dissects language

## Tokenizer Words (Pill Buttons)

Greed · Apathy · Selfishness · Manipulation · Oppression · Deception · Death · Cruelty

## Image Notes

- Featured work: **Mentes Extractae** — `public/artworks/MentesFull.jpg` plus three detail crops (`MentesDetail1.jpg`, `MentesDetail2.jpg`, `MentesDetail3.jpg`)
- Slideshow shows the full painting first, then details across slides 2–4
- All images link back to isabelledutoit.com/requiem

## Page Structure

1. Hero — canvas bg, "REQUIEM" large, scroll indicator  
2. About — brief series description  
3. Full-screen slideshow — cinematic, links to her site  
4. Tokenizer — scroll-reveal, word pills → animation → vector embedding  
5. Footer — links to isabelledutoit.com
