# श्री संत सखाराम महाराज संस्थान, अमळनेर — देणगी व यजमान व्यवस्थापन प्रणाली

Offline-first, single-page web app (plain HTML + CSS + JavaScript). No backend, no database server, no login.
All data is stored in **your own browser** (`localStorage`).

## How to run (simplest)
1. Unzip this folder.
2. Double-click **`index.html`** (opens in Chrome / Edge / Firefox).

Optional local server: `npm start` (needs Node.js) → opens http://localhost:8080

## Internet is needed for (loaded from CDNs)
| Library | Used for |
|---|---|
| Google Fonts – Noto Sans/Serif Devanagari | Marathi fonts |
| Tabler Icons 2.44 | icons (the app falls back to simple glyphs if offline) |
| Chart.js 4.4.4 | dashboard / report charts |
| jsPDF 2.5.1 + html2canvas 1.4.1 | PDF downloads (receipt, report, ledger, स्मरणपत्र) |
| jspdf-autotable 3.8.2 | loaded but no longer used for Marathi PDFs |
| SheetJS xlsx 0.18.5 | Excel export |
| qrcodejs 1.0.0 | receipt QR code |

Without internet the core app (entry, search, edit, cancel, print) still works; charts, PDF/Excel export and QR need those libraries.

## Features
- Yajaman registration with permanent ID (YJ-000001…), gotra, address, 2 mobile numbers, duplicate-mobile detection, संकल्पित रक्कम (pledge) → जमा / बाकी
- Donation entry: समर्थनार्थ, गोत्र, गाव/तालुका/जिल्हा/पिनकोड, मोबाईल १/२, full tithi list (आषाढ शु. नवमी → कार्तिक शु. पौर्णिमा), Cash / UPI / Cheque with reference no.
- Two buttons: **जतन करा** (save) and **अंतिम करा व पावती** (save + final + open receipt)
- Edit, print, PDF, **cancel (with reason) / restore** — donations are never hard-deleted; cancelled ones are excluded from all totals
- Receipt: A4 sheet with the SAME receipt twice (office copy + donor copy, dashed cut line), header "श्री. सद्गुरू सखाराम महाराज विठ्ठल रुख्मणी संस्थान, अमळनेर जि. जळगाव" and "न्यास नोंद क्रमांक : अ /४६५/जळगाव" (editable in Settings), amount in numerals and Marathi words (अक्षरी), QR, "समाधी मंदिर" watermark, CANCELLED stamp. Print uses A4, 1 page.
- Yajaman profile with monthly / yearly / all history filter, A4 ledger
- **स्मरणपत्र** (reminder letter) per yajaman with pledge / paid / due, amount in Marathi words and bank details (Settings → बँक तपशील)
- Reports from 2021: monthly / yearly / all, date-wise and tithi-wise summaries, Excel / PDF
- Accounts: income (donations) vs expenses, balance
- Settings: institution + bank details, JSON backup, delete old records

## Important notes
- **Backup / Restore**: sidebar → बॅकअप. "आता बॅकअप घ्या" downloads one JSON file with ALL data (donations, yajaman, pledges, expenses, settings, counters). Restore validates the file first; "नवीन नोंदी जोडा" (default) merges without duplicating or deleting; "सर्व डेटा बदला" replaces everything (current data is auto-downloaded first). Clearing browser data erases app data, so back up regularly.
- First run contains a few **sample donations / yajaman** (अजय कुलकर्णी, विजय पाटील, सुनिता देशमुख, रमेश जोशी – not real records). Remove them before real use (cancel/delete from the lists, or Settings → delete all donations).
- PDF downloads are generated from the rendered page, so Marathi text is correct (tested in Chromium). They are image-based (text is not selectable). Without internet the app falls back to the browser Print dialog → "Save as PDF".
- Marathi amount-in-words (स्मरणपत्र) should be proofread once before sending to donors.

## Project structure
```
sansthan-app/
├── index.html      the complete application (HTML + CSS + JS)
├── package.json    optional local-server script
├── README.md
└── docs/           reference images supplied for the letter / receipt design
```

## Not built yet
Cash book detail, activity/audit log, thermal-printer receipt size, family/group yajaman, yajaman ID cards.
