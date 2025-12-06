# Shikshaarthi

Shikshaarthi is a microservices-based MERN platform that centralizes essential campus services for students, including mess, rentals, laundry, medical, electrician, plumber, marketplace and rewards modules. It is built and maintained end‑to‑end by a single developer, focusing on reliability, scalability and a smooth user experience.[memory:4][memory:6]

## Tech Stack

- Frontend: React + Vite (separate user panel and admin panel)[file:2][file:4]
- Backend: Node.js, Express.js, REST APIs, MongoDB with indexing[memory:4]
- Architecture: Multiple domain microservices behind an API gateway with internal API‑key based communication[memory:4]
- Infrastructure: Nginx reverse proxy, Hostinger VPS, SSH-based deployment[memory:4]
- Payments: Razorpay subscription model for service access and billing[memory:4]

## Features

- Student web app to browse, book and track all campus services in one place.
- Admin dashboard to manage vendors, approve service requests, update statuses and monitor issues.[file:1][file:4]
- Authentication and authorization for users and admins via a dedicated service.
- Scalable backend with separate microservices per domain, enabling independent deployment and fault isolation.[file:5][memory:4]

## Repository Structure

shikshaarthi_v2/
├── Frontend/
│ ├── admin-panel/ # Admin React + Vite app
│ └── user-panel/ # Student React + Vite app
└── Backend/
├── api-gateway/ # Single public entry point, routes to services
├── auth-service/ # Login, signup, token validation
├── mess-service/ # Mess plans, menus, subscriptions, complaints
├── rental-service/ # Room/PG listings and rental bookings
├── laundry-service/ # Laundry orders and slot management
├── medical-service/ # Medical appointments and related data
├── electrician-service/ # Electrician tickets and resolution
├── plumber-service/ # Plumbing-related service requests
├── marketplace-service/ # Student marketplace for items
├── notification-service/ # Email / notification events
├── rewards-service/ # Reward points and offers
└── shared/ # Common models, utils, configuration

text
[file:1][file:5]

## Getting Started

### Prerequisites

- Node.js (LTS)
- MongoDB instance (local or cloud)
- Razorpay keys (for payment flows, optional in local dev)
- npm or yarn

### Clone the repository

git clone https://github.com/<your-username>/shikshaarthi_v2.git
cd shikshaarthi_v2

text

### Run the frontend (example: user panel)

cd Frontend/user-panel
npm install
npm run dev

text

The dev server will start on the port configured in `vite.config.js`.[file:2]

### Run a backend service (example: mess service)

cd Backend/mess-service
npm install
npm start

text

Repeat similar steps for other services such as `rental-service`, `laundry-service`, `medical-service`, etc.[file:5]

### Environment variables

Create `.env` files for each service (and frontend if needed). Common variables include:

- `MONGODB_URI`
- `JWT_SECRET`
- `RAZORPAY_KEY_ID`, `RAZORPAY_KEY_SECRET`
- Internal base URLs and API keys for inter-service communication[memory:4]

## Deployment

The production setup runs on a Hostinger VPS where each backend service runs as a Node.js process, the frontends are built and served behind Nginx, and the domain points to the API gateway and frontend via reverse proxy rules. SSH is used for deployments and process management, targeting high uptime and low latency for thousands of requests per second.[memory:4][memory:6]

## Future Improvements

- Containerize each service with Docker and orchestrate using Kubernetes or similar tools.
- Add CDN and caching layers to reduce frontend and API response times.
- Introduce centralized logging, tracing and dashboards for observability and faster debugging.
