# IRON — design system (Max Sandell, concept VI, power edition)

Replaces "Haven". Same client (women 40+), positioning now built on the present — calm, private, one client at a time, strength for the next thirty years — completely different feel: **power, not softness**. Think a Nike Women campaign shot by a fashion photographer, or a premium watch brand that happens to sell strength. Never girly, never bro-gym, never pink, never cream-and-rose. Her power, treated seriously.

## Tokens (use these exact custom properties)
```css
:root{
  --bg:#111113;        /* graphite black — page ground */
  --bg-2:#18181b;      /* surface */
  --bg-3:#222226;      /* raised / card */
  --line:rgba(236,230,218,.14);
  --line-strong:rgba(236,230,218,.32);
  --bone:#ece6da;      /* primary text on dark */
  --bone-2:#b9b2a6;    /* secondary text on dark */
  --bone-3:#7f796f;    /* muted */
  --ox:#8e2733;        /* oxblood — the ONE accent: primary buttons, key words, rules */
  --ox-hi:#b23a48;     /* hover / highlight */
  --light-bg:#e9e3d7;  /* light section ground (bone) — for rhythm, 1–2 sections per page */
  --light-ink:#141416; /* text on light sections */
  --light-line:rgba(20,20,22,.14);
}
```
Dark is the default. Use one or two **light (bone) sections** per page for rhythm — same type system, inverted.

## Type
- Display: **Big Shoulders Display** (Google Fonts), weights 600–800, UPPERCASE for headlines, tight leading (.92), tracking -.01em. Huge: hero clamp(56px, 11vw, 168px). Section titles clamp(40px, 6vw, 88px).
- Body/UI: **Instrument Sans** (Google Fonts) 400/500/600. Body 16–18px, line-height 1.6. 
- Micro-labels: Instrument Sans 600, 11px, uppercase, letter-spacing .22em, color var(--bone-3) (or var(--ox) for emphasis).
- Numerals for stats: Big Shoulders 700, large.
- Link: `<link href="https://fonts.googleapis.com/css2?family=Big+Shoulders+Display:wght@600;700;800&family=Instrument+Sans:ital,wght@0,400;0,500;0,600;1,400&display=swap" rel="stylesheet">`

## Shape & layout
- Hard edges. border-radius: 0 (max 2px). No pills, no arches, no blobs.
- Rules: 1px var(--line); section dividers 1px var(--line-strong); a short 48px × 3px oxblood bar under micro-labels as the signature mark.
- Grid: 12-col, max-width 1280px, gutters 24px (mobile) / 40px. Split layouts (text 5 cols / image 7 cols), full-bleed images, generous vertical rhythm (section padding clamp(72px, 10vw, 160px)).
- Section numbering "01 / 02 / 03" in Big Shoulders, muted.
- Big stats set in Big Shoulders with a thin label under.

## Photography treatment
- Black & white, high contrast, slightly warm: `filter: grayscale(1) contrast(1.15) brightness(.88) sepia(.18);` on a dark ground; on hover no change (no gimmicks).
- Optional oxblood duotone for ONE hero-scale image: image with `mix-blend-mode: luminosity` over a `var(--ox)` block at low opacity — use sparingly.
- Subjects: women lifting heavy (deadlift, barbell, chalk), Max (tattooed, calm). Verified Unsplash (append ?q=80&w=1600&auto=format&fit=crop):
  - Max: https://images.unsplash.com/photo-1601422407692-ec4eeec1d9b3 (tattooed, kettlebell) · https://images.unsplash.com/photo-1549476464-37392f717541 (dark gym, plate)
  - Women: https://images.unsplash.com/photo-1584863231364-2edc166de576 (rack deadlift) · https://images.unsplash.com/photo-1595078475328-1ab05d0a6a0e (barbell + chalk, moody) · https://images.unsplash.com/photo-1541534741688-6078c6bfb5c5 (overhead press) · https://images.unsplash.com/photo-1518459031867-a89b944bffe4 (coach + client, bright) · https://images.unsplash.com/photo-1518310383802-640c2de311b2 (small group)

## Components
- **Primary button**: background var(--ox), color var(--bone), Instrument Sans 600 12px uppercase tracking .18em, padding 18px 28px, no radius; hover background var(--ox-hi); a thin 1px bone border appears on focus-visible.
- **Ghost button**: transparent, 1px var(--line-strong) border, same type; hover border bone.
- **Micro-label + bar**: label, then the 48×3 oxblood bar (or bar first, then label) — the recurring signature.
- **Card**: var(--bg-3) surface, 1px var(--line) border, no radius, 28–32px padding.
- **Table**: 1px rules only, header micro-labels, generous row height, wrapped in overflow-x:auto.
- **Chips/tags**: 1px border, uppercase 10.5px tracking .16em, no radius.
- **Quote**: Big Shoulders 600 uppercase at 28–40px, oxblood opening mark.

## Motion
- Reveal on scroll: opacity 0 → 1, translateY(18px) → 0, 600ms ease-out, IntersectionObserver, staggered 60ms. Respect prefers-reduced-motion.
- Buttons: 180ms background transition. Nothing else moves. No parallax, no floating shapes.

## Voice (copy rules)
- Direct, calm, confident. Short sentences. Second person.
- Power belongs to *her*: "Stronger at fifty than you were at thirty." "Strong is not a size." "Built for the next thirty years."
- Never: "ladies", "toned", "bikini", "shred", "summer body", scale numbers, before/after bodies. Military = calm and preparation, never combat stories.
- **Max's past (his own request, 5 Sep 2026):** his military / security-work years abroad are backstory only — at most one calm sentence inside his story ("Before coaching, years in security work abroad. He left that life; this one is quieter."). Never a headline, sub-line, hook, stat, chip, section name or format concept. The brand is built on what he is NOW: calm, patient, private, one client at a time, evidence-based strength for women 40+.

## Hard requirements (every page)
Single self-contained index.html, inline <style>/<script>, vanilla JS only, Google Fonts via <link>. Responsive 360px → 1440px+, zero horizontal overflow (`html,body{overflow-x:clip}`; wide tables scroll in their own container). Every <img>: alt, loading="lazy" (except hero), object-fit cover container. Focus-visible states. `::selection{background:var(--ox);color:var(--bone)}`. No emoji anywhere. Inline SVG icons only, 1.5px stroke.
