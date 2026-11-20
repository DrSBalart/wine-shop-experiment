# Wine Shop Pavlovia draft

This package recreates the Wine Shop V11 study as a browser experiment using the recommended defaults:

- automatic anonymous participant ID, while accepting `participant`, `PROLIFIC_PID`, or `sona_id` URL parameters;
- one participant-level record;
- complete click history stored as JSON in the `event_log` field;
- desktop/laptop layout recommended;
- no consent page yet;
- final thank-you screen.

## Contents

- `index.html`: entry page
- `app.js`: experiment logic
- `style.css`: responsive presentation
- `products.json`: products, conditions, prices, claims, and image paths
- `assets/`: eight wine images
- `data_dictionary.csv`: output fields

## Important deployment note

The experiment UI and logic are complete as a pilot draft. The `saveToPavlovia()` function checks for a data bridge exposed as `window.psychoJS.experiment` or `window.Pavlovia.saveData`. If neither is present, the final screen offers a local pilot CSV download.

Before public data collection, connect the package to the data-saving method used by your Pavlovia project and run a pilot in PILOTING mode. Do not recruit participants until the resulting Pavlovia data file has been verified.

## Suggested process

1. Create a blank project on Pavlovia/GitLab.
2. Upload all files from this package, preserving the `assets` folder.
3. Add the project-specific Pavlovia/PsychoJS data bridge to `index.html` or adapt `saveToPavlovia()` in `app.js`.
4. Set the study to PILOTING.
5. Test Chrome, Edge, and Firefox on a 1024 x 700 viewport or larger.
6. Complete a session and verify these fields in the server-side data: participant, demographics, display order, selected wines, total, seven ratings, event log, completion time.
7. Only then change the experiment to RUNNING.

## Local pilot

Serve the folder through a web server rather than double-clicking `index.html`. Example:

    python -m http.server 8000

Open `http://localhost:8000`.

## Current study rules

- Budget: EUR 30.00
- Maximum basket: 3 bottles
- Eight products randomized once per participant
- Product view, add, remove, and checkout events are recorded
- Seven 1-to-7 evaluation questions follow checkout
