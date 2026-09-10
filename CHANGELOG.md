# Changelog

All notable changes to the South Africa ISP Tracker public demo are recorded here.
Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/); versioning
follows [Semantic Versioning](https://semver.org/) (MAJOR.MINOR.PATCH).

The version number shown here matches the `<meta name="app-version">` tag in
`index.html` and the `v{version}` badge in the page's footer.

## [1.1.0] — 2026-09-10

### Added
- **Real official language chips**, replacing the v1.0.0 English-only scope cut:
  English, Afrikaans, isiZulu, isiXhosa, isiNdebele, Sepedi, Sesotho, Setswana,
  siSwati, Tshivenda and Xitsonga — 11 of South Africa's 12 official languages
  (source: South African Parliament press release confirming all 12, checked
  2026-09-10). The 12th, South African Sign Language (added by the 2023
  constitutional amendment), is a visual-gestural language and isn't representable
  by this site's text-string UI, so it's explained in the translate panel's prose
  instead of given a fake text chip.
- isiXhosa, Sesotho, Setswana and Tshivenda reuse zwispqosd's existing best-effort-
  draft translations for the same standard languages (isiXhosa/Xhosa, Sesotho/
  Sotho, Setswana/Tswana, Tshivenda/Venda are shared across the border) — legitimate
  reuse, still marked unreviewed. Xitsonga also reuses a Zimbabwe draft, but it's
  flagged lower-confidence in the code comments: it's sourced from Zimbabwe's
  Shangani entry, a related dialect rather than standard South African Xitsonga.
  Afrikaans, isiZulu, Sepedi, siSwati and isiNdebele have no legitimate cross-border
  source — critically, South Africa's isiNdebele (Southern Ndebele) is a different
  language from Zimbabwe's Ndebele (Northern Ndebele) despite the similar name, so
  it was NOT conflated with Zimbabwe's existing Ndebele draft — so those five ship
  as chips with empty translation content, falling back to English with the
  standard "🚧 need translation" badge rather than being guessed.
- The suggest/endorse community-translation flow now covers all 11 text-chip
  languages.

### Fixed
- Corrected the README/CHANGELOG "English only" v1 scope note, which undersold what
  "replicate the same pattern as Zimbabwe" was always meant to include — Zimbabwe's
  own site treats its official/constitutional languages as core, not optional.

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
- English-only UI at launch — superseded in v1.1.0, see above.
- `ISP_ASN` and `PHONE_ISP_PREFIXES` both start empty — no verified data compiled
  for this build; both already degrade gracefully when empty.
- Cloudflare Radar national-benchmark feature not invoked (Zimbabwe-only edge
  function; a second, unverified proxy wasn't built sight-unseen for this release).
