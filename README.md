# MED2SYNC

MED2SYNC is a frontend prototype for coordinating non-clinical medical-event volunteers. It brings volunteer registration, opportunity discovery, applications, shift allocation and participation reporting into one simple browser-based experience.

> This is an academic prototype. It does not provide clinical guidance or collect real patient information.

## Features

- Volunteer profiles with skills, interests, experience and availability
- Event discovery with search and compatibility scoring
- Applications, cancellations and duplicate-application prevention
- Administrator tools for volunteer verification, decisions, events and shift assignment
- Shift capacity, availability and conflict validation
- Attendance tracking and verified volunteer-hour reporting
- Responsive interface, printable reports and resettable demo data

## Technology

- HTML, CSS and vanilla JavaScript
- Browser `localStorage` for demonstration data
- A small Node.js development server with no third-party dependencies
- Static deployment configuration for Vercel

## Getting started

### Prerequisites

Install a current version of [Node.js](https://nodejs.org/).

### Run locally

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser. No `npm install` step is required.

## Demo access

| Role | Email | Password |
| --- | --- | --- |
| Volunteer | `volunteer@med2sync.demo` | Any 4 or more characters |
| Administrator | `admin@med2sync.demo` | Any 4 or more characters |

The sample-access buttons on the sign-in screen provide the fastest way to explore the application. Passwords are never stored; authentication is simulated for the demo.

## Project structure

```text
.
├── dist/                 # Static application files
│   ├── assets/           # Images and other assets
│   ├── app.js            # Application behaviour and demo data
│   ├── index.html        # HTML entry point
│   └── style.css         # Visual design and responsive styles
├── docs/                 # Project notes and testing record
├── scripts/              # Local development utilities
├── package.json          # Project scripts
└── vercel.json           # Static-hosting configuration
```

## Data and matching

All demonstration data stays in the browser under a namespaced `localStorage` key. The event compatibility score is based on skills (40%), availability (30%), interests (20%) and experience (10%). Resetting the demo restores the original sample data.

## Deployment

The app is static. Deploy the contents of `dist/` to any static host. The included `vercel.json` is ready for Vercel deployments.

## Limitations

MED2SYNC is intentionally frontend-only. It has no real authentication, shared database, email notifications, access controls or production-grade privacy protections. A production version would require secure backend services, role-based access control and an appropriate privacy and security review.
