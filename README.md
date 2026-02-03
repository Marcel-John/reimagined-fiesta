# Project read me
- first install effekt
- run the main.effekt
- this opens the main menu
- here you can select the mode you want to play or quit
- their is a normal mode
- their is a pvp mode
- their is ai vs ai mode

# general rules are:
- player can select any planet
- when then selecting an other planet half of your ships go to the target
- when ships of two rivaling factions are on the same planet they battle
- when their are no ships of the deffending faction on the planet the control swiches
- once a faction controles no planets they lose the game

# game modes
- normal is you against the ai
- ai vs ai is two ais fight each other
- PvP two players aginst each other
- each player has 2 seconds to do their turn otherwis the next gets the turn



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
