# Lesson 1 — EC2 Lab Runs

**Student:** Kenneth (KP)
**Region:** us-east-1 (N. Virginia)
**Time zone used for proof lines:** America/Chicago

Each run: launched an EC2 instance from the lab template, connected through EC2 Instance Connect, activated the venv in `/opt/balerica-bank`, ran the proof line (`whoami`, Chicago date, `ec2-metadata -i`, `uptime -s`), started the API with `uvicorn app.main:app --host 0.0.0.0 --port 8000`, took the screenshot, then terminated the instance.

## Run log

| Run | Date (CT) | Instance ID | Boot time (UTC, `uptime -s`) | uvicorn PID | Public DNS | Screenshot | Status |
|---|---|---|---|---|---|---|---|
| 1 | 2026-10-29 | i-041d3584bd51c42f2 | 2026-10-29 09:07:35 | 37129 | ec2-98-94-13-85.compute-1.amazonaws.com | [lab1_run1.png](screenshots/lab1_run1.png) | Terminated |
| 2 | 2026-10-29 | i-00ed5025733bc0b72 | 2026-10-29 10:23:21 | 35541 | ec2-54-242-166-4.compute-1.amazonaws.com | [lab1_run2.png](screenshots/lab1_run2.png) | Terminated |
| 3 | 2026-10-29 | i-0e573a88eaf6e493f | 2026-10-29 10:47:30 | 35471 | ec2-52-201-245-25.compute-1.amazonaws.com | [lab1_run3.png](screenshots/lab1_run3.png) | Terminated |
| 4 | 2026-10-30 | i-0ab02167d86ecb1b9 | 2026-10-30 10:23:42 | 35436 | ec2-98-93-249-225.compute-1.amazonaws.com | [lab1_run4.png](screenshots/lab1_run4.png) | Terminated |
| 5 | 2026-10-30 | i-053b654f9a4e355b3 | 2026-10-30 10:42:43 | 35298 | ec2-54-89-167-2.compute-1.amazonaws.com | [lab1_run5.png](screenshots/lab1_run5.png) | Terminated |
| 6 | 2026-10-30 | i-0684b49eb0e369113 | 2026-10-30 11:01:54 | 35354 | ec2-34-224-87-141.compute-1.amazonaws.com | [lab1_run6.png](screenshots/lab1_run6.png) | Terminated |
| 7 | 2026-10-31 | i-040598873517ded7c | 2026-10-31 10:29:30 | 35898 | ec2-54-174-129-38.compute-1.amazonaws.com | [lab1_run7.png](screenshots/lab1_run7.png) | Terminated |

Runs per day: 3 on 10/29, 3 on 10/30, 1 on 10/31 (within the 3-per-day limit).

## Other screenshots

| What | Screenshot |
|---|---|
| COBOL return code 0 | [cobol_rc0.png](screenshots/cobol_rc0.png) |
| COBOL return code 4 | [cobol_rc4.png](screenshots/cobol_rc4.png) |
| COBOL return code 8 | [cobol_rc8.png](screenshots/cobol_rc8.png) |
| COBOL return code 12 | [cobol_rc12.png](screenshots/cobol_rc12.png) |
| COBOL ledger decode | [cobol_ledger_decode.png](screenshots/cobol_ledger_decode.png) |
| Cloning the homework repo | [git_clone.png](screenshots/git_clone.png) |

Notes and lessons learned: [lab1_notes.md](lab1_notes.md)
