# Intuition
This problem is about separating the received numbers into diferent list as if these were sets, i mean in different lists without repeting any number in each one.

The submitted code is in <https://leetcode.com/problems/convert-an-array-into-a-2d-array-with-conditions/submissions/1295039269/>

# Approach
We need to empty the received list, and move every number into another list in our final list of lists.
For each number in nums we have to go through every list in the final list trying to put the number in one of these. If we put it then we go to the next number in nums.
If the number is already in all the lists, then we create another list with the number and append it to the final list.

# Complexity
Time complexity: O(n^2)
Space complexity: O(n)

# Code
``` python3
class Solution:
    def findMatrix(self, nums: List[int]) -> List[List[int]]:
        final = [[]]  # Initialize with one empty sublist
        while len(nums) > 0:
            i = nums.pop(-1)  # Remove the last element
            a = True
            for ls in final:
                if i not in ls:  # Check if the element is not in the sublist
                    ls.append(i)  # Add to the sublist
                    a = False
                    break
            if a:
                final.append([i])  # If no suitable sublist, create a new one
        return final
```
