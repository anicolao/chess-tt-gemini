# chess-tt-gemini

A tabletop-focused chess game for large touchscreen surfaces. Built as a Progressive Web App (PWA) with SvelteKit.

## Vision
The goal is to create a digital chess experience that feels as tactile and social as a physical board. Optimized for face-to-face play on large horizontal displays (touchscreen tables). See [VISION.md](./VISION.md) for more details.

## Key Features
-   **Tabletop Mode**: Mirrored UI for two-player, face-to-face seating.
-   **Integrated Chess Clock**: Customizable timing controls on each side of the board.
-   **Move Validation**: Prevents illegal moves and detects game-ending states (Checkmate, Stalemate, etc.).
-   **PWA**: Installable for a full-screen, offline-capable experience.
-   **No Backend**: Purely client-side logic; data stays on the device.

## Tech Stack
-   **UI**: SvelteKit
-   **Chess Logic**: `chess.js`
-   **Styling**: Vanilla CSS (focused on high-resolution responsiveness)
-   **Testing**: Vitest (Unit), Playwright (E2E)
-   **Hosting**: GitHub Pages

## Documentation
- [VISION.md](./VISION.md) - High-level goals and target environment.
- [MVP_DESIGN.md](./MVP_DESIGN.md) - Technical architecture and user stories.
- [WORKFLOW.md](./WORKFLOW.md) - **Mandatory** development standards and hard requirements.
- [E2E_GUIDE.md](./E2E_GUIDE.md) - Playwright testing structure and strict constraints.
- [LICENSE](./LICENSE) - GNU General Public License v3.

## Workflow & Testing (Hard Requirements)
Following the standards from our reference repositories (`food`, `chess-clock`):

### 1. Design First
Every major feature must have a design artifact committed before implementation. See the [MVP Design](./MVP_DESIGN.md) for the initial plan.

### 2. Testing
- **Unit Tests**: All core logic must be covered by `vitest`.
- **E2E Tests**: Critical user journeys must be covered by `playwright`. See [E2E_GUIDE.md](./E2E_GUIDE.md).
- **CI**: Tests must pass with `CI=1` before merging.
- **Constraints**: No timeouts > 2000ms, no `waitForTimeout`.

### 3. Branches & PRs
All work must be done in feature branches. Pull Request descriptions **MUST** include the **original User Prompt(s)** verbatim to preserve history and context.

See [WORKFLOW.md](./WORKFLOW.md) for more detailed requirements.

## Tech Stack
-   **UI**: SvelteKit
-   **State Management**: Redux (Event Sourcing Pattern)
-   **Chess Logic**: `chess.js`
-   **Styling**: Vanilla CSS (focused on high-resolution responsiveness)
-   **Testing**: Vitest (Unit), Playwright (E2E)
-   **Hosting**: GitHub Pages (with per-PR preview deployments)
## Getting Started

### Development
```bash
# Install dependencies
npm install

# Run development server
npm run dev

# Run tests
npm test
npm run test:e2e
```

### Building
```bash
# Build for production
npm run build
```

---
*Created as part of the Gemini CLI research and development project.*
