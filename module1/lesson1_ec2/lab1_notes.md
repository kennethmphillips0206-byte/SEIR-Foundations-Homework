# Lab 1 Notes — EC2

**Student:** Kenneth (KP)
**Runs completed:** 7 of 7 (2026-10-29 to 2026-10-31)

## Routine for each run

1. Launch an instance from the lab template (us-east-1).
2. Connect with EC2 Instance Connect.
3. `cd /opt/balerica-bank`, then `source venv/bin/activate`.
4. Run the proof line:
   `whoami && TZ='America/Chicago' date && ec2-metadata -i && uptime -s`
5. Start the API: `uvicorn app.main:app --host 0.0.0.0 --port 8000`
6. Take the screenshot showing the proof lines and "Uvicorn running".
7. Copy the public DNS, then terminate the instance.

## Run notes

| Run | Date | Instance ID | PID | What happened |
|---|---|---|---|---|
| 1 | 10/29 | i-041d3584bd51c42f2 | 37129 | Skipped the proof line the first time. Stopped uvicorn with Ctrl+C, ran the proof line, then restarted uvicorn. |
| 2 | 10/29 | i-00ed5025733bc0b72 | 35541 | Skipped the proof line again and fixed it the same way (Ctrl+C, proof line, restart). |
| 3 | 10/29 | i-0e573a88eaf6e493f | 35471 | Ran the proof line correctly on the first try. |
| 4 | 10/30 | i-0ab02167d86ecb1b9 | 35436 | My first Run 4 attempt (i-08187379cb1c7a3c8) was thrown out because I terminated it before copying the DNS. This is the redo. |
| 5 | 10/30 | i-053b654f9a4e355b3 | 35298 | Clean run. Also tried `account_lookup` and `payment_post` before starting uvicorn. |
| 6 | 10/30 | i-0684b49eb0e369113 | 35354 | Clean run. Did the COBOL practice and the git clone on this instance. |
| 7 | 10/31 | i-040598873517ded7c | 35898 | Two mistakes: (1) ran `account_lookup` from `~`, which gave "No such file" because I hadn't changed into `/opt/balerica-bank`; (2) pasted `source venv/bin/activate` and the proof line together on one line, which ran together as `activatewhoami` and errored. Fixed both and finished the run. |

## Mistakes and what I learned

- **Run the proof line before starting uvicorn.** Uvicorn takes over the terminal, so if I forget the proof line, I have to press Ctrl+C, run it, and start uvicorn again.
- **Copy the DNS before terminating.** Once the instance is terminated, the public DNS is gone and the run can't be documented. That cost me a redo of Run 4.
- **Check the directory first.** The COBOL programs use relative paths (`./cobol/bin/...`), so they only work from `/opt/balerica-bank`.
- **Paste one command at a time.** Pasting two commands on one line can join them into a single command that doesn't exist.
- **Terminate every instance** to avoid charges. All 7 are terminated.

## COBOL practice

Done on Run 6 (i-0684b49eb0e369113) in `/opt/balerica-bank`. Transaction IDs used the `TXN-KP-` prefix.

**Return codes** (checked with `echo $?` after each program):

| Code | Meaning | Screenshot |
|---|---|---|
| 0 | Success. For example, `account_lookup 100001` returned Alice Johnson, ACTIVE, balance 5000.00 USD. | cobol_rc0.png |
| 4 | Account not found. For example, `account_lookup 999999` gave `ERROR=ACCOUNT NOT FOUND`. | cobol_rc4.png |
| 8 | Rejected by validation: `payment_post TXN-KP-0002 100001 0.00 USD INV-KP-0002` returned `STATUS=REJECTED` with `REASON=AMOUNT MUST BE GREATER THAN ZERO`. | cobol_rc8.png |
| 12 | File error: ran `account_lookup 100001` from `~` instead of `/opt/balerica-bank`, so it gave `ERROR=CANNOT OPEN data/accounts.dat` with `FILE-STATUS=35` (file not found), because the program looks for `data/` relative to the current directory. | cobol_rc12.png |

**Ledger decode** (`cat data/payments.dat`): each record is fixed-width with no separators. A line such as
`TXN0001  100001 0000012550 USD POSTED  INV-1001`
breaks down into the transaction ID, the account (100001), the amount in cents with no decimal point (0000012550 = 125.50), the currency (USD), the status (POSTED), and the invoice reference (INV-1001). See cobol_ledger_decode.png.

**Observation:** after posting a payment, the account balance was still **5000.00**. `payment_post` writes a record to the payments file, but it doesn't update the account balance.

## Git

Cloned the homework repo `github.com/kennethmphillips0206-byte/SEIR-Foundations-Homework`. See git_clone.png.
