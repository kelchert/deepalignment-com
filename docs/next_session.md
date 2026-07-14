# deepalignment-com — Next Session

Living handoff. Read at session start, update at session close. This repo is a sibling under
the [RDA] seat — keep this current so [RDA]'s rollup (→ DAC) can read it.

## Human status — deepalignment-com (seat's read, as-of 2026-07-14)
Onboarded into the doc-architecture today as a governed sibling repo (repo-local CLAUDE.md +
this handoff), following the FocusWheel-android precedent — the site had been taking commits
ad hoc with no spine. The site is live and stable, migrated off Wix to this self-hosted repo;
og:image is LinkedIn-tuned. The one active build ahead is the **da-android-notify** email-
capture form — the deepalignment.com twin of FocusWheel's Android-launch form — specced and
locked, not yet built. It's collect-only (no ESP wiring) and carries a one-time post-merge
form check once it lands.

## Current state (compact)
`main`, in sync with `origin`. HEAD `1e147cc` (Google Search Console verification token). The
site is live and stable; SEO/OG/JSON-LD metadata hand-maintained per page; Netlify serves
from repo root (`publish = "."`, `pretty_urls = true`). Pages: `/`, `/faq`, `/support`,
`/privacy-policy`. No Netlify Form present yet (da-android-notify is the first).

## Shipped (durable milestones, most recent first)
- **Google Search Console verification token** (`1e147cc`) — merged.
- **og:image refresh + LinkedIn tuning** (`82eb463`, `005a9e8`) — tagline + handle, then
  text stripped so LinkedIn renders `og:title` cleanly; `twitter:card` → large_image.
  Decision recorded in CLAUDE.md.
- **Self-host orb + og-image, drop Wix dependency** (`bf1b9e3`) — removed the Wix dependency
  for hero + preview card; upgraded the preview card.
- **Process list to 16 + hero pass** (`ed46261`) — 7 new entries, refined hero quote.
- **SEO metadata / OG / structured data / sitemap / robots foundation** (`bd6e497`).
- **Migrate deepalignment.com from Netlify(Wix) to this GitHub repo** (`2ee1dc0`) — origin.

## Open threads
- **da-android-notify capture (build) — FIRST tracked item, NOT built yet.** Port the
  FocusWheel Android-notify pattern onto deepalignment.com. Reference implementation:
  `focuswheelapp-com` commits `fa2c54e` + `fb0c6a0` (PR `b25dc06`). New form name
  **da-android-notify** — deliberately distinct from FW's `android-notify` (separate Netlify
  Forms tab entries, no co-mingling). Same badge-slot placement logic as FW: inline near the
  App Store badge, swaps to Play badge when Resurface Android ships. Known gap carried
  forward, not blocking: no ESP/export wiring yet, collect-only. Companion post-merge check
  once built: confirm da-android-notify detection in the Netlify Forms dashboard + one test
  submission. Spec locked 2026-07-13; durable spec home is the AP handoff
  (`attraction-promotion-docs/docs/next_session.md`, committed `e921873`). This is the
  deepalignment.com Android-launch capture pool — separate from FW's, no reconciliation.

## Parked
- OG/preview and copy are settled; no other design work queued.
