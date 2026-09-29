# SE5-Lab2 Refactoring — showDentistProfile()

## What this repo demonstrates
The function `showDentistProfile()` from `book-appointment.php` (patient module) is
refactored to separate three responsibilities that were mixed in one function:
1. Checking whether a schedule row is a working day
2. Building the weekly schedule HTML table
3. Building the dentist profile HTML

## How to run
1. Open `index.html` in any modern browser (Chrome, Firefox, Edge).
2. Click one of the four test-case buttons.
3. Click **Show Profile**.
4. Compare the modal contents against `tests/baseline.md`.

No server, database, or PHP is required — this is a self-contained harness
that isolates the refactored function.

## Branches
- `main` — baseline code (before refactor)
- `refactor/extract-profile-builders` — refactored code

## Test cases
| # | Input | Expected modal output |
|---|-------|----------------------|
| 1 | Full dentist data + Mon/Tue/Wed schedule | All fields shown; Mon + Tue show `9:00 AM - 5:00 PM`; Wed shows `Not available` |
| 2 | Missing optional fields | `General Dentist`, all other fields `N/A`; every day `Not available` |
| 3 | Only Friday available | Only Friday shows hours; other 6 days `Not available` |
| 4 | EDGE: schedule row with `00:00:00` times but `is_available=1` | Monday shows `Not available` (times treated as invalid) |