# 📊 Survey Management System

A full-stack, location-aware Survey Management System that connects **Users, Surveyers, and Admins** through a complete survey lifecycle.

Users can find nearby surveys and participate, Admins manage proposals and surveys, and approved Surveyers can create surveys, collect responses, analyze results, and submit reports.

## 🚀 Features

### 👤 User

* Register and login
* Submit survey proposals
* Find nearby surveys
* Location-based survey filtering
* Participate in active surveys
* One response per survey
* View proposal and participation status

### 📝 Surveyer

* Become a Surveyer after Admin approval
* Receive a unique Surveyer ID
* Create one approved survey
* Add:

  * Single Choice
  * Multiple Choice
  * Yes/No
  * Rating
  * Paragraph
* Configure survey location and radius
* Set start and end time
* Publish surveys
* View response analytics
* Generate and submit reports

### 👨‍💼 Admin

* View survey proposals
* Approve or reject proposals
* Assign Surveyer IDs
* View all surveys
* View response counts
* Access survey and report history

## 🔄 Survey Lifecycle

```text
User
 ↓
Submit Proposal
 ↓
Admin Approval
 ↓
Surveyer ID Assigned
 ↓
Create Survey
 ↓
Publish Survey
 ↓
Collect Responses
 ↓
View Analytics
 ↓
Generate Report
 ↓
Submit Report
 ↓
Survey Completed
 ↓
Surveyer Authorization Completed
 ↓
User
```

## 📍 Location-Based Survey

The system uses the browser **Geolocation API** to get the participant's location.

Each survey contains:

```text
City
Latitude
Longitude
Radius
```

The backend checks the distance between the participant and the survey location before allowing participation.

## 🛠️ Tech Stack

### Frontend

* React.js
* JavaScript
* Tailwind CSS
* React Router
* Axios
* Recharts

### Backend

* Node.js
* Express.js
* JWT
* bcryptjs
* Zod

### Database

* MongoDB
* Mongoose
* MongoDB Atlas

### Services

* Browser Geolocation API
* OpenStreetMap Nominatim
* Render

## 🏗️ Project Structure

```text
Survey-System/
├── client/
│   ├── src/
│   └── package.json
│
└── server/
    ├── config/
    ├── controllers/
    ├── middleware/
    ├── models/
    ├── routes/
    ├── services/
    ├── utils/
    ├── validators/
    ├── app.js
    ├── server.js
    └── package.json
```

## 🔐 Security

* JWT authentication
* Password hashing with bcrypt
* Role-based authorization
* Protected Admin and Surveyer routes
* Backend validation
* Duplicate response prevention
* Backend location verification
* Environment variables for secrets

## 📦 Database Collections

```text
users
proposals
surveys
responses
reports
notifications
```

## 📌 Main API Endpoints

### Authentication

```text
POST /api/auth/register
POST /api/auth/login
```

### Proposals

```text
POST /api/proposals
GET  /api/proposals/my
```

### Admin

```text
GET   /api/admin/proposals
PATCH /api/admin/proposals/:id/approve
PATCH /api/admin/proposals/:id/reject
GET   /api/admin/surveys
GET   /api/admin/surveys/:id
```

### Surveys

```text
POST /api/surveys
PUT  /api/surveys/:id
POST /api/surveys/:id/publish
GET  /api/surveys/available
```

### Responses

```text
POST /api/surveys/:id/responses
```

### Analytics

```text
GET /api/surveys/:id/analytics
```

### Reports

```text
POST  /api/surveys/:id/report
PATCH /api/reports/:id/submit
```

## ⚙️ Local Setup

### Clone Repository

```bash
git clone https://github.com/saravanan2006-art/Survey-System.git
cd Survey-System
```

### Backend

```bash
cd server
npm install
```

Create `.env`:

```env
PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
JWT_EXPIRES_IN=7d
```

Run backend:

```bash
npm run dev
```

Backend:

```text
http://localhost:5000
```

### Frontend

```bash
cd ../client
npm install
npm run dev
```

Frontend:

```text
http://localhost:5173
```

## 🌐 Production Backend

The backend is deployed on Render.

Axios configuration:

```javascript
import axios from "axios";

const api = axios.create({
  baseURL: "https://survey-y0wg.onrender.com/api",
});

export default api;
```

## 📋 Business Rules

* One approved proposal creates one Surveyer authorization.
* One Surveyer can create only one survey.
* One User can submit only one response per survey.
* Surveyers cannot participate while their Surveyer authorization is active.
* Surveyer ID becomes invalid after report submission.
* Completed surveys and reports remain available to Admin.
* Survey participation requires valid location and active survey timing.
* Authorization and validation are enforced by the backend.

## 🎯 Project Goal

The system provides a structured workflow for:

```text
Proposal
   ↓
Admin Approval
   ↓
Survey Creation
   ↓
Location-Based Participation
   ↓
Response Collection
   ↓
Analytics
   ↓
Report Generation
```

It reduces manual survey management and provides a centralized platform for collecting and analyzing survey data.

## 🔮 Future Enhancements

* Email and OTP verification
* Interactive maps
* Advanced analytics
* Automated PDF reports
* AI-powered survey insights
* Real-time notifications
* Cloud file storage

## 👨‍💻 Author

**Saravanan Balaji**

B.E. Computer Science and Engineering

GitHub: https://github.com/saravanan2006-art
