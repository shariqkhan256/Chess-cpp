# Lessons Learned - Chess Game

## Key Takeaways

1. **Flat Indexing over 2D Arrays**:
   - Working with a 1D array (`char B[64]`) simplified file reading and writing operations since the board can be outputted as a single continuous string.
   - However, it required writing custom index mapping logic (`two_oned()`) which was slightly harder to debug initially than simple nested index lookups `B[r][c]`.

2. **File Stream Processing**:
   - Encountered white-space skip errors when reading empty spaces `' '` from file stream input.
   - Resolved it by serializing space blocks as underscores `'_'` in the text file and replacing them with `' '` back in memory on loads.

3. **Rendering Optimizations**:
   - Frequent `system("cls")` calls created noticeable screen flickering.
   - Using specific terminal coordinates updating with `SetConsoleCursorPosition` bypassed standard buffer clears, leading to smooth frame transitions.

4. **Off-by-One Capture Issues**:
   - Initial piece scan bounds for checking clear paths (e.g. Bishop or Rook) had off-by-one errors that allowed clipping capture targets.
   - Refined scan boundaries (`small + 1` to `large`) to exclude the target landing square, permitting correct piece capturing.
