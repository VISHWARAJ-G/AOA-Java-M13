
# EX 3C Tug of War problem - Backtracking.
## DATE: 08/08/2026
## AIM:
To write a Java program to for given constraints.
Given an integer array nums, return true if you can partition the array into two subsets such that the sum of the elements in both subsets is equal or false otherwise.
Example 1:
Input: Enter the number of elements: 4
Enter the elements of the array:
1 5 11 5
Output: true
Explanation: The array can be partitioned as [1, 5, 5] and [11].

Constraints:

1 <= nums.length <= 200
1 <= nums[i] <= 100

## Algorithm

1. **Start**
2. Read the array `nums` and calculate the sum of all its elements.
3. If the total sum is odd, return `false` because it cannot be divided into two equal subsets.
4. Set the target sum as `total / 2`.
5. Recursively consider each element from the current index, either including it in the subset or skipping it.
6. If the target becomes `0`, return `true`; if all elements are processed or the target becomes negative, return `false`.
7. If either recursive choice produces the target sum, return `true`; otherwise return `false`.
8. Display whether the array can be partitioned into two subsets with equal sums.
9. **End**

## Program:
```
/*
Program to implement Reverse a String
Developed by: Vishwaraj G
Register Number: 212223220125
*/
import java.util.Scanner;
public class Solution {
    public boolean canPartition(int[] nums) {
        //Type your code here
        int total =0;
        for(int num:nums)total+=num;
        if(total%2!=0)return false;
        return canPartitionHelper(nums,0,total/2);
        
    }
    private boolean canPartitionHelper(int[] nums,int index,int target){
        if(target==0)return true;
        if(index>=nums.length||target<0)return false;
        if(canPartitionHelper(nums,index+1,target-nums[index]))return true;
        return canPartitionHelper(nums,index+1,target);
    }
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Solution sol = new Solution();
        int n = scanner.nextInt();
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = scanner.nextInt();
        }
        boolean canBePartitioned = sol.canPartition(nums);
        System.out.println(canBePartitioned);
    }
}

```

## Output:
<img width="346" height="142" alt="image" src="https://github.com/user-attachments/assets/d036d463-a0df-4139-a0f2-984d5b04e4c7" />



## Result:
The program successfully implemented and the expected output is verified.
