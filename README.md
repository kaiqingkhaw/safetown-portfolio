# SafeTown

[Open the live demo](https://kaiqingkhaw.github.io/safetown-portfolio/public/)

When a footpath is blocked, a resident has two questions. How do I get through today? Who will check that the repair worked? SafeTown follows one report through both decisions.

![SafeTown township dashboard](docs/preview.png)

## Try the garden entrance

Open the live demo above. On the overview, select the Community Garden access update. The sample neighbourhood includes a fallen branch at the Community Garden. Open **Community reports**, find **Fallen branch across the footpath**, and open its progress view. Under **Temporary access**, select **This approach is blocked**. The directions disappear and the report records why.

Open the same report in the **Management desk**. Under **Update access instructions**, describe a checked approach and set a review interval. Reopen the resident view to see the replacement instructions and review time. The example uses fictional locations.

## Implementation

The original reporting and resident-verified repair workflow was a Team Vortex University Hackathon 2026 project. This personal portfolio edition adds time-limited access instructions, resident challenges and report backup recovery. A backup import previews additions and duplicates. Conflicting histories stop the import before it writes to storage.

The app uses HTML, CSS and browser JavaScript. Roles are simulated and records are stored in the current browser. Use Node.js 22 or later for the development tools.

- `npm start` serves the app locally.
- `npm run check` runs the regression suite and builds a self-contained `dist/SafeTown.html` for offline demonstrations.

## Local setup

```sh
git clone https://github.com/kaiqingkhaw/safetown-portfolio.git
cd safetown-portfolio
npm start
```

Open the address printed by the server. The app has no installation dependencies.

## Design decisions

- Access instructions have a review deadline. An open report withdraws them when that deadline passes.
- Residents can flag a blocked approach. Replacement instructions require a new maintenance update.
- Repair evidence and resident verification are separate steps so the history explains who did what.
- Backups are checked before import. A conflicting report stops the import, and a failed storage write rolls back the change.

## Scope

This is a browser prototype with fictional locations and simulated roles. Reports are saved on the current device. A shared deployment would need authenticated accounts, a database, moderation and verified location data.
