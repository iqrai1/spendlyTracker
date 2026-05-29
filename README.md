# Spendly — Expense Tracker

A personal finance web app I'm building to learn Flask and full-stack web development. This project is a work in progress — the frontend is largely done; the backend (database, authentication, CRUD) is not yet implemented.

## What's built so far

- Landing page with hero section, features section, and a call-to-action
- Video modal on the landing page (vanilla JS, no libraries)
- Register and login pages (HTML/CSS only — no backend logic yet)
- Terms of Service and Privacy Policy pages
- A consistent CSS design system across all pages

## What's not built yet

- Database (SQLite schema, connection, queries)
- User authentication (register, login, sessions)
- Expense CRUD (add, edit, delete)
- Dashboard and spending reports

## Tech stack

- Python / Flask
- SQLite (planned)
- Jinja2 templates
- Vanilla CSS and JavaScript

## Running locally

```bash
git clone https://github.com/iqrai1/spendlyTracker.git
cd spendlyTracker

python -m venv venv
venv\Scripts\activate

pip install -r requirements.txt
python app.py
```

Open `http://localhost:5001`.
