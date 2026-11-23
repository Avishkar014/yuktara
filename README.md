# Enterprise Internal Talent Marketplace Platform
---
---
---
---
---
---
---
---
---
---
## 📜 License

This project is proprietary and confidential. All rights reserved.

For internal use only. Distribution without authorization is prohibited.

---
## 📞 Contact & Support

- **Product Owner:** [Name]
- **Technical Lead:** [Name]
- **Documentation Lead:** [Name]
- **Issue Tracker:** [GitHub Projects Link]
- **Slack Channel:** #talent-marketplace-dev
```
## 🔐 Security Guidelines

### Never Commit
- `.env` files containing secrets
- Database passwords
- JWT secrets
- API keys

### Environment Variable Best Practices
- Use `.env.example` to document required variables
- Never expose real secrets in version control
- Use secret management in production (AWS Secrets Manager, HashiCorp Vault)
- Rotate secrets regularly (90-day cycle recommended)

### Authentication Security
- JWT access tokens: 15-minute expiration
- JWT refresh tokens: 7-day expiration
- Passwords: bcrypt with minimum 12 salt rounds
- Session timeout: 30 minutes of inactivity
- MFA recommended for privileged roles

### Input Validation
- All API endpoints validate request bodies using class-validator
- Whitelist allowed fields for updates
- Sanitize all user-generated content
- Rate limiting: 100 requests per 15 minutes per IP
- CORS: Configured for allowed origins only
## 🛠️ Available Scripts

### Root Package.json Scripts
```json
{
  "test": "run-npm test:*",
  "test:unit": "jest",
  "test:integration": "jest --config integration.jest.config.js",
  "test:e2e": "cypress run",
  "test:coverage": "jest --coverage",
  "lint": "eslint . --ext .ts,.tsx,.js,.jsx",
  "lint:fix": "eslint . --fix --ext .ts,.tsx,.js,.jsx",
  "build": "run-s build:*",
  "build:frontend": "vite build",
  "build:backend": "nest build",
  "dev": "run-p dev:*",
  "dev:frontend": "vite",
  "dev:backend": "nest start --watch",
  "setup": "pnpm install && pnpm prisma:generate",
  "migrate": "prisma migrate deploy",
  "studio": "prisma studio",
  "docker:up": "docker-compose up -d",
  "docker:down": "docker-compose down",
  "docker:rebuild": "docker-compose up -d --build",
  "prepare": "husky install"
}
```
## 📁 Repository Structure

```
talent-marketplace/
├── .github/          # GitHub Actions workflows
│   └── workflows/    # Lint, test, build pipelines
│
├── infra/            # Infrastructure configuration
│   └── docker/       # Docker files and compose
│
├── backend/          # NestJS application
│   ├── src/          # Source code
│   ├── test/         # Test files
│   ├── config/       # Configuration
│   └── prisma/       # Database schema
│
├── frontend/         # React application
│   ├── src/          # Source code
│   ├── public/       # Static assets
│   ├── tests/        # Test files
│   └── vite.config.ts
│
├── design-system.md  # Design system specification
├── ARCHITECTURE.md   # Architecture documentation
├── STEP1_BRD_ANALYSIS.md  # BRD analysis document
├── .gitignore        # Git ignore rules
├── .env.example      # Environment variables template
├── README.md         # This file
├── package.json      # Root package scripts
└── tsconfig.json     # TypeScript config
```
## 🐳 Docker Development

### Prerequisites
- Docker Desktop
- Docker Compose v2+

### Setup
```bash
# Clone the repository
git clone <repository-url>
cd talent-marketplace

# Start all services
docker-compose up -d

# Wait for services to be ready
# - PostgreSQL on port 5432
# - Redis on port 6379
# - Backend API on port 4000
# - Frontend on port 3000

# View logs
docker-compose logs -f

# Stop all services
docker-compose down
```

### Service Ports
- **Frontend:** 3000 (React Vite dev server)
- **Backend API:** 4000 (NestJS)
- **PostgreSQL:** 5432
- **Redis:** 6379
- **PgAdmin:** 8080 (database management)

### Environment Configuration
```bash
# Copy environment templates
cp .env.example .env

# Update values for your environment
# - Database credentials
# - JWT secrets
# - Redis configuration
# - OAuth credentials
```
## 🧪 Testing Strategy

### Test Coverage Goals
- **Unit Tests:** >80% coverage for all modules
- **Integration Tests:** All API endpoints
- **E2E Tests:** Critical user workflows

### Test Suites
- `npm run test:unit` - Unit tests (Jest)
- `npm run test:integration` - Integration tests
- `npm run test:e2e` - End-to-end tests (Cypress)
- `npm run test:coverage` - Coverage report

### Test Scenarios Covered
- Positive scenarios (happy paths)
- Negative scenarios (error handling)
- Boundary conditions
- Empty/undefined/null inputs
- Duplicate record prevention
- Unauthorized access attempts
- Concurrent allocation conflicts
- Skill proficiency validation
## 📦 API Documentation

### Base URLs
- **Development:** `http://localhost:4000/api`
- **Production:** `https://api.talent-marketplace.com/v1`

### Key Endpoints

#### Authentication
- `POST /auth/login` - User login
- `POST /auth/register` - User registration
- `POST /auth/refresh-token` - Refresh JWT
- `POST /auth/logout` - User logout
- `GET /auth/me` - Get current user profile

#### Users
- `GET /users` - List all users (admin)
- `GET /users/:id` - Get user by ID
- `PATCH /users/:id` - Update user profile

#### Skills
- `GET /skills` - List all skills
- `POST /skills` - Create new skill (admin)
- `GET /skills/:id` - Get skill by ID

#### Projects
- `GET /projects` - List all projects
- `POST /projects` - Create new project
- `GET /projects/:id` - Get project by ID

#### Allocations
- `GET /allocations` - List allocations with filters
- `POST /allocations` - Create new allocation
- `GET /allocations/:id` - Get allocation by ID
- `POST /allocations/:id/release` - Release allocation

#### Audit
- `GET /audit/logs` - List audit logs (admin only)
- `GET /audit/:entityType/:entityId` - Get entity audit history
## 🏗️ Architecture

### Frontend Architecture (React + TypeScript)
```
src/
  app/              # Page components routed via React Router
  components/       # Reusable UI components
  hooks/            # Custom React hooks
  stores/           # State management
  layouts/          # Page layouts
  services/         # API service layer
  styles/           # Global styles and design tokens
  types/            # TypeScript type definitions
  utils/            # Utility functions
  tests/            # Test files
```

### Backend Architecture (NestJS)
```
src/
  auth/             # Authentication module
  users/            # User management
  skills/           # Skill inventory management
  projects/         # Project allocation
  allocations/      # Allocation lifecycle
  audit/            # Audit logging service
  departments/      # Department management
  analytics/        # Reporting and dashboard data
  common/           # Pipes, interceptors, guards
  config/           # Configuration and environment
```

### Database Schema (PostgreSQL)
- users, departments, projects, skills
- employee_skills (junction with proficiency)
- allocations (project-employee assignments)
- audit_logs (immutable audit trail)

### Infrastructure
- Docker containerization for all services
- Docker Compose for local development
- Redis for caching and background job queuing
- GitHub Actions CI/CD pipeline
## 🎯 Core Features

### 1. Authentication & Authorization
- OAuth 2.0 / OpenID Connect support
- JWT-based session management
- Role-based route guarding (4 roles: Super Admin, Department Manager, Employee, Talent Analyst)
- MFA support
- Refresh token rotation

### 2. Skill Inventory Management
- Hierarchical skill taxonomy
- Proficiency scoring (1-5)
- Certification tracking
- Skill gap analysis
- Bulk import/export

### 3. Project Allocation Engine
- Real-time allocation validation
- Conflict detection (max 3 concurrent projects per employee)
- Priority-based scheduling (P1-P4)
- Auto-suggestions based on skills
- Undo/rollback capabilities

### 4. Dashboard & Analytics
- Interactive charts and visualizations
- Real-time KPI metrics
- Custom report builder
- Scheduled reporting
- Drill-down capability

### 5. Employee Self-Service
- Profile editing
- Skill self-assessment
- Availability management
- Project request submission
- Learning progress tracking

### 6. Administration Console
- User management
- Department management
- Budget allocation
- Policy configuration
- Audit log viewer
## 📋 Overview

This platform enables enterprise organizations to manage workforce allocation, skill inventories, and project assignments with proper RBAC, audit tracking, and business rule enforcement.

**Technology Stack:**
- **Frontend:** React 18 + TypeScript + Vite
- **Backend:** NestJS + TypeScript
- **Database:** PostgreSQL with Prisma ORM
- **Caching/Queues:** Redis with BullMQ
- **DevOps:** Docker, GitHub Actions

A comprehensive enterprise workforce allocation and skill management platform.

**Tech Stack:** React + TypeScript, NestJS, PostgreSQL, Redis

**Core Features:**
- Authentication & RBAC
- Skill Inventory Management
- Project Allocation
- Dashboard & Analytics
- Employee Self-Service
- Administration Console

Full documentation in STEP1_BRD_ANALYSIS.md
