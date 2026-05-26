# Nazif Hamza Effendy — Portfolio

Personal portfolio website for **Nazif Hamza Effendy** (alias *Fizan*) — Computer Science student, ex-Software QA, and independent music producer based in Jakarta / South Tangerang, Indonesia.

---

## Overview

A single-page portfolio with horizontal panel navigation, ambient background music, and content dynamically loaded from Firebase Firestore. No build step or bundler required — runs directly in the browser via React + Babel CDN.

---

## Sections

| Panel | Description |
|-------|-------------|
| **Home** | Hero headline, portrait photo, and current status card |
| **About** | Biography, identity info, education history, coursework, personal philosophy, and interests |
| **Experience** | Timeline of professional and creative work history |
| **Skills** | Grouped skill sets across software development, AI/ML, and creative tools |
| **Projects** | Showcase of software and creative projects with descriptions and links |
| **Numbers** | Key stats and metrics |
| **Contact** | Social links and contact channels |

---

## Features

- **Horizontal panel navigation** — smooth slide transitions between sections, keyboard arrow key support, and hash-based URL routing (`#home`, `#about`, etc.)
- **Ambient audio player** — background music with play/pause toggle and volume slider; volume persisted via `localStorage`
- **Welcome overlay** — cinematic entry screen before the main portfolio loads
- **Dynamic content** — all data (projects, skills, experience, contact) loaded from Firebase Firestore via REST API; no page reload needed
- **Image hosting** — project and profile images served via ImgBB API
- **Responsive design** — desktop multi-column grid layout collapses to mobile with hamburger side menu
- **Zero build step** — React 18 + Babel Standalone loaded via CDN; open `index.html` directly in any browser

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| UI Framework | React 18 (UMD via CDN) |
| JSX Transpiler | Babel Standalone 7 (in-browser) |
| Styling | Vanilla CSS with custom properties (no framework) |
| Database | Firebase Firestore (REST API — no SDK) |
| Image Hosting | ImgBB API |
| Fonts | Instrument Serif · Inter · JetBrains Mono (Google Fonts) |
| Hosting | Netlify / GitHub Pages |

---

## Deployment

### Netlify (Recommended)

1. Push this repository to GitHub
2. Go to [netlify.com](https://netlify.com) → **Add new site** → **Import from Git**
3. Select your repository
4. Leave **Build command** empty
5. Set **Publish directory** to `.` (root)
6. Click **Deploy site**

> Alternatively: drag and drop the project folder directly into the Netlify dashboard for a one-click deploy without connecting GitHub.

### GitHub Pages

1. Push to GitHub
2. Go to **Settings → Pages**
3. Set source to `main` branch, root folder `/`
4. Your site will be live at `https://<username>.github.io/<repo-name>`

---

## Firestore Security

The site reads all portfolio content from Firebase Firestore publicly (read-only for visitors). To lock down write access, set the following rules in your **Firebase Console → Firestore → Rules**:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read: if true;
      allow write: if false;
    }
  }
}
```

This ensures anyone can view the portfolio data, but no one can modify it through the public API.

---

## Project Structure

```
/
├── index.html          # Main app (React + all logic inline)
├── portfolio.css       # All styles
├── favicon.ico
├── assets/             # Local images (certificates, project thumbnails, photos)
└── oldver/             # Previous version archive
```

---

## Local Development

No installation needed. Just open `index.html` in a browser:

```bash
# Option A — open directly
start index.html

# Option B — use a local server (avoids audio autoplay restrictions)
npx serve .
# or
python -m http.server 8080
```
