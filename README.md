# Nazif Hamza Effendy — Personal Portfolio

> *By day, he isolates software irregularities and analyzes NLP architectures. By night, he automates tempo transitions and curates sound textures in FL Studio. This portfolio is the digital coordinate where those two realities collide.*

A single-page interactive portfolio built for a Computer Science student, independent music producer, and ex-fintech QA engineer based in Jakarta / Tangerang Selatan. Set against a deep dark ambient canvas with glowing sepia and moss accents, it documents a multi-disciplinary journey across code, sound, and leadership — not as a static credential list, but as an active medium of expression.

---

## Sections

| # | Panel | Contents |
|---|---|---|
| 01 | **Home** | Hero card, 3D cursor-tracking photo tile, status card |
| 02 | **About** | Executive summary, education, identity details, coursework, philosophy |
| 03 | **Experience** | 5 experience cards — KMM HR leadership, Fizan music production, Bank Mega QA, Ramayana internship, Dels Cookies |
| 04 | **Skills** | 10 skill groups — AI/ML, NLP, Fuzzy Logic, Web Dev, Music Production, QA, Cybersecurity, Networking, Database, DSS |
| 05 | **Projects** | 10 project cards — research, web apps, music releases |
| 06 | **Numbers** | Live stat cards — GPA, years producing, competition wins, tracks, events |
| 07 | **Contact** | Social links, location, quick inquiry form, availability status |

---

## Features

- **Horizontal panel navigation** — keyboard (arrow keys, Home/End), click, or hash-based routing (`#experience`, `#skills`, etc.)
- **Interactive dot grid** — physics-based canvas, dots repel from cursor with spring dynamics
- **3D photo tile** — real-time cursor tracking tilt + radial spotlight effect
- **Ambient audio** — original score *Fizan — home (mastered 2)* with toggle control
- **Welcome overlay** — cinematic entrance gate before the main experience loads
- **Live admin panel** — `Ctrl + Shift + A` → password-protected; edit, add, delete, and drag-reorder all content sections in real time
- **Firebase Firestore sync** — all admin edits persist to cloud and broadcast live to every open browser tab (no page reload required)
- **Glassmorphism cards** — backdrop blur, radial gradient fills, sepia/moss glow variants

---

## Tech Stack

| Layer | Technology |
|---|---|
| UI Framework | React 18 (UMD CDN, no build step) |
| JSX Transform | Babel Standalone 7.29 |
| Database | Firebase Firestore (compat SDK v10) |
| Auth | Firebase Authentication (Email/Password) |
| Styling | CSS3 — custom properties, Grid, Flexbox, `clamp()` |
| Canvas | HTML5 Canvas API (dot grid physics) |
| Fonts | Instrument Serif · Inter · JetBrains Mono |
| Hosting | Netlify (static) |

No build process. No bundler. One HTML file.

---

## File Structure

```
pemweb/
├── index.html                        # Entire app — React + Babel inline
├── portfolio.css                     # All styles, grid layouts, animations
├── favicon.ico
├── assets/
│   ├── portrait-garden.jpg
│   └── portrait-jacket.jpg
└── Fizan - home (mastered 2).mp3    # Background score
```

---

## Admin Panel

The built-in admin system allows live content editing without touching code.

**Access:** `Ctrl + Shift + A` → enter password

**Capabilities per section:**

| Tab | Operations |
|---|---|
| Projects | Add · Edit · Delete · Drag-reorder |
| Skills | Add group · Add skills · Delete · Drag-reorder |
| Experience | Add · Edit (role, org, bullets, discography, special box) · Delete · Drag-reorder |
| About | Edit executive summary paragraphs · Edit/add/remove identity rows · Drag-reorder rows |
| Contact | Add · Edit social links · Delete · Drag-reorder |

All edits sync to **Firebase Firestore** in real time. Changes appear instantly across all browser tabs and all devices — no refresh needed.

**First-time setup:** After connecting Firebase, open the admin panel and click **⬆ Seed DB** to push all default data to Firestore.

---

## Firebase Setup

1. Create a project at [console.firebase.google.com](https://console.firebase.google.com)
2. Enable **Firestore Database** (production mode)
3. Enable **Authentication → Email/Password** → add user `admin@portfolio.local` / `skilliz09`
4. Set Firestore Security Rules:
   ```
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /portfolio/{document=**} {
         allow read: if true;
         allow write: if request.auth != null
                      && request.auth.token.email == "admin@portfolio.local";
       }
     }
   }
   ```
5. Paste your `firebaseConfig` into `index.html` lines 16–23

---

## Navigation

| Input | Action |
|---|---|
| `→` / `PageDown` | Next panel |
| `←` / `PageUp` | Previous panel |
| `Home` | First panel |
| `End` | Last panel |
| Click nav dots | Jump to panel |
| URL hash | Direct link — e.g. `/#experience` |
| `Ctrl+Shift+A` | Open admin panel |

---

## Local Development

No install required. Open `index.html` directly in a browser, or serve with any static server:

```bash
npx serve .
# or
python -m http.server 8000
```

---

*Built by Nazif Hamza Effendy · 2026 · Jakarta*
