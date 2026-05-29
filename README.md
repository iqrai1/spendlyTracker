# Spendly — Personal Expense Tracker

[![Python](https://img.shields.io/badge/Python-3.11+-3776AB?style=flat&logo=python&logoColor=white)](https://python.org)
[![Flask](https://img.shields.io/badge/Flask-3.1-000000?style=flat&logo=flask&logoColor=white)](https://flask.palletsprojects.com)
[![SQLite](https://img.shields.io/badge/SQLite-3-003B57?style=flat&logo=sqlite&logoColor=white)](https://sqlite.org)
[![Vanilla JS](https://img.shields.io/badge/JavaScript-Vanilla-F7DF1E?style=flat&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=flat)](LICENSE)

A full-stack personal finance web application built with Flask, SQLite, and a hand-crafted design system — no UI frameworks, no JavaScript libraries, no shortcuts.

Spendly lets users log expenses, track budgets, and understand spending patterns across categories and time periods. It was designed as a structured, nine-step learning project to teach full-stack web development from first principles, with particular emphasis on clean architecture, thoughtful UI/UX, and database design.

---

## Overview

```
Landing page  →  Register / Login  →  Dashboard  →  Add / Edit / Delete expenses
                                           ↑
                                   Category & date filters
                                   Monthly budget summary
                                   Spending pattern breakdown
```

The frontend is a cohesive design system built entirely from scratch: custom CSS variables, a two-font typographic scale (DM Serif Display + DM Sans), and component primitives (buttons, forms, cards, modals) that compose consistently across every page.

The backend follows a clean separation of concerns — Flask handles routing and request logic, a dedicated `database/` module owns all SQLite interaction, and Jinja2 templates handle rendering with a shared `base.html` layout.

---

## Tech Stack

| Layer | Technology | Rationale |
|---|---|---|
| Web framework | Flask 3.1 | Lightweight, explicit routing, minimal magic |
| Database | SQLite 3 + `sqlite3` stdlib | Zero-config, portable, sufficient for single-user finance data |
| Templating | Jinja2 (via Flask) | Server-side rendering, clean template inheritance |
| Styling | Vanilla CSS (custom design system) | Full control over every visual decision; no framework overhead |
| Scripting | Vanilla JavaScript | No build step; demonstrates DOM fluency without abstractions |
| Testing | pytest + pytest-flask | Route-level integration tests with a real test client |
| Password hashing | Werkzeug `generate_password_hash` | Industry-standard bcrypt-backed hashing, ships with Flask |

---

## Features

**Implemented**
- Marketing landing page with animated mock-browser dashboard preview
- Video modal (vanilla JS) — opens on demand, stops playback on close, closeable via button, backdrop click, or `Escape`
- User registration and login forms with server-side error handling
- Terms of Service and Privacy Policy pages
- Sticky responsive navbar; collapsing navigation on mobile
- Shared base layout with footer

**In Progress (curriculum steps 3–9)**
- Session-based authentication (login / logout / `@login_required` guard)
- SQLite schema: `users`, `expenses`, `categories` tables with foreign-key constraints
- Full CRUD for expenses — add, edit, delete with ownership checks
- Expense dashboard with category breakdown and monthly totals
- Date-range and category filters
- User profile page

---

## Design System

All visual decisions are encoded as CSS custom properties in `static/css/style.css`, making the system easy to reason about and extend.

**Color palette**

```css
--ink:          #0f0f0f   /* primary text          */
--paper:        #f7f6f3   /* page background        */
--paper-warm:   #f0ede6   /* section backgrounds    */
--accent:       #1a472a   /* forest green, CTAs     */
--accent-light: #e8f0eb   /* tinted green surfaces  */
--accent-2:     #c17f24   /* warm gold, secondary   */
--danger:       #c0392b   /* errors, alerts         */
--border:       #e4e1da   /* taupe borders          */
```

**Typography**

| Role | Font | Usage |
|---|---|---|
| Display | DM Serif Display | `h1`, `h2`, hero titles, section headers |
| Body | DM Sans | All body copy, labels, buttons, forms |

**Spacing scale** — `--radius-sm: 6px` / `--radius-md: 12px` / `--radius-lg: 20px`

**Responsive** — two breakpoints: `900px` (layout reflow) and `600px` (nav collapse, single-column stats).

---

## Project Structure

```
spendlyTracker/
├── app.py                  # Route definitions and Flask app config
├── requirements.txt        # Pinned dependencies
├── database/
│   ├── __init__.py
│   └── db.py               # get_db(), init_db(), seed_db()
├── templates/
│   ├── base.html           # Shared layout (navbar, footer, head)
│   ├── landing.html        # Marketing page with hero + features
│   ├── login.html          # Authentication form
│   ├── register.html       # Registration form
│   ├── terms.html          # Terms of service
│   └── privacy.html        # Privacy policy
└── static/
    ├── css/
    │   └── style.css       # Full design system (~700 lines)
    └── js/
        └── main.js         # Progressive enhancement scripts
```

---

## Getting Started

**Prerequisites:** Python 3.11+

```bash
# Clone the repository
git clone https://github.com/iqrai1/spendlyTracker.git
cd spendlyTracker

# Create and activate a virtual environment
python -m venv venv
venv\Scripts\activate        # Windows
# source venv/bin/activate   # macOS / Linux

# Install dependencies
pip install -r requirements.txt

# Run the development server
python app.py
```

Open `http://localhost:5001` in your browser.

**Run tests**

```bash
pytest
```

---

## Curriculum Structure

Spendly was built as a nine-step incremental project to teach full-stack development from scratch. Each step introduces exactly one new concept:

| Step | Concept | Deliverable |
|---|---|---|
| 1 | Flask routing + Jinja2 | Landing page, base layout |
| 2 | Static files, design system | CSS variables, typography, components |
| 3 | Sessions + Werkzeug | Login, logout, `@login_required` |
| 4 | SQLite schema design | `users` table, `get_db()`, `init_db()` |
| 5 | User registration | Form handling, password hashing, error display |
| 6 | Authentication | Login validation, session management |
| 7 | CRUD — create | Add expense form, INSERT with user FK |
| 8 | CRUD — update | Edit expense, ownership guard |
| 9 | CRUD — delete | Soft delete, dashboard with filters |

This structure reflects a deliberate pedagogical choice: students encounter each concept in isolation, with working code above and below the seam they are implementing.

---

## What This Project Demonstrates

- **Full-stack ownership** — every layer from database schema to CSS animation was written by hand, with no scaffolding tools or UI frameworks
- **Design sensibility** — a consistent visual language built from custom primitives, with deliberate typographic and colour choices
- **Software architecture** — clean separation between routing, data access, and presentation; template inheritance reducing duplication across six pages
- **Pedagogical thinking** — the step-by-step curriculum structure shows the ability to decompose a complex system into teachable, independently verifiable units
- **Attention to detail** — video stops on modal close, forms display inline errors, navigation collapses gracefully on mobile, legal pages are complete and properly dated

---

## License

MIT — see [LICENSE](LICENSE) for details.
