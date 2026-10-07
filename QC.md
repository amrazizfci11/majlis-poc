# QC report — Digital Majlis POC

Date: 7 October 2026 · Build: single static page (`index.html`, ~380 KB, no backend)

## Scope

Automated checks run in a headless Chromium browser across every page the account can open, in **English and Arabic**, **light and dark** themes, at **desktop (1440 px)**, **phone frame** and **real phone width (390 px)**, with five persona accounts.

| Check | Result |
|---|---|
| Pages × layouts covered | 141 page renders across 8 combinations (24 web views incl. 7 CADC tabs; 13 mobile views per persona) |
| Guided journeys (7, 44 steps) | Every step opens the right page as the right persona, finds its highlighted element, and returns to the presenter account |
| End-to-end flows | Booking + payment + QR ticket; tour scheduling, reschedule, cancel; indoor check-in, directions, stamps, rating; feedback → CADC → resident notified; ad approval; job post → applicant notified; partnership request → CADC contact; **CADC sends activity → user receives → opens → books → CADC sees opens and bookings**; first-sign-in consent; rating a past event from Home; borrow request → owner accepts → requester notified; ad rejected with reason → owner edits and resubmits; remind non-openers and duplicate an activity; Masmak ticket → indoor check-in |
| Untranslated text in English | 0 (1,392 dictionary entries + rule-based patterns) |
| Conflicting translations | 0 (2 found and fixed: “Date/History”, “Completed/Full”) |
| JavaScript errors / console errors | 0 |
| Horizontal scroll or off-screen elements | 0 at every width |
| Buttons and fields without an accessible name | 0 (5 routing drop-downs fixed) |
| Duplicate element IDs | 0 |
| Links to pages that don't exist | 0 |
| Colour contrast (WCAG AA 4.5:1) | All text pairs pass in both themes (success and warning chips raised from 4.26 / 4.03 to 6.0 / 5.9) |
| Page switch speed | All under 800 ms; largest page ≈ 580 DOM nodes |
| 3D views | Rendered and checked with a local copy of the 3D library; first-frame crash fixed |

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
