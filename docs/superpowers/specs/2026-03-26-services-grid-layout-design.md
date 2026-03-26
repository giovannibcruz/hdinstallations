# Services Section — Grid Layout Redesign

## Context
The current services section uses a horizontal scrolling carousel with 11 cards. The user wants to replace it with a structured grid layout inspired by a shadcn-style grid feature cards component, while keeping the existing stock photos as the primary visual element on each card.

## Design

### Layout
- **Grid:** 3 columns x 4 rows (12 cells total)
- **Cards 1-11:** The 11 services from `hd-installations.md`
- **Card 12 (bottom-right):** Dark CTA card — "Need Something Specific?" with "Request a Quote" button linking to `#contact`
- **Responsive:** 1 column on mobile, 2 columns on tablet (`sm:`), 3 columns on desktop (`md:`)
- **Borders:** Dashed borders between cards (`divide-x divide-y divide-dashed border border-dashed`) matching the reference component style
- **Container:** Max width `max-w-5xl`, centered within the section

### Card Structure (services 1-11)
Each card contains:
1. **Photo** — stock image from `services-pictures/`, `h-40` height, `object-cover`, with gradient overlay (`bg-gradient-to-t from-black/40 to-transparent`)
2. **Title** — `font-display text-sm md:text-base`, charcoal color
3. **Description** — `text-xs text-charcoal/45`, 1-2 lines from client brief

### Card 12 (CTA)
- Background: `bg-cream` (matches section bg) with a subtle gold-tinted border or accent to differentiate it from the photo cards
- Gold accent icon (phone or arrow SVG) at top, same style as trust point icons (`bg-gold/10` circle)
- Heading: "Need Something Specific?" in `font-display` charcoal
- Subtext: "Tell us about your project and we'll tailor a solution." in `text-charcoal/45`
- Button: `bg-charcoal text-cream` (dark button on light card — inverts the visual weight to make the CTA pop without breaking the color palette), links to `#contact`
- The CTA card stands out because it has no photo — the clean open space and prominent button draw the eye naturally within the grid

### Interactions
- **Hover on photo:** `scale-110` zoom with `transition-transform duration-500 ease-out` (same pattern already used on the current carousel cards)
- Each card has `overflow-hidden` to contain the zoom
- CTA button gets the existing `btn-gold` hover/active states

### Section Header
- Title: "From Delivery to Install, We've Got It Covered" (single line, `lg:text-[2.8rem]`)
- Gold divider below

### What Gets Removed
- The horizontal carousel (`servicesTrack`, `overflow-x-auto`, `flex gap-4`)
- The arrow navigation buttons (`servicesPrev`, `servicesNext`)
- The services carousel JS (prev/next scroll logic)

### Services Order (matches client brief)
1. Furniture Installation
2. Delivery Services
3. Project Management
4. Anti-Tip Services
5. Reconfiguration
6. Service Calls & Maintenance
7. Relocation & Move Services
8. Warehousing
9. Receiving Services
10. Decommissions
11. Fabric Cleaning
12. CTA → Contact

## Files to Modify
- `index.html` — lines ~671-833 (services section HTML)
- `index.html` — JS section (remove services carousel logic)

## Verification
1. Screenshot on localhost:3000 and verify 3x4 grid renders correctly
2. Verify all 11 service titles and descriptions match `hd-installations.md`
3. Verify hover zoom works on photos
4. Verify CTA card links to `#contact`
5. Check mobile responsiveness (1 col) and tablet (2 col)
