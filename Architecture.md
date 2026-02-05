# Architecture - Planet Conquest

This document describes the high-level architecture of the game and the responsibilities of each module.

## Code Map

### gamesate.effekt
* **Purpose:** Core effect definitions.
* Contains effects used to maintain and manipulate the global game state.
* Includes specialized effects designed to "break out" multiple loops (e.g., exiting a game session).

### input.effekt
* **Purpose:** Handles synchronous and asynchronous user input.
* **`getInput`:** A standard blocking function using the `ask` effect and `readline` for menu navigation (no timeout).
* **`getInputWithTimeout`:** Utilizes JavaScript `race` condition to implement an input timeout.
* **Timeout:** Currently hardcoded to `2000ms` (2 seconds). If no input is received, a default value is returned to skip the turn.

### ai.effekt
* **Purpose:** The "brain" of the computer-controlled factions.
* Defines data structures for move representation.
* **Logic:** Iterates through possible moves and evaluates them using a **heuristic scoring system** to determine the optimal action.

### logic.effekt
* **Purpose:** Pure game mechanics and state transitions.
* Contains functions for initializing the game (e.g., `initialGameState`).
* **Core Mechanics:** Logic for ship movement, planet state updates, and win-condition verification.
* **Ownership:** Helper functions to determine planet occupancy and faction control.

### state.effekt
* **Purpose:** Data modeling and visualization.
* Defines the primary data structures for the **GameState** and **Planets**.
* Includes state helpers (e.g., identifying which player has the ship majority).
* **View Layer:** Contains the printing logic used to render the game and stats in the terminal.

### main.effekt
* **Purpose:** Main entry point and game flow control.
* **Effect Handling:** Functions as the central hub where all algebraic effects from other modules are handled and resolved.
* **Game Management:** Connects the menu system with the actual game modes, managing the sequence of turns and transitions.
* **User Interface:** Handles the main menu and directs the user to the selected game mode (Normal, PvP, AI vs AI).