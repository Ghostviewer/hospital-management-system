# Hospital Information Management System

A desktop Hospital Information Management System built with Python, PyQt6, and SQLite. It provides role-aware dashboards for patient records, outpatient visits, pharmacy, reporting, and billing.

## Run

The project includes a configured virtual environment. From the project directory:

```bash
source pyqt_env/bin/activate
python main.py
```

On first launch, the application creates `data/hospital.db`, applies safe schema migrations, and adds demo accounts.

## Demo accounts

| Role | Username | Password |
| --- | --- | --- |
| Administrator | `admin` | `admin123` |
| Doctor | `doctor1` | `doctor123` |
| Nurse | `nurse1` | `nurse123` |
| Receptionist | `reception1` | `reception123` |

Change or remove these accounts before using the application with real patient data.

## Current features

- Secure bcrypt-based login and role-specific navigation
- Dashboard summary cards, a monthly-visit chart, and patient search
- Patient registration with validation and generated patient IDs
- Patient record editing and safe archiving that preserves clinical history
- EMR and patient management data views
- Appointment scheduling with date, time, department, clinician, and booking status
- Appointment availability protection against clinician double-booking, plus dashboard reminders for today and tomorrow
- OPD visit entry with clinician, status, diagnosis, symptoms, and fee
- Pharmacy prescription entry, optionally linked to a patient visit
- Procedure entry with cost and clinician details for reports
- Billing totals for collected, pending, and total visit fees
- SQLite storage by default with automatic schema upgrades and starter data
- Inventory register with low-stock flags and audit events
- CSV export and consistent SQLite backup helpers in `database.maintenance`
- Patient-document storage helpers and document metadata records
- User creation/password-change service methods with login/logout audit events

## Demo data

New demo databases are populated with five patients, five OPD visits, four prescriptions, and three procedures. These records give the OPD, Pharmacy, Reports, Billing, and dashboard chart useful content immediately. Each record type is seeded only when its table is empty.

## Operational tools

The `database.maintenance` module provides `create_backup`, `export_csv`, and
`store_patient_document` for scheduled backups, spreadsheet reporting, and
managed attachment storage. Configure database environment variables from
`database/connection.py` before deploying the application outside a demo setup.
