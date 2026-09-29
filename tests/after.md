# After Refactor Results

- **Filename:** index.html
- **Commit Identifier:** [PASTE YOUR REFACTOR BRANCH COMMIT HASH HERE]
- **Functions Changed:** Extracted `isWorkingDay()`, `buildScheduleTableHtml()`, and `buildDentistProfileHtml()`. `showDentistProfile()` now only orchestrates these helpers.

## Test Inputs and Observed Outputs

The same 4 test cases from the baseline were run manually by changing the `dentistData` and `schedules` variables and observing the modal.

| # | Input (Data in Code) | Expected Output (From Baseline) | Observed Output (After Refactor) | Matches Baseline? |
|---|---|---|---|---|
| 1 | **Full Data:** <br>Dentist: John Smith, Orthodontics, LIC123, 10 years, DMD, Smile Clinic, 123 Main St, 09171234567 <br>Schedule: Mon-Fri available, Sat-Sun unavailable | Modal shows all fields. Schedule table shows "9:00 AM - 5:00 PM" for Mon, Tue, Thu, Fri. Wed, Sat, Sun show "Not available". | Modal shows all fields. Schedule table shows "9:00 AM - 5:00 PM" for Mon, Tue, Thu, Fri. Wed, Sat, Sun show "Not available". | ✅ Yes |
| 2 | **Missing Optional Fields:** <br>Dentist: Jane Doe, all optional fields `null` <br>Schedule: Empty array | Modal shows "General Dentist" and "N/A" for missing fields. Schedule shows "Not available" for all 7 days. | Modal shows "General Dentist" and "N/A" for missing fields. Schedule shows "Not available" for all 7 days. | ✅ Yes |
| 3 | **Partial Schedule:** <br>Dentist: Bob Lee <br>Schedule: Only Friday (10:00 - 15:00) | Only Friday shows "10:00 AM - 3:00 PM". Other 6 days show "Not available". | Only Friday shows "10:00 AM - 3:00 PM". Other 6 days show "Not available". | ✅ Yes |
| 4 | **EDGE CASE:** <br>Schedule row: `{ day_of_week: "Monday", start_time: "00:00:00", end_time: "00:00:00", is_available: 1 }` | Monday shows "Not available" (despite `is_available=1`). | Monday shows "Not available" (despite `is_available=1`). | ✅ Yes |

## Diff Inspection
I ran `git diff main refactor/extract-profile-builders` and inspected the output. 
The only changes were within the `<script>` tag, specifically replacing the single `showDentistProfile()` function with the three new helper functions and the updated orchestrator. The HTML, CSS, test harness buttons, and mock data were untouched.
