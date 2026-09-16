
# EX 3C Tug of War problem - Backtracking.
## DATE: 15.09.2026
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
1. Start and calculate the total sum of all elements in the array.
2. If the total sum is odd, return false because equal partition is impossible.
3. Set the target as totalSum / 2 and create a Boolean DP array with dp[0] = true.
4. For each number, update the DP array from right to left to check whether the target sum can be formed.
5. Return dp[target]: true if the array can be divided into two equal-sum subsets, otherwise false.

## Program:
```
/*
Program to implement Reverse a String
Developed by: TIMMAPURAM YOGEESWAR
Register Number:  212223230233
*/
import java.util.Scanner;
public class Solution {
    public boolean canPartition(int[] nums) {
        //Type your code here
        if(nums.length==0) return false;
        int totalsum=0;
        for(int num:nums) totalsum+=num;
        if(totalsum%2!=0) return false;
        int subsets=totalsum/2;
        boolean[] dp=new boolean[subsets+1];
        dp[0]=true;
        for(int curr:nums){
            for(int j=subsets;j>=curr;j--) dp[j]|=dp[j-curr];
        }
        return dp[subsets];
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
<img width="382" height="215" alt="image" src="https://github.com/user-attachments/assets/4b948a24-c45a-40be-8ec2-609b926a3e6c" />



## Result:
The program successfully implemented and the expected output is verified.
