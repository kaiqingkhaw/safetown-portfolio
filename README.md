# SafeTown

When a footpath is blocked, a resident has two questions. How do I get through today? Who will check that the repair worked? SafeTown follows one report through both decisions.

![SafeTown township dashboard](docs/preview.png)

## Try the garden entrance

Open `public/index.html` in a browser. The sample neighbourhood includes a fallen branch at the Community Garden. Open **Community reports**, find **Fallen branch across the footpath**, and open its progress view. Under **Temporary access**, select **This approach is blocked**. The directions disappear and the report records why.

Open the same report in the **Management desk**. Under **Update access instructions**, describe a checked approach and set a review interval. Reopen the resident view to see the replacement instructions and review time. The example uses fictional locations.

## Implementation

The original reporting and resident-verified repair workflow was a Team Vortex University Hackathon 2026 project. This personal portfolio edition adds time-limited access instructions, resident challenges and report backup recovery. A backup import previews additions and duplicates. Conflicting histories stop the import before it writes to storage.

The app uses HTML, CSS and browser JavaScript. Roles are simulated and records are stored in the current browser. Use Node.js 22 or later for the development tools.

- `npm start` serves the app locally.
- `npm run check` runs the regression suite and builds a self-contained `dist/SafeTown.html` for offline demonstrations.
