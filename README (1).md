<div align="center">

# Kare Scan Center — Clinic Website

### A responsive clinic website with online appointment requests and a secure staff dashboard.

[![Live Demo](https://img.shields.io/badge/Live%20Demo-Add%20URL-0F9D9A?style=for-the-badge&logo=googlechrome&logoColor=white)](#-live-demo)
[![API](https://img.shields.io/badge/API-FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![Python](https://img.shields.io/badge/Python-3.12%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Database](https://img.shields.io/badge/Database-SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)](https://www.sqlite.org/)

**[Explore the repository](https://github.com/hadiinamdar/Clinic-Website-Updated) · [Report a bug](https://github.com/hadiinamdar/Clinic-Website-Updated/issues) · [Request a feature](https://github.com/hadiinamdar/Clinic-Website-Updated/issues)**

</div>

---

## ✨ Overview

Kare Scan Center is a clinic website project built to provide visitors with clear information about the centre, its services and timings, and a convenient way to request an appointment. It includes a separate staff dashboard for managing appointment requests and newsletter subscribers.

The project combines a browser-based frontend with a Python **FastAPI** backend and an **SQLite** database.

> **Project note:** Appointment requests are requests, not confirmed bookings. The clinic team must confirm them through the staff dashboard.

## 📌 Table of contents

- [Features](#-features)
- [Technology stack](#-technology-stack)
- [Project structure](#-project-structure)
- [Getting started](#-getting-started)
- [Run the application](#-run-the-application)
- [API documentation](#-api-documentation)
- [Admin dashboard](#-admin-dashboard)
- [Configuration](#-configuration)
- [Security notes](#-security-notes)
- [Troubleshooting](#-troubleshooting)
- [Roadmap](#-roadmap)
- [Contributing](#-contributing)
- [Author](#-author)

## 🚀 Features

### 🌐 Public website

- Responsive clinic website with sections for the clinic, doctor, services and contact information.
- Appointment request form with service, date and time selection.
- Displays available appointment slots returned by the backend.
- Supports light and dark appearance.
- Mobile-friendly navigation and quick contact actions.
- WhatsApp hand-off for sharing appointment request details.
- Built-in FAQ-style assistant for common questions about services, timings, address and booking. It does **not** provide medical advice.
- English and Marathi assistant responses.

### 🧑‍💼 Staff dashboard

- Password-based staff sign-in.
- Appointment overview with summary statistics.
- Search appointments by patient name, phone number or email.
- Filter by appointment status and date range.
- Quick filters for today, upcoming appointments and pending requests.
- Update appointment status: pending, confirmed, completed or cancelled.
- Delete an appointment when necessary.
- View newsletter subscribers.
- Export appointment and subscriber records as CSV.
- Dashboard refreshes its data periodically while open.

### ⚙️ Backend

- FastAPI application with interactive API documentation.
- SQLite-backed data storage.
- Appointment creation, listing, status updates and deletion.
- Appointment availability and scheduling logic.
- Admin authentication and protected dashboard endpoints.
- Health-check endpoints.
- Optional email notification configuration.

## 🧰 Technology stack

| Layer | Technology |
|---|---|
| Frontend | HTML, CSS, JavaScript |
| Backend | Python, FastAPI |
| Database | SQLite |
| API server | Uvicorn |
| Data access | SQLAlchemy |
| API documentation | OpenAPI / Swagger UI |
| Version control | Git and GitHub |

## 📁 Project structure

```text
Clinic-Website-Updated/
│
├── assets/
│   ├── favicon and application icons
│   └── clinic logo assets
│
├── clinic-website-backend/
│   ├── tests/
│   │   └── test_api.py
│   ├── .env.example
│   ├── .gitignore
│   ├── clinic_config.json
│   ├── config.py
│   ├── database.py
│   ├── main.py
│   ├── models.py
│   ├── notifications.py
│   ├── requirements.txt
│   ├── requirements-dev.txt
│   ├── run_server.bat
│   ├── run_server.sh
│   ├── scheduling.py
│   ├── security.py
│   ├── services.py
│   ├── siteconfig.py
│   └── validation.py
│
├── admin.html
├── clinic-website-pro.html
├── .gitignore
└── README.md
```

## 🛠️ Getting started

Follow these steps to run the project locally.

### 1. Prerequisites

Install:

- [Python](https://www.python.org/downloads/) (use a version supported by the packages in `requirements.txt`).
- [Git](https://git-scm.com/downloads/).
- A modern browser such as Chrome, Edge or Firefox.

Check your installations:

```bash
python --version
git --version
```

### 2. Clone the repository

```bash
git clone https://github.com/hadiinamdar/Clinic-Website-Updated.git
cd Clinic-Website-Updated
```

### 3. Open the backend folder

```bash
cd clinic-website-backend
```

### 4. Create and activate a virtual environment

**Windows — Git Bash:**

```bash
python -m venv .venv
source .venv/Scripts/activate
```

**Windows — PowerShell:**

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

**macOS / Linux:**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 5. Install dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 6. Configure environment variables

Create your local `.env` file from the example:

**Windows — Git Bash:**

```bash
cp .env.example .env
```

**Windows — PowerShell:**

```powershell
Copy-Item .env.example .env
```

Open `.env` and fill in the values required by the application. Configure the admin password/secret and email settings before using those features.

Also review `clinic_config.json` and replace any remaining sample or placeholder clinic information with approved details.

> Never commit your real `.env` file, credentials, API keys, database files or virtual environment.

## ▶️ Run the application

### 1. Start the backend

From inside `clinic-website-backend/`, run:

```bash
python -m uvicorn main:app --reload --host 127.0.0.1 --port 8000
```

The API should be available at:

| Resource | Local URL |
|---|---|
| API base | `http://127.0.0.1:8000` |
| Swagger documentation | `http://127.0.0.1:8000/docs` |
| ReDoc | `http://127.0.0.1:8000/redoc` |
| Health check | `http://127.0.0.1:8000/health` |

Keep this terminal running while testing the website.

### 2. Open the public website

In a second terminal, return to the repository root:

```bash
cd ..
```

You can open `clinic-website-pro.html` in your browser for local preview. When the page is opened directly as a local file, its frontend code is configured to call the API at `http://127.0.0.1:8000`.

For a deployment, serve the frontend and API using a correctly configured web server/reverse proxy or configure the frontend API base URL for your deployment. Do not assume that a local `127.0.0.1` address will work for public visitors.

### 3. Open the staff dashboard

Open `admin.html` in your browser. Ensure the backend is running and use the admin password configured for your local environment.

## 📚 API documentation

FastAPI generates interactive API documentation automatically.

- Swagger UI: `http://127.0.0.1:8000/docs`
- ReDoc: `http://127.0.0.1:8000/redoc`

### Main API operations

| Method | Endpoint | Purpose |
|---|---|---|
| `GET` | `/` | API root, if configured |
| `GET` | `/health` | Application health check |
| `GET` | `/db-health` | Database health check |
| `POST` | `/appointments` | Submit an appointment request |
| `GET` | `/appointments` | List and filter appointments |
| `PATCH` | `/appointments/{id}/status` | Change appointment status |
| `DELETE` | `/appointments/{id}` | Delete an appointment |
| `POST` | `/admin/login` | Staff dashboard login |
| `GET` | `/admin/stats` | Dashboard summary statistics |
| `GET` | `/admin/subscribers` | List newsletter subscribers |
| `GET` | `/admin/appointments.csv` | Export appointment records |
| `GET` | `/admin/subscribers.csv` | Export subscriber records |

The exact request fields, query parameters and response schemas are documented in Swagger UI for the running backend.

## 🔐 Admin dashboard

The dashboard is intended for authorised clinic staff. It provides appointment and subscriber management.

Appointment statuses used by the dashboard:

| Status | Meaning |
|---|---|
| `pending` | Request received; awaiting clinic confirmation |
| `confirmed` | Appointment confirmed by staff |
| `completed` | Appointment marked as completed |
| `cancelled` | Appointment cancelled |

The dashboard uses a bearer token after login for protected API requests. Configure a strong admin credential and keep it private.

## ⚙️ Configuration

| File | Purpose |
|---|---|
| `.env` | Local secrets and environment-specific settings; do not commit |
| `.env.example` | Template showing the environment variables expected by the application |
| `clinic_config.json` | Clinic/site configuration and content settings |
| `requirements.txt` | Backend runtime dependencies |
| `requirements-dev.txt` | Development and testing dependencies |
| `.gitignore` | Excludes local environments, secrets, caches and database files |

Check the example configuration and application settings before deploying. Do not publish real patient information or production database contents in this repository.

## 🛡️ Security and privacy notes

- Keep `.env` out of version control.
- Use a strong, unique admin password and protect any signing or secret keys.
- Use HTTPS in production.
- Restrict the staff dashboard and admin API to authorised users.
- Do not use real patient information in screenshots, sample data or public issue reports.
- Configure database backups and access controls for any real deployment.
- Review email provider credentials and delivery settings before enabling notifications.
- This repository is a software project, not a certified medical device or a substitute for clinical judgement.

## 🧪 Testing

The backend includes a `tests/` directory. Install development dependencies if required:

```bash
pip install -r requirements-dev.txt
```

Run the test suite from `clinic-website-backend/`:

```bash
python -m pytest
```

If `pytest` is not installed in the environment:

```bash
python -m pip install pytest
```

## 🧩 Troubleshooting

<details>
<summary><strong>Backend does not start</strong></summary>

- Confirm that your terminal is inside `clinic-website-backend/`.
- Activate the virtual environment.
- Install dependencies with `pip install -r requirements.txt`.
- Check the full error message in the terminal.
- Confirm that port `8000` is not already in use.

</details>

<details>
<summary><strong>The website cannot connect to the API</strong></summary>

- Start the backend first.
- Visit `http://127.0.0.1:8000/health`.
- Check the browser console for network or CORS errors.
- If deployed, make sure the frontend API base URL points to the deployed backend and the server is configured to allow the frontend origin.

</details>

<details>
<summary><strong>Email notifications are not working</strong></summary>

- Check the email/SMTP settings in your local `.env`.
- Verify the provider credentials and sender configuration.
- Check the backend terminal logs.
- The admin dashboard may indicate when email notifications are disabled.

</details>

<details>
<summary><strong>Appointment slots or records are not appearing</strong></summary>

- Confirm that the backend is running.
- Check the API response in Swagger UI.
- Review `clinic_config.json` and the scheduling configuration.
- Check the database health endpoint and backend logs.

</details>

## 🗺️ Roadmap

The following are possible future improvements, not claims that they are already implemented:

- [ ] Add automated end-to-end tests for the complete booking journey.
- [ ] Add deployment instructions and a verified live demo.
- [ ] Add a documented production database and backup strategy.
- [ ] Add role-based staff access if multiple staff roles are required.
- [ ] Add monitoring and structured application logging.
- [ ] Add a documented email delivery test procedure.

## 🤝 Contributing

Contributions, suggestions and bug reports are welcome.

1. Fork the repository.
2. Create a feature branch: `git checkout -b feature/your-feature`.
3. Commit your changes: `git commit -m "Add: your feature"`.
4. Push the branch: `git push origin feature/your-feature`.
5. Open a Pull Request describing your changes.

For bugs or feature ideas, use [GitHub Issues](https://github.com/hadiinamdar/Clinic-Website-Updated/issues).

## 👨‍💻 Author

**Hadi Inamdar**

- GitHub: [@hadiinamdar](https://github.com/hadiinamdar)
- Project: [Clinic-Website-Updated](https://github.com/hadiinamdar/Clinic-Website-Updated)

---

<div align="center">

**Built with care to make clinic information and appointment requests easier to access.**

If you find this project useful, consider giving the repository a ⭐.

</div>
