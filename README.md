# Appointments and Schedule

**A school project and website prototype for City College of San Jose del Monte (CCSJDM).**

Appointments and Schedule brings common campus activities into one place. It demonstrates how students could book appointments with school offices or professors, take a digital queue number, browse campus events, and keep track of their schedules. Professors and event organizers have their own views for managing appointments and events.

This repository contains the source files and assets for a classroom submission and presentation. It is a demonstration prototype, not a production system or an official college service.

## Project overview

| Item | Details |
| --- | --- |
| **Project type** | School project / website prototype |
| **Institution** | City College of San Jose del Monte |
| **Purpose** | Demonstrate a campus appointment, queue, and event system for class submission |
| **Technologies** | HTML, CSS, and JavaScript |
| **Data storage** | Browser local storage with sample data |

## Main features

- **Appointments:** Browse school offices and professors, review requirements, and book available slots.
- **Digital queues:** Take a walk-in queue number and view its status when a service is open.
- **Campus events:** Browse events, view their details, and register to attend.
- **My Schedule:** Review appointments, queue numbers, and event registrations in one place.
- **Professor desk:** View and manage professor appointments using a demo faculty login.
- **Event dashboard and check-in:** Organizers can manage events, review registrations, and record attendance. These organizer pages are intended for desktop use.
- **Interface:** Responsive student-facing pages, a mobile navigation menu, and a dark mode option.

## Run the project locally

No package installation or build step is required. A modern web browser and a local web server are enough.

1. Download or clone this repository and open a terminal in the project folder.
2. If Python 3 is installed, start a local server:

   ```bash
   python3 -m http.server 8000
   ```

   On Windows, `python -m http.server 8000` may be used instead.
3. Open **http://localhost:8000/** in your browser. The home page is `index.html`.
4. Stop the server with `Ctrl+C` when finished.

The site may also be hosted as static files on a web server. Keep the `assets/` folder alongside the HTML, CSS, and JavaScript files.

## Demo access

The login screens simulate different user roles for presentation purposes. They do **not** provide real authentication; do not enter actual passwords or sensitive personal information.

- **Student:** Enter a name, an ID in the format `2026-00123`, and any non-empty demonstration password.
- **Professor:** Use a sample faculty ID such as `fac-001` and any non-empty demonstration password.
- **Event organizer:** Use a sample faculty or staff ID such as `fac-001` or `STF-001`, plus any non-empty demonstration password. The event dashboard and check-in desk require a desktop-sized screen.

## Project files

| Path | Purpose |
| --- | --- |
| `index.html` | Home page and introduction |
| `services.html`, `service-details.html` | Office and professor directory, appointments, and queues |
| `events.html`, `event-details.html` | Event directory and event information |
| `my-events.html` | Student schedule and registrations |
| `faculty.html` | Professor desk |
| `officer.html`, `checkin.html` | Event dashboard and attendance check-in |
| `about.html`, `privacy.html`, `contact.html` | Project information pages |
| `app.js` | Shared interface, login, and event functionality |
| `services.js` | Appointment, queue, and related demo functionality |
| `style.css` | Shared styling and responsive layouts |
| `assets/` | Images and other project assets |
| `CHANGELOG.md`, `PROGRESS.md` | Development notes and project progress |

## Prototype limitations

- Appointments, registrations, queue numbers, and sessions are stored in the current browser's local storage. They are not synchronized across devices or users, and other people using the same browser profile may be able to view them.
- Clearing the site's browser data removes local changes; sample data may be created again when the site is opened.
- The site uses sample records and simulated logins. It is not connected to a production database or a real campus booking service.
- Some pages reference `manifest.json`, which is not included in this repository. A browser may report a missing manifest, and app installation is not configured.

For a class submission, the project team can add its course, section, member names, instructor, and submission date as required by the instructor.
