# E2E Testing Guide

This project uses [Playwright](https://playwright.dev/) for End-to-End testing. Our E2E tests are the primary source of truth for application correctness.

## 1. The Philosophy: "Zero-Pixel Tolerance"

We enforce a strict **Zero-Pixel Tolerance** policy for visual regression. Since visual state is the primary feedback mechanism for the user, any deviation is considered a bug.

*   **Software Rendering**: We use software rendering (browsers launched with specific flags) to ensure 100% consistent snapshots across CI and local environments.
*   **Determinism**: Tests must be perfectly deterministic. Random seeds must be fixed.

## 2. Test Structure

All E2E tests live in `tests/e2e/`. Each test case gets its own numbered directory.

```
tests/e2e/
├── helpers/                   # Shared utilities (TestStepHelper)
├── 001-basic-load/            # Scenario Directory
│   ├── 001-basic-load.spec.ts # Main test file
│   ├── README.md              # Auto-generated verification doc
│   └── screenshots/           # Committed baseline images
```

## 3. Strict Constraints

To ensure test reliability and speed:

-   **No arbitrary timeouts**: The maximum acceptable timeout for any condition is **2000ms**.
-   **No `waitForTimeout`**: Use of `page.waitForTimeout()` or `setTimeout` in tests is strictly prohibited. Always wait for specific UI states using `expect().toBeVisible()` or `waitForSelector`.
-   **Atomic Steps**: Use the `TestStepHelper` to encapsulate actions, verifications, and screenshot captures in a single `step()` call.

## 4. Playwright Configuration

-   **Browsers**: Tests run in Chromium by default.
-   **CI Environment**: Always run with `CI=1` to ensure non-interactive execution.
-   **Hardware Acceleration**: Disabled in CI to ensure consistent rendering.
