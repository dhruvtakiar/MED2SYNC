# MED2SYNC — Viva Notes

## File guide

- `dist/index.html`: the small HTML entry point; it loads the stylesheet and JavaScript.
- `dist/style.css`: visual system, responsive layouts, form states and print styling.
- `dist/app.js`: sample data, localStorage functions, screens, forms, matching, validation and event listeners.
- `dist/assets/med2sync-logo.jpeg`: the provided MED2SYNC logo.
- `README.md`: setup and product documentation.

## How it works

HTML supplies a single `#app` container. JavaScript reads the URL hash such as `#events` and renders the relevant screen. CSS Grid powers dashboards and cards; Flexbox handles alignment. A media query rearranges layouts on narrow screens.

`read()` uses `JSON.parse(localStorage.getItem(DB))` to retrieve the data object. `save(data)` uses `JSON.stringify(data)` to persist it. `seed()` runs only when no MED2SYNC data exists, protecting edits after refresh. User-entered text is passed through `escapeHtml()` before it is added to template markup.

The login form is intentionally simulated: a password is only checked for length and is never stored. Session state contains only the selected user ID. This prototype never asks for real medical, patient, identity or password data.

### Important algorithms

`scoreEvent(profile, event)` calculates skills (40%), availability (30%), interests (20%) and experience (10%). `assignShift()` stops assignment when the weekday is not declared available, the time overlaps a scheduled shift, or the role capacity is full. The comparison is `newStart < existingEnd && newEnd > existingStart`.

When an administrator records attendance, the code sets the assignment to `Present` and `Completed`, then derives the hours from the shift start/end times. `stats()` only totals completed assignments with present attendance, so approval alone does not create service hours.

## Viva questions and concise answers

1. What is localStorage? Browser storage that survives refreshes on the same device.
2. Why JSON? It converts JavaScript arrays and objects into storable text.
3. Why use IDs? IDs connect profiles, applications, events and assignments safely.
4. What is DOM manipulation? JavaScript updating HTML shown in the browser.
5. What is a hash route? The `#section` part of a URL used here to change screens without a server.
6. Why are passwords not saved? This is a frontend-only demonstration and saving real passwords would be unsafe.
7. What triggers sample data? `seed()` runs only when the storage key is empty.
8. How is duplicate signup blocked? The app searches applications with the same user and event IDs.
9. What is a status field? A short value such as Pending, Approved or Completed that describes a workflow stage.
10. What skills are supported? Non-clinical skills such as communication, registration and logistics.
11. What does profile verification mean? The demo administrator marks a volunteer as reviewed.
12. What is rule-based matching? A transparent formula written by developers, not a trained AI model.
13. Why use weights? They express the relative importance of matching factors.
14. What does 40% skills mean? Skills contribute 0.4 of the final compatibility score.
15. How is availability represented? A list of weekdays selected on the profile form.
16. What is a scheduling conflict? Two shift time ranges overlap for the same volunteer.
17. How does the overlap check work? A new start before an old end and a new end after an old start means conflict.
18. What is role capacity? The maximum number of volunteers permitted for an event role.
19. When are hours awarded? Only after present attendance and completed shift status.
20. How is attendance rate calculated? Present completed records divided by records marked Present or Absent.
21. Why use `textContent`/escaping? To avoid rendering unexpected user-entered HTML.
22. What does responsive mean? The page rearranges to remain usable on desktop, tablet and mobile widths.
23. What is a CSS variable? A reusable value such as `--teal` defined in `:root`.
24. Why use semantic labels? They make form fields clearer and more accessible.
25. What is event delegation? One document listener responds to buttons based on `data-action`.
26. Why use confirmation for reset? It prevents accidental removal of browser demo data.
27. What is a toast? A short on-screen success or error message.
28. Can users share data across devices? No; localStorage is limited to one browser/device.
29. What would a backend add? Secure accounts, shared data, server validation and permissions.
30. Why is this suitable for static deployment? Everything is client-side and uses only relative files.

## Ten practice modifications

1. Add a new sample event in `seed()`.
2. Change the matching weights and explain the impact.
3. Add a new skills option to a profile.
4. Add a status colour in CSS.
5. Make profile verification required before showing recommendations.
6. Add an explicit “Absent” attendance button for the administrator.
7. Add a date filter to Explore Events.
8. Add a completed-event filter to Applications.
9. Change the 5/10/25-hour milestones.
10. Create a new dashboard card using a value from `stats()`.
