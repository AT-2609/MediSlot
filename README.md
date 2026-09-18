# MediSlot

### Doctor Appointment Booking & Management

MediSlot is a full-stack MERN application for booking medical appointments and managing the workflows around them. Patients can explore doctors and manage bookings, while doctors and administrators use a separate portal to manage appointments, profiles, and availability.

## Overview

The project brings three connected applications together in one repository:

| Application | Purpose |
| --- | --- |
| Patient frontend | Doctor discovery, patient accounts, profiles, and appointment booking |
| Admin and doctor portal | Doctor onboarding, availability management, and appointment dashboards |
| Backend API | Authentication, application logic, database operations, and image uploads |

## Features

### For patients

- Register and log in to a patient account.
- Browse doctors and explore their profiles and specialities.
- Book appointments and view existing bookings.
- Cancel appointments and update profile information.
- Upload a profile picture.
- Use a mock payment flow for demonstration purposes.

### For doctors

- Log in to a dedicated doctor dashboard.
- View assigned appointments.
- Mark appointments as completed or cancel them.
- Update professional profile information.
- View dashboard summaries.

### For administrators

- Access the administration dashboard.
- Add doctors and upload their profile images.
- View registered doctors and change their availability.
- View and manage appointments across the platform.
- Review dashboard metrics.

### Technical highlights

- JWT-based authentication and role-specific access middleware.
- Password hashing with bcrypt.
- MongoDB persistence through Mongoose models.
- Image uploads using Multer and Cloudinary.
- React interfaces built with Vite and styled with Tailwind CSS.
- API communication through Axios and navigation with React Router.
- Toast notifications for user feedback.

> The payment flow is a mock implementation. Live payment gateway integration is a future enhancement.

## Technology Stack

| Layer | Technologies |
| --- | --- |
| Frontend and portal | React, Vite, Tailwind CSS |
| Navigation and API requests | React Router, Axios |
| Notifications | React Toastify |
| Server | Node.js, Express.js |
| Database | MongoDB, Mongoose |
| Authentication | JSON Web Tokens, bcrypt |
| Image handling | Cloudinary, Multer |
| Configuration | dotenv, cors |

## Repository Layout

| Path | Contents |
| --- | --- |
| `frontend/src/` | Patient pages, shared components, assets, and application context |
| `admin-portal/src/` | Admin and doctor pages, layouts, components, and contexts |
| `backend/config/` | Database and image service configuration |
| `backend/controllers/` | User, doctor, and admin request handlers |
| `backend/middlewares/` | Authentication and upload middleware |
| `backend/models/` | User, doctor, and appointment models |
| `backend/routes/` | API route definitions |
| `backend/server.js` | Backend entry point |

## Run Locally

### Prerequisites

- Node.js and npm.
- Git.
- A MongoDB database and connection URI.
- A Cloudinary account for image uploads.

### 1. Clone the repository

```bash
git clone https://github.com/AT-2609/MediSlot.git
cd MediSlot
```

If you already have this repository on your computer, open that copy instead.

### 2. Configure and start the backend

In the first terminal, from the repository root:

```bash
cd backend
npm install
```

Create `backend/.env` with your own values:

```dotenv
PORT=8000
MONGODB_URI=mongodb+srv://YOUR_USERNAME:YOUR_PASSWORD@YOUR_CLUSTER.mongodb.net
JWT_SECRET=REPLACE_WITH_A_LONG_RANDOM_SECRET
CLOUDINARY_NAME=YOUR_CLOUDINARY_CLOUD_NAME
CLOUDINARY_API_KEY=YOUR_CLOUDINARY_API_KEY
CLOUDINARY_API_SECRET=YOUR_CLOUDINARY_API_SECRET
ADMIN_EMAIL=YOUR_ADMIN_EMAIL
ADMIN_PASSWORD=REPLACE_WITH_A_STRONG_PASSWORD
```

Start the backend and leave this terminal running:

```bash
npm run server
```

### 3. Configure and start the patient frontend

Open a second terminal at the repository root:

```bash
cd frontend
npm install
```

Create `frontend/.env`:

```dotenv
VITE_BACKEND_URL=http://localhost:8000
```

Start the frontend:

```bash
npm run dev
```

Open the local URL printed by Vite in the terminal.

### 4. Configure and start the admin and doctor portal

Open a third terminal at the repository root:

```bash
cd admin-portal
npm install
```

Create `admin-portal/.env`:

```dotenv
VITE_BACKEND_URL=http://localhost:8000
```

Start the portal:

```bash
npm run dev
```

Open the separate local URL printed by Vite. Keep all three terminals running while using the application.

Environment files belong inside their respective application folders. Restart the affected server after changing them. Keep actual credentials out of Git, and never put backend secrets in variables prefixed with `VITE_`, which are exposed to the browser.

## Try the Appointment Flow

1. Open the admin portal and log in using the configured administrator credentials.
2. Add a doctor and set their availability.
3. Open the patient frontend and create a patient account.
4. Select a doctor and book an available appointment slot.
5. Log in to the doctor portal using the doctor credentials created during onboarding.
6. Review the appointment and mark it completed or cancel it.
7. Check the updated appointment status in the patient and admin views.

## API Organization

| Base path | Responsibilities |
| --- | --- |
| `/api/user` | Registration, login, patient profiles, bookings, cancellations, and mock payments |
| `/api/doctor` | Doctor listing, login, profiles, appointments, and dashboard data |
| `/api/admin` | Admin login, doctor onboarding, availability, appointments, and dashboard data |

See `backend/routes/` for the exact endpoints and `backend/controllers/` for request handling. Protected endpoints require the authentication expected by their associated middleware.

## Manual Verification

- Check registration and login for each supported role.
- Confirm protected operations reject unauthenticated requests.
- Test doctor creation, image uploads, and availability changes.
- Test booking, cancellation, and appointment completion across the three interfaces.
- Check profile updates and feedback for invalid inputs.
- Review the interfaces at desktop and mobile screen sizes.

These are suggested manual checks, not a claim of automated test coverage.

## Future Enhancements

- Booking confirmations and reminders by email.
- Live payment gateway integration and payment verification.
- A calendar view for doctor schedules.
- Pagination and additional appointment filters.
- Automated API and interface tests.

## Author

**Arpit Thakur**  

