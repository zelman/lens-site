# Lens — public site

A single static credibility page. It gives warm intros and LinkedIn traffic a
legitimate place to land. **Reference surface, not a funnel** — it collects
nothing and links to nothing functional.

Scope: `Lens Public Site — Scope v1.0` (June 2026).

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

## Before deploy — required substitutions (2)

1. **Contact alias** — replace the placeholder address in `index.html`
   (appears in both CTAs; search: `CONTACT`):

        hello@lens.invalid   →   <branded contact alias>

   The `.invalid` TLD is deliberate — it guarantees the placeholder cannot
   silently ship as a working address. (Recommended: a branded alias, **not**
   personal Gmail, on a public page.)

2. **Validation quotes** — replace the three `[ PLACEHOLDER … ]` lines in the
   "Early signal" section (search: `PLACEHOLDER`) with the exact anonymized
   callouts from investor deck v7.4.4 slide 3. Held as placeholders on
   purpose — **do not manufacture quotes.** Roles are already in place
   (managing partner / PE operating partner / ICF-credentialed coach).

## Open inputs (owned by Eric)

| Input | Status | Notes |
|---|---|---|
| **Domain** | open | Credibility precondition; does **not** block the build. Point a custom domain when chosen; Vercel subdomain first. |
| **Contact alias** | open | Required substitution #1 above. |
| **Validation quotes** | open | Required substitution #2 above — drop the three anonymized lines from deck v7.4.4 slide 3. |

## Deploy (Eric — owns Vercel + any credential step)

1. Substitute the contact alias (above).
2. Create a **new, separate** Vercel project from this repo (do not reuse the
   product project). Framework preset: **Other / static**. No build command,
   no env vars.
3. Deploy. Vercel serves `index.html` at the root.
4. Point the custom domain when chosen.

## Versioning

Bump the build stamp on every deploy — it appears in two places in
`index.html`: `<meta name="build">` and the footer (`BUILD …`). Current:
`2026.06.04-v0.2`.

## Out of scope (v0)

No app link · no forms · no auth · no CMS/blog · no multi-page · no
cookies/trackers · no Airtable · no changes to the product repo.
