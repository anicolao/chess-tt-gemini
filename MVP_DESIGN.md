# MVP Design - Tabletop Chess (Gemini)

This document outlines the Minimum Viable Product (MVP) for `chess-tt-gemini`.

## Goals
1.  **Immersive Tabletop UI**: A full-screen, responsive chess board optimized for two players sitting opposite each other.
2.  **Move Validation & Logic**: Enforce legal moves (Stockfish or `chess.js`) and detect check/mate/stalemate.
3.  **Built-in Chess Clock**: Integrated, customizable timers for each player.
4.  **Local-Only Operation**: No server required; fully functional offline as a PWA.

## Architecture

### Tech Stack
-   **Framework**: SvelteKit (for fast, reactive UI).
-   **State Management**: **Redux (Event Sourcing Pattern)**.
    - All game moves and UI interactions are stored as an append-only log of events.
    - The current state is a projection of these events.
-   **Chess Logic**: `chess.js` (for move validation and game state).
-   **Rendering**: SVG or HTML/CSS for the board (ensuring sharpness on large screens).
-   **Deployment**: Static Adapter (GitHub Pages).

### Component Structure
- `Board`: The central 8x8 grid, driven by the current state projection.
- `Piece`: Individual pieces, dispatching actions to the Redux store.
- `PlayerDashboard`: Mirrored controls (one at the top, one at the bottom).
- `GameController`: Coordinates the Event Sourcing flow, persistence, and synchronization.

## User Stories

### Gameplay
-   **US-001**: As a player, I want to see the board centered on the table so that both I and my opponent have a clear view.
-   **US-002**: As a player, I want to move a piece by dragging it or tapping the piece and then the destination so that I can choose my preferred interaction method.
-   **US-003**: As a player, I want the app to prevent me from making illegal moves so that we don't have to argue about the rules.
-   **US-004**: As a player, I want to see visual feedback for the last move made so that I can follow my opponent's action.

### Timing
-   **US-005**: As a player, I want a chess clock visible on my side of the table so that I can manage my remaining time.
-   **US-006**: As a player, I want to start/stop the clock with a large, easy-to-hit button so that I don't fumble after making a move.
-   **US-007**: As a player, I want to configure the time control (e.g., 5 min, 10 min, or Blitz) before starting a game.

### UX/UI
-   **US-008**: As a player, I want labels (like player names or clock info) on the "top" side of the table to be inverted (rotated 180 degrees) so that my opponent can read them easily from their position.
-   **US-009**: As a player, I want to install this as a PWA on my tablet/table so that I can play without a browser UI in full-screen mode.
-   **US-010**: As a player, I want to reset the game to the starting position quickly so that we can play another round.

## Testing Strategy (Hard Requirements)
Following the standards from `food` and `chess-clock`:

1.  **Unit Tests**: Use `vitest` for core game logic (move validation, clock decrementing).
2.  **E2E Tests**: Use `playwright` for critical user journeys (starting a game, making a move, clock running out).
3.  **CI Validation**: All tests must pass in CI (`CI=1`) before merging.
4.  **Manual Testing**: Verify touch interactions on actual large-format screens.
