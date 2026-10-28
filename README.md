# AEVON Studio

The five supplied Figma screens, implemented in the managed Next.js / Payload template.

## Pages

All pages are statically generated:
- `/` (Home): features the 4 selected projects (Cold Sober, STONECREST, NLTA Online, STASH), Kurt's portrait and red statue graphic, updated about copy, marquee, and manifesto.
- `/work`: features all 6 projects (Cold Sober, GSD BREW, STONECREST, SCARB RUN CLUB, STASH, NLTA Online) linking to their respective subpages.
- `/studio`: updated About copy, new 4-tile photographic mosaic, updated Approach copy, and rewritten Founder section with portrait.
- `/contact`: working contact form saving submissions privately into Payload.
- `/work/[slug]`: 6 dedicated project subpages (`/work/cold-sober`, `/work/stonecrest`, `/work/gsd-brew`, `/work/scarb-run-club`, `/work/stash`, `/work/nlta-online`), each with custom editorial banners, alternating image pair galleries, and an interactive "Next project" bar that cycles through the projects.

## Motion

- `src/components/motion/motion-provider.tsx`: shared animation frame loop, Lenis scrolling, session intro, page shutter, cursor, reveals, parallax, marquee, and reading progress.
- Reusable primary button, navigation link, project card, floating input, audience chips, gallery image, and footer wordmark components live in `src/components`.
- Motion and design tokens are in `src/app/(frontend)/styles.css`.
- Reduced-motion preferences disable inertia, parallax, marquees, custom cursor, tilt, and large transforms.

## Contact backend

Messages save to **Payload Admin → Studio → Contact messages**, at `/admin`. Only administrators may read, update, or delete messages. Anonymous creation is restricted to the validated contact Server Action. Fields are allowlisted, workflow status is server-owned, and the form includes a honeypot and a per-email submission cooldown.

Email notifications are not configured: “Sent” confirms that the message was saved, not that an email was delivered. No public account system or custom Admin authentication was added.

## Design limitations

- The supplied Inter faces resolve successfully. Helvetica Now Display Bold, Medium, Regular, Extra Bold, and Extra Black could not be resolved for this Make file (`not_found`). Requested family names remain declared with Arial as the explicit fallback; no substitute font is registered under a Helvetica name.
- Social profile URLs were not supplied. Links currently open the corresponding social platform homepage.
- Only one case-study design was supplied. Project placeholders open the Cold Sober case study; the “Next project” bar returns to Work.

## Checks

```sh
pnpm exec tsc --noEmit
pnpm format --check 'src/app/(frontend)' src/components src/collections/ContactMessages.ts src/lib/contact-validation.ts src/payload.config.ts
figma make verify-deploy
```

The development server is host-managed; do not start another development server.
