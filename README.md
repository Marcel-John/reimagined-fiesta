# Planet Conquest

A strategic planet-conquering game developed using the **Effekt** programming language.

---

## 🛠 Installation & Setup

1.  **Install Effekt:** Ensure you have the [Effekt language](https://effekt-lang.org/) installed on your system.
2.  **Clone the Repository:**
    ```bash
    git clone [https://https://github.com/Marcel-John/reimagined-fiesta.git](https://https://github.com/Marcel-John/reimagined-fiesta.git)
    cd planet-conquest
    ```
3.  **Run the Game:**
    ```bash
    effekt main.effekt
    ```

---

## General Rules

The objective is simple: control every planet. A faction loses the game once they no longer control any planets.

* **Selection:** Select one of your planets, then select a target planet.
* **Deployment:** Upon selection, **50% of your ships** from the source planet are sent to the target.
* **Combat:** When ships of rivaling factions occupy the same planet, they battle until only one faction remains.
* **Conquest:** If there are no defending ships left on a planet, control switches to the attacking faction.

---

## Game Modes

| Mode | Description |
| :--- | :--- |
| **Normal** | You against the AI. |
| **PvP** | Two players face off locally. |
| **AI vs AI** | Watch two AI factions fight each other. |

> [!IMPORTANT]
> **Turn Timer:** During the game, you have exactly **2 seconds** to perform an input, or your turn will be skipped. There is no timer in the main menu.

---

## Menus & Commands

Interaction is handled via the console. Type your command and press `Enter`.

### General Commands
* **[ID]** – Type the ID of a planet to select it.
* **q** – Quit the game.
* **r** – Return to the main menu.

### Navigation
* Follow the specific prompts shown in the console to navigate the main menu.
* Context-specific commands will be displayed in the console during gameplay.



# Effekt Template

> [!WARNING]
> This is a work-in-progress, feel free to contribute!

This template provides a starting point for Effekt projects.

## Table of contents

- [First steps](#first-steps)
- [Useful commands](#useful-commands)
  - [Effekt commands](#effekt-commands)
  - [Nix-related commands](#nix-related-commands)
- [Example projects](#example-projects-using-this-template)
- [Repository structure](#repository-structure)
- [CI](#ci)

---

## First steps

After using this template, follow these steps to set up your project:

1. Set up your development environment:
   - Clone this repository locally.
   - Open it in VSCode.
   - Install the Effekt VSCode extension offered in the pop-up in the bottom right.

2. Customize the project:
   - Open `flake.nix` and update the project name and other relevant values (follow the comments).
   - Push your `flake.nix` file after the changes and see if the CI agrees.

3. Set-up auto-update CI in order to get weekly PRs on Tuesday which update the Effekt version in CI:
   - Go to Settings -> Actions -> General:
     - and set "Workflow permissions" to "Read and write permissions"
     - and check "Allow GitHub Actions to create and approve pull requests"    
   - See the [CI](#ci) section for more details

3. Replace this `README` with your own!

## Useful commands

### Effekt commands

Run the main file:
```sh
effekt src/main.effekt
```
This (like many other Effekt commands) uses the JavaScript backend by default.
To use a different backend, add the `--backend <backend>` flag.

Run the tests:
```sh
effekt src/test.effekt
```

Open the REPL:
```sh
effekt
```

Build the project:
```sh
effekt --build src/main.effekt
```
This builds the project into the `out/` directory, creating a runnable file `out/main`.

To see all available options and backends, run:
```sh
effekt --help
```

### Nix-related commands

While Nix installation is optional, it provides several benefits:

Update dependencies (also runs automatically in CI):
```sh
nix flake update
```

Open a shell with all necessary dependencies:
```sh
nix develop
```

Run the main entry point:
```sh
nix run
```

Build the project (output in `result/bin/`):
```sh
nix build
```

## Example projects using this template

- [see the `effekt-community` GitHub organization](https://github.com/effekt-community/)
- This very project!

## Repository structure

- `.github/workflows/*.yml`: Contains the [CI](#ci) definitions
- `src/`: Contains the source code
  - `main.effekt`: Main entry point
  - `test.effekt`: Entry point for tests
  - `lib.effekt`: Library code imported by `main` and `test`
- `flake.nix`: Package configuration in a Nix flake
- `flake.lock`: Auto-generated lockfile for dependencies
- `LICENSE`: Project license
- `README`: This README file

## CI

Two GitHub Actions are set up:

1. `flake-check`:
   - Checks the `flake.nix` file, builds and tests the project
   - Runs on demand, on `main`, and on PRs
   - To run custom commands, add a step using:
     - `nix run -- <ARGS>` to run the main entry point with the given arguments
     - `nix develop -c '<bash command to run>'` to run commands in the correct environment

2. `update-flake-lock`:
   - Updates package versions in `flake.nix`
   - Runs on demand and weekly (Tuesdays at 00:00 UTC)
