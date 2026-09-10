# Changelog

All notable changes to the South Africa ISP Tracker public demo are recorded here.
Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/); versioning
follows [Semantic Versioning](https://semver.org/) (MAJOR.MINOR.PATCH).

The version number shown here matches the `<meta name="app-version">` tag in
`index.html` and the `v{version}` badge in the page's footer.

## [1.0.0] — 2026-09-10

### Added
- First build, replicating the zwispqosd (Zimbabwe) demo/backend split pattern for
  South Africa from day one — no export options here (see `saispqosp` for those),
  brand footer/logo matching zwispqosd, versioning in place.
- Provider list (`DATA`), ten entries: Vodacom, MTN South Africa, Telkom Mobile,
  Cell C, rain (mobile); Openserve, Vumatel, Herotel, MetroFibre Networx, Frogfoot
  Networks (fixed/fibre) — sourced from ICASA's State of the ICT Sector Report and
  each company's own investor/trading results, with published-vs-derived figures
  and known data gaps (rain's undisclosed subscriber count; single-aggregator-
  sourced fibre figures) called out explicitly in each entry's `note`/`source`.
- 10 real South African cities for GPS/nearest-city matching (Johannesburg, Cape
  Town, Durban, Pretoria, Gqeberha, Bloemfontein, East London, Polokwane,
  Mbombela, Kimberley) and small, clearly-illustrative seed QoS/status/speed data
  across them.
- South Africa-correct phone number handling (`+27`, leading-0 national format)
  in `normalizePhone`/`isValidPhone`.

### Notes — deliberate v1 scope cuts (see README.md for the full list)
- English-only UI (community-translation code stays functional for English wording
  fixes; South Africa's 12 official languages are a future addition, not
  fabricated here).
- `ISP_ASN` and `PHONE_ISP_PREFIXES` both start empty — no verified data compiled
  for this build; both already degrade gracefully when empty.
- Cloudflare Radar national-benchmark feature not invoked (Zimbabwe-only edge
  function; a second, unverified proxy wasn't built sight-unseen for this release).
