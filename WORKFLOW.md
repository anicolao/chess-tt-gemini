# Project Workflow

All contributors (including AI agents) must adhere to the following workflow when working on `chess-tt-gemini`. This workflow is based on established standards from our reference projects (`food`, `chess-clock`).

## 1. Design First
- **Mandatory Design Artifacts**: Before any implementation, a design document (e.g., `MVP_DESIGN.md` or a new file in a `docs/` directory) must be committed.
- **Iterative Updates**: As the implementation evolves, update the design document or add supplementary documentation (e.g., `IMPLEMENTATION_PLAN.md`, `WALKTHROUGH.md`) to reflect the current state and decisions.

## 2. Branching & PRs
- **Feature Branches**: All work must be done in feature branches (e.g., `feature/move-validation`, `fix/clock-sync`).
- **PR Descriptions (Hard Requirement)**: 
  - Pull Request descriptions MUST include the **original User Prompt(s)** and any relevant **User Comments** verbatim.
  - **VERBATIM**: Copy the text exactly as written. Do not summarize or edit.
  - **ENTIRETY**: Include the full text of the prompt to ensure complete context in the git history.
- **Small PRs**: Favor small, incremental PRs over monolithic changes.

## 3. Testing Standards
- **Zero Tolerance for Regression**: All tests must pass before merging.
- **Unit Testing**: Core logic (e.g., chess rules, timer logic) must be covered by `vitest`.
- **E2E Testing**: User journeys (e.g., "Player A moves and Player B's clock starts") must be covered by `playwright`.
- **CI Consistency**: Tests must pass with `CI=1` to ensure non-interactive execution.

## 4. Technical Quality
- **Idiomatic Code**: Follow established patterns in the codebase.
- **Minimal Dependencies**: Use built-in Svelte/SvelteKit features where possible.
- **Mobile/Touch First**: Since this is a tabletop app, all UI must be designed for touch interaction first.

---
*Failure to follow these workflow requirements will result in rejected PRs.*
