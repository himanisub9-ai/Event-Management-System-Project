# Event-Management-System-Project
A production-ready MERN stack application for creating, discovering, and managing events.

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React 18 + Vite |
| Styling | Tailwind CSS |
| State | Context API |
| HTTP | Axios |
| Animations | Framer Motion |
| Backend | Node.js + Express.js |
| Database | MongoDB + Mongoose |
| Auth | JWT + bcryptjs |
| File Upload | Multer |
| PDF | jsPDF |
| QR Code | qrcode.react |

---

## Project Structure

```
Event Management System/
├── client/                     # React frontend (Vite)
│   ├── src/
│   │   ├── components/
│   │   │   ├── common/         # ProtectedRoute, AdminRoute
│   │   │   ├── events/         # EventCard, EventFilters, EventForm
│   │   │   └── layout/         # Navbar, Footer, Layout
│   │   ├── context/            # AuthContext, ThemeContext
│   │   ├── pages/
│   │   │   ├── admin/          # AdminDashboard, AdminUsersPage, AdminEventsPage
│   │   │   ├── HomePage.jsx
│   │   │   ├── EventsPage.jsx
│   │   │   ├── EventDetailPage.jsx
│   │   │   ├── CreateEventPage.jsx
│   │   │   ├── EditEventPage.jsx
│   │   │   ├── ProfilePage.jsx
│   │   │   ├── MyEventsPage.jsx
│   │   │   ├── MyRegistrationsPage.jsx
│   │   │   ├── BookmarksPage.jsx
│   │   │   ├── LoginPage.jsx
│   │   │   ├── RegisterPage.jsx
│   │   │   └── NotFoundPage.jsx
│   │   └── utils/              # api.js (Axios), helpers.js
│   ├── .env
│   └── package.json
│
└── server/                     # Express backend
    ├── config/db.js            # MongoDB connection
    ├── controllers/            # authController, eventController, etc.
    ├── middleware/             # auth, admin, errorHandler, upload
    ├── models/                 # User, Event, Registration, Review, Bookmark
    ├── routes/                 # auth, events, registrations, reviews, users, admin
    ├── utils/
    │   ├── generateToken.js
    │   └── seedData.js         # Sample data seeder
    ├── uploads/                # Auto-created for file uploads
    ├── .env
    └── server.js
```

---

## Quick Start

### Prerequisites

- Node.js v18+
- MongoDB (local or Atlas)
- npm

---

### 1. Clone / Open the project

```bash
# The project is already at:
# c:\Users\subho\OneDrive\Documents\Event Management System\
```

---

### 2. Setup the Backend

```bash
cd server
npm install
```

Create `server/.env` (already created — edit as needed):

```env
PORT=5000
MONGO_URI=mongodb://localhost:27017/eventmanagement
JWT_SECRET=eventmanagement_super_secret_jwt_key_2024_change_in_production
JWT_EXPIRE=30d
NODE_ENV=development
CLIENT_URL=http://localhost:5173
```

Start the server:

```bash
npm run dev
```

The API will be available at `http://localhost:5000`

---

### 3. Setup the Frontend

```bash
cd client
npm install
npm run dev
```

The app will be available at `http://localhost:5173`

---

### 4. Seed Sample Data (Optional but Recommended)

```bash
cd server
npm run seed
```

This creates:
- 5 users (1 admin + 4 regular users)
- 12 events across all categories
- Sample registrations, reviews, and bookmarks

**Login credentials after seeding:**

| Role | Email | Password |
|------|-------|----------|
| Admin | admin@eventmanager.com | Admin@123 |
| User | john@example.com | User@123 |
| User | jane@example.com | User@123 |
| User | mike@example.com | User@123 |
| User | sarah@example.com | User@123 |

---

## API Endpoints

### Auth
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/auth/register | Register new user |
| POST | /api/auth/login | Login |
| GET | /api/auth/me | Get current user |
| PUT | /api/auth/profile | Update profile |
| PUT | /api/auth/change-password | Change password |
| POST | /api/auth/avatar | Upload avatar |

### Events
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /api/events | Get all events (with filters) |
| POST | /api/events | Create event |
| GET | /api/events/featured | Get featured events |
| GET | /api/events/my-events | Get my events |
| GET | /api/events/:id | Get event by ID |
| PUT | /api/events/:id | Update event |
| DELETE | /api/events/:id | Delete event |
| PATCH | /api/events/:id/views | Increment views |

### Registrations
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/registrations/:eventId | Register for event |
| GET | /api/registrations/my | Get my registrations |
| PUT | /api/registrations/:id/cancel | Cancel registration |
| GET | /api/registrations/event/:eventId | Get event registrations |
| GET | /api/registrations/:id/qr | Get QR code data |

### Reviews
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/reviews/:eventId | Add review |
| GET | /api/reviews/event/:eventId | Get event reviews |
| PUT | /api/reviews/:id | Update review |
| DELETE | /api/reviews/:id | Delete review |

### Users / Bookmarks
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /api/users/bookmarks | Get bookmarks |
| POST | /api/users/bookmarks/:eventId | Toggle bookmark |

### Admin
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /api/admin/dashboard | Dashboard stats |
| GET | /api/admin/users | All users |
| DELETE | /api/admin/users/:id | Delete user |
| GET | /api/admin/events | All events |
| DELETE | /api/admin/events/:id | Delete event |
| PATCH | /api/admin/events/:id/featured | Toggle featured |
| PATCH | /api/admin/events/:id/status | Update status |
| GET | /api/admin/analytics/registrations | Analytics |

---

## Features

### User Features
- Register & login with JWT authentication
- Profile management with avatar upload
- Create, edit, delete own events
- Upload event banner images
- Browse & search events with filters
- Register / cancel event registration
- Download ticket as PDF
- QR code for event tickets
- Bookmark / save events
- Write reviews and ratings
- Dark / Light mode toggle
- Responsive mobile-first design
- Toast notifications
- Loading skeletons

### Admin Features
- Admin dashboard with statistics
- Manage all users (view, delete)
- Manage all events (view, edit, delete)
- Toggle event featured status
- Update event status inline
- Category breakdown charts
- Registration analytics

### Event Features
- 7 categories: Conference, Workshop, Seminar, Concert, Sports, Networking, Other
- Date, time, venue, city, country
- Capacity tracking with visual progress bar
- Real-time seat availability
- Free / Paid pricing
- Tags
- Featured flag
- View counter
- Average rating from reviews

---

## MongoDB Setup

### Option A — Local MongoDB

1. Install MongoDB Community: https://www.mongodb.com/try/download/community
2. Start MongoDB service
3. Use connection string: `mongodb://localhost:27017/eventmanagement`

### Option B — MongoDB Atlas (Cloud)

1. Create free account at https://cloud.mongodb.com
2. Create a cluster
3. Get connection string
4. Replace `MONGO_URI` in `server/.env`

---

## Testing the Application

1. Start MongoDB
2. Start backend: `cd server && npm run dev`
3. Start frontend: `cd client && npm run dev`
4. Seed data: `cd server && npm run seed`
5. Open http://localhost:5173
6. Login with `admin@eventmanager.com` / `Admin@123`

---

## Environment Variables

### server/.env
```env
PORT=5000
MONGO_URI=mongodb://localhost:27017/eventmanagement
JWT_SECRET=your_secret_key_here
JWT_EXPIRE=30d
NODE_ENV=development
CLIENT_URL=http://localhost:5173
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USER=your_email@gmail.com
EMAIL_PASS=your_app_password
```

### client/.env
```env
VITE_API_URL=http://localhost:5000/api
```

---

## Build for Production

```bash
# Build frontend
cd client
npm run build
