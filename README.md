# HostABD - A Complete Hosting Business Website

This project is a complete, production-ready hosting business website named "HostABD.com" with full automation. It includes a Next.js frontend, an Express.js backend, and integration with MongoDB and a placeholder for the Proxmox VE API.

## Tech Stack

- **Frontend:** Next.js (App Router), Tailwind CSS, Zustand
- **Backend:** Node.js, Express.js, TypeScript, JWT Authentication
- **Database:** MongoDB (with Mongoose)
- **Infrastructure:** Proxmox VE API (placeholder)

## Features

- **Public Website:** Modern, responsive UI with pages for hosting plans, domains, about, contact, etc.
- **Authentication:** Customer registration and login.
- **Customer Dashboard:** View services, credentials, invoices, and manage support tickets (with placeholder data).
- **Admin Dashboard:** Manage customers, plans, orders, and services (with placeholder data).
- **Automation Pipeline:** A placeholder for automated VM creation on successful payment using the Proxmox VE API.

## Project Structure

The project is a monorepo with the following structure:

- `/frontend`: The Next.js application.
- `/backend`: The Express.js REST API.
- `/shared`: For shared types and utility functions (not used in this version).
- `/docs`: For documentation (not used in this version).

## Getting Started

### Prerequisites

- Node.js (v18 or later)
- npm
- MongoDB

### Installation and Running the Project

1.  **Clone the repository:**
    ```bash
    git clone <repository-url>
    cd <repository-name>
    ```

2.  **Backend Setup:**
    ```bash
    cd backend
    npm install
    cp .env.example .env
    # Edit the .env file with your MongoDB connection string and a JWT secret
    npm run build
    npm start
    ```
    The backend server will be running on `http://localhost:3001`.

3.  **Frontend Setup:**
    ```bash
    cd ../frontend
    npm install
    npm run dev
    ```
    The frontend development server will be running on `http://localhost:3000`.

## How to Use

1.  Start both the backend and frontend servers.
2.  Open your browser and navigate to `http://localhost:3000`.
3.  You can register a new user and log in.
4.  The dashboard pages will be accessible after logging in.
5.  To test the admin functionality, you can manually change a user's role to `admin` in the MongoDB database.

## API Endpoints

All API endpoints are prefixed with `/api`. The main routes are:

- `/api/auth`: User authentication (register, login)
- `/api/users`: User management (admin)
- `/api/products`: Product management (public and admin)
- `/api/orders`: Order management
- `/api/services`: Service management
- `/api/tickets`: Support ticket management

## Automation

The automation pipeline is triggered when an order is marked as paid. The `provisionService` function in `backend/src/automation/proxmox.ts` is called, which simulates the creation of a VM and a new service in the database. To test this, you can create an order and then manually update its status to `paid` in the database, or use the `/api/orders/:id/pay` endpoint.

## Future Improvements

- Implement the full Proxmox VE API integration.
- Integrate a real payment gateway.
- Add email notifications for registration, orders, and tickets.
- Replace placeholder data in the dashboard with real data from the API.
- Complete the shared types and docs directories.
- Add more comprehensive tests.
- Create Dockerfiles for easier deployment.
