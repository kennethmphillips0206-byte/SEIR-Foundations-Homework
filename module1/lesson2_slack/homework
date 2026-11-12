
# Lesson 2 Notes — Seven Alerts, Seven Wins

- **Date:** 2026-11-12 (America/Chicago)
- **Instance:** i-0df5fc7e5975bbdd8
- **Slack channel:** #balerica-alerts
- **Threshold during homework:** `SLACK_ALERT_SEVERITY=INFO`

## Script answers

### hw1 — Hello Slack
Sent HW-001: "Hello from KENNETH! I sent this alert myself, from my own EC2 instance." (No notes question.)

### hw2 — Which severities arrived, and why those?
All 4 arrived (INFO, WARNING, ERROR, CRITICAL). My threshold was INFO, the lowest level, so nothing was below it and nothing got filtered.

### hw3 — How many hours apart are server time and your wall clock?
6 hours. The server said 09:14 UTC while my clock said 3:14 AM CST. Central Standard Time is UTC-6 (it would be 5 hours during daylight saving time). Servers use UTC so logs from everywhere line up.

### hw4 — Why is a quiet INFO here good design, not a failure?
The disk was 25.3% used, so it's healthy and the code chose INFO. If healthy checks sent loud alerts, people would start ignoring alerts and miss the real one. Severity should match how urgent the problem actually is.

### hw5 — What would make this number spike on the Balerica bank?
Load was 0.00 / 0.00 / 0.00 on 2 CPUs, so INFO. I predicted it would go up, but the server was idle. Load would spike from lots of traffic: many customers logging in at once on payday, or the end-of-day COBOL batch job processing all the day's transactions.

### hw6 — Which fake incident deserves to wake a human at 3 AM?
The CRITICAL "ledger file not reachable" and the ERROR "/payments responded 500," because customers can't look up accounts or make payments right now. The WARNINGs (slow batch job, SWIFT queue) can wait until morning, and the INFO backup message never needs a human.

### hw7 — Morning report
Delivered HW-007: disk 25.3% used, load 0.00, Python 3.9.25, time 09:29:51 UTC.

## Experiments

### 1. `SLACK_ALERT_SEVERITY=CRITICAL`, rerun hw2
- **Prediction:** 1 of 4 (only CRITICAL)
- **Result:** 1 of 4. Only CRITICAL arrived. INFO, WARNING and ERROR are below CRITICAL, so the filter skipped them before sending.

### 2. `SLACK_ALERTS_ENABLED=false`, run hw1
- **Result:** "Skipped" and nothing reached Slack. A kill switch is useful during maintenance windows because engineers restart things on purpose, and you don't want every monitor paging the on-call person for planned work.

### 3. hw4 WARNING threshold changed 75 → 20
- **Result:** Same 25.3% disk, but the severity changed from INFO to WARNING. The disk didn't change; my rule did. The code decides the severity,
