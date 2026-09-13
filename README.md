# Interactive Sudoku Generator & Game 🧩

An end-to-end Python implementation of a Sudoku puzzle generator and interactive terminal game. I built this project to demonstrate my understanding of algorithmic logic, particularly **Recursive Backtracking**, and how to handle 2D data structures in Python.

## Features
* **Backtracking Engine:** A core algorithm that efficiently searches the solution space of a 9x9 grid, validating constraints (rows, columns, subgrids) at every step.
* **Random Puzzle Generation:** Uses the `random` module to shuffle inputs, ensuring a unique, valid, and completely solvable Sudoku board is generated every single time.
* **Interactive Gameplay:** A continuous `while` loop that allows users to play the generated puzzle directly in the terminal, complete with an automated referee that prevents illegal moves.

## How to Play
Run the script in your terminal:
```bash
python sudoku_game.py
