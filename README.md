# 🧱 Tetris — C++ OOP Edition

A recreation of the classic **Tetris game built in C++ using Object-Oriented Programming and raylib**.

The project applies core OOP principles to game development by separating the game board, Tetromino blocks, positions, colors, and overall game logic into independent classes and modules.

Built as an OOP project using **C++, raylib, and Visual Studio**.

---

## 🎮 About the Project

Tetris is a tile-matching puzzle game in which different shaped blocks, known as **Tetrominoes**, fall onto a grid.

The player positions and rotates the falling pieces to create complete horizontal rows.

This project recreates the core Tetris experience while focusing on a clean **object-oriented architecture** rather than placing the entire game inside a single source file.

```text
                TETRIS
        C++ • OOP • raylib

        ┌────────────────────┐
        │ . . . . . . . . . │
        │ . . . . █ . . . . │
        │ . . . █ █ █ . . . │
        │ . . . . . . . . . │
        │ . . . . . . . . . │
        │ . . . . . . . . . │
        │ █ █ . . . . . . . │
        │ █ █ █ █ . . █ █ . │
        │ █ █ █ █ █ █ █ █ . │
        └────────────────────┘
```

---

## ✨ Features

- 🧱 Classic Tetris-style gameplay
- 🎮 Keyboard-controlled blocks
- 🔄 Tetromino rotation
- ⬅️ ➡️ Horizontal block movement
- ⬇️ Falling block mechanics
- 🧩 Multiple Tetromino shapes
- 📦 Grid-based game board
- 🎨 Colored blocks using raylib
- 🧠 Object-Oriented Programming architecture
- ⚡ Real-time game loop
- 🖥️ Graphical rendering with raylib
- 🧹 Row-clearing game mechanics
- 💥 Collision and boundary handling

---

# 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| **C++** | Core programming language |
| **raylib** | Graphics, rendering, input, and game window |
| **OOP** | Game architecture and code organization |
| **Visual Studio** | Development environment |
| **C++ Header/Source Files** | Modular project structure |

---

# 🧠 Object-Oriented Design

One of the main goals of the project is to organize the game using **classes and objects**.

Instead of implementing everything inside `main.cpp`, responsibilities are divided between different components.

```text
                 ┌──────────────┐
                 │     Game     │
                 └──────┬───────┘
                        │
             ┌──────────┴───────────┐
             │                      │
             ▼                      ▼
        ┌─────────┐            ┌─────────┐
        │  Grid   │            │  Block  │
        └─────────┘            └────┬────┘
                                    │
                              Tetrominoes
                                    │
                                    ▼
                              ┌──────────┐
                              │ Position │
                              └──────────┘
```

This makes the project easier to understand, debug, maintain, and extend.

---

# 📁 Project Structure

```text
TETRIS-final/
│
├── main.cpp
│
├── game.cpp
├── game.h
│
├── grid.cpp
├── grid.h
│
├── block.cpp
├── block.h
│
├── blocks.cpp
│
├── position.cpp
├── position.h
│
├── colors.cpp
├── colors.h
│
├── Projectoop.sln
├── Projectoop.vcxproj
├── Projectoop.vcxproj.filters
└── README.md
```

---

# 🧩 Project Components

## 🎮 `main.cpp`

Acts as the entry point of the application.

It initializes the game environment and runs the main game loop where the application continuously:

```text
Input
  ↓
Update Game
  ↓
Draw Game
  ↓
Repeat
```

raylib handles the graphical window and frame-based execution.

---

## 🎯 `game.cpp` / `game.h`

The `Game` component acts as the central controller for Tetris.

It coordinates the other parts of the application, including the grid and blocks.

Conceptually:

```text
Game
 │
 ├── Game State
 ├── Current Block
 ├── Grid
 ├── Input
 ├── Movement
 ├── Collision Handling
 └── Rendering Coordination
```

Keeping the main gameplay logic inside its own class prevents `main.cpp` from becoming unnecessarily large.

---

## 🧱 `block.cpp` / `block.h`

Contains the general representation and behavior of a Tetris block.

A block can be represented using a collection of positions on the game grid.

Conceptually:

```text
Block
 │
 ├── Position
 ├── Rotation State
 ├── Cells
 ├── Movement
 └── Drawing
```

This provides a common representation for the different Tetromino shapes.

---

## 🧩 `blocks.cpp`

Contains the definitions of the different Tetris pieces.

Classic Tetris contains seven Tetromino shapes:

```text
I       O       T       S       Z       J       L

████    ██      ███      ██    ██      █       █
        ██       █      ██      ██     ███     ███
```

Each piece can use the common block behavior while defining its own arrangement of cells.

---

## 🟦 `grid.cpp` / `grid.h`

Responsible for the Tetris playing field.

The grid component handles the board on which Tetrominoes are placed.

Its responsibilities can include:

- Maintaining grid cells
- Drawing the board
- Detecting occupied cells
- Determining valid block positions
- Handling completed rows
- Managing placed blocks

Conceptually:

```text
Grid
│
├── Empty Cell
├── Empty Cell
├── Occupied Cell
├── Empty Cell
└── ...
```

This keeps board management separate from individual Tetromino behavior.

---

## 📍 `position.cpp` / `position.h`

Represents positions within the game grid.

A position can describe the row and column occupied by part of a Tetromino.

Conceptually:

```cpp
Position(row, column)
```

Using a dedicated position representation makes it easier for blocks to manage their individual cells.

---

## 🎨 `colors.cpp` / `colors.h`

Stores and manages the colors used by the game's graphical elements.

This separates visual configuration from gameplay logic and allows different Tetrominoes or interface components to use their own colors.

---

# 🧠 OOP Concepts Demonstrated

## 1. Classes & Objects

Major parts of the game are represented as separate objects.

For example:

```text
Game
Grid
Block
Position
```

Each component is responsible for a specific part of the application.

---

## 2. Encapsulation

Game data and behavior are grouped inside their corresponding classes.

Instead of directly manipulating every piece of data from `main.cpp`, operations are handled by the objects responsible for them.

For example:

```text
Grid  → manages board state
Block → manages block behavior
Game  → coordinates gameplay
```

---

## 3. Abstraction

Complex game behavior is divided into simpler interfaces.

The main game controller does not need to manually manage every individual grid cell whenever a block moves.

Instead, responsibilities are delegated to appropriate components.

```text
High-Level Game Logic
          ↓
     Game Objects
          ↓
 Low-Level Operations
```

---

## 4. Inheritance

The block architecture allows different Tetromino types to share common block behavior while defining their individual shapes and rotations.

Conceptually:

```text
                  Block
                    │
        ┌───────────┼───────────┐
        │           │           │
        ▼           ▼           ▼
     I Block     T Block     L Block
        │           │           │
        └─────── etc. ──────────┘
```

This reduces duplication between different block types.

---

## 5. Composition

The game is created by combining several objects.

Conceptually:

```cpp
Game
 ├── Grid
 ├── Block
 └── Position data
```

Rather than making one massive class responsible for everything, the final game emerges from multiple cooperating objects.

---

# 🎨 Why raylib?

**raylib** is a lightweight library designed for graphics and game development.

In this project, it provides the graphical foundation required for a real-time Tetris game, including:

- Creating the game window
- Drawing shapes
- Rendering colors
- Detecting keyboard input
- Managing frame timing
- Running a real-time graphical application

This allows the C++ code to focus on the actual **game mechanics and OOP architecture**.

---

# 🔄 Game Flow

The general execution flow is:

```text
             Start Program
                   │
                   ▼
          Initialize raylib
                   │
                   ▼
             Create Game
                   │
                   ▼
        ┌──── Main Game Loop ────┐
        │                        │
        │   Read Player Input    │
        │           ↓            │
        │    Update Game State   │
        │           ↓            │
        │    Update Tetromino    │
        │           ↓            │
        │   Check Grid / Rows    │
        │           ↓            │
        │       Draw Frame       │
        │                        │
        └───────────┬────────────┘
                    │
                    ▼
                Game Ends
                    │
                    ▼
              Close Window
```

---

# 🎯 Core Game Logic

A typical falling block follows a lifecycle similar to:

```text
Create Tetromino
       │
       ▼
Block Falls
       │
       ├──── Player Moves Block
       │
       ├──── Player Rotates Block
       │
       ▼
Check Valid Position
       │
       ▼
Block Reaches Bottom / Another Block
       │
       ▼
Lock Block Into Grid
       │
       ▼
Check Completed Rows
       │
       ▼
Generate Next Block
       │
       └──────────────► Repeat
```

---

# 🚀 Running the Project

## Requirements

Before building the game, make sure you have:

- Windows
- C++ compiler
- Microsoft Visual Studio
- raylib installed and configured

---

## Visual Studio

The repository contains:

```text
Projectoop.sln
Projectoop.vcxproj
```

so the project can be opened directly in Visual Studio.

### Step 1

Clone the repository:

```bash
git clone https://github.com/4aleeza/TETRIS-final.git
```

### Step 2

Navigate into the project:

```bash
cd TETRIS-final
```

### Step 3

Open:

```text
Projectoop.sln
```

in Visual Studio.

### Step 4

Make sure **raylib is correctly configured** for the project.

### Step 5

Build and run the application.

---

# 📚 What I Learned

Building this project provided practical experience with:

- Object-Oriented Programming in C++
- Designing classes with separate responsibilities
- Header and implementation files
- Inheritance
- Encapsulation
- Abstraction
- Composition
- Game loops
- Real-time keyboard input
- 2D grid systems
- Collision detection
- Game state management
- Graphical rendering
- Working with raylib
- Structuring a larger C++ project

---

# 🔮 Possible Improvements

Future versions of the project could include:

- 🏆 Persistent high-score system
- 🎵 Music and sound effects
- ⏸️ Pause menu
- 🎚️ Difficulty levels
- ⚡ Increasing speed as the player progresses
- 👻 Ghost piece
- 📦 Hold-piece system
- 🔜 Next-piece preview
- 🎨 Improved UI and animations
- 🏅 Leaderboard
- 💾 Save/load functionality
- 🎮 Controller support

---

# 🎓 Project Purpose

This project was created to apply **Object-Oriented Programming concepts to a complete graphical application**.

Tetris provides a useful OOP problem because different parts of the game naturally have different responsibilities:

```text
Block     → Tetromino behavior
Grid      → Game board
Position  → Cell coordinates
Game      → Overall game logic
Colors    → Visual configuration
raylib    → Rendering and input
```

Separating these responsibilities produces a more modular and maintainable implementation than putting the complete game inside a single source file.

---

# 📌 Summary

**Tetris — C++ OOP Edition** is a graphical implementation of the classic Tetris game developed using **C++ and raylib**.

The project combines:

```text
        C++
         +
        OOP
         +
      raylib
         ↓
   Tetris Game
```

It demonstrates how fundamental OOP concepts can be applied to real-time game development while working with graphics, keyboard input, grids, collision logic, Tetrominoes, and game-state management.

---

## 👩‍💻 Author

**Aleeza**

GitHub: `@4aleeza`

Repository: `4aleeza/TETRIS-final`
