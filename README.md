# saispqosd

Public demo for the South Africa ISP Tracker — crowdsourced quality-of-service
ratings, live status reports and speed tests for South Africa's internet providers,
sourced from ICASA's sector reporting and operators' own published results.

Sibling of [zwispqosd](https://github.com/edmundondo/zwispqosd) (Zimbabwe) and
[bwispqosd](https://github.com/edmundondo/bwispqosd) (Botswana) — same codebase
pattern, same shared Supabase backend (multi-tenant via a `site` column), different
country data. See `zwispqosd`'s README/SETUP docs for the full technical background
on how the backend, live feeds (IODA) and speed test work — nothing about that
plumbing is South Africa-specific.

Formatted report exports (PDF/CSV/EPUB) live on the privileged
[saispqosp](https://github.com/edmundondo/saispqosp) backend, not here — see its
README for details.

## What's different about this site (v1 scope)

- **English only.** South Africa has 12 official languages, but populating verified
  translations for all of them is out of scope for this build — a deliberate v1
  scope cut, not a bug. The community-translation code path exists and works for
  English wording fixes today; adding a new language later needs no rebuild.
- **No backbone (RIPEstat/ASN) badges.** `ISP_ASN` is intentionally empty — no
  verified ASN-to-operator mapping has been compiled for South Africa's ten tracked
  providers yet. The badge simply doesn't render for any ISP without an entry, the
  same graceful fallback the Zimbabwe site already relies on for its own untracked
  ISPs.
- **No Cloudflare Radar national benchmark.** That feature calls a Supabase Edge
  Function that's hardcoded server-side to Zimbabwe's numbers only (and is a
  separately-tracked, not-fully-verified feature even there) — rather than build a
  second country-specific proxy sight-unseen, it's simply never invoked on this site.
- **No phone-prefix ISP detection.** `PHONE_ISP_PREFIXES` starts empty — South
  African mobile numbers have been portable between networks for years, so a small
  static prefix table wouldn't be reliable; left off rather than guessed.
- Seed ratings/status/speed data is illustrative, not a real crowdsourced history.

See `CHANGELOG.md` for version history.
