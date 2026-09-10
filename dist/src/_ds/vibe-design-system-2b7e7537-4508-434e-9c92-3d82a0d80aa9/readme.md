# vibe — Design System

> A playful, collage-first social/dating app. People build a **collage board** —
> photos, album art, stickers and scribbled text on a candy-colored canvas — and
> others browse those boards in a feed, like or pass, and start chatting. Built
> iOS-first (Saint Petersburg / Moscow market; copy is bilingual-friendly).

This project is the consumable design system: tokens, fonts, icons, brand assets,
reusable React components and a full interactive UI kit.

---

## Source of truth

- **Figma:** "vibe (Copy).fig" (mounted virtual file). Page `/design` holds the
  product frames (`collage-feed`, `my-collage`, `buttons`, `headers`,
  `illustration`, `appstore-v3`) plus a ~369-component library.
- Tokens were materialized from the file's two Variable collections (399 vars,
  Light/Dark + brand/platform theme modes) → `tokens/fig-tokens.css`.
- Icons materialized from the `Icon16/24/40/52/56*` set → `assets/icons/`.
- The reader is NOT assumed to have Figma access; everything needed is copied in.

---

## What's inside (manifest)

| Path | What |
|------|------|
| `styles.css` | Global entry point — `@import` manifest only. Consumers link this. |
| `tokens/fig-tokens.css` | Figma Variables (colors, scales, all theme modes). |
| `tokens/colors.css` | Brand semantic colors (`--vibe-red/blue/yellow/heart`, ink, status). |
| `tokens/fonts.css` | Font families + Fredoka webfont. |
| `tokens/typography.css` | Type scale (`--vibe-text-*`). |
| `tokens/effects.css` | Radii, spacing, shadows, the liquid-glass fills. |
| `assets/brand/` | The `vibe` wordmark (SVG, single-color). |
| `assets/icons/` | `icon-data.js` + `Icon.jsx` (44 bundled brand glyphs) + name index. |
| `assets/imagery/` | Sample collage photos & sticker cut-outs. |
| `components/` | React primitives — see list below. |
| `ui_kits/vibe-app/` | Interactive collage-app prototype (feed · likes · chats · profile · editor). |
| `guidelines/` | Foundation specimen cards (Design System tab). |

**Components:** `buttons/` (EllipseButton, RectButton) · `forms/` (Input, Checkbox,
Radio, Switch) · `feedback/` (Counter, PageControl, Tooltip) · `media/` (Avatar,
MusicCard) · `navigation/` (Tabbar, NavHeader) · `feed/` (HeartButton) ·
`core/` (Card, Tag, ListRow) · plus the `Icon` component.

Use components via the compiled bundle: `const { EllipseButton } = window.VibeDesignSystem_2b7e75`.

---

## CONTENT FUNDAMENTALS

The voice is **warm, lowercase, playful and a little flirty** — like a friend
hyping you up, never a corporate product.

- **Casing:** lowercase by default, even the logo (`vibe`) and headlines
  (`find your vibe`, `it's a vibe!`). Sentence case for body; rarely all-caps.
- **Person:** speaks as **"we"** to the user and addresses them as **"you"**
  ("Allows vibe to see your music and find out something about you").
- **Length:** ultra-short. Buttons are 1–2 words (`Continue`, `Customise`,
  `Done`, `Skip`). Prompts are one friendly sentence.
- **Tone:** human and concrete ("sushi date?", "looking for a gig buddy",
  "film photos & techno") over marketing-speak. Music & taste are the love language.
- **Emoji:** used sparingly and naturally inside chat/user content (🌼 🍣),
  NOT in system UI labels or headings.
- **Signature lines:** "find your vibe", "it's a vibe!", "your collage, your people".
- **Bilingual:** real screens mix English and Russian (city names «Санкт-Петербург»);
  keep that lived-in feel when localizing.

---

## VISUAL FOUNDATIONS

**The big idea — collage.** Every profile is a scrapbook board: a flat candy
backdrop with photos (white 5px borders, slightly rotated), album-art "music
stickers", die-cut PNG stickers (drop-shadowed), and text on little white pills.
Items are deliberately tilted ±4–8° for a hand-pasted feel.

- **Color:** signature **yellow** backdrops, plus lilac / mint / paper. The accent
  is **electric blue** `rgb(12,105,255)` (and its glass gradient → cyan). The red
  `rgb(240,63,53)` wordmark and the vivid **pink like-heart** `rgb(255,45,146)`
  are the emotional pops. Text is near-black ink `rgb(10,12,17)`.
- **Type:** rounded **display face** (Fredoka, standing in for "Rooftop Dodo")
  for big playful moments and button labels; **SF Pro** at standard iOS sizes for
  all UI text. Min UI size 12px.
- **The "liquid glass" control system** — the defining surface treatment:
  gradient fill + a top **sheen** overlay (white→transparent, `mix-blend:overlay`)
  + an **inset rim** (1px color edge, inner bottom glow, inner dark) + a soft drop
  shadow. Primary = blue glass, secondary = gray glass, tertiary = white glass.
  Captured in `--vibe-glass-*`, `--vibe-rim-*`, `--vibe-sheen`.
- **Shape:** very round. Controls are circles or pills (radius 100); cards 14–20px;
  bottom sheets 34px top corners. Icon buttons are perfect circles.
- **Elevation:** soft, low-contrast shadows (`--vibe-shadow-control/card/pop`),
  never harsh. Floating elements (tabbar, hearts, tooltips) hover over content.
- **Backgrounds:** full-bleed flat color behind collage; white/`#fff` for list,
  chat and settings surfaces. Frequent `backdrop-filter: blur` on floating chips.
- **Motion:** quick and springy. Buttons scale up ~1.06 with a focus ring on press;
  the like-heart pops with an overshoot spring; toggles slide. Keep it under ~200ms.
- **States:** hover/press = scale + brightness dip + colored focus ring (blue, or
  red for destructive). Disabled = flat `rgba(244,244,244,.9)` fill, 30%-ink content.
- **Transparency & blur** used for floating overlays (match screen, music ticker,
  tool docks) — `rgba` white/ink + `blur(6–8px)`.
- **Imagery vibe:** warm, real, a little lo-fi — film photos, magazine covers,
  album art, quirky 3D sticker objects. Not stocky, not corporate.

---

## ICONOGRAPHY

- **Two tiers.** (1) **Brand glyphs** — filled, friendly icons and third-party
  logos (Apple Music, Google, Pinterest, Unsplash, Instagram, Telegram) plus the
  tabbar fills (house / heart / chat / person) and feed glyphs. These are the
  44 real vectors materialized into `assets/icons/icon-data.js`; render with
  `<Icon name="Icon24HeartFill" size={24} />` (single-color icons paint with
  `currentColor`). See `assets/icons/Icon.d.ts` for the full valid-name list.
- **Line icons.** The Figma file draws most UI line icons (plus, close, chevrons,
  search, undo, crop…) with **Apple SF Symbols**, a proprietary font that can't be
  redistributed. We substitute **Lucide** (CDN) — same clean ~2px rounded stroke.
  ⚠️ *Substitution flagged:* if you have the real SF Symbols / licensed set, swap
  the Lucide usages. Load Lucide via `<script src="https://unpkg.com/lucide">` and
  render `<i data-lucide="plus">` then `lucide.createIcons()`.
- Sizes follow the source: 16 / 24 / 40 / 52 / 56. 24 is the workhorse.
- Emoji appear only inside user content (chat, board text), never as UI chrome.

---

## ⚠️ Substitutions & caveats (please help us perfect these)

- **Fonts.** "Rooftop Dodo" (display/buttons) and "SF Pro" (text) are not
  redistributable here. We render Fredoka (Google) for display and the native SF
  stack for text. **Please upload the licensed Rooftop Dodo + SF Pro web fonts**
  and we'll wire real `@font-face` rules.
- **Icons.** Line icons are Lucide stand-ins for Apple SF Symbols (see above).
- **fig-tokens.css** carries the whole multi-brand variable system from the file
  (Atomize / Project-X/Y/Z, iOS platform modes). The vibe product itself uses the
  `--vibe-*` semantic layer; the raw vars are kept for completeness.

---

## Using the system

```html
<link rel="stylesheet" href="styles.css">
<script src="_ds_bundle.js"></script>
<script>const { EllipseButton, Tabbar, HeartButton, Icon } = window.VibeDesignSystem_2b7e75;</script>
```

Everything is driven by CSS custom properties — reference `--vibe-*` tokens rather
than hard-coding values, and lean on the `--vibe-glass-*` / `--vibe-rim-*` recipe
to keep new controls on-brand.
