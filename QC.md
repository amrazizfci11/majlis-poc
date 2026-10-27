# QC report — Digital Majlis POC

Date: 25 October 2026 · Build: single static page (`index.html`, ~430 KB, no backend)

## Scope

Automated checks run in a headless Chromium browser across every page the account can open, in **English and Arabic**, **light and dark** themes, at **desktop (1440 px)**, **phone frame** and **real phone width (390 px)**, with five persona accounts.

| Check | Result |
|---|---|
| Pages × layouts covered | 174 page renders across 8 combinations (31 web views incl. 11 CADC tabs; 17 mobile views per persona) |
| Guided journeys (9, 61 steps) | Every step opens the right page as the right persona, finds its highlighted element, and returns to the presenter account |
| End-to-end flows | Booking + payment + QR ticket; tour scheduling, reschedule, cancel; indoor check-in, directions, stamps, rating; feedback → CADC → resident notified; ad approval; job post → applicant notified; partnership request → CADC contact; **CADC sends activity → user receives → opens → books → CADC sees opens and bookings**; first-sign-in consent; rating a past event from Home; borrow request → owner accepts → requester notified; ad rejected with reason → owner edits and resubmits; remind non-openers and duplicate an activity; Masmak ticket → indoor check-in; **parking: find → book and pay → plate entry → extend → find my car → exit with VAT receipt; CADC price change, event pricing, closure → bookings moved and owners notified; resident permit and first-hour discount** |
| Untranslated text in English | 0 (2,366 dictionary entries + rule-based patterns) |
| Conflicting translations | 0 (2 found and fixed: “Date/History”, “Completed/Full”) |
| JavaScript errors / console errors | 0 |
| Horizontal scroll or off-screen elements | 0 at every width |
| Buttons and fields without an accessible name | 0 (5 routing drop-downs fixed) |
| Duplicate element IDs | 0 |
| Links to pages that don't exist | 0 |
| Colour contrast (WCAG AA 4.5:1) | All text pairs pass in both themes (success and warning chips raised from 4.26 / 4.03 to 6.0 / 5.9) |
| Page switch speed | All under 800 ms; largest page ≈ 580 DOM nodes |
| 3D views | Rendered and checked with a local copy of the 3D library; first-frame crash fixed |

## Upload to Balady, thirteenth pass (25 October 2026)

New CADC tab **Upload to Balady**, tested end to end in Arabic and English (28 checks pass):
- **File checks:**
  - Photos: a valid sample image; a low-resolution photo warned; an unsupported file and an oversized file rejected.
  - GeoJSON: valid; outside Riyadh rejected; partly outside warned; broken JSON rejected; empty file rejected.
  - Others: KML valid; complete Shapefile ZIP accepted; incomplete ZIP rejected; PDF plan accepted.
- **Sending:** blocked until a valid file, a title and rights confirmation are given; only valid files are sent; a reference number is issued.
- **Status:** sent → review → published.
  - Low-resolution photos are returned for changes with a reason, and the tab shows a badge.
  - Edit and resend works; unpublishing removes the item from the app.
- **In the app:**
  - Published photos appear on the Masmak map card (opening full size) and in the 3D tour card.
  - Published layers are drawn on the map and can be switched on or off.
  - Uploads persist after a reload.
- **Journey 4:** gains an "Uploads photos and maps to Balady" step, bringing the total to 61.

Regression: all 61 journey steps; 299 action checks in Arabic and English; 82 add/update checks; 0 untranslated strings; 0 JavaScript errors; every account's pages open.

## Review, twelfth pass (25 October 2026)

- **3D performance:** the scenery is now merged by material. Draw calls per frame dropped from 952 to 46 outside and from 276 to 15 inside Masmak, so the tour runs smoothly on mid-range phones. The look is unchanged.
- **Dark theme:** the 3D tour uses warm evening lighting under the night sky instead of midday light.
- **Tickets:** tickets for past events can no longer be edited.
- **Reload:** edits survive a page reload (renamed new car park, edited CADC event, no duplicate events).
- **Navigation:** the 3D animation stops when you leave the tour, including when moving to the digital twin.
- **Regression:** all 60 journey steps; 295 action checks in Arabic and English; 82 add/update checks; 0 untranslated strings; 0 JavaScript errors.

## Add/update everywhere and 3D tour, eleventh pass (24 October 2026)

**Add and update.** Each account added and then edited its items, and every other place that shows them was checked, including other accounts' screens: 82 checks pass in Arabic. The English run fails only checks that look for Arabic text on translated screens.
- **CADC car park:** add, edit, edit a built-in one. Checked in: parking list, map, booking price, active booking, Home spaces, CADC booking count.
- **CADC event:** add, book, edit, cancel. Checked in: calendar, ticket, account, notifications, booking removal.
- **Facility event:** edit while pending, approve, book, change after approval, approve the change, then reject a second change. Checked in: calendar time, ticket holder notified, no duplicate.
- **Ad:** edit when live, then re-approve. The visitor sees the new text.
- **Job:** edit, then close. Checked for: resident view and applicant notifications.
- **Resource:** add, edit, remove. Checked for: CADC view and removal.
- **Resident:** feedback and proposal.
- **Visitor:** booking size (seats left everywhere), tour reschedule (CADC list), car added (parking booking), review.
- **3D description:** write, edit, reset.
- **Partner:** request, then CADC contact.

Fixed:
- Calendar entries didn't refresh when an event changed after publishing; re-approved ad promotions created duplicate events.
- Edits to newly added car parks didn't reach the parking list, map or bookings.
- Missing edit actions were added: CADC edit/cancel event, owner edit of pending/approved events and live ads, job edit/close, resource edit/remove, ticket size change.

**3D tour.** Rendered with WebGL on desktop and phone, in Arabic and English, and reviewed frame by frame.
- **Outside, rebuilt:** sky, textured streets and buildings with windows, landmarks modelled individually, names on the model that you can tap (overlapping names hide), smooth camera flight, zoom buttons and pinch. The canvas is taller on phones.
- **Inside Masmak, improved:** mud-plaster textures, wooden gate with the khokha, Najdi triangular vents, crenellated rooms and towers, hall names hidden by walls, “You are here” caption. The camera looks ahead along the route and stands on top of the watchtower.
- The animation stops when you leave the page.

Regression: all 60 journey steps; 295 action checks in Arabic and English; 0 untranslated strings; 0 JavaScript errors; every account's pages open.

## Full journey review, tenth pass (23 October 2026)

Every step of all 9 journeys (60 steps) was performed, not just opened: each action was carried out as the step's persona, and its effect was checked on the other accounts. In total 295 checks ran, in both Arabic and English, and **all pass** with no JavaScript errors. They cover:
- **Visitor:** plan saved; event booked and paid with a QR ticket; route; heritage walk; 3D tour into Masmak; rating from Today; impact summary.
- **Resident:** Nafath; 3D tour; offer code used; map report auto-classified, then closed by CADC with a notification at each stage, then rated; vote and proposal; borrow accepted and requested.
- **Facility owner:** adds an event, CADC approves it into the calendar with its price, the owner is notified and opens it; ad approved; job posted, and the owner is notified when a resident applies.
- **CADC administrator:** car park added and edited; daily occupancy; CADC event; approve and reject with a reason; 3D description visible to visitors.
- **Partner:** donation receipt; crowdfunding; carbon offset with payment; partnership request reaches CADC, which contacts the partner.
- **CADC activity:** sent; the visitor gets it on Home and in the bell, books from it, and CADC sees opens and bookings, with remind and duplicate options.
- **Indoor visit:** check-in, crowds, directions, audio, upper floor, 6 stamps for the badge, end and rate; CADC analytics.
- **Parking:** book, CADC closure moves the booking with a notification, plate arrival, extend, find car, exit with a VAT receipt.
- **Tour generator:** three tours, edit and save, walk.

The 60 steps were also reviewed as screenshots, each account's pages were opened (none broken, no visible links to pages it can't use), and a phone-width check (390 px) was run.

Fixed in this pass:
- The indoor journey opened on the 3D tab if the visitor had entered Masmak 3D from the virtual tour, so the floor-plan steps were missing. Guide steps now open the floor plan.
- “Books straight from the notification” closed the event opened from the notification; the step now reopens the new event ready to book.
- Resident account now states “Verified via Nafath”, matching the journey text.
- Jobs posted by the facility owner now show her facility (Al Sadu Store) instead of a different shop name.

## Facility owners' events, ninth pass (23 October 2026)

Events now come from facility owners. The facility owner adds an event for her facility; it is saved as *Awaiting CADC approval* and CADC is notified. CADC approves it (added to the calendar, owner notified) or rejects it with a reason (owner notified). The owner sees the status of each event, opens approved ones in the calendar, and edits and resubmits rejected ones (CADC notified again). Residents no longer submit events. Journey 3 now starts with this flow (7 steps; 60 in total).

Results: add, approve (ticket price carried to the calendar), reject with reason and note, owner notifications, status list, open in calendar, edit and resubmit all pass; all 60 journey steps pass; 0 untranslated strings in English; 0 JavaScript errors.

## CADC as portal administrator, eighth pass (23 October 2026)

CADC's journey now shows the team as the administrator of the portal rather than a reviewer. New and tested end to end in English and Arabic:
- **Car parks:** add a car park and edit an existing one (shown for booking at once); daily occupied / vacant chart by hour with peak hour, per car park or all, with earlier days.
- **Events:** CADC adds events to the calendar; facility owners add events; CADC approves (added to the calendar, owner notified) or rejects with a reason (owner notified); pending suggestions counted in “Needs action”.
- **3D view content:** CADC writes building descriptions in Arabic and English, publishes or resets them.
- **3D virtual tour** for visitors, residents and CADC: pick a building, the camera flies to it with a pin and its description; step inside Masmak in 3D.
- Journeys: j4 rewritten (8 steps); j1 (visitor) and j2 (resident) each gain a 3D-tour step — 57 steps in total.

Results: all 57 journey steps open the right page as the right persona and find their highlighted element; 0 untranslated strings in English; 0 JavaScript errors.

## Independent review, seventh pass (8 October 2026)

A separate reviewer with no knowledge of the build signed in as every persona, performed all nine journeys and explored each menu. All 20 findings were verified and fixed: per-persona account pages; Masmak Explorer badge actually awarded; “not satisfied” reopens a report and alerts CADC; carbon offset with payment and receipt; partnership request form with contact details, no duplicates, status updates; car park closures move only overlapping bookings; ticket → parking keeps the event date; seats, bookings and satisfaction consistent across screens; employer sees job applicants; business tools first for business owners; prototype modules and data reset hidden from app users; resident “Waiting for you” on Home; problem-report rating removed and English reports classified; remaining untranslated text; business ads show real event dates and venues; NHCI pitch/demo pages hidden from CADC; ticket check-in only on the visit day; map/plan label overlaps, twin chart and star wrapping fixed; borrow pickup scheduling; tomorrow's parking in the Today card; names unified. Full regression and QC passed in English and Arabic.

## Role-fit review, sixth pass (8 October 2026)

Each account now sees only what its persona needs. Visitor: donations & partnerships, future expansion and digital twin removed (including their Home cards), visit summary without donation figures, community limited to feedback and polls, no job openings or business promotion. Resident, business, partner and CADC each have their own menu, tab bar, Home cards and account summary. Links to pages an account can't open are hidden. Journeys trimmed to their personas' needs: j1 merges the guided-tour and heritage-walk steps, j4 drops the NHCI solutions step, j6 drops the on-site 3D step, j9 drops the two steps that repeated j6 (52 steps in total). Verified per account: menus, tab bars, Home cards, shared-page sections, no visible links to inaccessible pages; full regression and QC passed.

## Journey review, fifth pass (8 October 2026)

All 9 journeys (57 steps) walked again, including the new “Design your tour” journey and the indoor journey on Masmak's real layout; all steps smooth, no dead ends. Fixed in this pass: suggested tours show whether they fit the chosen time and stay within it (at least two stops); “Tidy the route” for hand-edited tours; distance from the starting point to the first stop; the indoor tour checks in and collects stamps; step-free version of the indoor tour.

Still open: step-free and shaded outdoor routing; real push/SMS delivery; real narration and audio (content from CADC); verify the Masmak plan against measured drawings.

## Tour generator and real-building indoor tour (8 October 2026)

New: three automatically suggested tours (with edit and create), My tours with per-tour progress, and the Masmak indoor guide rebuilt on the fort's real layout (from published descriptions) with a nine-stop, two-floor indoor tour. Tested: suggestions for several interest/time/start combinations, editing (reorder, remove, add, rename), creating, starting and finishing tours, indoor tour across floors with badge, indoor directions to every room, 3D view of the new layout, English and Arabic, phone and web, light and dark. Fixed during testing: route colours missing outside the walk screen, overview maps cropping routes, upper-floor rooms hard to see, a walk-screen click handler running while signed out.

## Journey review, fourth pass (8 October 2026)

All 8 journeys (51 steps) walked again after the Heritage walk and back navigation were added; all steps smooth, no dead ends. Fixed in this pass: guided-tour ticket for the walk route opens the Heritage walk; next-stop distance and time on each stop; walk card on Home and in the Today card; walk completion marks the route completed; car park closures have an end time and reopen automatically; new Help page with messages to CADC and replies; hints inside text boxes are now translated in English mode (they stayed in Arabic before).

Still open: step-free and shaded outdoor routing; real push/SMS delivery; real narration and audio for the Heritage walk (content from CADC).

## Heritage walk (7 October 2026)

New stop-by-stop Heritage walk (overview, six stop screens with narration and sample audio player, completion with badge and rating). Tested in English and Arabic, phone and web, light and dark. Also fixed: when all of today's tour slots have passed, tour booking now opens on the next day with free slots instead of a disabled button.

## Back navigation (7 October 2026)

Back button on every screen (web: above the title; phone: top bar), restoring the previous screen and CADC tab; back arrow on payment steps (events, tours, parking). Tested in English and Arabic (arrow mirrors in right-to-left), web and phone.

## Journey review, third pass (7 October 2026)

All 8 journeys (51 steps) were walked again, including the new parking journey. All 51 steps are now smooth (89% in the second pass, 70% in the first), with no dead ends. Fixed in this pass:

- Resident codes show their expiry and can be marked as used.
- Event-promotion ads carry a date, time and place and become bookable calendar events when CADC approves them.
- Digital-twin indicators are live (event bookings, satisfaction from ratings, parking occupancy, open feedback).
- Donations and crowdfunding contributions produce receipts with reference numbers; partners get a printable impact report.
- Parking booked from an event ticket targets that event; a reminder arrives 15 minutes before parking time ends; overstay is shown on the exit receipt.

Still open: step-free outdoor routing, in-app help for visitors, scheduled reopening of closed car parks, and real push/SMS delivery (the prototype alerts in-app only).

## Parking service (7 October 2026)

New Smart parking module, CADC Parking tab and journey 8, all tested end to end in English and Arabic. Also fixed during this pass: two-column pages (Events, Destination, Proposals, Sharing, Parking) did not stack on the phone; they now collapse to one column.

## Journey review, second pass (7 October 2026)

All 7 journeys were walked again after the fixes. 39 of 44 steps are now smooth (was 31), 5 have minor friction (was 11) and there are no dead ends (was 2).

- Home: “Today and tomorrow” card with tickets, tours, plan and one-tap rating of a finished event.
- First sign-in for app personas: welcome with language, notification types and consent; settings also in My account.
- Tour tickets start the trail; Masmak event and tour tickets check the visitor in to the indoor guide.
- Resource sharing: requests reach the owner (Incoming requests) with accept or decline, and the requester is notified.
- Ads: CADC rejects with a reason and note; the owner sees it, edits and resubmits.
- CADC dashboard: pending counts on tabs and a “Needs action” list on the overview.
- Sent activities: “Remind non-openers” and “Duplicate”.

Still open: resident codes have no used/expiry state, event-promotion ads don't create calendar events, twin indicators are static, no donation receipt or shareable partner report.

## Fixed during QC

- Feedback routing drop-downs had no label for screen readers.
- Success and warning chips were below AA contrast in light mode.
- Two Arabic phrases mapped to different English meanings (date vs history; completed vs full).
- Side-panel text ended with a double full stop.
- Dropdown values were saved in English when the UI was in English (fixed earlier; re-verified).

## Pass 14: date, temperature, sharing, resident services

- Date, time and Central Riyadh temperature bar added on web and phone, in Arabic and English.
- Share sheet with 8 social networks; consent chip removed from Notifications & privacy.
- Resident access now matches the visitor (16 sections each); city of residence selectable; permit limited to Central Riyadh addresses.
- Regression: journeys 299/299 (AR and EN), 61 guided steps, add/update 82/82, Balady upload 28/28, role access clean, 0 untranslated strings.

## Pass 15: business focus, donations, CADC supervision, Balady reviews

- Business home rebuilt around the owner's events and ratings; event browsing, booking and tours removed; image, voice and video uploads; maximum attendees.
- Donations from every visitor, resident and business account.
- CADC supervision landing with live camera; booking removed from every CADC screen; parking tiles per car park by day; Balady ratings forwarded to owners.
- Regression: journeys 300/300 (AR and EN), 61 guided steps, add/update 82/82, Balady upload 28/28, new checks 30/30, 0 untranslated strings.

## Pass 16: journey review, CADC main tab, presenter removed, cross-account testing

- Presenter account removed; guided journeys start from the sign-in screen and return to it.
- Journeys reviewed: business-owner journey rewritten (dashboard, max attendees, attachments, visitor booking, Balady reviews and improvement plan); CADC journey starts with supervision and camera; parking and visitor steps updated (65 steps).
- CADC main tab: no duplicate figures; supervision board, needs action, this week's indicators, event occupancy (bookings / max), feedback by category, tours, partnerships, proposals; closed venues listed in one line.
- Cross-account test (add/update in one account, checked in the others): car park add/edit/close, business event create/approve/book/edit max, ad with video, donations from three accounts, Balady reviews and improvement plan, resident city, feedback lifecycle, CADC read-only — 49/49 in Arabic and English.
- Regression: journeys 326/326 (AR and EN), 65 guided steps, add/update 82/82, Balady upload 28/28, new-feature checks 30/30, role access clean, 0 untranslated strings.

## Pass 17: CADC as content manager for heritage and inside buildings

- Heritage for CADC: landmarks, trails and timeline content (photos, maps, bilingual information); tours, walks, booking and quiz removed for CADC.
- Inside the building for CADC: building selector, plan and component table, edit halls, add/delete components, upload a building plan; visitor guide, stamps and analytics removed for CADC.
- 3D tour: "How to use the tour" hidden for CADC.
- Visitors see the published content (heritage page, map card, hall cards, extra components, newly opened buildings); Arabic input fields are excluded from automatic translation.
- Fixed: the audio-story timer could run after sign-out and raise an error.
- Content test 29/29 (AR and EN); regression suites all pass.

## Known limits (by design for a POC)

- Login is a front-end demo gate; passwords are visible to anyone reading the code.
- Data lives in each browser's local storage; cross-persona flows work on the same browser only.
- Map and Masmak floor plan are illustrative; figures, names and reach estimates are sample data.
- Push, SMS and email channels are simulated; in-app notifications are delivered to demo accounts.
- Camera feeds are simulated; in operation they link to the venues' cameras.
- The 3D library loads from cdnjs; if it is blocked, the page shows a notice instead of the model.
