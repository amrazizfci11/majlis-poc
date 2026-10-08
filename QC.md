# QC report — Digital Majlis POC

Date: 7 October 2026 · Build: single static page (`index.html`, ~430 KB, no backend)

## Scope

Automated checks run in a headless Chromium browser across every page the account can open, in **English and Arabic**, **light and dark** themes, at **desktop (1440 px)**, **phone frame** and **real phone width (390 px)**, with five persona accounts.

| Check | Result |
|---|---|
| Pages × layouts covered | 174 page renders across 8 combinations (29 web views incl. 8 CADC tabs; 17 mobile views per persona) |
| Guided journeys (9, 52 steps) | Every step opens the right page as the right persona, finds its highlighted element, and returns to the presenter account |
| End-to-end flows | Booking + payment + QR ticket; tour scheduling, reschedule, cancel; indoor check-in, directions, stamps, rating; feedback → CADC → resident notified; ad approval; job post → applicant notified; partnership request → CADC contact; **CADC sends activity → user receives → opens → books → CADC sees opens and bookings**; first-sign-in consent; rating a past event from Home; borrow request → owner accepts → requester notified; ad rejected with reason → owner edits and resubmits; remind non-openers and duplicate an activity; Masmak ticket → indoor check-in; **parking: find → book and pay → plate entry → extend → find my car → exit with VAT receipt; CADC price change, event pricing, closure → bookings moved and owners notified; resident permit and first-hour discount** |
| Untranslated text in English | 0 (2,001 dictionary entries + rule-based patterns) |
| Conflicting translations | 0 (2 found and fixed: “Date/History”, “Completed/Full”) |
| JavaScript errors / console errors | 0 |
| Horizontal scroll or off-screen elements | 0 at every width |
| Buttons and fields without an accessible name | 0 (5 routing drop-downs fixed) |
| Duplicate element IDs | 0 |
| Links to pages that don't exist | 0 |
| Colour contrast (WCAG AA 4.5:1) | All text pairs pass in both themes (success and warning chips raised from 4.26 / 4.03 to 6.0 / 5.9) |
| Page switch speed | All under 800 ms; largest page ≈ 580 DOM nodes |
| 3D views | Rendered and checked with a local copy of the 3D library; first-frame crash fixed |

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

## Known limits (by design for a POC)

- Login is a front-end demo gate; passwords are visible to anyone reading the code.
- Data lives in each browser's local storage; cross-persona flows work on the same browser only.
- Map and Masmak floor plan are illustrative; figures, names and reach estimates are sample data.
- Push, SMS and email channels are simulated; in-app notifications are delivered to demo accounts.
- The 3D library loads from cdnjs; if it is blocked, the page shows a notice instead of the model.
