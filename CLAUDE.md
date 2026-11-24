# Skin Fairy Co. website

Production site for Skin Fairy Co., a solo esthetics brand. Owner of the code: Martin. Owner of the brand: his girlfriend (the esthetician). The goal: a visitor should feel like they are stepping into a spa the moment the page loads. Calm, slow, soft, intentional. Fairy, spa, holistic, wellness.

## Stack and commands
- Default: Vite + React + plain CSS (same as the portfolio) unless Martin says otherwise.
- `npm run dev`, `npm run build`. Run `npm run build` at the end of every pass.
- Hosting is Vercel. Work on a branch, never commit or push `main`. Small commits.
- Dependencies: allowed are Lenis (smooth scroll) and ONE animation library (GSAP + ScrollTrigger, or Motion). Propose which and why before installing. Nothing else without asking.

## Brand tokens (define once in :root, no other colors anywhere)
```css
:root {
  --sage: #788560;        /* brand green, large type, shapes, buttons */
  --sage-light: #C9D9B0;  /* washes, section tints */
  --blush: #E9A9B8;       /* soft accent, hovers, sparkles */
  --cream: #F6F3E4;       /* page background */
  --stone: #A39E9B;       /* hairlines, quiet UI */
  --ink: #2F3B2A;         /* TEXT. Proposed, verify >= 4.5:1 on cream, adjust if needed */
}
```
- Contrast facts: sage on cream is only 3.5:1, stone 2.4:1, blush 1.7:1, sage-light 1.3:1. Those are for large type, shapes and decoration only. Body text and small text use --ink.
- No dark sections, no dark mode, no heavy gradients. Soft washes only.
- Fonts: serif display (thin, high-contrast, elegant; Cormorant Garamond is the free baseline, test alternatives) paired with a clean sans for body (Catamaran or similar). Propose the pairing, show it, then lock it.

## Brand assets
- `assets/logo.png` (SF monogram with fairy and sparkles), `assets/Icon.png` (circular badge). Use the logo; do not redraw or alter it.
- The four-point sparkle from the logo is the signature motif. Reuse it sparingly (cursor dust, dividers, hover, tiny twinkles). Derive it as an SVG.

## Sections (order)
1. Hero. 2. Intro / mission. 3. Services. 4. About ("Meet the Skin Fairy"). 5. Credentials. 6. Before your visit (policies and prep). 7. Booking (small popup, bottom right, plus CTAs in header and hero). 8. Contact / footer.

## Services (names are settled, details are placeholders)
- Tooth gems: basic, model, complex
- Facials: 3 to 4 tiers
- Korean lash lifts
- Waxing: underarm, lip, eyebrows
- Back facials
Appointment types: silent, catch-up, music. Pricing, durations and package details: use obvious placeholders (`[PRICE]`, `[DURATION]`) until Martin supplies the refined packages. Layout reference for service cards: photo, title, price, duration, Book button.

## Motion spec (from the Venetian Spa reference; study the idea, never copy assets, code or layout)
Four moves, done well, not twelve:
1. Arch sheet: the first section is a cream sheet with a large rounded arch top that slides up over the hero like a curtain.
2. Scroll-scrubbed headline reveal: key headlines reveal word by word, tied to scroll position, by opacity only. Text stays real, selectable text in the DOM.
3. Pinned headline with floating arches: a centered headline stays pinned while arch-shaped images or cards drift past at different speeds (parallax layers). Credentials appear here as arch-shaped cards.
4. Slow drift: a very faint large fairy/sparkle watermark moves at its own slow speed behind content.
- Shape language: arches everywhere (image masks, cards, section tops). One slow cadence.
- Smooth scroll: Lenis, lerp about 0.08 to 0.1, native touch scrolling kept on phones. Stop the scroller while the booking popup is open.
- Only animate transform and opacity. No layout thrash.
- `prefers-reduced-motion`: no smooth scroll, no parallax, everything visible and static.
- Mobile: pinned and parallax sections get simplified so they stay smooth on a real phone.

## Imagery policy
- There are no final photos yet. Her professional headshots and full-body photos are coming. Build every image slot as a real arch/rounded frame fed from one config file, so photos drop in without layout changes.
- Until then: illustrations only. Soft sage/blush washes, botanical line art (SVG), grain, the sparkle motif. Mark every placeholder in code with `PLACEHOLDER`.
- Do NOT generate or add photorealistic people or faces, and no stock photos of faces or "results". They would misrepresent her work. Non-person ambient stock (botanicals, towels, candles) is allowed only if Martin approves each one and the license allows it.
- `assets/a_photo_of_my_treatment_room.png` is not a photo. It is her annotated reference board: examples of a treatment room and facial bar, the style of professional photo she wants, how she wants service/booking cards and the header to look, and another business's booking policies and prep steps (not hers; do not use them). Use it as direction only, never on the site. Where her board notes conflict with this file, her notes win.

## Content rules (no invented facts)
- Source of truth for copy: the mission and vision statements Martin provides. Mission: personalized skincare treatments that enhance natural beauty, using customized services and Korean skincare techniques. Vision: a calming, holistic space to escape daily stress. Audience: women 18 to 45 who love beauty and self-care.
- Never invent prices, testimonials, reviews, review counts, results, or credentials. Placeholders must be visibly marked.
- Licensing wording: she is an esthetics student working toward her Illinois license. Never write "licensed" or "licensed esthetician" until Martin supplies it. Credentials are described as courses completed, as text.
- Credentials (text list, confirm dates with Martin): 5 Day Accelerated Esthetics (Aesthetics Exposed Education); Laser Safety 101 (2 hours, Aesthetics Exposed Education); Introduction to Laser and Light Therapy (2 hours, Aesthetics Exposed Education); Introduction to Classic Eyelash Extension (training course); Brow Henna Expert, Brow Hybrid tint and mapping (Supercilium Academy). Certificate images live in `certificates/` with certificate IDs already covered. Do not use the unredacted originals. Showing her full legal name is Martin's call.

## Booking and forms
- Provider not chosen yet. Build the front-end popup only: name, email, service, appointment type (silent / catch-up / music), optional message. Submit does nothing yet and is labeled as a placeholder in code.
- Do NOT build consent or medical questionnaires. Do NOT collect health information, allergies, medications, or pregnancy status in any custom form or database. That goes through a vetted provider later.

## Working method
- Small changes. Screenshots at 1440px and 390px after each pass. Check performance on a phone for scroll sections.
- Passes in this order, one at a time, commit after each: (0) propose three genuinely different hero concepts as short written briefs and wait for Martin's pick, (1) tokens and fonts, (2) page skeleton with placeholder content, (3) hero and arch sheet, (4) smooth scroll and reveals, (5) services, about, credentials, before-your-visit, (6) booking popup UI, (7) illustrations, (8) polish: accessibility, performance, reduced motion, meta tags and favicon.
- Accessibility: real headings, alt text, visible focus, keyboard-operable popup (Esc closes, focus returns), 4.5:1 text contrast.
- Don't touch anything outside the current pass. If a request seems to conflict with this file, ask.
