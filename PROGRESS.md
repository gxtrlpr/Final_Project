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

## Round 2: review fixes
- [x] "undefined" office icon, "&bull;" text, hero contrast, hamburger menu, link color, empty profile chip fixed.
- [x] node --check, verify, and the jsdom suites re-run. Same baseline failures in run-tests only.
- [ ] Re-deploy to GitHub Pages. This was not done here.

## Round 3: mobile nav and dark theme
- [x] Professor Desk in main nav, bell icon on Alerts, dark mode toggle.
- [x] node --check, verify, and jsdom suites re-run. Same 11 baseline run-tests failures.
- [ ] Visual check of the dark theme and the 768px menu in a browser (not available here).

## Round 4: restored original items
- [x] Greeting, eyebrow, footer links restored. About, Privacy, and Contact pages created.
- [x] Dark block regenerated after CSS changes. Braces balance.
- [x] node --check, verify, and jsdom suites re-run. Greeting assertions updated to the restored behavior.
- [ ] Emoji icons: pending user decision.

## Round 5: duplicate Student ID column
- [x] Registrants and attendees tables fixed (headers, cells, colspan).
- [x] Table audit (table-audit.js in .testenv-v2): 24 pages, visitor and host, plus professor. Clean.
- [x] verify, syntax, and jsdom suites re-run. Same 12 date-dependent run-tests failures as the original.

## Round 6: event dates moved to November
- [x] All 4 event dates and 4 registration deadlines moved from OCT to NOV.
- [x] Login pop-up blur restored.
- [x] verify, syntax, table audit, and jsdom suites re-run. run-tests: 1 failure left, a queue position rule question (open item).

## Round 7: course and name placeholders
- [x] Courses replaced everywhere in data and placeholders. Names replaced in seeds, placeholders, speaker, emails.
- [x] Suites: 238 of 239 run-tests assertions pass. Other suites pass. Table audit clean.
- [ ] Open: queue position counting a ticket being served.
