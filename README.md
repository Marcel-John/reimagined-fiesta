# Planet Conquest

A strategic planet-conquering game developed using the **Effekt** programming language.

---

## Installation & Setup

1.  **Install Effekt:** Ensure you have the [Effekt language](https://effekt-lang.org/) installed on your system.
2.  **Clone the Repository:**
    ```bash
    git clone [https://https://github.com/Marcel-John/reimagined-fiesta](https://https://github.com/Marcel-John/reimagined-fiesta)
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
