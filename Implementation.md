# Implementation Details - Chess Game

## Development Phases

- **Phase 1: Board representation & mapping**: Set up the 1D 64-char array mapping. Designed the `two_oned()` formula to convert user-supplied 2D console positions to 1D index offsets.
- **Phase 2: Move Validation Core**: Programmed the math rules for pawn, knight, bishop, and rook. Implemented the collision checks scanning intermediate array slots for blocking pieces.
- **Phase 3: Graphics & Rendering**: Built out coordinate labels (1-8) and drew the game board bounds using Windows console handle functions.
- **Phase 4: Persistence Integration**: Integrated state serialization using `<fstream>` to auto-save matching turns. Developed the save/load menu system.

## Testing Strategy

- **Manual Unit Testing**:
  - Validated piece movement boundaries individually (e.g. testing if pawns can jump over pieces or if knights jump obstacles correctly).
  - Executed tests for edge-case actions like capturing pieces and boundary checks to avoid index-out-of-bounds exceptions.
- **State Persistence Test**:
  - Saved files under several board layouts, validated `board.txt` formatting, and confirmed clean deserialization.
