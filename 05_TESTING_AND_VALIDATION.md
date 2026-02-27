# Testing & Validation Mandates

## 1. Mandatory Testing
- All backend code must pass the test suite (e.g., Pytest, Go tests) before merge.
- Add automated tests for every new feature or bug fix.
- Use mock fixtures to avoid network calls in unit tests.

## 2. Autonomous Bug Fixing
- When given a bug report: reproduce, diagnose, and fix.
- Don't ask for hand-holding; point at logs, errors, or failing tests to justify the fix.
- Ensure the fix addresses the root cause, not just the symptom.

## 3. Verification Protocol
- "Trust but verify" — use `run_shell_command` to execute tests and build commands.
- Check logs and side effects of changes (e.g., DB schema updates).
- Demonstrate correctness with empirical data or test output.

## 4. No Regressions
- Run existing test suites to ensure no regressions were introduced.
- If a fix is hacky, it's a regression in quality; aim for elegance.
