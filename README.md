# Western Province Disaster Watch

Leaflet web map for reporting and monitoring floods, landslides and storm damage in Colombo, Gampaha and Kalutara.

## Files
- `index.html`: the whole web app (map, report form, insights, live weather and river panels)
- `data/`: web-ready GeoJSON (WGS84) and `stats.json` (pre-computed Ditwah analysis)
- `tools/prep_data.py`: Python script that produced `data/` from the original layers (reproject, clip, simplify, analyse)

## Publish on GitHub Pages
1. Open your repository, click **Add file > Upload files**.
2. Drag in `index.html` and the whole `data` folder. Commit.
3. **Settings > Pages**: Deploy from branch `main`, folder `/ (root)`.
4. Open `https://YOUR-USERNAME.github.io/REPO-NAME/` in a private/incognito window.

## Storage (Google Sheet + Apps Script)
`CONFIG.SCRIPT_URL` at the top of the script in `index.html` holds the web app URL.
- Reports arrive in the `reports` tab of your Google Sheet with `verified = FALSE`.
- Change `verified` to `TRUE` to publish a report on the map.
- Photos are saved in the Drive folder `disaster-report-photos`.
- If you edit the Apps Script, use **Deploy > Manage deployments > Edit > New version**. The URL stays the same.

## Test checklist
1. Open the map: the badge in the top-left should say "0 reviewed public reports" (not "unavailable").
2. Report tab: tap the map, fill the form, add a photo, submit. A new row should appear in the Sheet.
3. Set `verified` to TRUE, press **Refresh** in the Insights tab: the report appears on the map.
4. Live tab: weather and river cards load.
5. Open the link on a phone.

## Adding layers
Add a GeoJSON file (WGS84) to `data/`, add its name to the `files` array in `boot()`, add an entry to `LAYERS`, and a `case` in `buildLayer()`.
