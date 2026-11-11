# Changelog

## v1.0.0 — 11 Nov 2026
- The uptime page becomes its own Cedwyn webapp at /uptime/ (repo unclehowell/cedwyn-uptime), with the shared header, footer and Day/Night theme.
- Checks move from every 5 minutes to twice a day (06:00 and 18:00 UTC), with a confirm re-check 5 minutes after a check that differs.
- Live data at /uptime/uptime.json, served by the change-monitor Worker; the old watch.bucklerfamily.estate/uptime addresses answer 301 here.

## v0.1.0 — 24 Oct 2026
- First uptime page on the change monitor (watch.bucklerfamily.estate/uptime), checked every 5 minutes.
