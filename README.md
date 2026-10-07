# Digital Majlis · Central Riyadh — Prototype (POC)

Interactive proof-of-concept of the Central Riyadh **Digital Majlis** app, prepared by **NHC Innovation**.
It is a single static page (`index.html`) with no backend. Everything runs in the browser.

> This is a demo, not an official application. All data is sample data and is saved only in the viewer's browser.

## Demo accounts

All accounts use the same password: **`Cadec@2026`**.

| Persona | Username | Password | Opens on |
|---|---|---|---|
| Visitor | `sara` | `Cadec@2026` | Home |
| Verified resident | `abukhalid` | `Cadec@2026` | Home |
| Business owner | `munira` | `Cadec@2026` | Business |
| Partner & donor | `partner` | `Cadec@2026` | Donations |
| CADC team | `cadc.ops` | `Cadec@2026` | CADC dashboard |
| NHCI presenter (all access) | `nhci.admin` | `Cadec@2026` | User journeys |

- Visitor, resident, business and partner accounts see the app modules only.
- `cadc.ops` adds the CADC dashboard, roadmap, solutions and guided journeys.
- `nhci.admin` sees everything and is the account to present with.
- Each account keeps its own bookings, points, notifications and plan. Shared items (feedback, ads, Balady+ content, proposals) are common to all accounts **on the same browser**, so cross-persona flows (resident reports → CADC processes → resident is notified) can be demonstrated by logging out and in.

## Languages

The site opens in **English**. Use the **ع / EN** button in the top bar (or on the sign-in page) to switch between English and Arabic; the layout flips between left-to-right and right-to-left, and the choice is remembered in the browser.

## Mobile app

Visitor, resident, business and partner accounts open as a **mobile app**: on a desktop screen the app appears inside a phone frame with a status bar, bottom tab bar (Home, Map, Events, Heritage, More) and bottom-sheet pop-ups; on a real phone it fills the screen like a native app. The CADC team and NHCI presenter accounts open the full web dashboard, with a phone button in the top bar to preview the app. Guided journeys switch between phone (visitor steps) and web (CADC steps) automatically.

## Heritage tours

On **Heritage & culture → Schedule a tour**, visitors pick a trail, day and time slot (live seat availability), tour type (guided SAR 35/person, self-guided audio free, private group SAR 250), guide language, group size and accessibility needs, pay (test gateway) and get a QR tour ticket with meeting point and guide. Tours can be rescheduled or cancelled, appear under My account, and are listed for CADC on the dashboard overview.

## Sending activities to app users

CADC dashboard → **Send activities**: create a new event (added to the app calendar), an offer, a service alert, a heritage tour or a community campaign; choose the audience segment (all users, visitors, verified residents, businesses, partners, heritage enthusiasts, people in Central Riyadh now), channels (in-app, push, SMS, email — push/SMS/email simulated), send now or schedule, and preview the phone notification. Users who turned off that notification type are excluded. Recipients see a “Message from CADC” card on Home and an actionable item in the bell that opens the event ready to book; the **Sent activities** table shows reach, open rate and bookings per activity.

## Guided user journeys

Sign in as `nhci.admin` (or `cadc.ops`) and open **User journeys**. Each journey switches automatically to the right persona account at every step (for example, resident → CADC team → resident) and returns you to your own account at the end:

1. First-time visitor — first-sign-in consent, plan, book and pay, arrive, schedule a tour, heritage trail, rate a finished event from the Home “Today” card, post-visit impact summary
2. Neighbourhood resident — resident offers, map feedback, CADC resolves it, resident is notified and rates it, proposals, resource sharing (borrow requests reach the owner, who accepts or declines)
3. Business owner — create ad, CADC approves (or rejects with a reason so she can edit and resubmit), ad performance, post a job and get notified of applicants
4. CADC team — indicators and a “Needs action” list with counts on each tab, send an activity, Balady+ content approval, utilities coordination, digital twin, solutions
5. Donor or partner — donate, crowdfund, carbon offset, sponsorship request, CADC follows up, impact summary
6. Visit inside a building (Masmak Fortress) — check-in straight from the event or tour ticket, floor plan with “you are here” and live crowd levels, step-by-step indoor directions (with a step-free option), audio stories per hall, upper floor and watchtower, 3D walk-through, collecting stamps for the Explorer badge, then CADC's indoor analytics
7. CADC sends an activity — create a new event and audience, preview and send, the visitor receives it and books from the notification, CADC measures opens and bookings, reminds non-openers and duplicates the activity

The Masmak floor plan is illustrative, not the architectural drawing.

See **QC.md** for the latest quality-check results.

## Security note

The login is a **demo gate only**. Passwords are stored as SHA-256 hashes in the page, but anyone with the page source can bypass a front-end check. Do not reuse these passwords elsewhere and do not put real or confidential data in this repo.

## Hosting on GitHub Pages

1. Push this folder to the repository's `main` branch.
2. Repository **Settings → Pages → Build and deployment → Source: Deploy from a branch**, branch `main`, folder `/ (root)`.
3. The site is served at `https://<owner>.github.io/<repo>/` within a minute or two.

GitHub Pages on a free account requires a public repository; private-repo Pages needs GitHub Pro, Team or Enterprise. The page carries `noindex, nofollow` so search engines skip it.

To reset demo data: Home → «إعادة ضبط البيانات التجريبية», or clear the site's browser storage.
