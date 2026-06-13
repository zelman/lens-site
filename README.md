# Lens — public site

A single static credibility page. It gives warm intros and LinkedIn traffic a
legitimate place to land. **Reference surface, not a funnel** — it collects
nothing and links to nothing functional.

Scope: `Lens Public Site — Scope v1.0` (June 2026).

**Status:** live in production at <https://zelmanlabs.com> (apex + `www`, own
Vercel project). Build `2026.06.12-v0.8`. `git push` to `main` auto-deploys.

## Hard constraints

1. **Zero PII capture.** No forms, no database, no Airtable, no email widget,
   no newsletter. The only contact mechanism is the `mailto:` link.
2. **No link into the live app.** Informational only — no "try it," no link to
   the R→C / C→C flows.
3. **Product-link is gated.** Linking this page to the product is allowed only
   after ALL of: R→C consent notice shipped · purge automation live · Privacy
   Policy published. Until then the page stands alone.
4. **Separate surface.** This is its own repo and its own Vercel project. It
   shares no code, routes, env, or analytics with the product. **Do not merge
   this into `zelman/lens`, and make no edits to `zelman/lens` for it.**

## Files

- `index.html` — the entire site (HTML + inline CSS, no JS, no dependencies).
- `vercel.json` — static deploy config + locked-down security headers
  (CSP `default-src 'none'`, no scripts, no third-party origins → reinforces
  the zero-tracker / zero-PII posture).
- `.gitignore`

## Contact alias

Both CTAs use the branded alias **`hello@zelmanlabs.com`** (the original
`hello@lens.invalid` placeholder has been removed). The CTAs also prefill the
draft body (Firm / Role / How I found Lens).

> ⚠️ **Forwarding receipt unverified.** A 2026-06-12 test to
> `hello@zelmanlabs.com` bounced. Confirm mail actually lands in Eric's inbox
> before relying on the CTA — the address is already live in production.

## Content

The "Early signal" section carries the locked trio of verbatim beta-tester
quotes (technical recruiter · executive beta tester · retired partner &
human-capital COO). No placeholders remain.

## Open inputs (owned by Eric)

| Input | Status | Notes |
|---|---|---|
| **Domain** | done | Live at `zelmanlabs.com` (apex + `www` on Vercel). |
| **Contact alias** | done — forwarding unverified | `hello@zelmanlabs.com` in both CTAs; 6/12 forwarding test bounced — verify receipt. |
| **Validation quotes** | done | Locked trio in place (v0.7 → restyled v0.8). |

## Deploy

Push to `main` → Vercel auto-deploys (project: `lens-site`, Lens team).
Framework preset **Other / static**, no build command, no env vars. Vercel
serves `index.html` at the root.

DNS: Squarespace-managed (Google Cloud DNS backend) →
`A @ 216.150.1.1` and `CNAME www aa81152aef73b33f.vercel-dns-016.com`.

## Versioning

Bump the build stamp on every deploy — it appears in two places in
`index.html`: `<meta name="build">` and the footer (`BUILD …`). Current:
`2026.06.12-v0.8`.

## Out of scope (v0)

No app link · no forms · no auth · no CMS/blog · no multi-page · no
cookies/trackers · no Airtable · no changes to the product repo.
