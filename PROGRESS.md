# Progress: restyle copy (project-v2)

## Round 1: restyle pass
- [x] Copy of project created, original untouched.
- [x] Audit: 29 box-shadow, 24 transform, 22 transition, 1 gradient, 2 backdrop-filter, 1 keyframes, 12 uppercase, 29 bold weights, footer href="#" on 10 pages.
- [x] CSS: gradients, backdrop filters, transforms, transitions, keyframes removed. Radii mapped to 4/6/8px. Shadows kept on overlays only. Weights 400/600. Tabular numerals added.
- [x] Copy: emoji removed, footer links removed, greetings removed, sentence case, exclamation marks and em dashes removed.
- [x] Home stats restructured. initHomeIntroPage null-safe.
- [x] Theme toggle and greeting code removed from app.js.
- [x] node --check app.js and services.js: pass.
- [x] verify (copy of tools/verify.js pointed at project-v2): VERIFY CLEAN.
- [x] jsdom: smoke 42/42, prof 16/16, fac-desk 18/18, banner 17/17, org 26/26 (assertions updated for removed greeting and theme toggle, and new heading casing).
- [x] run-tests: same 11 failures as the untouched original. Cause is date-dependent (event dates and registration flow relative to 2026-10-21), not the restyle.
- [ ] 360px and desktop visual check in a browser (no browser available).
- [ ] Full hardcoded color move to :root (about 54 literals remain).
