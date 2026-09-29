# Baseline results (main branch)

Commit: <paste `git rev-parse HEAD` here>
File: index.html
Function: showDentistProfile()

| # | Input | Expected | Observed |
|---|-------|----------|----------|
| 1 | Full dentist data | All fields, Mon/Tue 9:00 AM–5:00 PM, Wed Not available | ✅ matches |
| 2 | Missing optional fields | General Dentist, N/A everywhere, all days Not available | ✅ matches |
| 3 | Partial schedule (Fri only) | Only Friday shows hours | ✅ matches |
| 4 | EDGE: 00:00:00 times, is_available=1 | Monday Not available | ✅ matches |