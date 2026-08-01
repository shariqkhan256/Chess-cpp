# Technology Stack - Chess Game

## Core Stack

- **Language**: C++ (C++11 standard elements).
- **Console API**: Windows SDK API (`windows.h`) for hardware device output configuration and cursor coordinates control.
- **I/O Library**: standard C++ `<fstream>` for game state persistence and `<conio.h>` / `<iostream>` for terminal interaction.

## Rationale

- **C++**: Selected for high-performance execution, low memory overhead, and straightforward pointer/array manipulation which is optimal for array-based board representations.
- **Windows Console Handlers**: Used standard console output mapping rather than graphical libraries like SFML or SDL to build a lightweight, dependency-free application running directly in standard command shell environments.
- **Text-based Serialization**: Using basic text dump serialization for saving game states is highly readable, lightweight, and easy to parse, eliminating the need for database integration for a local console application.
