# PMP Practice Exam Simulator - Exam 3

Static web app (no build step) simulating a full PMP practice exam.

- **Login page** (username `pmpractice03`), then an **instructions page**, then the exam.
- **180 questions**: 75 People, 75 Process, 30 Business Environment (single-answer, options shuffled).
- **NEXT** button plus Previous, flagging and a question navigator.
- **4-hour exam timer** and one **20-minute break** (exam clock pauses during the break).
- Auto-submit at zero, score + full answer review, progress saved in the browser.

## Run / deploy
Open `index.html` locally, or push to GitHub and enable Settings -> Pages -> Deploy from branch (`main`, root).

## Answer key - please review
The `180 PMP practice 2` sheet in the source workbook has **no answer key**. The key in `tools/answer_key.txt` was drafted separately
(PMI-style reasoning, with the calculation questions worked out by hand). Review it, fix anything you disagree with, then regenerate:
```bash
pip install openpyxl
python tools/convert_xlsx.py PMP_practice_Q_A.xlsx questions.js
```
`answer_key.txt` uses the ORIGINAL option order from the sheet; the converter shuffles options and re-letters them.
Question 11 (Tuckman model after a team change) is genuinely debatable: the key says Forming, but some sources say Storming.

## Security note
Static hosting means the login is only a client-side gate (credentials are SHA-256 hashes) and the answers ship in `questions.js`.
Use a private repo or a backend for real access control.
