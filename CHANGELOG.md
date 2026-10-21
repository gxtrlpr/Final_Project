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
