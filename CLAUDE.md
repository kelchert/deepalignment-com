# deepalignment-com — CLAUDE.md

The Deep Alignment brand/marketing site (deepalignment.com) — the LLC's web presence and the
Resurface web property. Static HTML/CSS, Netlify-hosted, migrated off Wix to a self-hosted
repo. Sibling repo under the [RDA] seat; reports to DAC. Not a port and not the app — this is
the web property. No parity target; the app repo (`~/Developer/Resurface`) is a separate seat.

## Session start (read first)
<!-- Intentionally a top-level section, not nested under Workflow: reading the shared docs
is portfolio-level policy (see deepalignment-docs/docs/DOC_ARCHITECTURE.md), a different
scope than this repo's workflow rituals. Do not flatten without revisiting that scope. -->
1. `git pull` the `~/Developer/deepalignment-docs` clone; read `docs/START_HERE.md` (hub
   index), `docs/DOC_ARCHITECTURE.md` (charter), `docs/COLLABORATION.md` (claude.ai
   disciplines — Kenn relays this into the claude.ai session), `docs/SESSION_RITUAL.md`
   (the open/close procedure — **run it**), and `docs/OUTSTANDING.md` / any handoff briefs
   relevant to this work. **To start, the human says: "run the session open ritual"; to
   end: "run the session close ritual."**
2. Read this repo's `docs/next_session.md` — the canonical handoff (current standing +
   owed work).
3. Precedence: the repo is canonical. No claude.ai-side or panel copy overrides an on-disk
   doc. Pull before reading; pull before push.

## What this repo is
The static site served at deepalignment.com. Plain HTML/CSS (no build step, no framework),
deployed by Netlify from the repo root (`netlify.toml` → `publish = "."`, `pretty_urls = true`).
Pages: `index.html` (home), `faq/`, `support/`, `privacy-policy/`; assets in `images/`; plus
`sitemap.xml`, `robots.txt`, and the Google Search Console verification file. og:image and
metadata are hand-maintained per page and tuned for LinkedIn (see Decisions Log). No email-
capture form is live yet — the `da-android-notify` Netlify Form is the first tracked build
(see `docs/next_session.md`).

## Deploy
Netlify deploys from the repo root (`publish = "."`) with `pretty_urls = true` and
email-obfuscation disabled (the toml comment explains why — it otherwise mangles support@
addresses into cdn-cgi artifacts). After any OG/metadata change, verify the rendered preview
on the target surface (LinkedIn for this site's promotion track) before considering it done.

## Data boundary
`publish = "."` means the whole repo root is a publication surface: anything present in the
tree ships on deploy, so keep non-public material out of the repo entirely (gitignore alone
does not stop a folder-root deploy — the portfolio publish-root lesson). When `da-android-notify`
ships, its submissions are the system of record in the **Netlify Forms** dashboard, never
mirrored here.

## Workflow (per COLLABORATION.md — the base layer, not restated here)
- claude.ai ([RDA] seat) designs/decides/specs; CC applies all file + git work; Kenn gates.
- Audit-first before any change; one-task-one-commit; the approval-before-commit gate is
  absolute.
- Verification for a site is the deployed page, not the local file: OG/preview changes are
  proven on the target surface; form changes in the Netlify Forms dashboard.

## Current state
Branch-state records the **sync condition** (e.g. "main, in sync with origin"), never the
self-HEAD SHA. The rolling state — what shipped, what's in-flight, what's owed — lives in
`docs/next_session.md`, refreshed every session close. Read it for current standing; this
file holds the durable spine, not the moving state.

<!-- Project-specific sections (page conventions, decisions log) added below as the work
surfaces them — not front-loaded. -->

## Decisions Log

### 2026-06 — og:image is text-free for LinkedIn (`005a9e8`, refined `82eb463`)
Text baked into the og:image was stripped so LinkedIn renders `og:title` cleanly and avoids
the PNG-text compression artifacts that appear when LinkedIn re-encodes an image-with-text.
Standing rule for this site's cards: keep promotional text in `og:title`/`og:description`,
not painted into the image; `twitter:card` is `summary_large_image`.
