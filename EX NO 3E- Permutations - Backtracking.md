
# EX 3E Generate Permutations using Backtracking  Approach.
## DATE: 12/08/2026
## AIM:
To write a Java program to for given constraints.
Given an array nums of distinct integers, return all the possible Permutation. You can return the answer in any order.
Example 1:
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]

## Algorithm

1. **Start**
2. Read the array `nums` and initialize an empty list `ans` and a `used` array.
3. Start backtracking with an empty current permutation.
4. If the current permutation contains all elements, add a copy of it to `ans`.
5. Traverse all elements and skip an element if it is already marked as `used`.
6. Mark the selected element as used, add it to the current permutation, and recursively continue.
7. After recursion, remove the selected element and mark it as unused to backtrack.
8. Repeat until all possible permutations are generated, then display `ans`.
9. **End**

## Program:
```
/*
Program to implement Reverse a String
Developed by: Vishwaraj G
Register Number: 212223220125
*/
import java.util.*;

public class Solution {

    boolean[] used;
    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        used = new boolean[nums.length];
        backtrack(
            new ArrayList<>(),
            ans,
            nums
        );
        return ans;
    }

    public void backtrack(
        List<Integer> curr,
        List<List<Integer>> ans,
        int[] nums
    ) {
        if (curr.size() == nums.length) {
            ans.add(new ArrayList<>(curr));
            return;
        }
        for (int i = 0; i < nums.length; i++) {
            if (used[i]) {
                continue;
            }
            used[i] = true;
            curr.add(nums[i]);
            backtrack(curr, ans, nums);
            curr.remove(curr.size() - 1);
            used[i] = false;
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String inputLine = scanner.nextLine().trim();
        inputLine = inputLine.replaceAll(".*\\[|\\].*", ""); 
        String[] parts = inputLine.split(",");

        int[] nums = new int[parts.length];
        for (int i = 0; i < parts.length; i++) {
            nums[i] = Integer.parseInt(parts[i].trim());
        }
        Solution solution = new Solution();
        List<List<Integer>> permutations = solution.permute(nums);
        System.out.println(permutations);
        scanner.close();
    }
}
```

## Output:
<img width="855" height="113" alt="image" src="https://github.com/user-attachments/assets/80056807-fecd-4788-9336-252e90c5878f" />


## Result:
The program successfully implemented and the expected output is verified.
