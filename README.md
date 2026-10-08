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

Each account sees only what its persona needs (no gold plating):

- **Visitor (`sara`):** plan your visit, events, maps, smart parking, heritage, Heritage walk, Design your tour, inside the building, destination info, community feedback and polls, sustainability, offers and featured places, My account (visit summary), Help. No donations & partnerships, future expansion or digital twin.
- **Resident (`abukhalid`):** events, maps, parking with resident permit, destination info, heritage, community (feedback, polls, proposals, resource sharing), sustainability, resident offers and jobs, My account, Help.
- **Business (`munira`):** Business (ads and event promotions, jobs, featured places), events, maps, parking, destination info, community feedback and polls, My account, Help.
- **Partner (`partner`):** Donations & partnerships, sustainability, events, My account (contribution summary and impact report), Help.
- **CADC team (`cadc.ops`):** the CADC dashboard (overview, send activities, parking, feedback and messages, ads, Balady+ content, utilities, map services), digital twin, future expansion, indoor analytics, events, maps, parking, destination info, heritage and community. The guided user journeys and NHCI solutions pages are for the NHCI presenter (`nhci.admin`).
- `nhci.admin` sees everything and is the account to present with.
- Each account keeps its own bookings, points, notifications and plan. Shared items (feedback, ads, Balady+ content, proposals) are common to all accounts **on the same browser**, so cross-persona flows (resident reports → CADC processes → resident is notified) can be demonstrated by logging out and in.

## Languages

The site opens in **English**. Use the **ع / EN** button in the top bar (or on the sign-in page) to switch between English and Arabic; the layout flips between left-to-right and right-to-left, and the choice is remembered in the browser.

## Navigation

Every screen except Home has a back button that returns to the previous screen, including the CADC dashboard tab you came from. It sits above the page title on the web and in the top bar of the phone app (Alt + ← also works on a keyboard). Payment steps in event, tour and parking bookings have a back arrow that returns to the booking form without losing your choices.

## Mobile app

Visitor, resident, business and partner accounts open as a **mobile app**: on a desktop screen the app appears inside a phone frame with a status bar, bottom tab bar (Home, Map, Events, Heritage, More) and bottom-sheet pop-ups; on a real phone it fills the screen like a native app. The CADC team and NHCI presenter accounts open the full web dashboard, with a phone button in the top bar to preview the app. Guided journeys switch between phone (visitor steps) and web (CADC steps) automatically.

## Heritage walk

**Heritage walk** (from Heritage & culture, or More on the phone) is a self-guided walk through six stops: Masmak Fortress, Al Deerah Square, Imam Turki bin Abdullah Mosque, Qasr Al Hokm, Al Thumairi Gate and Souq Al Zal.

- **Overview:** the route on the map, 2.1 km and about 55 minutes, the list of stops and “Start the walk”, or “book it as a guided tour”.
- **Each stop:** the map follows you to the current stop, with numbered pins, “Stop 1 of 6” and progress dots. The stop card has an illustration, a sample narration and a note that CADC writes and approves the final text. An audio-story player shows progress (sample audio; no file plays).
- **Moving through:** each stop shows the next stop with its distance and walking time; “Next stop” and a back button; tap any pin or stop to jump to it. Progress is saved, so you can continue later.
- **Finish:** a summary, +30 points, the “Al Deerah Explorer” badge, a 1–5 rating and an option to book the same route with a guide.

## Design your tour (three suggested tours)

**Design your tour** (Heritage & culture, Home, or More on the phone) suggests three different walking tours automatically from what the visitor chooses:

- **Interests:** heritage & history, palaces & museums, markets, coffee & food, family & parks.
- **Time:** 1 hour, 2 hours or half a day.
- **Starting point:** a metro station or car park.
- **Pace:** normal or relaxed.
- **Coffee break:** optional.

The three suggestions are built differently: *closest to your interests*, *a mix of heritage and breaks*, and *short & easy*. Each card shows the distance, duration, stops on a map, which interests it matches, and whether it fits the time chosen. Well-known landmarks such as Masmak are favoured, a tour never starts at a café, the route order is optimised to avoid backtracking, and coffee breaks are added only when they fit the time chosen.

The visitor can:
- **Choose & start** a tour in the stop-by-stop walk (map, narration, sample audio, next-stop distance).
- **Edit** any suggestion: rename it, reorder stops (↑ ↓) or use “Tidy the route” for the shortest walk, remove stops or add new ones, with distance, time and map updating live.
- **Create a new tour** from scratch.

Saved tours appear under **My tours** alongside the ready-made Heritage walk and the Masmak indoor tour. Each tour keeps its own progress.

## Tour inside a real building: Masmak Fortress

The indoor guide and a new nine-stop **Tour inside Masmak Fortress** use a plan of the real fort, simplified from published architectural descriptions (Wikipedia, ArchNet, Saudipedia):

- **Gate:** the palm and tamarisk wood gate in the **west wall** (3.6 m × 2.65 m), with the small *al-Khokha* door in its middle.
- **Front courtyard:** with the **mosque** on the north side (left as you enter): a columned prayer hall with a mihrab and Quran shelves.
- **Majlis (diwaniyah):** straight ahead on the east side, lit by triangular openings and keeping its original plaster.
- **Al-Murabba:** the rectangular central tower joining the mosque and the majlis.
- **Rear colonnaded courtyard:** with the **well** in the north-east corner and the **east stairs**.
- **Upper floor:** the **governor's quarters**, **treasury** and **guest suite**, and the roshan overlooking the courtyard.
- **Corner towers:** four round towers about 18 m high, with walls 1.25 m thick.

The tour follows you across both floors, tells you when to take the east stairs, and checks you in and collects a Masmak stamp at each stop. A seven-stop **step-free version** stays on the ground floor and links to the 3D view of the upper floor. Positions of today's visitor services (help point, shop, restrooms) and the exhibition halls are approximate; the narration is sample text based on these descriptions, to be written and approved by CADC.

## Help

**Help** (menu, or More on the phone) has quick answers, emergency numbers (911, Balady 940) and a form to message CADC. Messages appear on the CADC dashboard under Feedback, where the team replies; the visitor is notified and sees the reply under “My messages”.

## Heritage tours

On **Heritage & culture → Schedule a tour**, visitors pick a trail, day and time slot (live seat availability), tour type (guided SAR 35/person, self-guided audio free, private group SAR 250), guide language, group size and accessibility needs, pay (test gateway) and get a QR tour ticket with meeting point and guide. Tours can be rescheduled or cancelled, appear under My account, and are listed for CADC on the dashboard overview.

## Smart parking

**Smart parking** (in the menu, under More on the phone, or from the parking figure on Home and the map):

- **Find:** pick where you're going and see the four car parks sorted by walking time, with live free spaces, price per hour, EV charging, accessible bays, covered parking and valet, plus a map of the walk from the car park.
- **Book and pay:** choose the day, arrival time (now or later), duration, bay type (standard, EV, accessible, family), your car and valet, then pay with the test gateway. Verified residents get the first hour free, and CADC can switch on evening event pricing.
- **Enter without a ticket:** the pass shows the QR code, plate and assigned bay. “I've arrived” simulates number-plate recognition at the gate and starts the clock.
- **While parked:** the time left shows on the parking page and the Home “Today and tomorrow” card. Extend by an hour, open “Where's my car?” for the bay number and walking route back, then exit to get a VAT receipt saved in parking history.
- **My vehicles and resident permit:** save plates. Verified residents can get a digital resident parking permit.
- **CADC dashboard → Parking:** live occupancy, bookings and revenue; change the hourly price; turn evening event pricing on or off; temporarily close a car park for an event or maintenance, choosing how long (rest of today, until 06:00 tomorrow, or until reopened); it reopens on its own. Closing it moves affected bookings to the alternative car park and notifies their owners.

## Sending activities to app users

CADC dashboard → **Send activities**: create a new event (added to the app calendar), an offer, a service alert, a heritage tour or a community campaign; choose the audience segment (all users, visitors, verified residents, businesses, partners, heritage enthusiasts, people in Central Riyadh now), channels (in-app, push, SMS, email — push/SMS/email simulated), send now or schedule, and preview the phone notification. Users who turned off that notification type are excluded. Recipients see a “Message from CADC” card on Home and an actionable item in the bell that opens the event ready to book; the **Sent activities** table shows reach, open rate and bookings per activity.

## Guided user journeys

Sign in as `nhci.admin` and open **User journeys**. Each journey switches automatically to the right persona account at every step (for example, resident → CADC team → resident) and returns you to your own account at the end:

1. First-time visitor — first-sign-in consent, plan, book and pay, arrive, explore heritage (walk it step by step or book the same route with a guide), rate a finished event from the Home “Today” card, post-visit impact summary
2. Neighbourhood resident — resident offers (codes show expiry and can be marked as used), map feedback, CADC resolves it, resident is notified and rates it, proposals, resource sharing (borrow requests reach the owner, who accepts or declines)
3. Business owner — create an ad or an event promotion (becomes a bookable calendar event once approved), CADC approves (or rejects with a reason so she can edit and resubmit), ad performance, post a job and get notified of applicants
4. CADC team — indicators and a “Needs action” list with counts on each tab, live digital-twin indicators, send an activity, Balady+ content approval, utilities coordination, digital twin
5. Donor or partner — donate with a receipt for each contribution, crowdfund, carbon offset, sponsorship request, CADC follows up, printable impact report
6. Visit inside a building (Masmak Fortress) — check-in straight from the event or tour ticket, floor plan with “you are here” and live crowd levels, step-by-step indoor directions (with a step-free option), audio stories per hall, upper floor and watchtower, 3D walk-through, collecting stamps for the Explorer badge, then CADC's indoor analytics
7. CADC sends an activity — create a new event and audience, preview and send, the visitor receives it and books from the notification, CADC measures opens and bookings, reminds non-openers and duplicates the activity
8. Parking — find a car park near Masmak, book and pay, CADC closes it for an event and the booking moves automatically with a notification, arrive with plate recognition, 15-minute reminder, extend and find the car, exit with a receipt (overstay shown)
9. Design your tour — choose interests and time, compare three suggested tours, edit one or create a new one, then walk it stop by stop

The Masmak plan is simplified from published architectural descriptions of the fort; positions are approximate and it is not the measured architectural drawing.

See **QC.md** for the latest quality-check results.

## Security note

The login is a **demo gate only**. Passwords are stored as SHA-256 hashes in the page, but anyone with the page source can bypass a front-end check. Do not reuse these passwords elsewhere and do not put real or confidential data in this repo.

## Hosting on GitHub Pages

1. Push this folder to the repository's `main` branch.
2. Repository **Settings → Pages → Build and deployment → Source: Deploy from a branch**, branch `main`, folder `/ (root)`.
3. The site is served at `https://<owner>.github.io/<repo>/` within a minute or two.

GitHub Pages on a free account requires a public repository; private-repo Pages needs GitHub Pro, Team or Enterprise. The page carries `noindex, nofollow` so search engines skip it.

To reset demo data: Home → «إعادة ضبط البيانات التجريبية», or clear the site's browser storage.
