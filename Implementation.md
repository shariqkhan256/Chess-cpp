# Key Features - Chess Game

## 1. Custom Console Graphics & Coordinate Board
- **Description**: Displays a stylized checkerboard interface directly in the standard command line without graphic library dependencies.
- **Technical Implementation**: Implemented coordinates printing via nested loops using standard character `219` (block) for cell borders. Employs direct cursor positioning:
  ```cpp
  void gotoRowCol(int rpos, int cpos) {
      COORD scrn;
      HANDLE hOutput = GetStdHandle(STD_OUTPUT_HANDLE);
      scrn.X = cpos;
      scrn.Y = rpos;
      SetConsoleCursorPosition(hOutput, scrn);
  }
  ```
- **Challenges Overcome**: Solved screen flickering during updates by rewriting only changed cells and writing board labels directly to specified coordinates instead of using `system("cls")` repeatedly.

---

## 2. Stateful Save/Load Engine
- **Description**: Lets the user close the game at any point and resume from their exact board layout and current active turn later.
- **Technical Implementation**: File streams (`ifstream`/`ofstream`) dump the 64-char array and turn boolean into local text files:
  - `board.txt`: Flat record of the board layout, replacing empty spaces `' '` with underscores `'_'` to prevent space-parsing issues during line reading.
  - `turn.txt`: Holds a `0` or `1` state.
- **Challenges Overcome**: Solved white-space issues in standard `cin >>` file reads by mapping spaces to `_` before file output and converting back to `' '` on load.

---

## 3. Strict Move Constraints Checker
- **Description**: Validates that all pieces conform to real chess movement constraints and catches path blocking.
- **Technical Implementation**:
  - **Pawn**: Checked for initial double-step ranges (`score < 18 && score > 7` for Player 1, `score < 56 && score > 47` for Player 2) and diagonal capture rules if target cell is not empty.
  - **Path Clear validation**: Loops incrementally with `++i` (for rows) or `i += dim` (for columns) or `i += dim + 1` (for diagonals) to inspect intermediary elements.
- **Challenges Overcome**: Corrected bugs where players could slide pieces through blockades by introducing custom boundary-range check iterations prior to updates.
