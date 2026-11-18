MED2SYNC
MED2SYNC is a browser-only Medical Volunteer Coordination Platform created as a CSE326 academic prototype. It coordinates only non-clinical volunteer work: registration, logistics, documentation, awareness support, information desks and crowd coordination.

Run locally
From the repository root, run npm run dev and open http://localhost:3000. The included development server uses only Node.js built-ins, so no package installation is needed. You can also open dist/index.html directly in a modern browser.

Demo access
Volunteer: volunteer@med2sync.demo with any 4+ character demonstration password
Administrator: admin@med2sync.demo with any 4+ character demonstration password
Use the sample-access buttons on the sign-in page for the fastest route. Passwords are never saved; authentication is simulated through localStorage.

Features
Volunteer profiles, skills, interests, role preferences and weekly availability
Event discovery, search, compatibility scores, duplicate-application prevention and cancellation
Admin application approval/rejection, profile verification, event creation and shift assignment
Shift conflict, capacity and availability validation before an assignment
Attendance confirmation and automatic verified-service-hour calculation
Personal impact metrics, CSS chart, milestones, printable report and resettable demo data
Data and architecture
The single-page application uses HTML, CSS and vanilla JavaScript. app.js stores JSON collections for users, profiles, events, applications, assignments and activity logs under one namespaced localStorage key. It only creates sample data once, and Reset Demo Data deliberately restores it.

Matching algorithm
For each active event, MED2SYNC calculates:

skills × 0.4 + availability × 0.3 + interests × 0.2 + experience × 0.1

Each component becomes a 0–100 score from saved profile and event details. Results are sorted by the final score. This is an explainable rule-based recommendation, not AI.

Limitations and next steps
This frontend-only prototype has no real user identity, multi-device sync, email, sensitive-data collection, clinical decisions, or production authorization. Browser data is device-specific. A production system would need secure server-side authentication, access control, encrypted storage and privacy review.

Deployment
Deploy the contents of dist as a static site (including the assets folder). The included hosting manifest targets this directory and is compatible with static-hosting services such as Vercel.
