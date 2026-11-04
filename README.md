# SafeTown | Report recovery

SafeTown helps a township resident follow a blocked path or broken light from the initial report to a repair they can check. The [original browser prototype](https://kaiqingkhaw.github.io/safetown/public/) was a Team Vortex project for University Hackathon 2026. This separate repository explores what happens to those reports when local data needs to be restored.

**[Browse the portfolio implementation](https://github.com/kaiqingkhaw/safetown-portfolio/tree/codex/portfolio-backups)** · [Import code](https://github.com/kaiqingkhaw/safetown-portfolio/blob/codex/portfolio-backups/public/app.js) · [Regression tests](https://github.com/kaiqingkhaw/safetown-portfolio/blob/codex/portfolio-backups/tests/smoke.cjs)

![Team Vortex prototype interface](docs/preview.png)

## Why an import needs a preview

The team prototype could export its reports. Someone returning with a backup had no way to bring those records back through the interface. Simply replacing the browser's copy would risk losing newer repair notes.

The extension checks the file before writing anything. A new report ID can be added. If the ID and contents match, it skips the duplicate, even if JSON keys are in a different order. If the ID matches but the contents differ, it rejects the whole import. That last choice costs convenience, but makes a disagreement visible instead of guessing which repair history to keep. A failed storage write rolls back the change.

## Try it in two minutes

Use Node.js 22 or later. The extension is on the branch below; the public hackathon demo shows the original team version.

```sh
git clone --branch codex/portfolio-backups https://github.com/kaiqingkhaw/safetown-portfolio.git
cd safetown-portfolio
npm start
```

Open http://127.0.0.1:5173 with a fresh browser profile. Save the example below as **example-backup.json**.

1. Open **Community reports → Import backup** and choose the file. The preview should show one new report. Choose **Add these reports**, then search for **ST-9100**.
2. Choose the same file again. The preview should show zero new reports and one duplicate.
3. Change only the title in the file and import it again. The app should identify **ST-9100** as a conflict. The original title should still appear in Community reports.

<details><summary>Example backup (fictional report)</summary>

```json
{
  "project": "SafeTown",
  "schemaVersion": 1,
  "reports": [{
    "id": "ST-9100",
    "title": "Uneven paving beside the garden gate",
    "description": "Fictional example for checking backup recovery.",
    "location": "Community Garden",
    "category": "Damaged walkway",
    "priority": "Medium",
    "barrier": "Passable",
    "affected": "Wheelchair and mobility-aid users",
    "status": "Reported",
    "sample": true,
    "votes": 0,
    "created": "2026-10-28T09:00:00.000Z",
    "events": [{"text": "Example report created", "at": "2026-10-28T09:00:00.000Z"}]
  }]
}
```

</details>

## Verification and limits

Run `npm run check` to run the tests and build the app. The regression suite covers legacy exports, unsupported formats, conflicts and failed writes. The three example outcomes above were checked against the import logic. Manual desktop file-picker and mobile layout checks are still pending.

Reports and photos stay in one browser. Roles are simulated; importing a report does not authenticate its author. This prototype has not been trialled with a township, and no improvement in real repair times has been measured.
