
# EX 3D Sudoku solver - Backtracking.
## DATE: 11/08/2026
## AIM:
To write a Java program to solve a Sudoku puzzle by filling the empty cells.

For example:
<img width="357" height="322" alt="image" src="https://github.com/user-attachments/assets/334b8c39-d547-4743-aca0-de92e38bdd1c" />


## Algorithm

1. **Start**
2. Read the `9 × 9` Sudoku board, using `0` for empty cells.
3. Traverse the board row by row and column by column to find an empty cell.
4. For each empty cell, try placing numbers from `1` to `9`.
5. Check whether the number is safe by verifying its row, column, and corresponding `3 × 3` subgrid.
6. If safe, place the number and recursively solve the next cell.
7. If the placement leads to no solution, reset the cell to `0` and backtrack to try another number.
8. When all cells are filled, display the solved Sudoku; otherwise, display that no solution exists.
9. **End**

## Program:
```
/*
Program to implement Reverse a String
Developed by: Vishwaraj G
Register Number: 212223220125
*/
import java.util.Scanner;

public class SudokuSolver {

    // Check if it's safe to place the number
    static boolean isSafe(int[][] board, int row, int col, int num) {
        // Check row and column
        for (int i = 0; i < 9; i++) {
            if (board[row][i] == num || board[i][col] == num)
                return false;
        }

        // Check 3x3 subgrid
        int startRow = row - row % 3;
        int startCol = col - col % 3;

        for (int i = 0; i < 3; i++)
            for (int j = 0; j < 3; j++)
                if (board[startRow + i][startCol + j] == num)
                    return false;

        return true;
    }

    // Recursive backtracking solver
    static boolean solveSudoku(int[][] board, int row, int col) {
        //Type your code here
        if (row == 9) {
            return true;
        }
        if (col == 9) {
            return solveSudoku(board, row + 1, 0);
        }
        if (board[row][col] != 0) {
            return solveSudoku(board, row, col + 1);
        }
        for (int num = 1; num <= 9; num++) {
            if (isSafe(board, row, col, num)) {
                board[row][col] = num;
                if (solveSudoku(board, row, col + 1)) {
                    return true;
                }
                board[row][col] = 0;
            }
        }
        return false;
    }

    // Utility to print the board
    static void printBoard(int[][] board) {
        for (int[] row : board) {
            for (int val : row)
                System.out.print(val + " ");
            System.out.println();
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int[][] board = new int[9][9];

      //  System.out.println("Enter the Sudoku puzzle row by row (use 0 for empty cells):");

        for (int i = 0; i < 9; i++) {
            //System.out.print("Enter row " + (i + 1) + ": ");
            for (int j = 0; j < 9; j++) {
                board[i][j] = sc.nextInt();
            }
        }

      //  System.out.println("\nSolving...\n");

        if (solveSudoku(board, 0, 0)) {
            System.out.println("Solved Sudoku:");
            printBoard(board);
        } else {
            System.out.println("No solution exists.");
        }

        sc.close();
    }
}

```

## Output:
<img width="495" height="362" alt="image" src="https://github.com/user-attachments/assets/d7379f3d-e816-4a5f-8550-7613b1b41e74" />



## Result:
The program successfully implemented and the expected output is verified.
