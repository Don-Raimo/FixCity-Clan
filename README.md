# 🏛️ FixCity - Municipal Fault Reporting Platform

> A full-stack municipal issue-tracking system that enables residents to report infrastructure faults (burst pipes, potholes, power outages, broken streetlights) by snapping geotagged photos, automatically routing actionable alerts to local municipal repair crews.

---

## 📖 App Overview

**FixCity** is an intuitive, community-driven civic reporting platform engineered to streamline communication between residents and local government authorities. 

When infrastructure issues arise, residents can log a fault in under 30 seconds. By taking a real-time photo and submitting a report, the app captures precise GPS coordinates (`[longitude, latitude]`) and sends the data to a fast **Node.js** backend. Using MongoDB **`2dsphere` spatial indexing**, reports are mapped to administrative zones and routed directly to designated repair teams—reducing response times and keeping residents updated through every stage of resolution.

---

## ✨ Core Features

- 📸 **Quick Fault Reporting:** Snap a photo of an issue, select a category, and submit in seconds.
- 📍 **Automatic Geotagging:** High-accuracy location capture using device GPS at the moment of photo capture.
- 🗺️ **Geospatial Dispatching:** Native MongoDB `2dsphere` index maps faults directly to municipal department zones.
- ⚡ **Async Background Alerts:** Asynchronous background tasks queue SMS, email, or push notifications to field crews without delaying user uploads.
- 🔐 **Secure Auth:** JWT-based user authentication with bcrypt password hashing.
- 📊 **Live Ticket Tracking:** Users can track report status in real time (`PENDING` → `IN_PROGRESS` → `RESOLVED`).

---

## 🛠️ Tech Stack

| Layer | Technology | Description |
| :--- | :--- | :--- |
| **Mobile Frontend** | **React Native (Expo)** | Cross-platform iOS and Android mobile app |
| **Backend API** | **Node.js + Express** | Fast, asynchronous JavaScript RESTful API framework |
| **Database & ODM** | **MongoDB + Mongoose** | NoSQL document database with native GeoJSON indexing |
| **Hardware Access** | **Expo Camera & Location** | Native camera hardware and GPS access |
| **Authentication** | **jsonwebtoken + bcryptjs** | OAuth2 Bearer token flow & password encryption |

---

## 📁 Repository Structure

```text
fix-my-city/
├── backend/
│   ├── src/
│   │   ├── controllers/     # Auth and report request handlers
│   │   ├── models/          # Mongoose models (User, Report, Location)
│   │   ├── middleware/      # JWT auth middleware & Multer file upload
│   │   ├── routes/          # Express route definitions
│   │   └── server.js        # Node.js Express app entrypoint
│   ├── package.json         # Backend Node dependencies
│   └── .env.example         # Environment variable template
│
└── mobile/
    ├── src/
    │   ├── screens/         # ReportScreen, AuthScreen, TicketStatusScreen
    │   ├── components/      # Custom UI components & Camera controls
    │   └── services/        # API client & Auth context
    ├── App.js               # Main React Native component
    └── package.json         # Mobile Node dependencies
