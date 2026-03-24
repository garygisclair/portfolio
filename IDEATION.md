# Portfolio Redesign — Ideation Notes

## Direction: Warm Organic
**Branch:** `redesign/warm-organic`
**Status:** Foundation applied, needs refinement
**Date:** March 24, 2026

---

## Reference Sites

### Primary Inspiration
- **Tenor Finance** (tenor.finance) — serif+sans pairing, cream backgrounds, warm near-black text, generous spacing, pill buttons
- **Ogaki Digital** (ogakidigital.com) — warm beige `#F2EDEB`, staggered text animations, backdrop-blur nav, scroll reveals
- **New Genre Studio** (newgenre.studio) — warm gradients, green/orange accents, immersive scroll backgrounds
- **DreamLab** (enterdreamlab.com) — glassmorphism, 14px border-radius, smooth scroll, scroll-triggered reveals

### Refinement Reference (Latest)
- **Claude Blog** (claude.com/blog) — the closest match to our target direction. Key observations below.

---

## Claude Blog Design Analysis (from screenshot)

### Color
- **Background**: Warm off-white/cream — very similar to our `#FAFAF5`
- **Text**: Warm near-black — close to our `#28281F`
- **Accent**: Warm terracotta/rust (the asterisk in the Claude logo)
- **CTAs**: Pure black `#000` solid buttons with white text — NOT colored accent buttons
- **Muted text**: Warm gray for dates, descriptions
- **Borders/dividers**: Very faint warm gray hairlines

### Typography
- **Headings/category links**: Large serif font, confident weight — "Agents →", "Claude Code →", "Enterprise AI →" are massive, editorial
- **Body/nav/dates**: Clean sans-serif, regular weight
- **Nav links**: Sentence case (not uppercase), medium weight, no letter-spacing
- **Hierarchy is extreme**: The category links are easily 48-64px, body text is 14-16px. The contrast between heading and body creates visual drama
- **Arrow links (→)**: Used as navigation cues alongside serif headings

### Layout & Spacing
- **Hero area**: Enormous vertical padding — the "Blog" heading + category links take up nearly the full viewport
- **Nav**: Ultra-clean — white/cream background, thin bottom border only, NO shadow, NO backdrop blur. Flat and confident.
- **Card row**: Horizontal scroll of article cards — text only (title + date), separated by thin vertical divider lines, no card borders or backgrounds
- **Thin horizontal divider** between hero and card section — just a 1px hairline
- **"Filter and sort" section**: Below the fold, unobtrusive
- **Content max-width**: Roughly 1200-1400px

### Cards / Article List
- **No card backgrounds** — articles are just title + date on the cream background
- **Vertical dividers** between cards (thin gray lines)
- **No hover shadows or lifts** visible — the interaction is likely opacity-based
- **Dates are small, muted** — secondary info, not competing with titles

### Buttons
- **Primary CTA**: Solid black pill (`border-radius: 9999px`), white text — "Try Claude"
- **Secondary**: Outline pill with dark border — "Contact sales"
- **No colored accent on buttons** — the terracotta/rust appears only in the logo mark, not in UI elements

### Shape Language
- **Pill buttons**: Full rounded (9999px radius)
- **Content areas**: No visible rounded corners — the design is flat/editorial
- **Very minimal use of containers/cards** — content floats directly on the background

---

## Refinements to Apply to warm-organic

### Priority 1 — High Impact
1. **Swap CTA button from terracotta to black** — solid black pill with white text for primary, outline black for secondary. The terracotta accent should appear in decorative elements (section labels, timeline dots, hover states) but NOT on buttons
2. **Simplify nav** — remove backdrop-filter blur and box-shadow. Just cream background + thin border-bottom. Flat and confident like Claude's
3. **Remove section header border-top lines** — replace with thin hairline dividers or remove entirely. Let whitespace and typography create section separation
4. **Increase vertical spacing** — the hero especially needs 2x the current padding. Sections need more breathing room between them

### Priority 2 — Typography
5. **Make headings bolder/larger** — the DM Serif Display headings could be larger, especially the hero name and title. Claude's blog uses massive serif text that fills the viewport
6. **Consider swapping hero subtitle styling** — make it lighter/more muted, push it further from the heading to create more contrast
7. **Remove the decorative section-label__line** — or make it much more subtle. Claude's blog uses no decorative line elements, just text hierarchy

### Priority 3 — Cards & Components
8. **Simplify portfolio cards** — reduce or remove card borders. Let the image and text do the work. Consider removing the card background and letting content float on cream
9. **Simplify card hover** — instead of border-color change + translateY + shadow, consider just opacity dimming of siblings (like Claude's blog does)
10. **Skill tags** — already good as paper labels on warm surface. Could make border even more subtle

### Priority 4 — Polish
11. **Noise texture overlay** — currently applied. Verify it's subtle enough (3% opacity). May need to reduce or remove if it feels grainy on a bright background
12. **Scroll reveal animations** — currently 0.6s with cubic-bezier. Good. Could slow down slightly to match the contemplative, editorial pace
13. **Logo treatment** — consider if the split-color logo (gary/gisclair) still works in this context, or if a single-color approach is more aligned

---

## Current Token State (warm-organic branch)

```css
--color-bg:             #FAFAF5;      /* warm cream */
--color-card:           #FFFFFF;      /* white cards */
--color-accent:         #C4764E;      /* terracotta — keep for decorative, NOT buttons */
--color-text:           #28281F;      /* warm near-black */
--color-text-muted:     #44403B;      /* medium gray-brown */
--color-text-dim:       #7E7D7A;      /* light warm gray */
--color-surface-warm:   #F3EDE4;      /* secondary warm surface */
--font:                 'DM Sans', sans-serif;
--font-heading:         'DM Serif Display', serif;
--radius-sm:            12px;
--radius-md:            16px;
--radius-lg:            24px;
```

### Proposed Token Changes (next iteration)
```css
/* Buttons — black instead of terracotta */
--color-btn-primary-bg:   #28281F;    /* near-black solid */
--color-btn-primary-text: #FFFFFF;    /* white on black */
--color-btn-outline:      #28281F;    /* dark outline */

/* Nav — simplified */
/* Remove backdrop-filter, remove box-shadow, keep thin border only */

/* Section borders — remove or replace */
/* .section-header--blue border-top: none */
/* .section-header--purple border-top: none */
/* Use thin hairline dividers between major sections instead */
```

---

## What's Already Working Well
- Cream background tone (`#FAFAF5`) — nearly identical to Claude's blog
- DM Serif Display for headings — right family, editorial feel
- DM Sans for body — clean, humanist, warm
- Terracotta accent for decorative elements
- Scroll reveal animations
- Warm shadow palette
- Skill tags as paper labels
- No uppercase on buttons/nav (already removed)

## Questions to Resolve
- Should the hero keep the dashboard preview image, or go full editorial like Claude's blog (just text)?
- Should portfolio cards have any background/border at all, or float like Claude's article cards?
- Is the noise texture adding or distracting?
- Font size scaling — how large should the hero name/title go? Claude goes massive (60-80px+ equivalent)

---

## Files Modified (warm-organic branch)
- `styles.css` — all design tokens, component styles, animations, texture
- `index.html` — font swap, video removed, reveal classes, observer script
- `portfolio.html` — font swap, reveal classes, observer script
