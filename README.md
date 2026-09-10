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

- **11 of South Africa's 12 official languages as chips (English, Afrikaans,
  isiZulu, isiXhosa, isiNdebele, Sepedi, Sesotho, Setswana, siSwati, Tshivenda,
  Xitsonga); the 12th, South African Sign Language, is explained in prose instead**
  — SASL was added as an official language by the 2023 constitutional amendment
  (source: South African Parliament press release, checked 2026-09-10), but as a
  visual-gestural language it isn't representable by this site's text-based chip/
  string UI, so it's called out in the translate panel rather than given a fake
  text chip. Of the 11 text chips, isiXhosa, Sesotho, Setswana and Tshivenda ship
  with real best-effort-draft translations reused from the Zimbabwe site's existing
  (unreviewed) drafts for the same standard languages (isiXhosa/Xhosa, Sesotho/
  Sotho, Setswana/Tswana, Tshivenda/Venda). Xitsonga also has a reused draft, but
  flagged lower-confidence — it's derived from Zimbabwe's Shangani entry, a related
  dialect rather than the standard-Xitsonga-as-taught-in-South-Africa. Afrikaans,
  isiZulu, Sepedi, siSwati and isiNdebele have no legitimate cross-border source
  (South Africa's isiNdebele/Southern Ndebele is a different language from
  Zimbabwe's Ndebele/Northern Ndebele, despite the similar name — not conflated
  here) so those four chips exist and fall back cleanly to English with a
  "🚧 need translation" badge rather than being guessed. Community translation via
  the suggest/endorse flow works for all 11 text-chip languages today.
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
