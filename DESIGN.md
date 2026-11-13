# Beyond Culture — DESIGN.md

Governs all future generation of beyondculture.ai. Chosen direction: **Style I — pastel bento** (warm cream canvas, one pastel tile per product, rounded 30px cards, near-black pill buttons, coral accent #e8553d). References from awesome-design-md: notion / pinterest (soft coloured tiles), claude (warm paper, serif).

## 1. Overview
One page, one idea: **a necklace of seven pearls on one thread** — 知る→問う→見る→確かめる→整える→語る→贈る. The thread follows a life: childhood (①–④), working years (⑤ 整, Kitchiri for law firms), later life (⑥⑦). One idea across every field: AI is the tool; the person thinks, decides and feels.
The page explains why one company makes a kanji app, a math course and a 60th-birthday gift, then routes each visitor to the right brand site. It does not sell.
Mood: ink on paper, generous space, one red seal. No decorative bubbles, no glass blur.

## 2. Colors
| Token | Hex | Use |
|---|---|---|
| --washi / --kami | #E9E7E1 / #F5F3EE | page and cards |
| --sumi | #14161A | text, thread, dark philosophy band |
| --shu | #e8553d | the ONLY accent: clasp, later-life pearls (語 一), header button |
| tiles | #fde3cf #dcecd3 #d8e6f7 #f0dcef (①–④), #f8d5cf #eddfc6 (⑤⑥) | one pastel per product |
| canvas | #fffaf2 | page; philosophy band #1f1d1a |
| --koke | #7A8A5C | focus ring only |
| --lamp | #E9B870 | small labels on dark band only |
Rule: one accent per screen. Brand colors of products stay on their own sites.

## 3. Typography
Shippori Mincho B1 (headlines, pearl characters, weight 800), Zen Kaku Gothic New (labels), Cormorant Garamond (Latin captions).
Body ≥ 14.5px, line-height ≥ 1.9. Japanese: `line-break:strict; word-break:auto-phrase`. Hero headline is vertical (`vertical-rl`) in ja / zh-Hant, horizontal in en; "AI" uses `text-combine-upright`.

## 4. Layout
Max width 1180px. Order: Hero + necklace → seven pearls in three doors → Philosophy (dark band) → News/Payments → Contact → Company.
Children's door (①–④) comes first and is wider; the professional door (⑤, slate tile, ink pearl) and later-life door (⑥⑦) share the second row. Kitchiri wording: a tool for lawyers, never "AI lawyer", "legal advice" or 法律相談; no prices, no numbers; English and Chinese say "Japanese-language service".
Mobile: ring becomes a vertical thread, pearls stacked, 44px+ tap targets, no horizontal scroll.

## 5. Elevation & Shapes
Hairline `0 0 0 1px` borders; shadow only on hover. Cards radius 6px, pearls are circles, buttons are pills. No backdrop blur.

## 6. Components
- **Pearl**: white circle, ink outline, one Mincho character; coral fill for ⑥⑦, ink fill for ⑤. Hover/tap shows promise in the ring centre.
- **Product card (one component ×6)**: character + number/verb, name, audience tag, one-line promise, "from" price, one button (無料で試す / 詳しく見る).
- **Clasp**: red square seal 留 at the top of the ring.
- Books hang on ② and ③ as a small line, not as cards.

## 7. Motion
Thread draws in 1.8s, pearls appear ①→⑦. CSS only. `prefers-reduced-motion` shows the finished state.

## 8. Do / Don't
Do: Japanese first, then EN / 繁中; keep each language a full version; keep one file, push-to-deploy.
Don't: add prices/checkout (brand sites sell), add a founder's note (philosophy replaces it), add a second accent color, use glass/blur or floating bubbles, change the 特商法 / payment text without checking Shopify.

## ICHIREI wording (Nov 2026)
ICHIREI is a same-day e-gift for any important relationship (verb 贈る). Never write 木に刻む, 手彫り, hand-carved, gold leaf, or wood delivery dates; never say the receiver chooses the character; never mention AI in ICHIREI text. Its card may show the e-gift price line; the English button goes to ichirei.soul-id.jp/en.

## Card illustrations
Each product card carries one line-drawing (inline SVG, ink strokes, one coral accent) showing what the product does, with a one-line caption under it. They are illustrations, never fake screenshots. Replace with real product images only when the owner supplies them.
