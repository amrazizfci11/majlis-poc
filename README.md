# Digital Majlis · Central Riyadh — Prototype (POC)

Interactive proof-of-concept of the Central Riyadh **Digital Majlis** app, prepared by **NHC Innovation**.
It is a single static page (`index.html`) with no backend. Everything runs in the browser.

> This is a demo, not an official application. All data is sample data and is saved only in the viewer's browser.

## Demo accounts

| Persona | Username | Password | Opens on |
|---|---|---|---|
| Visitor | `sara` | `Visitor@2026` | Home |
| Verified resident | `abukhalid` | `Resident@2026` | Home |
| Business owner | `munira` | `Business@2026` | Business |
| Partner & donor | `partner` | `Partner@2026` | Donations |
| CADC team | `cadc.ops` | `Cadc@2026` | CADC dashboard |
| NHCI presenter (all access) | `nhci.admin` | `Nhci@2026` | User journeys |

- Visitor, resident, business and partner accounts see the app modules only.
- `cadc.ops` adds the CADC dashboard, roadmap, solutions and guided journeys.
- `nhci.admin` sees everything and is the account to present with.
- Each account keeps its own bookings, points, notifications and plan. Shared items (feedback, ads, Balady+ content, proposals) are common to all accounts **on the same browser**, so cross-persona flows (resident reports → CADC processes → resident is notified) can be demonstrated by logging out and in.

## Languages

The site opens in **English**. Use the **ع / EN** button in the top bar (or on the sign-in page) to switch between English and Arabic; the layout flips between left-to-right and right-to-left, and the choice is remembered in the browser.

## Guided user journeys

Sign in as `nhci.admin` (or `cadc.ops`) and open **User journeys**. Each journey switches automatically to the right persona account at every step (for example, resident → CADC team → resident) and returns you to your own account at the end:

1. First-time visitor — plan, book and pay, arrive, heritage trail, review, post-visit impact summary
2. Neighbourhood resident — resident offers, map feedback, CADC resolves it, resident is notified and rates it, proposals, resource sharing
3. Business owner — create ad, CADC approves, ad performance, jobs
4. CADC team — indicators, Balady+ content approval, utilities coordination, digital twin, solutions
5. Donor or partner — donate, crowdfund, carbon offset, sponsorship, impact summary

## Security note

The login is a **demo gate only**. Passwords are stored as SHA-256 hashes in the page, but anyone with the page source can bypass a front-end check. Do not reuse these passwords elsewhere and do not put real or confidential data in this repo.

## Hosting on GitHub Pages

1. Push this folder to the repository's `main` branch.
2. Repository **Settings → Pages → Build and deployment → Source: Deploy from a branch**, branch `main`, folder `/ (root)`.
3. The site is served at `https://<owner>.github.io/<repo>/` within a minute or two.

GitHub Pages on a free account requires a public repository; private-repo Pages needs GitHub Pro, Team or Enterprise. The page carries `noindex, nofollow` so search engines skip it.

To reset demo data: Home → «إعادة ضبط البيانات التجريبية», or clear the site's browser storage.
