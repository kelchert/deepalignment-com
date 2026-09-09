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

## Current state (compact) — refreshed 2026-09-09 session close
`main`, in sync with `origin`. HEAD `3053b25`. The site is live and stable; SEO/OG/JSON-LD
metadata hand-maintained per page; Netlify serves from repo root (`publish = "."`,
`pretty_urls = true`). Pages: `/`, `/faq`, `/support`, `/privacy-policy`, **`/guide`**
(`9c1bb84`, 2026-09-01), **`/user-agreement`**. No Netlify Form present yet
(da-android-notify is the first).

**App context — Resurface iOS 3.8 (43) was SUBMITTED 2026-09-08 and is IN REVIEW**, as was
Resurface-android vC7 / 1.0.6. 📌 **Resurface-android is held by MANAGED PUBLISHING: Google
approval does NOT publish it. Kenn's keystroke does.** A future reader must not read
"approved" as "live" — and note this same distinction is the release trigger for
focuswheelapp-com's held `feat/google-play-badge` branch.

## Shipped (durable milestones, most recent first)
- **Privacy policy: false clear-all claim struck, export corrected to present tense**
  (`866d55c`, 2026-09-06). `:311` claimed "Clear all data through iOS Settings" — a pathway
  that ships in NO release build: Reset for Demo is gated by `#if DEBUG || KENNSURFACE`
  (`SettingsView.swift:414`, `:589`) behind a five-tap reveal (`:377-383`), and the app
  publishes no `Settings.bundle`, so neither reading of the sentence was reachable. Removed
  rather than qualified. `:312`/`:319` said export was "coming soon" / "planned" — it has
  shipped on BOTH platforms since before this repo's first commit (`ExportManager.swift:18`
  text, `:161` PDF on iOS; `ConversationExport.kt:61` text on Android), so both now read in
  the present tense with the platform split named. **Verified live on the deployed page.**
  📌 `adef05f` (2026-07-22) was itself a correctness pass over this same file and walked
  past `:312` — the claim had been wrong since `2ee1dc0`, this repo's first commit.
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
