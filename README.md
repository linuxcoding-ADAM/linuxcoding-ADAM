<a href="https://ademmila.dev">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/linuxcoding-ADAM/linuxcoding-ADAM/main/assets/hero-dark.svg">
    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/linuxcoding-ADAM/linuxcoding-ADAM/main/assets/hero-light.svg">
    <img src="https://raw.githubusercontent.com/linuxcoding-ADAM/linuxcoding-ADAM/main/assets/hero-dark.svg" width="100%" alt="Adam Mila — web platforms, Linux tooling and interactive educational software. L2 Science and Technology, University of Béjaïa, Algeria." />
  </picture>
</a>

<p align="center">
  <a href="https://ademmila.dev"><img src="https://img.shields.io/badge/Portfolio-ademmila.dev-2f81f7?style=flat-square&logo=googlechrome&logoColor=white&labelColor=0D1117" alt="Portfolio: ademmila.dev" /></a>
  <a href="https://ademmila.dev"><img src="https://img.shields.io/badge/1st_Place-Mostaganem%20Hackathon%202026-2f81f7?style=flat-square&logo=awesomelists&logoColor=white&labelColor=0D1117" alt="First place, Mostaganem Hackathon 2026" /></a>
  <img src="https://img.shields.io/badge/Based_in-B%C3%A9ja%C3%AFa%2C%20Algeria-2f81f7?style=flat-square&logo=linux&logoColor=white&labelColor=0D1117" alt="Based in Béjaïa, Algeria" />
</p>

I build **web platforms, Linux tools and interactive educational software**: a Rust terminal app with a sandboxed systemd daemon, a parametric CAD tool that runs in the browser, and multilingual platforms for young Algerians, some of them with public institutions.

I'm an undergraduate in my **second year (L2) of Science & Technology** at the University of Béjaïa, with a Baccalaureate in Technical Mathematics (Electrical Engineering). Linux has been my daily driver for four years.

---

## 🏛️ Institutional Collaborations

<table>
<tr>
<td valign="top" width="50%">

### WLADZ — Wlad Dzayer
**Educational Platform**

An educational and awareness platform designed for Algerian children, combining interactive games covering drug prevention, civics, history, and values.

I presented WLADZ to Algeria's **Minister of Youth**, who expressed interest in adopting the platform. Discussions included potential collaboration with the **Ministry of Youth**, including providing designers, to develop it toward a national-level platform.

**My contribution:** *Salati*, a 3D prayer-training game built with Three.js and GSAP, featuring Learn and Challenge modes, three difficulty levels, and an integrated scoring system.

`Three.js` · `GSAP` · `JavaScript`

<sub>👥 Co-developed by a team · Prototype stage · Source private</sub>

</td>
<td valign="top" width="50%">

### ODEJ Kiosk — Béjaïa
**In collaboration with ODEJ Béjaïa** · [**▶ live site**](https://odej-bejaia.netlify.app)

A touch-screen kiosk presenting Béjaïa province's 67 youth establishments on an interactive 3D map, in Arabic and English, in portrait and landscape. Built for the national youth-establishments fair in Algiers (11 November 2026).

**My contribution:** the establishment data and media pipeline. I structured the data for every establishment with a recorded source for each field, placed GPS pins from ODEJ's coordinate table, and encoded and published media to the CDN. I also built the establishment sheet and contact views.

`React 19` · `TypeScript` · `Vite` · `MapLibre` · `Netlify` · `Cloudflare Pages`

<sub>👥 Co-developed with <b>Slimane Sahnoune</b> · Source private</sub>

</td>
</tr>
</table>

---

## 🧩 Featured Engineering

### 🕌 [Salat](https://github.com/linuxcoding-ADAM/Salat) · prayer times and Adhan for the Linux terminal

A keyboard-first Rust TUI in the spirit of `btop` and `lazygit`, plus a headless `salat daemon` that runs as a sandboxed **systemd** user unit. [Landing page ↗](https://salat-website.vercel.app)

- **Scheduling that doesn't lie:** a dedicated scheduler owns wall-clock instants on a one-second tick, **decoupled from rendering**. A fired-event ledger and a catch-up pass mean no prayer is dropped or announced twice across redraws, restarts or suspend.
- **Deterministic under test:** time is injected behind one `Clock` abstraction, so DST, day rollover and catch-up are testable. Integration tests replay recorded API fixtures, including malformed responses, and make **no network calls**.
- **Offline by design:** city search uses a GeoNames index **compiled into the binary**. Config is human-editable TOML, written atomically, and unknown keys are rejected *with the line number*.
- **Hardened service:** `NoNewPrivileges`, a read-only filesystem outside its own directories, and `MemoryMax=128M`. It honours `NO_COLOR` and uses meaningful exit codes, so `salat status` works in a status bar.

`Rust 2024` · `Ratatui` · `Tokio` · `sqlx` + `SQLite` · `clap` · `reqwest`/`rustls` · `systemd`

<table>
<tr>
<td valign="top" width="50%">

### 🌍 [Forsati](https://github.com/linuxcoding-ADAM/forsati) · فرصتي
[**▶ live demo**](https://forsatii.vercel.app)

One mobile-first hub for the ODEJ youth establishments across Béjaïa, so young people can find their opportunities in one place.

- **Four languages, including Kabyle** (`ar` · `fr` · `en` · `kab`), with proper RTL.
- **A recommender with no model in it:** a pure scoring function over interests and location. It runs in about a millisecond and can't hallucinate.
- **QR ticketing end to end:** registration issues a unique ticket, and an admin scanner confirms attendance on-site.

`Next.js` · `TypeScript` · `Tailwind` · `Firebase Auth` · `Firestore`

<sub>🏆 Built with <b>SUDOTeam</b> (team of 3) at EcoHack Chellata · MIT</sub>

</td>
<td valign="top" width="50%">

### 📐 [LhadjCAD](https://github.com/linuxcoding-ADAM/LhadjCAd) · parametric CAD in the browser
[**▶ live demo**](https://lhadjcad.vercel.app)

Dimensioned, print-ready cabinet fabrication plans, without a desktop CAD suite.

- A **deterministic cabinet model** feeds geometry, layout and dimension solvers that recompute the drawing on every change.
- **Architectural auto-dimensioning** covers overall, internal, door and drawer dimensions.
- An SVG workspace with undo and redo, and one-click **SVG → PDF** export. What you see is exactly what prints.

`Next.js` · `React 19` · `TypeScript` · `Zustand` · `shadcn/ui` · `jsPDF`

</td>
</tr>
</table>

---

## 🚀 More Shipped Work

<table>
<tr>
<td valign="top" width="50%">

**💰 Moula** · [live](https://moulaa.vercel.app) · <sub>source private</sub><br/>
Personal finance in Algerian dinars, built on a **strict integer money model**. The financial core has **204 unit tests**, and the Firestore security rules are tested against the emulator.<br/>
`React 19` · `TypeScript` · `Firebase` · `Vercel Functions`

</td>
<td valign="top" width="50%">

**🎓 [ST Affichage](https://github.com/linuxcoding-ADAM/moodle-notifier)**<br/>
Watches the University of Béjaïa's Moodle announcement boards, detects new notices with **SHA-256 hashing**, sanitizes them, and pushes them to students over Firebase Cloud Messaging.<br/>
`Python` · `Flask` · `BeautifulSoup4` · `FCM`

</td>
</tr>
<tr>
<td valign="top" width="50%">

**📊 [S2 Grade Calc](https://github.com/linuxcoding-ADAM/S2_Grade_Calc)** · [live](https://s2-grade-calc.vercel.app)<br/>
L1 LMD semester grades, computed with each module's official weighting and coefficient. It shows the mention instantly and exports a PDF transcript.<br/>
`React` · `Vite` · `jsPDF` · `Recharts`

</td>
<td valign="top" width="50%">

**🔢 [Base_304](https://github.com/linuxcoding-ADAM/Base_304)** · [live](https://base-304.vercel.app)<br/>
A base converter (binary, octal, decimal, hex, quaternary and UTF-8 text) backed by **`BigInt`**, so large values never lose precision. It has zero dependencies.<br/>
`Vanilla JS` · `HTML` · `CSS`

</td>
</tr>
</table>

### 🐧 Linux & Shell Tooling

| Tool | What it does | Stack |
|:--|:--|:--|
| [**links_scanner**](https://github.com/linuxcoding-ADAM/links_scanner) | URL and domain triage in one command: DNS, SSL, WHOIS and HTTP status, with optional Google Safe Browsing and VirusTotal checks | `Bash` |
| [**Ultimate_System_Cleaner**](https://github.com/linuxcoding-ADAM/Ultimate_System_Cleaner) | Reclaims disk space on Debian-based systems (temp files, caches, orphaned packages, old journals) behind an interactive confirmation | `Bash` |
| [**data_organizer**](https://github.com/linuxcoding-ADAM/data_organizer) | Sorts files into category folders by extension, safely and idempotently, using only the standard library | `Python` |

---

## ⚡ Stack

<sub>Grouped by how well I actually know each one.</sub>

**Proficient**: use regularly, work with independently<br/>
<img src="https://skillicons.dev/icons?i=linux,bash,py,js,ts,react,nextjs,nodejs,tailwind,html,css,git,github,postgres,vite&perline=15&theme=dark" alt="Linux, Bash, Python, JavaScript, TypeScript, React, Next.js, Node.js, Tailwind CSS, HTML, CSS, Git, GitHub, PostgreSQL, Vite" />

**Familiar**: practical experience, used when a project calls for it<br/>
<img src="https://skillicons.dev/icons?i=rust,threejs,firebase,flask,sqlite,prisma,githubactions,vercel&theme=dark" alt="Rust, Three.js, Firebase, Flask, SQLite, Prisma, GitHub Actions, Vercel" />

**Learning**: `Cybersecurity` · `Cloud Infrastructure` · `DevOps` · `AI Engineering`

---

<p align="center">
  <a href="https://ademmila.dev"><img src="https://img.shields.io/badge/Portfolio-2f81f7?style=for-the-badge&logo=googlechrome&logoColor=white" alt="Portfolio" /></a>
  <a href="https://www.linkedin.com/in/adammila"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
  <a href="mailto:adam.mila.dev@gmail.com"><img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /></a>
  <a href="https://instagram.com/adamm.dev"><img src="https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white" alt="Instagram" /></a>
</p>

<p align="center"><sub>Open to collaboration and interesting problems. Reach out anytime.</sub></p>
