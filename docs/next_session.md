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
`main`, in sync with `origin`. The site is live and stable; SEO/OG/JSON-LD
metadata hand-maintained per page; Netlify serves from repo root (`publish = "."`,
`pretty_urls = true`). Pages: `/`, `/faq`, `/support`, `/privacy-policy`, **`/guide`**
(`9c1bb84`, 2026-09-01), **`/user-agreement`**. No Netlify Form present yet
(da-android-notify is the first).

**App context — Resurface-android vC7 / 1.0.6 is PUBLISHED AND LIVE on Google Play as of
2026-09-09 ~11:11 AM ET** — 100% rollout, 177 countries. Public listing verified: title
"Resurface: Deep Alignment", developer Deep Alignment LLC, updated September 9, 2026.
`https://play.google.com/store/apps/details?id=com.deepalignment.resurface`
📌 **It published by Kenn's keystroke under MANAGED PUBLISHING, not by Google's approval** —
the distinction held exactly as recorded, and this is now the record of how it shipped rather
than a caution about what "approved" means. That same distinction remains the release trigger
for focuswheelapp-com's held `feat/google-play-badge` branch.
**Resurface iOS 3.8 (43) was SUBMITTED 2026-09-08 and remains IN REVIEW** — unchanged.

## Shipped (durable milestones, most recent first)
- **Google Play badge added to both CTAs — the site now tells the two-platform story**
  (`b160223`, 2026-09-09). Resurface: Deep Alignment Android 1.0.6 went live on Google Play
  the same day; `index.html` had been iOS-only. Adds the Play badge beside the App Store
  badge in the hero CTA and the closing CTA. Ports `.badge-row` + `.badge-link--play` from
  `focuswheelapp-com` `c726d18`; **not** ported were `.badge-group` and the price-note
  grouping, which have no counterpart in these simpler CTAs. The two badge heights are
  **optically matched, not numerically matched** — 48px Apple == 71px Play, because Google's
  badge PNG ships 646x250 with the artwork only 564x168 inside it (transparent padding baked
  in, ratio 1.488). That constant is recorded in the CSS comment; normalising the two numbers
  breaks the match. The block comment at `index.html:214` was also corrected from
  "App Store Badge" to "Store Badges" — Kenn-ruled, since the block now governs both stores.
  **Verified live on the deployed page** 2026-09-09 18:15:37 GMT, fetched cache-busted from
  outside: falsifier "Get it on Google Play" = 2 and `play.google.com/store` = 2; negative
  control (proves iOS was ADDED TO, not replaced) `badge-download-on-the-app-store` = 2 and
  `id6748240318` = 2; positive control "Your emotions are guidance" = 1, proving the fetch
  returned the real page so a zero would have meant absence, not a failed download.
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
- 🔑 **da-android-notify — DECISION FOR KENN. Its premise expired 2026-09-09. NOT DECIDED
  HERE.** The thread was specced 2026-07-13 as an Android-*launch notification* capture:
  "inline near the App Store badge, swaps to Play badge when Resurface Android ships."
  **Resurface Android has now shipped, and `b160223` is that badge swap.** Building the form
  as specced would collect people for an announcement that has already happened — the thing
  they would be waiting for is on the page above the form. The spec is not wrong; it was
  overtaken.
  **The two options, and Kenn picks:**
  1. **RETIRE it.** The launch it was built to announce is public. Nothing is owed.
  2. **REPURPOSE it to general updates**, the way `focuswheelapp-com` already did in
     `bec7cfa` — same form, re-aimed copy, no launch framing. If this is the pick, that
     commit is the port source and the audit-first rule applies to it.
  Unchanged either way if it is built: form name stays **da-android-notify**, deliberately
  distinct from FW's `android-notify` (separate Netlify Forms tab entries, no co-mingling);
  collect-only, no ESP/export wiring; companion post-merge check is da-android-notify
  detection in the Netlify Forms dashboard plus one test submission. Reference
  implementation `focuswheelapp-com` `fa2c54e` + `fb0c6a0` (PR `b25dc06`); durable spec home
  is the AP handoff (`attraction-promotion-docs/docs/next_session.md`, committed `e921873`).
- **`.claude/` is unguarded against the folder-root publish — small, separate task.**
  `netlify.toml:6` sets `publish = "."`, so the repo root IS the publication surface, but
  `.gitignore` does not list `.claude/`. `.claude/settings.local.json` exists on disk today
  and is **untracked**, so nothing ships right now — a single `git add .` is all that stands
  between that and a public settings file. Verified 2026-09-09: `git ls-files .claude` is
  empty and `git check-ignore .claude` reports NOT IGNORED. Fix is one line in `.gitignore`
  matching the existing anchored shape (`/relay/`, `/_to_delete/` from `3053b25`). Not done
  in `b160223` — that commit was scoped to `index.html` alone.

## Parked
- OG/preview and copy are settled; no other design work queued.
