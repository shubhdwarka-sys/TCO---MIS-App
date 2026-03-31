# TCO Analytics Platform

Production-ready full-stack analytics platform for Loan 11 Possible Pvt. Ltd. (`TCO - The Car Owner`) that turns operational Excel data into a role-based analytics system.

## Architecture

- `apps/api`: Express + TypeScript + Prisma + PostgreSQL backend
- `apps/web`: React + TypeScript + Vite frontend
- JWT-based role-aware authentication
- Excel/CSV import pipeline with normalization and KPI derivation

## Folder Structure

```text
.
|-- apps
|   |-- api
|   |   |-- prisma
|   |   |   |-- schema.prisma
|   |   |   `-- seed.ts
|   |   |-- src
|   |   |   |-- config
|   |   |   |-- lib
|   |   |   |-- middleware
|   |   |   |-- routes
|   |   |   |-- services
|   |   |   |-- types
|   |   |   `-- utils
|   |   `-- package.json
|   `-- web
|       |-- src
|       |   |-- assets
|       |   |-- components
|       |   |-- data
|       |   |-- hooks
|       |   |-- layouts
|       |   |-- pages
|       |   |-- services
|       |   |-- styles
|       |   `-- types
|       `-- package.json
|-- docker-compose.yml
|-- package.json
`-- README.md
```

## Included Features

- Employee ID + password authentication with role-based access control
- Management, Accounts, RTO, Sales Executive, and Team Leader dashboards
- KPI computation for revenue, total/closed/pending cases, conversion rate, and average processing time
- Upload pipeline for Excel and CSV files with dedupe, normalization, and flexible header mapping
- Export pipeline for Excel reports
- Fintech-style responsive UI with branding, sidebar, header, KPI tiles, charts, and drill-down table

## Setup

1. `npm.cmd install`
2. `Copy-Item .env.example .env`
3. `docker compose up -d`
4. `npm.cmd --workspace apps/api run prisma:generate`
5. `npm.cmd --workspace apps/api run prisma:migrate`
6. `npm.cmd --workspace apps/api run seed`
7. `npm.cmd run dev`

Demo users:

- `MGT001 / Password@123`
- `ACC001 / Password@123`
- `RTO001 / Password@123`
- `SAL001 / Password@123`
- `TL001 / Password@123`

## Notes

- The source workbook path shared in the request was not readable inside the sandbox, so the ingestion layer uses flexible header mapping instead of assuming fixed column names.
- The implementation below is structured for production scaling, with role-based dashboards, import/export endpoints, and normalized data models.
