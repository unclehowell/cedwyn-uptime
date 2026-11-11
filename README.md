# cedwyn-uptime — Uptime (Cedwyn webapp, number pending)

**Live:** https://cedwyn.bucklerfamily.estate/uptime/ (also https://bucklerfamily.estate/uptime/) — this repo's `main`, folder `public/`,
copied into the site by the central Cedwyn build (`split-repos.json` row "Uptime", deploy `repo`; `themes.json` id `uptime`).

Whether Archwilio (the Welsh Historic Environment Records), its record GGAT02038s and its `/wp/` path answer, with Coflein site 20182
and Heneb checked at the same moment as controls.

## Data
- The page reads `uptime.json` in its own folder: `https://cedwyn.bucklerfamily.estate/uptime/uptime.json`. That path is not a file in
  this repo: a Cloudflare zone route sends it to the change-monitor Worker (`ghf-watch`), which runs the checks and keeps the state, so the
  data is always live and a push here is never needed for fresh numbers.
- Schedule: twice a day at **06:00 and 18:00 UTC**, inside the Worker's shared 5-minute cron (the site/branch monitor keeps its 5-minute
  pace). A change of state counts after 2 checks in a row; the confirming re-check runs 5 minutes after a check that differs. A missed
  slot is caught up on the next run more than 12 h 15 min after the last check. 90 days of outages are kept.
- Fields: `checks[]` (name, url, status, ms, up, since, pend, hist), `outages[]`, `last_run`, `next_check`, `schedule_utc`, `confirm_checks`,
  `keep_days`.
- The old addresses `watch.bucklerfamily.estate/uptime` and `/uptime.json` answer 301 to this page and its data.

## Rules
Public text never names private people; no outbound links (site addresses appear as text). Commits carry the agent signature; no force-push.
