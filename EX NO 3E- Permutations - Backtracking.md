
# EX 3E Generate Permutations using Backtracking  Approach.
## DATE: 15.09.2026
## AIM:
To write a Java program to for given constraints.
Given an array nums of distinct integers, return all the possible Permutation. You can return the answer in any order.
Example 1:
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
For example:
## Algorithm
1. Start with an empty list curr to store the current permutation and an ans list to store all permutations.
2. Choose an unused element from the input array and add it to curr.
3. Recursively repeat the process until curr contains all elements.
4. Add a copy of curr to ans, then remove the last element to backtrack and try another element.
5. Continue until all possible arrangements are generated, then return and print ans.

## Program:
```
/*
Program to implement Reverse a String
Developed by: TIMMAPURAM YOGEESWAR
Register Number:  212223230233
*/
import java.util.*;

public class Solution {

    public List<List<Integer>> permute(int[] nums) {
        //add your code here
        List<List<Integer>> ans=new ArrayList<>();
        backtrack(new ArrayList<>(),ans,nums);
        return ans;
    }

    public void backtrack(List<Integer> curr, List<List<Integer>> ans, int[] nums) {
        //Add your code here
        if(curr.size()==nums.length){
            ans.add(new ArrayList<>(curr));
            return;
        }
        for(int num:nums){
            if(!curr.contains(num)){
                curr.add(num);
                backtrack(curr,ans,nums);
                curr.remove(curr.size()-1);
            }
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
<img width="1266" height="200" alt="image" src="https://github.com/user-attachments/assets/2540851e-01c7-4c23-b1df-050f8d53f95d" />



## Result:
The program successfully implemented and the expected output is verified.
