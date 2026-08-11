# Space Dogs Hackathon Assistant

**Friend Project · Global Hack Week: Agents 2026**  
**Team:** ARPIP / Space Dogs  
**Event:** August 7–13, 2026

## Overview

A single-page mission control panel that tracks every challenge from the ARPIP Operational Action Plan.  
Built so the team (Maryfer, José and José Echeverría) can see the same progress, next tasks, deadlines and evidence locations in one place.

This project satisfies the **Build a Project for a Friend** challenge while remaining a practical internal tool for the rest of the week.

## Features

- Live mission progress bar (completed / total)
- Automatic “next critical deadline” highlight
- Crew cards that show each member’s current priority task
- Full challenge matrix pre-loaded from the Action Plan (22 items)
- Status controls: To do · In progress · Blocked · Completed
- Editable evidence location / link per challenge
- Filters by owner and status
- Add new missions or extra crew members
- One-click **Load ARPIP Action Plan** (official defaults)
- Export full state as JSON
- Fully offline — single HTML file, no backend, no API keys

## How to run

1. Download `space-dogs-control-panel.html`
2. Open it in any modern browser (Chrome, Edge, Firefox, Safari)
3. Click **⚡ Load ARPIP Action Plan** the first time
4. Start updating statuses and evidence

Data is saved in the browser’s `localStorage`.  
To share progress with another teammate, send the HTML file or the exported JSON.

## Tech stack

- HTML5 + CSS3 + Vanilla JavaScript
- localStorage for persistence
- Space Grotesk / Inter / Space Mono (Google Fonts)

## Team roles (from Action Plan)

| Role                          | Person            |
|-------------------------------|-------------------|
| Technical Lead                | José Peñalba      |
| Communications / UX / Evidence| Maryfer Higuera   |
| Testing / Operations / Embedded | José Echeverría |

## Evidence for submission

Recommended screenshots:

1. Full control panel (progress + crew section)
2. Mission log with several challenges marked In Progress / Completed
3. Crew card showing José’s critical task (Challenge 6 + HITL)
4. This README visible in the repository

## Notes

- Submissions on the GHW platform are immutable. Always have a second person verify evidence before submitting.
- This tool is intentionally lightweight. No authentication, no database, no deployment required.
- Designed to leave ARPIP with a reusable tracking surface rather than a one-off demo.

## License

Internal use for ARPIP / Space Dogs — Global Hack Week Agents 2026.
