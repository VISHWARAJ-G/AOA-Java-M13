
# EX 3B Rat in Maze- Backtracking 
## DATE: 07/08/2026
## AIM:
To write a Java program to for given constraints.
here is a ball in a maze with empty spaces (represented as 0) and walls (represented as 1). The ball can go through the empty spaces by rolling up, down, left or right, but it won't stop rolling until hitting a wall. When the ball stops, it could choose the next direction.

Given the m x n maze, the ball's start position and the destination, where start = [startrow, startcol] and destination = [destinationrow, destinationcol], return true if the ball can stop at the destination, otherwise return false.

You may assume that the borders of the maze are all walls (see examples).
<img width="573" height="573" alt="image" src="https://github.com/user-attachments/assets/d6f1c054-cdc2-4bb3-9c55-512fb2cf0fb7" />
Input: maze = [[0,0,1,0,0],[0,0,0,0,0],[0,0,0,1,0],[1,1,0,1,1],[0,0,0,0,0]], start = [0,4], destination = [4,4]
Output: true
Explanation: One possible way is : left -> down -> left -> down -> right -> down -> right.


## Algorithm

1. **Start**
2. Read the maze dimensions, maze elements, starting position, and destination position.
3. Initialize a `visited` matrix and perform DFS from the starting position.
4. If the current position is the destination, return `true`; if it has already been visited, return `false`.
5. Mark the current position as visited and consider the four directions: up, down, left, and right.
6. Roll the current position continuously in each direction until a wall or boundary is reached, then move back to the last valid cell.
7. Recursively perform DFS from each reachable stopping position.
8. If the destination is reached, return `true`; otherwise, return `false` after all directions are explored.
9. **End**

## Program:
```
/*
Program to implement Reverse a String
Developed by: Vishwaraj G
Register Number: 212223220125
*/

import java.util.*;

public class Main {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Read maze dimensions
        int m = sc.nextInt();
        int n = sc.nextInt();

        int[][] maze = new int[m][n];
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                maze[i][j] = sc.nextInt();
            }
        }

        // Read start position
        int[] start = new int[]{sc.nextInt(), sc.nextInt()};

        // Read destination position
        int[] destination = new int[]{sc.nextInt(), sc.nextInt()};

        Solution sol = new Solution();
        boolean result = sol.hasPath(maze, start, destination);

        System.out.println(result);
    }
}

class Solution {
    public boolean dfs(int m, int n, int[][] maze, int[] curr, int[] destination, boolean[][] visit) {
        int row = curr[0];
        int col = curr[1];
        if (row == destination[0] && col == destination[1])
            return true;
        if (visit[row][col])
            return false;
        visit[row][col] = true;
        int[][] directions = {
            {1, 0},
            {-1, 0},
            {0, 1},
            {0, -1}
        };
        for (int[] dir : directions) {
            int r = row;
            int c = col;
            while (r >= 0 && r < m &&
                   c >= 0 && c < n &&
                   maze[r][c] == 0) {
                r += dir[0];
                c += dir[1];
            }
            r -= dir[0];
            c -= dir[1];
            if (dfs(m, n, maze, new int[]{r, c},
                    destination, visit)) {
                return true;
            }
        }
        return false;
    }
    public boolean hasPath(int[][] maze, int[] start, int[] destination) {
        int m = maze.length;
        int n = maze[0].length;
        boolean[][] visit = new boolean[m][n];
        return dfs(m, n, maze, start, destination, visit);
    }
}

```

## Output:
<img width="450" height="321" alt="image" src="https://github.com/user-attachments/assets/b440fe6d-059a-481b-9a94-c750c24ef218" />



## Result:
The program successfully implemented and the expected output is verified.
