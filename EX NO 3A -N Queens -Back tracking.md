
# EX 3A N Queens Problem - Backtracking Approach.
## DATE: 06/08/2026
## AIM:
To Write a Java program for N queens using backtracking approach.
You are given an integer N. For a given N x N chessboard, find a way to place 'N' queens such that no queen can attack any other queen on the chessboard.
A queen can be attacked when it lies in the same row, column, or the same diagonal as any of the other queens. You have to print one such configuration.
Chess Board
<img width="241" height="209" alt="image" src="https://github.com/user-attachments/assets/96aacb61-4f34-423f-b324-5e34454e42b8" />


Note :

Get the input from the user for N . The value of N must be from 1 to 4

If solution exists Print a binary matrix as output that has 1s for the cells where queens are placed

If there is no solution to the problem  print  "Solution does not exist"

## Algorithm

1. **Start**
2. Read the board size `N` and initialize an `N × N` board with all cells set to `0`.
3. Start placing queens column by column using backtracking.
4. For each column, check every row to determine whether placing a queen is safe.
5. Verify that no queen exists in the same row, upper-left diagonal, or lower-left diagonal.
6. If the position is safe, place a queen and recursively move to the next column.
7. If no valid position exists, remove the previously placed queen and backtrack to try another position.
8. When all `N` queens are placed, print the board; otherwise, display that no solution exists.
9. **End** 

## Program:
```
/*
Program to implement Reverse a String
Developed by: Vishwaraj G
Register Number: 212223220125
*/
import java.util.Scanner;

public class NQueens {
    static int N;

    
    static void printSolution(int[][] board) {
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++) {
                System.out.print(board[i][j] + " ");
            }
            System.out.println();
        }
    }

    
    static boolean isSafe(int[][] board, int row, int col) {
        // Check left side of current row
        for (int i = 0; i < col; i++)
            if (board[row][i] == 1)
                return false;

       
        for (int i = row, j = col; i >= 0 && j >= 0; i--, j--)
            if (board[i][j] == 1)
                return false;

        
        for (int i = row, j = col; i < N && j >= 0; i++, j--)
            if (board[i][j] == 1)
                return false;

        return true;
    }

    // Recursive utility function to solve N-Queens
    static boolean solveNQUtil(int[][] board, int col) {
        //Add your code Here
        if (col >= N)
            return true;
        for (int row = 0; row < N; row++) {
            if (isSafe(board, row, col)) {
                board[row][col] = 1;
                if (solveNQUtil(board, col + 1))
                    return true;
                board[row][col] = 0;
            }
        }
        return false;
    }

    
    static boolean solveNQ() {
        int[][] board = new int[N][N];

        if (!solveNQUtil(board, 0)) {
            System.out.println("Solution does not exist");
            return false;
        }

        printSolution(board);
        return true;
    }

   
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        N = scanner.nextInt(); // Accept board size
        solveNQ();
    }
}

```

## Output:

<img width="447" height="160" alt="image" src="https://github.com/user-attachments/assets/9da030b0-0979-498b-970e-12d912d39179" />


## Result:
The program successfully implemented and the ouput is verified. 
