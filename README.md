# المجلس الرقمي · وسط الرياض — نموذج أولي (POC)

Interactive proof-of-concept of the Central Riyadh **Digital Majlis** app, prepared by **NHC Innovation**.
It is a single static page (`index.html`) with no backend. Everything runs in the browser.

> This is a demo, not an official application. All data is sample data and is saved only in the viewer's browser.

## Demo accounts

| Persona | Username | Password | Lands on |
|---|---|---|---|
| زائرة (Visitor) | `sara` | `Visitor@2026` | الرئيسية |
| ساكن موثّق (Resident) | `abukhalid` | `Resident@2026` | الرئيسية |
| صاحبة نشاط تجاري (Business) | `munira` | `Business@2026` | الأعمال |
| شريك ومتبرع (Partner) | `partner` | `Partner@2026` | التبرعات |
| فريق الشركة (Company ops) | `cadc.ops` | `Cadc@2026` | لوحة الشركة |
| مدير العرض (NHCI presenter, all access) | `nhci.admin` | `Nhci@2026` | رحلات المستخدم |

- Visitor, resident, business and partner accounts see the app modules only.
- `cadc.ops` adds the company dashboard, roadmap, solutions and guided journeys.
- `nhci.admin` sees everything and is the account to present with.
- Each account keeps its own bookings, points, notifications and plan. Shared items (feedback, ads, Balady+ content, proposals) are common to all accounts **on the same browser**, so cross-persona flows (resident reports → company processes → resident is notified) can be demonstrated by logging out and in.

## Security note

The login is a **demo gate only**. Passwords are stored as SHA-256 hashes in the page, but anyone with the page source can bypass a front-end check. Do not reuse these passwords elsewhere and do not put real or confidential data in this repo.

## Hosting on GitHub Pages

1. Push this folder to the repository's `main` branch.
2. Repository **Settings → Pages → Build and deployment → Source: Deploy from a branch**, branch `main`, folder `/ (root)`.
3. The site is served at `https://<owner>.github.io/<repo>/` within a minute or two.

GitHub Pages on a free account requires a public repository; private-repo Pages needs GitHub Pro, Team or Enterprise. The page carries `noindex, nofollow` so search engines skip it.

To reset demo data: Home → «إعادة ضبط البيانات التجريبية», or clear the site's browser storage.
