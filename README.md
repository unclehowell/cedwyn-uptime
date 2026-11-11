# cedwyn-uptime — Change log monitor (Cedwyn webapp 59 of 59)

**Live:** https://bucklerfamily.estate/uptime/ — this repo's `main`, folder `public/`, copied into the site by the central Cedwyn build
(`split-repos.json` row "Uptime", deploy `repo`; `themes.json` id `uptime`, `"slot": 59`).

A change log of the Archwilio pages (the Welsh Historic Environment Records), its record GGAT02038s and its `/wp/` path, with Coflein
site 20182 and Heneb read at the same moment as controls. No change, no news: a row is marked only when the page's text changed.

## Data
- The page reads `uptime.json` in its own folder (`https://bucklerfamily.estate/uptime/uptime.json`). That path is not a file in this
  repo: a Cloudflare zone route sends it to the change-monitor Worker (`ghf-watch`), which runs the checks and keeps the state.
- Schedule: twice a day at **06:00 and 18:00 UTC**. Each check reads every page, reduces it to its visible text (no scripts, styles,
  markup, or a line that is only the page's own date-and-time stamp) and compares a short hash with the last check.
- Per page (`checks[]`): `hash`, `baseline_at`, `changed_at`, `changes[]` (at, added/removed line counts, words before/after, up to 4
  sample lines each way; lines carrying words the editorial rules keep out are counted, not quoted), `chk[]` = `[time, mark]` per check,
  newest first, up to 180 (2 = baseline, 1 = changed, 0 = no change, -1 = not read). `status`, `hist`, `outages[]` remain for reference.
- The graph button on each row opens a dialog: a bar per check with a running total of changes, and a text log view (newest first).
- The old addresses `watch.bucklerfamily.estate/uptime`, `/uptime/`, `/uptime.html` and `/uptime.json` answer 301 straight to this page / JSON.

— Sion's Tab agent
