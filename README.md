# React + Django To-Do App — Setup Guide

## Prerequisites
- Python 3.8+
- Node.js 14+ and npm

---

## Step 1 — Set up the Django backend

Open a terminal and run:

```bash
# 1. Navigate to the project folder
cd React-Django-To-Do-App-master

# 2. Create and activate a virtual environment
python -m venv venv

# On Windows:
venv\Scripts\activate
# On Mac/Linux:
source venv/bin/activate

# 3. Install Python dependencies
pip install -r requirements.txt

# 4. Run database migrations
python manage.py migrate

# 5. Start the Django development server
python manage.py runserver
```

Django will be running at: http://localhost:8000

---

## Step 2 — Set up the React frontend

Open a **second terminal** (keep Django running in the first):

```bash
# 1. Navigate to the frontend folder
cd React-Django-To-Do-App-master/frontend

# 2. Install Node dependencies
npm install

# 3. Start the React development server
npm start
```

React will open automatically at: http://localhost:3000

---

## How it works

- The React app runs on port **3000** and talks to Django on port **8000**
- The `proxy` field in `package.json` handles the routing automatically
- Data is stored in a local SQLite database (`db.sqlite3`)

---

## Changes made to fix the original code

| File | Fix |
|------|-----|
| `todo_drf/settings.py` | Renamed `CORS_ORIGIN_WHITELIST` → `CORS_ALLOWED_ORIGINS` (API changed in newer django-cors-headers) |
| `todo_drf/settings.py` | Added `localhost` and `127.0.0.1` to `ALLOWED_HOSTS` (was empty) |
| `frontend/src/App.js` | Replaced deprecated `componentWillMount` → `componentDidMount` |
| `frontend/package.json` | Added `"proxy": "http://localhost:8000"` so API calls work in dev |
| `requirements.txt` | Relaxed pinned versions to work with modern Python environments |
