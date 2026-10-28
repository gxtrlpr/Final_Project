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
