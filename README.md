AMRAP API

A backend service for managing gyms, users, and memberships.
Built with Node.js, TypeScript, Express, Prisma (SQLite), and organized using Clean Architecture.

Project Overview
Category	Details
Tech Stack	Node.js, TypeScript, Express, Prisma, SQLite
Architecture	Clean Architecture (Domain → Application → Infrastructure → Interface)
Deployment	Railway
Documentation	Swagger (OpenAPI)
Testing	Jest + Supertest
Project Structure
Clean Architecture Layers
Layer	Description
Domain	Entities, core business rules, repository interfaces
Application	Use-cases, DTOs, business logic
Infrastructure	Prisma client, database config, repository implementations
Interface	Controllers, routes, HTTP server

Directory organization:

src/
 ├── domain/
 ├── application/
 ├── infrastructure/
 └── interface/
       └── http/

Setup Instructions
1. Clone Repository
git clone https://github.com/patel-jhanvi/amrap-gym-api.git
cd amrap-gym-api

2. Install Dependencies
npm install

3. Environment Variables

Create .env (local):

DATABASE_URL="file:./prisma/dev.db"
PORT=3000


On Railway: set DATABASE_URL in the dashboard only.

4. Run Prisma Migrations
npx prisma migrate dev --name init

5. Generate Prisma Client
npx prisma generate

6. Run Development Server
npm run dev

7. Build & Run Production
npm run build
npm start

API Documentation (Swagger)
Type	URL
Live Swagger Docs	https://amrap-gym-api-production.up.railway.app/docs
Local Swagger Docs	http://localhost:3000/docs

Includes:
✔ Request/response schemas
✔ Parameters
✔ Tags (Users, Gyms, Memberships)

Endpoints Summary
Users
Method	Endpoint	Description
POST	/users	Create user
GET	/users	List all users
GET	/users/:id	Fetch user by ID
GET	/users/:id/gyms	List gyms user belongs to
PUT	/users/:id	Update user
Gyms
Method	Endpoint	Description
POST	/gyms	Create gym
GET	/gyms	List gyms
GET	/gyms/:id	Get gym by ID
GET	/gyms/:id/users	Users in a gym
GET	/gyms/available/spots	Gyms with available capacity
Memberships
Method	Endpoint	Description
POST	/memberships	Add user to gym
DELETE	/memberships	Remove user from gym
Deployment
Environment	URL
Production	https://amrap-gym-api-production.up.railway.app

Example Request:

GET https://amrap-gym-api-production.up.railway.app/users

Technical Decisions
Area	Choice	Reason
Architecture	Clean Architecture	Maintainability & separation of concerns
ORM	Prisma	Type-safe queries + schema migrations
DB	SQLite	Lightweight + Railway compatible
Business Logic	Application Use-Cases	Testable and framework-independent
Validation	Controller-level	Keeps API predictable
Membership Rules	Capacity check + join date sorting	Business-driven behavior
Author

Jhanvi Patel
