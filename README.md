# Inventory Management System

Production-ready MERN Inventory Management System for a small warehouse. The application includes JWT authentication, admin/viewer authorization, product CRUD, atomic stock movement tracking, dashboard metrics, low-stock alerts, CSV export, dark mode, charts, Docker support, CI, seed data, tests, Postman examples, and deployment configuration for Vercel, Render, and MongoDB Atlas.

## Documentation
All related project, product, engineering, QA, security, deployment, and operations documents are available in [docs/INDEX.md](./docs/INDEX.md).

Key documents:
- [Business Requirements Document](./docs/BRD.md)
- [Software Requirements Specification](./docs/SRS.md)
- [Architecture Document](./docs/ARCHITECTURE.md)
- [API Documentation](./docs/API_DOCUMENTATION.md)
- [Database Design](./docs/DATABASE_DESIGN.md)
- [Security Documentation](./docs/SECURITY.md)
- [Testing Strategy](./docs/TESTING_STRATEGY.md)
- [QA Test Cases](./docs/QA_TEST_CASES.md)
- [Deployment Guide](./docs/DEPLOYMENT_GUIDE.md)
- [Deployment Checklist](./docs/DEPLOYMENT_CHECKLIST.md)
- [Operations Runbook](./docs/OPERATIONS_RUNBOOK.md)
- [User Guide](./docs/USER_GUIDE.md)
- [Admin Guide](./docs/ADMIN_GUIDE.md)

## Tech Stack
- Frontend: React, Redux Toolkit, RTK Query, React Router, Tailwind CSS, Recharts.
- Backend: Node.js, Express.js, Mongoose.
- Database: MongoDB / MongoDB Atlas.
- Authentication: JWT and bcrypt.
- Deployment: Vercel frontend, Render backend, MongoDB Atlas database.

## Project Structure
```text
.
|-- backend
|   |-- src
|   |   |-- config
|   |   |-- controllers
|   |   |-- middleware
|   |   |-- models
|   |   |-- routes
|   |   |-- seed
|   |   |-- services
|   |   |-- utils
|   |   `-- validators
|   `-- tests
|-- docs
|-- frontend
|   `-- src
|       |-- app
|       |-- components
|       |-- features
|       |-- pages
|       |-- services
|       `-- test
|-- postman
`-- .github/workflows
```

## Quick Start
Backend:
```bash
cd backend
cp .env.example .env
npm install
npm run seed
npm run dev
```

Frontend:
```bash
cd frontend
cp .env.example .env
npm install
npm run dev
```

Root helper:
```bash
npm install
npm run install:all
npm run dev
```

## Demo Users
- Admin: `admin@example.com` / `Admin123!`
- Viewer: `viewer@example.com` / `Viewer123!`

## Environment Variables
Backend variables are documented in [backend/.env.example](./backend/.env.example) and [docs/ENVIRONMENT_VARIABLES.md](./docs/ENVIRONMENT_VARIABLES.md).

Frontend variables are documented in [frontend/.env.example](./frontend/.env.example) and [docs/ENVIRONMENT_VARIABLES.md](./docs/ENVIRONMENT_VARIABLES.md).

## API Summary
Auth:
- `POST /api/auth/register`
- `POST /api/auth/login`
- `GET /api/auth/me`

Products:
- `GET /api/products`
- `GET /api/products/:id`
- `POST /api/products`
- `PUT /api/products/:id`
- `DELETE /api/products/:id`

Inventory:
- `POST /api/inventory/movement`
- `GET /api/inventory/movements`
- `GET /api/inventory/dashboard`

Full API details are in [docs/API_DOCUMENTATION.md](./docs/API_DOCUMENTATION.md).

## Testing
Backend:
```bash
cd backend
npm test
```

Frontend:
```bash
cd frontend
npm test
npm run build
```

Manual API testing is available through [postman/Inventory-Management-System.postman_collection.json](./postman/Inventory-Management-System.postman_collection.json).

## Deployment
- Backend Render config: [backend/render.yaml](./backend/render.yaml)
- Frontend Vercel config: [frontend/vercel.json](./frontend/vercel.json)
- Docker Compose: [docker-compose.yml](./docker-compose.yml)
- Deployment guide: [docs/DEPLOYMENT_GUIDE.md](./docs/DEPLOYMENT_GUIDE.md)
- Deployment checklist: [docs/DEPLOYMENT_CHECKLIST.md](./docs/DEPLOYMENT_CHECKLIST.md)

## Assumptions And Trade-Offs
- Admin self-registration is enabled for demo and local setup. Production should use invite-only or seed-only admin creation.
- Product quantity cannot be edited directly after creation. All quantity changes must go through stock movements.
- Product deletion currently removes related movement records. Audit-heavy production systems should use soft delete.
- JWT is stored in localStorage for simplicity. HttpOnly cookies can be introduced for stronger browser token protection.

## Future Improvements
- Soft delete products and preserve immutable movement history.
- Invite-only user provisioning and password reset.
- Barcode scanning workflow.
- Purchase order and supplier modules.
- Redis cache for dashboard metrics.
- End-to-end tests with Playwright.
