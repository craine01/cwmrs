# 🌿 Community Waste Management & Reporting System
### Barangay 7 Bliss Portal — Cuenca, Batangas

---

## 📋 Overview

The **Community Waste Management and Reporting System (CWMRS)** is a web-based portal built for the residents of **Barangay 7 Bliss, Cuenca, Batangas**. It empowers community members to report waste issues in real time, track garbage collection schedules, and stay informed about local environmental actions — all through a secure, resident-authenticated interface.

> *"A cleaner neighborhood starts with a single report."*

---

## ✨ Key Features

| Feature | Description |
|---|---|
| 🔐 **Resident Authentication** | Secure login and registration with admin-reviewed ID verification |
| 📢 **Waste Reporting** | Submit real-time waste concern reports with photo evidence |
| 📊 **Live Analytics** | Community-wide stats on pending cases, resolved reports, and active members |
| 🗓️ **Garbage Truck Tracker** | Collection schedules, designated drop-off cage locations, and waste sorting guides |
| 📰 **Community News** | Latest local environmental actions, programs, and awards |
| 🔄 **Report Status Tracker** | Transparent three-step tracking: Pending → In-Progress → Resolved |

---

## 🏗️ System Architecture

```
index.html          ← Main portal homepage (this file)
about.html          ← About the barangay program
waste.html          ← Waste sorting & collection details
community.html      ← Community news & announcements
contact.html        ← Contact the barangay office
report.html         ← File a new waste report
```

**External Services Used:**

- **SheetDB** (`sheetdb.io`) — Google Sheets-based database for storing resident registrations and login credentials
- **Cloudinary** — Cloud image hosting for resident ID photo uploads
- **Google Fonts** — Poppins typeface
- **Font Awesome 6** — Icon library

---

## 🔐 Authentication Flow

### Registration
1. Resident fills in their full name, email, password, and barangay address
2. A valid government ID photo is uploaded (stored securely on Cloudinary)
3. The record is saved to SheetDB with a **"Pending"** status
4. A Barangay 7 Admin reviews and manually sets the status to **"Verified"**

### Login
1. Resident enters their registered email and password
2. The system searches SheetDB for a matching record
3. Account status is checked:
   - ✅ **Verified** → Access granted to the portal
   - ⏳ **Pending** → Resident is informed to wait for admin approval
   - ❌ **Other** → Resident is directed to contact the barangay office

> ⚠️ **Security Note for Admins:** Passwords are currently stored and compared as plain text. For a production deployment, passwords should be hashed (e.g., using bcrypt) before storage. Do not use this system for sensitive data without upgrading the authentication layer.

---

## 🗑️ Waste Collection Schedule

| Day | Time |
|---|---|
| Every **Sunday** | 10:00 AM |
| Every **Thursday** | 10:00 AM |

### Waste Sorting Categories
Residents must separate waste into three categories before collection:

1. **Biodegradable** — Food scraps, garden waste, paper
2. **Non-Biodegradable** — Plastics, metals, glass
3. **E-Waste** — Electronics, batteries, cables (set aside separately)

Bags must be deposited at the designated **metal mesh waste cages** within the community.

---

## 📊 Report Status Tracker

Every submitted waste concern follows a transparent three-step process:

```
[ 1. PENDING ]  →  [ 2. IN-PROGRESS ]  →  [ 3. RESOLVED / UNRESOLVED ]
   Verifying         Teams deployed           Case officially closed
   your report       on-ground                in community records
```

---

## 🛠️ Setup & Configuration

If you are deploying or maintaining this system, update the following constants at the top of the `<script>` block in `index.html`:

```javascript
var SHEETDB_URL    = 'https://sheetdb.io/api/v1/YOUR_SHEET_ID';
var CLOUDINARY_URL = 'https://api.cloudinary.com/v1_1/YOUR_CLOUD_NAME/image/upload';
var UPLOAD_PRESET  = 'YOUR_UPLOAD_PRESET';
```

### SheetDB Column Headers
Your connected Google Sheet must have exactly these column headers (row 1):

```
date | name | email | password | address | id_proof | status
```

### Cloudinary Setup
1. Create a free Cloudinary account at [cloudinary.com](https://cloudinary.com)
2. Create an **unsigned upload preset** named `TCWMRS` (or update the variable above)
3. Uploaded IDs are stored in the `TCWMRS_IDs` folder in your Cloudinary media library

---

## 👤 Admin Responsibilities

As the Barangay 7 Admin, your responsibilities include:

- [ ] Reviewing new resident registrations in the SheetDB Google Sheet
- [ ] Changing new accounts from `Pending` → `Verified` after ID review
- [ ] Monitoring submitted waste reports via the report system
- [ ] Updating community news and announcements on `community.html`
- [ ] Keeping the garbage truck schedule current on `waste.html`

---

## 📱 Responsive Design

The portal is fully responsive and tested across:
- 🖥️ Desktop (1024px and above)
- 📱 Tablet (768px – 1024px)
- 📲 Mobile (below 768px, with hamburger navigation)

---

## 📈 Community Stats (Live Counters)

These figures animate in when the analytics section scrolls into view and are updated manually or via the reporting system:

- **1,500** Cases Pending
- **3,000** Cases Solved
- **56,300** Active Members
- **90,000** Community Actions

---

## 🤝 Credits & Contact

**Developer:** Kent Reyes
**Email:** kentreyes208@gmail.com
**Phone:** +63 936 943 3099
**Community:** Barangay 7 Bliss, Cuenca, Batangas

**Social:**
- Instagram: [@kentii_88](https://www.instagram.com/kentii_88/)
- Facebook: [Kent Reyes](https://www.facebook.com/kent.reyes.904339)

---

## 📄 License

© 2026 Community Waste Management & Reporting System — Barangay 7 Bliss Portal.
All rights reserved. Built for community use by and for the residents of Cuenca, Batangas.
