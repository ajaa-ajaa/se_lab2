# Baseline Results

- **Filename:** index.html
- **Commit Identifier:** [PASTE YOUR COMMIT HASH HERE]
- **Function Name:** showDentistProfile()

## Current Behavior
Opening `index.html` in any browser and clicking the "View Profile" button opens a floating modal (Bootstrap modal) that displays the dentist's personal information, clinic information, and weekly schedule.

## Concrete Maintenance Problem
The `showDentistProfile()` function mixes three responsibilities into one block of code:
1. Checking the schedule availability.
2. Building the weekly schedule HTML table.
3. Building the dentist profile HTML.

Because these are mixed, modifying how schedule availability is checked forces a developer to read and edit the same function that handles the profile layout. The logic is also duplicated elsewhere in the original system, making future changes risky.

## Test Inputs and Expected Outputs

The following test cases were run by manually changing the `dentistData` and `schedules` variables in the code and observing the modal.

| # | Input (Data in Code) | Expected Output (Modal Display) |
|---|---|---|
| 1 | **Full Data:** <br>Dentist: John Smith, Orthodontics, LIC123, 10 years, DMD, Smile Clinic, 123 Main St, 09171234567 <br>Schedule: Mon-Fri available, Sat-Sun unavailable | Modal shows all fields. Schedule table shows "9:00 AM - 5:00 PM" for Mon, Tue, Thu, Fri. Wednesday, Saturday, and Sunday show "Not available". |
| 2 | **Missing Optional Fields:** <br>Dentist: Jane Doe, specialization=null, license=null, experience=null, education=null, clinic=null, address=null, phone=null <br>Schedule: Empty array | Modal shows "General Dentist" for specialization, and "N/A" for all other missing fields. The schedule table shows "Not available" for all 7 days. |
| 3 | **Partial Schedule:** <br>Dentist: Bob Lee, General, LIC999, 5 years, DDS, City Dental, 456 Oak Ave, 09181112222 <br>Schedule: Only Friday (10:00 - 15:00) | Modal shows all fields. The schedule table shows hours only for Friday ("10:00 AM - 3:00 PM"). All other 6 days show "Not available". |
| 4 | **EDGE CASE:** <br>Schedule row: `{ day_of_week: "Monday", start_time: "00:00:00", end_time: "00:00:00", is_available: 1 }` | Monday shows "Not available" (even though `is_available` is 1, the `00:00:00` times are treated as invalid/empty by the function). |
