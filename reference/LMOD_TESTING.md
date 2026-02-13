# LMOD_TESTING (Reference)

Minimal notes for running and updating Lmod regression tests.

Where tests live:
- Test directories are under rt/ (each test has a .tdesc definition).
- The test harness is typically invoked via the "t" helper.

Common workflow:
1) cd rt/<test_name>/
2) Run the test:
   - t .
3) Inspect results:
   - cat t1/*/results.csv
4) If output is correct but golden files need updating, follow your local Lmod practice:
   - update golden files in that rt/<test_name>/ directory (varies by test)

Useful notes:
- stdout often captures environment changes; stderr is user-facing output.
- Clean/sanitize steps normalize paths and system-specific noise before diffing.
