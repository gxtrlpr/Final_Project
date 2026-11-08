# Changelog: restyle copy (project-v2)

Source: /home/user/project (unchanged). This copy holds the flat restyle.

## Decisions
- Accent: #1d5fa6, a deep blue sampled from the seal's blue globe. Contrast on white is above 4.5:1. The seal's dominant magenta and gold fail text contrast, so they are not used as text colors. The old #1a73e8 is replaced everywhere in CSS, theme-color, and manifest.
- Typeface: one system stack from the original file. A web font would need a local font file, which was not provided.
- Radii: 4px, 6px, 8px. The 999px pills became 6px. Circular avatars keep 50%.
- Shadows: kept only on the modal, bell dropdown, mobile nav, and toast. Removed elsewhere, and 1px hairline borders added where a shadow was removed.
- Weights: 400 and 600 only.
- Theme toggle (light, dark, high contrast) removed. It was not a requirement and added a third visual mode.
- "Welcome" greetings removed from the top bar and login toasts. Toasts now read "Signed in as <name>." This conflicts with the earlier "greeting once per login" rule and is pending a user decision.
- Footer About, Privacy Policy, and Contact links removed. They were `href="#"` placeholders.
- Emoji icons removed (office icons, stat icons, auth choice icons, bell). The bell button now reads "Alerts". Meaningful symbols kept: star, check, back arrow.
- Buttons and headings converted to sentence case. Form labels were left as-is.
- Home stats: "Appointment slots left today" is the single large figure. The other three are secondary lines. A zero count shows "None" or "None left", not 0. initHomeIntroPage is null-safe.
- Hero eyebrow text, uppercase transforms, transitions, transforms, gradients, backdrop filters, keyframes, and reduced-motion overrides removed.
- Tabular numerals applied to counts, codes, and slots.
- Exclamation marks and em dashes removed from user-facing copy.

## Known gaps
- About 54 hardcoded hex colors remain in style.css. They are not yet moved to :root variables.
- Not visually checked at 360px or desktop in a browser. No browser is available here. Checked by jsdom suites and grep only.
- The repository name "webpge" is noted, not renamed.

## Round 2: review fixes
- Office cards: removed the leftover "undefined" icon text from the office card heading and the service details hero.
- Replaced every literal "&bull;" with a middle dot (·).
- Hero: the background was a pale blue while the text stayed white. The hero is now the solid accent with white text.
- Hamburger menu: restored as a bordered button with three bars, shown at 768px and below.
- Links: set to the accent color, replacing the browser's default purple.
- Profile chip: the empty course badge is no longer rendered when the course is blank.
- Theme: a stale stored theme attribute is cleared on load, so every page shows the plain light theme.

## Round 3: mobile nav and dark theme
- Professor Desk and Event Dashboard links moved into the main nav list, next to Home, Appointments, Events, and My Schedule.
- Alerts now has a bell icon (inline SVG, no emoji).
- Dark mode added as a text link in the nav (not a button, so Logout stays the only button-styled item). The choice is saved in localStorage.
- The dark theme is generated from the light CSS by flipping each color's lightness. Hues are kept. Seal and wordmark images keep their own white backgrounds.

## Round 4: restored original items
- Greeting ("Welcome back, <name>!" with avatar) restored, once per login, using the original code and styles. Login toasts restored to "Login successful. Welcome, <name>!" and "Welcome, <name>!".
- Hero eyebrow "City College of San Jose del Monte" restored on the home page, in flat style without uppercase.
- Footer About, Privacy Policy, and Contact restored as links to new pages: about.html, privacy.html, contact.html. They replace the old "#" placeholders.
- Footer links now have a simple flat style (the original had none).
- Not restored: emoji icons on event cards, detail pages, and the empty state. They conflict with the "no emoji icons" rule. Pending user decision.

## Round 5: duplicate Student ID column
- Registrants table on officer.html: removed the second "Student ID" column. It repeated the student ID, because the pass code is the student ID. Empty-state colspan changed from 7 to 6.
- Attendees list on checkin.html: removed the same duplicate column. Empty-state colspan changed from 7 to 6.
- Check-in by code still uses the same value. Only the repeated display column was removed.
- Audit: every table on all pages, for visitor and host sessions, plus the professor page, was checked with jsdom. Each table's header count matches every row's cell count, and no table has duplicate headers.

## Round 6: event dates moved to November
- Event dates: OCT 10, 15, 22, 29 changed to NOV 10, 15, 22, 29. Registration deadlines OCT 07, 13, 20, 27 changed to NOV 07, 13, 20, 27. Day numbers unchanged.
- Login pop-up blur restored (backdrop blur 3px on .auth-modal and .modal). The restyle had removed it, but the original brief requires the pop-up to blur and dim the background.
- Test harness only (not the app): the date-filter test uses November dates. The queue test starts from an empty queue, because the demo seed adds today's tickets. The clinic walk-in check runs only when the clinic is open, matching the registrar check.
- Open: queuePosition counts a ticket that is being served as still ahead until it is completed. One test expects it to stop counting once called. Pending a decision.

## Round 7: course and name placeholders
- Every course reference (BSIT 3A, BSCS 1B, BSBA 2C, BSCS 2A, and the "BSIT and BSCS" event audience text) now reads "BSEMC-GD and BSEMC-DA".
- Seeded student names are "Student. Name". Seeded professor names are "Professor. Name". Form placeholder examples follow the same rule.
- Event speaker: "Professor. Name, President, CCSJDM".
- Professor emails use their faculty IDs (for example fac-001@ccsjdm.edu.ph) instead of surnames.
- Note: the user's text said "Proffesor. Name". The spelling was corrected to "Professor. Name". Tell me if the misspelling was intended.
- Tests: expectations updated to the placeholder names. The queue-position question remains open.

## Round 8: course codes and placeholder names (corrected)
- Course codes: seeded students use BSEMC-2GD, BSEMC-3DA, and BSEMC-4GD (years 2 to 4). Placeholders use "e.g. BSEMC-2GD". The event audience reads "BSEMC-2GD, BSEMC-3DA, and BSEMC-4GD majors, 2nd to 4th year".
- Professor placeholder spelled "Professor. Name" (the spelling used in the earlier round was corrected; the user's "Proffesor" spelling was not used).
- Student names in seed data and placeholders are "Student. Name". No person names remain in the copy.
- The original project is unchanged.

## Round 9: verified course codes and names, queue position fix
- Verified on disk: no BSIT, BSCS, BSBA, or BSEMC-GD references remain in HTML, JS, or JSON. Course codes are BSEMC-2GD, BSEMC-3DA, and BSEMC-4GD.
- Verified on disk: seeded students are "Student. Name". Professors are "Professor. Name" (correct spelling).
- Verified rendered text: 12 pages across visitor, host, student, and professor sessions show no old course codes or person names.
- Verified Registrants table on the Event Dashboard: rows show "Student. Name", a student ID, a course code, and an event title.
- Queue position: a ticket that is being served or called no longer counts as ahead. Waiting tickets still count. This matches the intended behavior and the queue test.
- The preview server on port 8001 had stopped. It was restarted from /home/user/project-v2.
- Queue assertions in run-tests run only while the registrar is open. Outside office hours, they are skipped.

## Round 10: repo sync, button text verification, dark-mode fix, manifest

- Uploaded files synced into the repository. The uploaded `style.css` was missing the `.btn-primary:visited` and `.btn-register:visited` rules described in Round 9, so the button-text fix was not actually present. It is restored.
- Task 1 (button text) verified with a cascade calculator instead of a browser: 156 button states pass WCAG AA across 6 page contexts, light and dark, normal, hover and visited. The 12 disabled-button states stay below AA on purpose, because WCAG 1.4.3 exempts inactive controls.
- Real bug found and fixed: in dark mode `.hero-actions .btn-secondary` was painted by the dark `.btn-secondary` rule (specificity 0,2,0) instead of `.hero-actions .btn-secondary` (0,1,1). It rendered near-black text on a near-black background, 1.12:1. The dark hero now keeps the transparent background and light text, 12.18:1.
- `manifest.json` created. All 12 pages linked it and the file was missing. It uses the two icons already in `assets/` and the accent color.
- Verification: 36 of 36 page renders clean (12 pages x visitor, student, host), 0 broken asset references, CSS braces balance, JS syntax passes.
- Written but not yet acted on: a full text-contrast audit over 2502 text elements found smaller items, including `.demo-note` at 2.56:1, the hero eyebrow chip, and four category badges. Scheduled as a separate step.

## Round 11: navbar redesign (Task 2)

- Built from the three reference images, in separate steps: HTML, then CSS, then JavaScript, then verification.
- Assets: the supplied `ccsjdm-seal.jpeg` and `ccsjdm-wordmark.jpeg` are byte-identical (same MD5) to the copies already in `assets/`, so no file was replaced. The seal now sits in a circular frame, matching the reference's rounded logo slot.
- Desktop bar: seal, the user pill, the centred segmented nav (the current page is a raised white pill with accent text), and a moon button on the right. Dark mode is a moon button, as in the reference.
- User pill: the display name and the notification bell with a red count badge, and nothing else. There is no chevron and no person icon, per the user's instruction.
- Names follow the requested rule. Students show the username they chose. Professors show "Prof." plus the name. Organizers show "Organizer." plus the name. The prefix is not stacked if the stored name already starts with it.
- Signed out: a blue "Log In" button in the pill's place, as chosen.
- Account menu: clicking the pill opens a menu with the role page (Professor Desk or Event Dashboard) and Log out.
- Mobile (860px and below): the nav collapses to a drawer under the bar. The drawer holds the links, the role link, a Dark Mode row with a toggle switch, and a red Log out row, matching the reference.
- The hamburger closes on outside taps, on picking a link, and when the window widens past 860px. Its label switches between Open menu and Close menu.
- The initials circle and the online dot were removed. You asked for the pill to hold only the name and the bell, and the only circle in the bar is the seal.

- The current page keeps a real link with `aria-current="page"` instead of a plain span, so it is still clickable and screen readers still announce the position.
- A small inline script in `<head>` applies the saved theme before first paint, so dark mode no longer flashes white on load.

### Bugs found and fixed while verifying
- The drawer's Log out row was rendering with a raw browser button border because it sat outside the `.nav-menu` rules. It now has its own full reset.
- The notifications dropdown was positioned against the small bell icon inside the pill, so it overflowed off the left edge of the screen. It is now anchored to the account area.
- The signed-out Log In button sat cramped inside the grey pill. It now has its own compact shape.

### Verification
- 41 of 41 interaction assertions pass: login, logout from both the drawer and the menu, the account menu open and close, the hamburger, theme switching and persistence, the professor role label, and `aria-current`.
- A real Chromium sweep of 96 loads (12 pages x 4 sessions x light and dark) reports no console errors, no failed requests, no missing images and the correct theme on every page.
- Screenshots reviewed at 1400px, 820px and 420px, in light and dark, signed in and signed out.
- Earlier checks still pass: 36 of 36 jsdom renders, 0 broken asset references, 156 of 156 button contrast states, JS syntax, CSS braces balanced.

## Round 12: remove the remaining initials circles

- The welcome card on the home pages had its own initials circle. Removed for the same reason as the navbar: the seal is the only circle.
- Removed the unused `.greeting-avatar` rules so nothing is left dead.
- Deleted `assets/example.txt`, a stray test file no page referenced. The assets folder now holds only the four real images.

## Round 13: log in from anywhere, land on home

- Logging in as a student or a professor now always sends the user to the home page, wherever they were on the site. The rule applies from every one of the 12 pages.
- The welcome message is carried through the page load. A toast that was on the old page would vanish the instant the browser navigated, so the message is saved to `sessionStorage` and shown once on home.
- Registering for an event while logged out still works: the register intent survives the login, and the welcome message explains that the event must be opened again. There is deliberately no second redirect, because that would bounce the user back and forth.
- The organizer login still goes straight to the Event Dashboard. That page is the organizer's workspace, and sending them home would have been a downgrade. They see their login gate when signed out, so there is no redirect loop.

### Care taken
- An earlier draft of the register resume redirected to `events.html`, which looped forever because every page runs the same start-up code. It was caught in review and replaced with a message instead of a redirect.
- A pending-action queue existed for this exact case, but nothing called it, so it is left alone rather than re-wired into a redirect path.

### Verification
- 25 of 25 real-browser assertions: student login from 10 different pages all land on home, the faculty login does too, logging in while already on home stays on home, the navbar shows the name after arrival, and the organizer reaches the dashboard.
- The register-while-logged-out flow completes in a single navigation, with no loop.
- 96 of 96 page loads clean (12 pages x 4 sessions x light and dark), with no console errors, no failed requests and the correct navbar.
