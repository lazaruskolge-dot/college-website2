# Kestrel College — Website

A static, multi-page college website for **Kestrel College**, styled with a hand-drawn **"campus zine / sketchbook editorial"** aesthetic. The site is intentionally simple, with pure HTML and CSS (no build tools, no dependencies), making it easy to open and host anywhere.

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Tech Stack](#tech-stack)
3. [Project Structure](#project-structure)
4. [Pages](#pages)
5. [Design System](#design-system)
6. [Navigation](#navigation)
7. [How to Run](#how-to-run)
8. [Customization](#customization)
9. [Roadmap / TODO](#roadmap--todo)

---

## Project Overview

The website presents Kestrel College — a fictional institution "Est. 1968" affiliated to a State University. It communicates institutional stats, governance, course offerings, campus life, and contact information through a playful, sketchbook-like visual identity.

Key facts featured across the site:
- **Established:** 1968
- **Departments:** 18
- **Students:** 3,200
- **Faculty–Student Ratio:** 1:14
- **Address:** 12 University Road, Riverside District, 411001
- **Contact:** +91 20 2345 6789 / admissions@kestrelcollege.edu

---

## Tech Stack

| Layer      | Technology          |
|------------|---------------------|
| Markup     | HTML5               |
| Styling    | CSS3 (custom props) |
| Fonts      | Google Fonts (Bricolage Grotesque, Gochi Hand, Caveat) |
| Scripts    | None (static site)  |
| Build      | None (requires no build step) |

---

## Project Structure

```
college-website2/
├── index.html      # Home page (hero, stats, feature cards)
├── about.html      # About page (governance, mission)
├── courses.html    # Courses page (Science, Commerce, Arts programs)
├── gallery.html    # Gallery page (campus life photo tiles)
├── contact.html    # Contact page (info list + form)
├── style.css       # Global stylesheet (design system + all pages)
├── README.md       # This documentation file
└── TODO.md         # Task / progress tracking
```

---

## Pages

### 1. `index.html` — Home
- **Hero** section with the college tagline, CTA buttons (`Explore Courses`, `Plan a Visit`).
- **Stats row** (`Years Running`, `Departments`, `Students`, `Faculty Ratio`).
- **"Why Kestrel"** section with three feature cards (Academics, Faculty, Campus).

### 2. `about.html` — About
- **Hero** describing the college's founding (1968, three departments → eighteen).
- **Governance** section with three cards (Office of the Principal, Departmental Councils, Student Council).
- **Mission** statement.

### 3. `courses.html` — Courses
- **Hero:** "Eighteen departments. Three faculties."
- Program sections grouped by faculty:
  - **Science:** B.Sc. & M.Sc. — Computer Science, Physics, Biotechnology
  - **Commerce:** B.Com & BBA — Accounting & Finance, Business Administration
  - **Arts:** B.A. — English Literature, Economics, Psychology

### 4. `gallery.html` — Gallery
- **Hero:** "Campus Life"
- **Gallery grid** of six photo tiles (Annual Day, Sports Day, Industrial Visit, Cultural Fest, Graduation, Orientation Week).

### 5. `contact.html` — Contact
- **Hero:** "Reach the admissions office."
- **Campus details** list (Address, Phone, Email, Office Hours).
- **Contact form** (Name, Email, Message) — currently non-functional (`onsubmit="return false;"`).

---

## Design System

All design tokens are defined as CSS custom properties in `style.css` under the `:root` block.

### Color Palette

| Variable        | Value      | Usage                          |
|-----------------|------------|--------------------------------|
| `--paper`       | `#FBF6E9`  | Warm pressed-paper background  |
| `--paper-2`     | `#F3EAD3`  | Slightly darker paper pad      |
| `--ink`         | `#20201B`  | Near-black ink (text/borders)  |
| `--ink-soft`    | `#4A483E`  | Muted body text                |
| `--tomato`      | `#E4572E`  | Punchy accent (CTAs, highlights) |
| `--sun`         | `#F2B705`  | Sticky-note yellow             |
| `--kestrel`     | `#5C6E52`  | Kestrel green (tags/labels)    |
| `--sky`         | `#7FB3C9`  | Pen blue                       |

### Typography
- **Headings / Brand / Buttons:** `Bricolage Grotesque` (heavier weights, condense/dark)
- **Body:** `Caveat` (hand-written style)
- **Tags/labels:** `Gochi Hand`

### Signature Components
- **Buttons (`.btn`):** hard-offset `box-shadow`, rotate on hover for a pressed/tactile feel.
- **Cards (`.card`):** skewed alternating rotation, thick ink border, hover lift.
- **Stats (`.stat-row`):** dashed border, large wavy-underlined numbers.
- **Gallery tiles (`.gallery-tile`):** gradient covers, rotated tiles, film-noise texture.
- **Background:** animated grain / paper-noise texture via an inline SVG turbulence filter.
- **Sticky header** with a highlighted `aria-current="page"` active nav item.

### Responsive Breakpoints
- `@media (max-width: 720px)` — stacks the header, converts the contact grid to one column, hides the hero doodle, and collapses the stats row to two columns.

---

## Navigation

The primary navigation is a sticky header present on every page. It links to all five pages:

| Nav Item | Link          | `aria-current="page"` |
|----------|---------------|------------------------|
| Home     | `index.html`  | Yes (on Home)          |
| About    | `about.html`  | Yes (on About)         |
| Gallery  | `gallery.html`| Yes (on Gallery)       |
| Courses  | `courses.html`| Yes (on Courses)       |
| Contact  | `contact.html`| Yes (on Contact)       |

> **Note:** `courses.html` and `contact.html` currently contain some duplicated/incorrect `aria-current="page"` attributes and repeated nav items. See [Roadmap / TODO](#roadmap--todo).

---

## How to Run

Because this is a fully static site, there is **no build step or installation required**.

1. Open any `.html` file directly in a browser:
   - Double-click `index.html`, **or**
   - Run `start index.html` (Windows)

2. Or serve it locally with a lightweight server:
   ```bash
   # Python 3
   python -m http.server

   # or Node (npx)
   npx serve .
   ```
   Then visit `http://localhost:8000`.

---

## Customization

- **Colors / fonts:** adjust the CSS variables in the `:root` block of `style.css`.
- **Content:** edit the text directly within the corresponding HTML files.
- **Contact form:** the form currently has `onsubmit="return false;"` and does not submit. To make it functional, wire it up to a backend endpoint or form service (e.g., Formspree) and update the `action`/`method`, or add form-handling JavaScript.
- **Gallery images:** the gallery tiles currently use CSS gradients rather than real photos. Replace them with actual `<img>` elements or background images as needed.

---

## Roadmap / TODO

See [`TODO.md`](./TODO.md) for the active task list. Remaining known items include:

- Verify/fix duplicate navigation items and `aria-current="page"` attributes in `courses.html` and `contact.html`.
- Add real gallery imagery (currently CSS-gradient placeholders).
- Wire up the contact form to a backend or form service.
- Final responsive polish and cross-browser consistency checks.

---

## License

This is a sample/educational project. No license is specified.
