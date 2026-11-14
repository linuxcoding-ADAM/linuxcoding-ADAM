<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0D1117,50:00D9FF,100:0D1117&height=120&section=header" width="100%" alt="" />

<p align="center">
  <a href="https://github.com/linuxcoding-ADAM">
    <img src="https://capsule-render.vercel.app/api?type=transparent&fontColor=2f81f7&fontSize=54&height=90&width=730&text=Hello!%20I'm%20Adam%20Mila" alt="Hello! I'm Adam Mila" />
  </a>
</p>

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Caveat&weight=600&size=26&pause=1000&color=2f81f7&center=true&vCenter=true&width=625&height=44&lines=Student%20%26%20Developer;Build%20First%20.%20Break%20Things%20.%20Learn%20Fast" alt="Student & Developer — Build first. Break things. Learn fast." />
</p>

<p align="center">
  <a href="https://ademmila.dev"><img src="https://img.shields.io/badge/Portfolio-ademmila.dev-2f81f7?style=flat-square&logo=googlechrome&logoColor=white&labelColor=0D1117" alt="Portfolio: adammila.vercel.app" /></a>
  <img src="https://img.shields.io/badge/Based_in-Akbou,%20B%C3%A9ja%C3%AFa%20%C2%B7%20Algeria-00D9FF?style=flat-square&logo=linux&logoColor=white&labelColor=0D1117" alt="Based in Akbou, Béjaïa, Algeria" />
  <a href="https://adammila.vercel.app"><img src="https://img.shields.io/badge/1st_Place-Mostaganem%20Hackathon%202026-2f81f7?style=flat-square&logo=awesomelists&logoColor=white&labelColor=0D1117" alt="First place, Mostaganem Hackathon 2026" /></a>
</p>

<p align="center">
  <b>I build web platforms, terminal tools, and automation — with a Linux foundation.</b><br/>
  <sub>19, first-year Science &amp; Technology student at the University of Béjaïa · four years on Linux as a daily driver<br/>
  I care about software that solves a problem someone actually has, and about getting the details right.</sub>
</p>

---

## 💻 `$ whoami`

```console
adam@bejaia:~$ whoami

  Adam Mila — developer & engineering student
  ───────────────────────────────────────────────────────────
  location    Akbou, Béjaïa · Algeria
  studying    Science & Technology, 1st year · Univ. Béjaïa
  background  Bac in Technical Mathematics (Electrical Eng.)
  daily       Fedora Linux · zsh · VS Code
  building    Rust TUIs · Next.js platforms · Bash automation
  focus       full-stack web · Linux & systems · scripting
  motto       build first, break things, learn fast

adam@bejaia:~$ ls ~/dev          # ordered by engineering depth, not by date

  salat/  forsati/  lhadjcad/  st-affichage/  moula/  base_304/
```

---

## 🧩 Featured Engineering

> The three projects I'd want to be judged on. Ordered by engineering depth, not by date.

### 🕌 [Salat](https://github.com/linuxcoding-ADAM/Salat) · prayer times and Adhan for the Linux terminal

**The problem.** Knowing when the next prayer is shouldn't require a browser tab, a phone, or trusting a background app you can't inspect.

**What it is.** A keyboard-first Rust TUI in the spirit of `btop` and `lazygit`. Bare `salat` prints a live view *inside* your shell without clearing scrollback; `salat --full` opens the complete interface — dashboard, per-prayer config, notifications, location, and system status.

<table>
<tr><td valign="top" width="50%">

**Scheduling that doesn't lie**

- A dedicated scheduler owns absolute wall-clock instants on a one-second tick, **decoupled from rendering** — redraws, resizes, suspend/resume and config saves can't drop or duplicate an event.
- Every fired event is written to a ledger, so a restart never re-fires it.
- A catch-up pass replays events missed while the machine was off, if they're still inside their grace window.
- Single-owner locking: the TUI and the daemon can't both fire. The loser exits with `E903`, naming the process that holds the schedule.

</td><td valign="top" width="50%">

**Built to be tested and trusted**

- Time is injected behind one `Clock` abstraction, so day rollover, DST and catch-up are **deterministic** under test.
- Integration tests run against recorded AlAdhan fixtures — including malformed and truncated responses — and make **no real network calls**.
- A ten-component health model reports `degraded` / `down` rather than a false `OK`.
- Offline city search from a GeoNames index **compiled into the binary** (cities ≥ 15k population).
- Config is human-editable TOML, written atomically; unknown keys are rejected *with the line number*.

</td></tr>
</table>

Runs headless as `salat daemon` under a sandboxed **systemd** user unit — `NoNewPrivileges`, read-only filesystem outside its own three directories, `PrivateTmp`, `MemoryMax=128M` — and deliberately does not restart after a config error, because retrying can't fix one. Honours `NO_COLOR`, degrades to plain text when piped, and exits `0`/`1` so `salat status` works in a status bar. XDG-compliant paths, `0600` files. Dual-licensed MIT OR Apache-2.0.

`Rust 2024` · `Ratatui` · `Tokio` · `sqlx` + bundled `SQLite` · `clap` · `reqwest`/`rustls` · `chrono-tz` · `systemd`

<sub>📐 Design is documented in `docs/ARCHITECTURE.md`, which the implementation follows phase by phase. Pre-release — build from source.</sub>

<br/>

<table>
<tr><td valign="top" width="50%">

### 🌍 [Forsati](https://github.com/linuxcoding-ADAM/forsati) · فرصتي

[**▶ live demo**](https://forsatii.vercel.app)

Young Algerians don't lack opportunities — they lack one place to find them. Forsati puts 68 real ODEJ youth establishments across Béjaïa into a single mobile-first hub.

- **Four languages, including Kabyle** (`ar` · `fr` · `en` · `kab`) with proper RTL.
- **A recommender with no model in it** — `lib/recommend.ts` is a pure scoring function over interests × wilaya. It runs locally in about a millisecond and cannot hallucinate.
- The assistant answers natural phrasing (*"sport in Akbou"*) by searching the **bundled dataset**, so every answer traces to real ODEJ data.
- **QR ticketing end to end**: dynamic registration forms issue a unique ticket, and an admin scanner confirms attendance on-site.
- Firestore rules are the security boundary; every read is filtered server-side with `where()` rather than fetching collections.

`Next.js 14` · `TypeScript` · `React 18` · `Tailwind` · `Firebase Auth` · `Firestore`

<sub>🏆 Built with <b>SUDOTeam</b> at EcoHack Chellata · MIT</sub>

</td><td valign="top" width="50%">

### 📐 [LhadjCAD](https://github.com/linuxcoding-ADAM/LhadjCAd) · parametric CAD in the browser

[**▶ live demo**](https://lhadjcad.vercel.app)

Joiners and fit-out shops need dimensioned, print-ready fabrication plans — without a desktop CAD suite.

- A **flat, deterministic cabinet model** feeding geometry, layout and dimension solvers that recompute the whole drawing on every parameter change.
- **Architectural auto-dimensioning**: overall, internal, door and drawer dimensions, with configurable arrow styles, offsets and extension lines.
- Live pan/zoom **SVG workspace**, undo/redo and keyboard shortcuts.
- Libraries for handles, materials and legs — per-component colour and finish.
- One-click **SVG → PDF** A4 fabrication plan, auto-scaled and centred.

`Next.js 16` · `React 19` · `TypeScript` · `Zustand` · `Radix` / `shadcn` · `dnd-kit` · `jsPDF` + `svg2pdf.js`

<sub>⚙️ What you see in the workspace is exactly what the PDF exports.</sub>

</td></tr>
</table>

---

## 🚀 Web Applications & Platforms

<table>
<tr><td valign="top" width="50%">

**🎓 [ST Affichage](https://github.com/linuxcoding-ADAM/moodle-notifier)** · `moodle-notifier`

University announcements, without the logins. A daemon thread polls the Univ Béjaïa ST faculty Moodle board; BeautifulSoup extracts the `li.activity` nodes, each announcement is **SHA-256 hashed for change detection**, sanitized with `bleach`, then broadcast to every student over Firebase Cloud Messaging. Hardened with `Flask-Limiter` IP rate limiting and security headers, and shipped with an Android APK whose share sheet falls back to `tg://` / `whatsapp://` deep links inside the WebView.

`Python` · `Flask` · `BeautifulSoup4` · `bleach` · `Firebase Admin` · `Gunicorn`

<sub>📦 Public source of the original service. A private Next.js rewrite (<i>StAffichage V2</i>) succeeded it; its hosted deployment is currently offline.</sub>

</td><td valign="top" width="50%">

**💰 Moula** · [live](https://moulaa.vercel.app) · *source private*

Personal finance built around the dinar. A **strict integer money model** — no floats anywhere near the ledger — with search and filtering, live analytics, JSON/CSV import with duplicate detection, and monthly reports delivered by email. The browser talks straight to Firestore, with security enforced by **tested rules** instead of a CRUD API.

The financial core is covered by **204 unit tests**, and the Firestore rules are tested against the emulator.

`React 19` · `TypeScript (strict)` · `Tailwind v4` · `Recharts` · `Firebase` · `Vercel Functions`

</td></tr>
<tr><td valign="top" width="50%">

**📊 [S2 Grade Calculator](https://github.com/linuxcoding-ADAM/S2_Grade_Calc)** · [live](https://s2-grade-calc.vercel.app)

Semester-2 grades for L1 LMD students, done properly: each module's note follows its **official weighting** (60% exam / 40% CA, TP modules 100% CA) and coefficient, and the overall average is the coefficient-weighted mean. Instant colour-coded *mention*, multi-template **PDF transcripts** via jsPDF + AutoTable, and a protected admin dashboard with Recharts statistics and per-student detail.

`React 18` · `Vite` · `jsPDF` · `Recharts`

</td><td valign="top" width="50%">

**🔢 [Base_304](https://github.com/linuxcoding-ADAM/Base_304)** · [live](https://base-304.vercel.app)

A base converter that doesn't quietly lose your number. Binary, octal, decimal, hexadecimal, quaternary and UTF-8 text, all backed by **`BigInt`** so arbitrarily large values convert without precision loss. **Zero dependencies** — no framework, no build step, just HTML, CSS and ES6+.

`Vanilla JS` · `BigInt` · `HTML5` · `CSS3`

</td></tr>
</table>

---

## 🐧 Linux, Shell & Developer Tooling

<table>
<tr>
<th align="left">Tool</th><th align="left">What it does</th><th align="left">Stack</th>
</tr>
<tr>
<td valign="top"><b><a href="https://github.com/linuxcoding-ADAM/links_scanner">links_scanner</a></b></td>
<td valign="top">URL and domain triage from one command: resolves DNS, inspects the SSL certificate, runs WHOIS for registrar / country / creation and expiry dates, and checks HTTP status — then optionally cross-references <b>Google Safe Browsing v4</b> and <b>VirusTotal v3</b> for phishing and multi-engine malware verdicts. API keys stay placeholders in the repo.</td>
<td valign="top"><code>Bash</code><br/><code>dig</code> · <code>openssl</code><br/><code>whois</code> · <code>curl</code></td>
</tr>
<tr>
<td valign="top"><b><a href="https://github.com/linuxcoding-ADAM/Ultimate_System_Cleaner">Ultimate_System_Cleaner</a></b></td>
<td valign="top">Reclaims disk on Debian-based systems without touching anything that matters: <code>/tmp</code> and <code>/var/tmp</code>, user cache, the APT cache, orphaned packages, journal entries older than three days, and the trash — behind an interactive confirmation, with colour-coded output and a filesystem sync. Entirely local; no network.</td>
<td valign="top"><code>Bash</code><br/><code>apt</code> · <code>journalctl</code></td>
</tr>
<tr>
<td valign="top"><b><a href="https://github.com/linuxcoding-ADAM/data_organizer">data_organizer</a></b></td>
<td valign="top">Points at one or many messy directories and sorts every file into a category folder by extension, creating folders as needed and handling name collisions safely so it's idempotent across runs. <b>Standard library only</b> — no third-party packages — and it runs the same on Linux, macOS and Windows.</td>
<td valign="top"><code>Python 3</code><br/>stdlib only</td>
</tr>
</table>

---

## ⚡ Tech Stack

<div align="center">

<sub>Grouped by how well I actually know each one — no progress bars, no inflated percentages.</sub>

<br/><br/>

**Proficient** — use regularly, work with independently

<img src="https://skillicons.dev/icons?i=linux,bash,python,js,ts,react,nextjs,nodejs&theme=dark" alt="Linux, Bash, Python, JavaScript, TypeScript, React, Next.js, Node.js" />
<br/>
<img src="https://skillicons.dev/icons?i=tailwind,html,css,git,github,postgres,vite&theme=dark" alt="Tailwind CSS, HTML5, CSS3, Git, GitHub, PostgreSQL, Vite" />

<br/><br/>

**Familiar** — practical experience, reached for when a project calls for it

<img src="https://skillicons.dev/icons?i=rust,firebase,flask,sqlite,prisma,githubactions,vercel&theme=dark" alt="Rust, Firebase, Flask, SQLite, Prisma, GitHub Actions, Vercel" />

<br/><br/>

**Learning** — actively improving

<sub>`Cybersecurity` · `Cloud Infrastructure` · `DevOps` · `AI Engineering`</sub>

</div>

---

## 🏙️ My GitHub City

<div align="center">

*Every contribution builds something. Each tower is a day; the taller it is, the more that day shipped.*

<a href="https://gitcity.natrajx.in/linuxcoding-ADAM/isometric">
  <img src="https://gitcity.natrajx.in/api/svg?u=linuxcoding-ADAM&theme=noir" width="460" alt="An isometric city generated from Adam Mila's GitHub contribution history" />
</a>

<br/>

<a href="https://gitcity.natrajx.in/linuxcoding-ADAM/isometric"><b>↗ Explore it in interactive 3D</b></a>

</div>

---

## 📊 GitHub Statistics

<div align="center">

<img src="https://github-readme-stats-five-sigma-99.vercel.app/api?username=linuxcoding-ADAM&show_icons=true&theme=tokyonight&title_color=2f81f7&icon_color=00D9FF&text_color=c9d1d9&hide_border=true&bg_color=0D1117&count_private=true&include_all_commits=true" height="170" alt="Adam Mila's GitHub statistics" />
<img src="https://github-readme-stats-five-sigma-99.vercel.app/api/top-langs/?username=linuxcoding-ADAM&layout=compact&theme=tokyonight&title_color=2f81f7&text_color=c9d1d9&hide_border=true&bg_color=0D1117&langs_count=8" height="170" alt="Most-used languages across Adam Mila's repositories" />

</div>

---

## 📬 Connect

<div align="center">

<a href="https://ademmila.dev"><img src="https://img.shields.io/badge/Portfolio-2f81f7?style=for-the-badge&logo=googlechrome&logoColor=white" alt="Portfolio" /></a>
<a href="https://www.linkedin.com/in/adammila"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
<a href="mailto:adam.mila.dev@gmail.com"><img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /></a>
<a href="https://instagram.com/_adam_mila_"><img src="https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white" alt="Instagram" /></a>

<br/><br/>

<i>Open to collaboration and to interesting problems — just reach out.</i>

</div>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0D1117,50:00D9FF,100:0D1117&height=80&section=footer" width="100%" alt="" />
