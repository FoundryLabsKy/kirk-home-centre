# Kirk Home Centre website

A complete, production-grade, multi-page brochure/catalog website for Kirk Home
Centre, 257 Eastern Avenue, George Town, Grand Cayman, delivered as a single
self-contained `index.html`. Hash-routed, no build step, no external JavaScript.

Open `index.html` in any modern browser, or host it on any static host behind
HTTPS (GitHub Pages, Netlify, S3, or a plain web server). HTTPS hosting is a
launch requirement; the current kirkhomecentre.ky one-pager is plain HTTP.

## Pages

Home, Departments (all 11), Exclusive Brands, Storm Prep, Contractor Sales,
Delivery & Installation, Our Story, Visit Us. Routes are hash-based:
`#/home`, `#/departments`, `#/brands`, `#/storm`, `#/contractors`,
`#/delivery`, `#/about`, `#/visit`.

## Design

- **Palette:** validated against an owner-supplied storefront photo. The
  accent is Kirk's actual sign red, `#C0272D`, sampled from the ships-wheel
  mark and exposure-corrected against the white sign panel; it is the single
  accent, used only on CTAs and aisle tabs. Kirk Heritage Navy `#0B2C4D`
  (from the brand research) is the supporting dark ground, Warm White
  `#F7F5F0` the base, Charcoal `#2B2B2B` the body text, and Garden Green
  `#3E7C3A` semantic success. All colour pairs pass WCAG AA (verified with
  axe). All colours are CSS variables in one token block.
- **Type:** Bricolage Grotesque (display) + Karla (body), loaded async from
  Google Fonts with clean system-font fallbacks; a slow font CDN can never
  block first paint.
- **Signature element:** departments are presented as numbered in-store
  aisle signboards, and the home hero's right side is the store directory
  board. Renumber the aisles in the `DEPTS` array (top of the script) if the
  store's real aisle plan differs.

## What is real vs. what to confirm

Everything factual comes from researched sources: the address, P.O. box,
phone and fax, split hours (Home Centre 7:00–5:30, Contractor Sales 7:00–5:00,
Mon–Sat), founding year and founders, the Kirkconnell family history, the 2026
expansion figures (26,072 sq ft addition, 208 parking spaces), the exclusive
SIW/CWS supplier status, the Rohl/Toto/American Standard/Huffy lines, the
4.2★/365+ Google rating, and every testimonial (verbatim, with attribution).

Items the owner should confirm before launch:

1. **Form email.** Forms compose a `mailto:` to `info@kel.ky`; that is the currently
   published support address (`FORM_EMAIL` constant in the script). Replace it
   with a kirkhomecentre.ky mailbox when one exists, and consider replacing the
   whole `mailto:` step with a `fetch()` to a form endpoint.
2. **Aisle numbers** are illustrative; set them to the real floor plan.
3. **Delivery promise** wording ("delivery day in writing on your receipt",
   "call before the window if anything slips") is a proposed service standard,
   drafted to answer the store's most common complaint. Management should sign
   off before it goes live.
4. **Logo.** The header carries a full inline-SVG recreation of the storefront
   sign lockup: the ships-wheel with turned club handles and open centre, the
   heavyweight K, and the stacked KIRK HOME CENTRE wordmark on a white panel.
   It was rebuilt from an owner-supplied photo of the Eastern Avenue signage.
   Swap in the official vector art in the `.logo` block and the favicon
   `<link>` when Kirk provides it; also confirm permission to use the mark,
   and match the wordmark typeface, before public launch.
5. **Best of Cayman awards** wording on the Our Story page; confirm the exact
   categories/years the store wants to claim.
6. **WhatsApp.** A click-to-chat link is recommended (heavily used in Cayman)
   but deliberately omitted until the store confirms a WhatsApp-enabled number.

## Seasonal behaviour

The storm-season banner shows itself automatically from 1 June through
30 November (visitor's local clock) and links to the Storm Prep page. The
open/closed chip in the utility bar is also computed from the visitor's clock
against the Mon–Sat 7:00–5:30 hours.

## Photography

The site is deliberately photography-independent (typographic + aisle-sign
visual system) so it can launch before a photo shoot. When professional photos
of the storefront, departments, and brand displays arrive, natural slots are:
the home hero's directory column, the department rows, and the Our Story page.

## Accessibility and quality

Verified in a headless browser: all eight routes render with correct titles
and no horizontal overflow at 1440px and 375px, the mobile menu opens/closes
and navigates, forms validate inline (name/email/topic) and compose their
mailto, `aria-current` tracks the active route, the storm banner toggles by
month, and an axe scan reports zero critical or serious issues on sampled
pages. Reduced motion is respected (reveal animations and smooth scroll are
disabled), focus states are visible throughout, and touch targets are ≥44px.

## SEO

`HardwareStore` JSON-LD structured data with the full NAP, split department
hours and exclusive brands is embedded in the head, along with complete
Open Graph/Twitter meta. After launch, the highest-value follow-ups from the
research report: claim the Google Business Profile, and consolidate the
directory listings (Ecay, Yabsta, Cayman.Directory, FindYello, Cybo) to the
canonical name "Kirk Home Centre", one phone number, and 7:00 AM hours.
