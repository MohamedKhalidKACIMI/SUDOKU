"""
Interactive Sudoku Generator and Solver.
This script uses a backtracking algorithm to generate a unique, random Sudoku puzzle 
and allows the user to play it interactively in the terminal.
"""

import random

# Global list used to shuffle the numbers for random puzzle generation
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9]
random.shuffle(numbers)

def create_empty_board():
    """Creates an empty 9x9 Sudoku grid filled with zeros."""
    board = []
    for _ in range(9):
        line = []
        for _ in range(9):
            line.append(0)
        board.append(line)
    return board

def is_valid(board, row, col, num):
    """
    Acts as the referee. Checks if placing 'num' at board[row][col] is legal 
    according to Sudoku rules (row, column, and 3x3 subgrid constraints).
    """
    # Check row
    for i in range(9):
        if board[row][i] == num:
            return False
            
    # Check column
    for i in range(9):
        if board[i][col] == num:
            return False
            
    # Check 3x3 box
    if row < 3:
        box_row = 0
    elif row < 6:
        box_row = 3
    else:
        box_row = 6
        
    if col < 3:
        box_col = 0
    elif col < 6:
        box_col = 3
    else:
        box_col = 6
        
    for i in range(box_row, box_row + 3):
        for j in range(box_col, box_col + 3):
            if board[i][j] == num:
                return False
                
    return True

def find_empty(board):
    """Finds the next empty cell (represented by 0) on the board."""
    for row in range(9):
        for col in range(9):
            if board[row][col] == 0:
                return (row, col)
    return None

def solve_sudoku(board):
    """
    The core backtracking algorithm. It recursively tries numbers 1-9 
    to completely solve the Sudoku board.
    """
    find = find_empty(board)
    if not find:
        return True
    row, col = find

    for num in numbers:
        if is_valid(board, row, col, num):
            board[row][col] = num
            if solve_sudoku(board):
                return True
            board[row][col] = 0 # Backtrack if the guess is wrong
            
    return False

def playeble_board(num_holes):
    """
    Generates a new puzzle by fully solving an empty board, 
    then randomly poking 'num_holes' holes (setting values to 0).
    """
    board = create_empty_board()
    solve_sudoku(board)

    holes_made = 0
    while holes_made < num_holes:
        row = random.randint(0, 8)
        col = random.randint(0, 8)
        if board[row][col] != 0:
            board[row][col] = 0
            holes_made += 1
            
    return board

def print_board(board):
    """Formats and prints the 9x9 board with borders for easy reading."""
    print("\n    0 1 2   3 4 5   6 7 8")
    print("  +-------+-------+-------+")
    for i in range(9):
        print(f"{i} | ", end="")
        for j in range(9):
            # Replace 0s with dots to make the empty spaces clearer
            val = "." if board[i][j] == 0 else str(board[i][j])
            print(val + " ", end="")
            if (j + 1) % 3 == 0:
                print("| ", end="")
        print()
        if (i + 1) % 3 == 0:
            print("  +-------+-------+-------+")

def play_sudoku(board):
    """The main game loop that allows a user to interact with the board."""
    print("\nWelcome to the Interactive Sudoku!")
    print("Enter '99' as the row to quit the game at any time.\n")
    
    while True:
        print_board(board)
        
        # 1. Ask the player for coordinates
        row = int(input("\nWhich row (0-8)? : "))
        if row == 99:
            print("Thanks for playing! Goodbye.")
            break
            
        col = int(input("Which column (0-8)? : "))
        num = int(input("Which number (1-9)? : "))
        
        # 2. Check if the cell is already filled
        if board[row][col] != 0:
            print("\n❌ This cell is already filled! Try again.")
            continue
            
        # 3. Use the referee function to check if the move is legal
        if is_valid(board, row, col, num):
            board[row][col] = num
            print("\n✅ Valid move!")
        else:
            print("\n❌ Invalid move! This number conflicts with a row, column, or 3x3 box.")

# --- Main Execution ---

# Generate the game board with 40 holes 
my_board = playeble_board(40)

# Start the interactive game
play_sudoku(my_board)
