# C++ Console Chess Game

*Status: VERIFIED*  
*Period: Dec 2023 - Jan 2024*  
*Role: Sole Developer*  

## Tagline
A lightweight, classic C++ console-based Chess game featuring custom grid rendering, full move validation, and game state persistence.

## Overview
This project is an interactive Chess game built entirely in C++ for the command-line interface. It implements object-oriented-like procedural logic to represent the board state, handle two-player turn-based movement, and validate moves for all standard chess pieces. It also includes game-saving functionality using file-stream handling, allowing players to resume their matches at any time.

---

## 🎮 Game Controls & Interface

### Main Menu
Upon starting, players are presented with a styled ASCII text interface:
- **Press (1)**: Start a New Game (initializes board).
- **Press (2)**: Load Game (restores board state from `board.txt` and turn state from `turn.txt`).
- **Alt + F4**: Quit.

### How to Play
During play, the console prompts the active player for coordinate inputs:
1. **Select Piece**: Enter the row (1-8) and column (1-8) of the piece you want to move.
2. **Move Destination**: Enter the target row (1-8) and column (1-8) where you want to place the piece.
3. If the move is invalid under chess rules or path collision is detected, the program will recursively ask for a valid move.

---

## ⚡ Core Features

- **Full Move Validation**: Custom rule checking algorithms for:
  - **Pawn (`P`/`p`)**: Supports single-forward step, double-forward step on start, diagonal capturing, and turn-based constraints.
  - **Rook (`R`/`r`)**: Restricts movement to horizontal/vertical axes and verifies that path is clear of intervening pieces.
  - **Knight (`N`/`n`)**: Allows L-shaped moves (`+6`, `+10`, `+15`, `+17` index shifts) and jumping over other pieces.
  - **Bishop (`B`/`b`)**: Diagonal axis check and clear-path check.
  - **Queen (`Q`/`q`)**: Combines Rook, Bishop, and King movement validation rules.
  - **King (`K`/`k`)**: Restricts movement to exactly 1 adjacent square in any direction.
- **Custom Console Rendering**: Leverages Windows API console handling (`gotoRowCol`, `SetConsoleCursorPosition`) with block characters (`219`) to draw a clean coordinate-mapped chess grid.
- **Save/Load State Persistence**: 
  - Automatically saves the game board state to `board.txt` and the active turn state to `turn.txt` after every valid move.
  - Re-load previous game states seamlessly from the main menu.
- **Win Condition Check**: Scans the board state for the presence of both kings. If a player's king is captured, the game terminates and declares the victor.

---

## 🛠️ Architecture & Code Map

The game uses a **1D 64-character array representation** of the 8x8 grid coordinates for efficiency, translating coordinate values using standard 2D-to-1D mapping formulas.

- `two_oned()`: Translates row/col user inputs (1-8) to the corresponding 0-63 array index: `index = (row-1) * 8 + (col-1)`.
- `in_it()`: Populates the array with default chess pieces (uppercase representing Player 1, lowercase representing Player 2).
- `print_board()` & `print_array()`: Standard rendering routine utilizing cursor positions for flickering-free screen updates.
- `wincheck()`: Evaluates the victory state by verifying the presence of 'K' and 'k' characters.

---

## 🚀 How to Compile & Run

1. Open your terminal or IDE (VS Code, Visual Studio, or Dev-C++).
2. Ensure you are on a **Windows platform** (the game uses `windows.h` and `<conio.h>` for screen control).
3. Compile using a standard C++ compiler (G++):
   ```bash
   g++ -o ChessGame main.cpp
   ```
4. Run the compiled executable:
   ```bash
   ./ChessGame
   ```
