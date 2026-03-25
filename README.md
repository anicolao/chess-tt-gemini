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

## Workflow & Testing (Hard Requirements)
Following the standards from our reference repositories (`food`, `chess-clock`):

### 1. Design First
Every major feature must have a design artifact committed before implementation. See the [MVP Design](./MVP_DESIGN.md) for the initial plan.

### 2. Testing
-   **Unit Tests**: All core logic must be covered by `vitest`.
-   **E2E Tests**: Critical user journeys must be covered by `playwright`.
-   **CI**: Tests must pass with `CI=1` before merging.

### 3. Branches & PRs
-   All work happens in feature branches.
-   Pull Request descriptions must include the **original User Prompt(s)** and any relevant comments verbatim.

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
