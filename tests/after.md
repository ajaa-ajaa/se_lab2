# After-refactor results (refactor/extract-profile-builders branch)

Commit: <paste hash>
File: index.html
Functions: isWorkingDay(), buildScheduleTableHtml(), buildDentistProfileHtml(), showDentistProfile()

| # | Input | Expected | Observed |
|---|-------|----------|----------|
| 1 | Full dentist data | Same as baseline | ✅ identical |
| 2 | Missing optional fields | Same as baseline | ✅ identical |
| 3 | Partial schedule | Same as baseline | ✅ identical |
| 4 | EDGE: 00:00:00 times | Same as baseline | ✅ identical |

Diff inspected with `git diff main refactor/extract-profile-builders` — only the
showDentistProfile() function block changed; HTML, CSS, test harness untouched.