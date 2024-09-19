## Union of two Sorted Arrays
[https://www.geeksforgeeks.org/problems/union-of-two-sorted-arrays-1587115621/1](https://www.geeksforgeeks.org/problems/union-of-two-sorted-arrays-1587115621/1)
```java
// Brute Force
//Time Complexity : O((m+n) * log(m+n))
//Space Complexity: O(n)
class Solution
{
    public static ArrayList<Integer> findUnion(int arr1[], int arr2[], int n, int m)
    {
        Set<Integer> set = new TreeSet<>();
        for(int i=0;i<n;i++){
            set.add(arr1[i]);
        }
        for(int i=0;i<m;i++){
            set.add(arr2[i]);
        }
        ArrayList<Integer> arr = new ArrayList<>();
        arr.addAll(set);
        return arr;
    }
}

//Optimal Solution
//Time Complexity : O(m+n)
//Space Complexity: O(1)
class Solution
{
    public static ArrayList<Integer> findUnion(int arr1[], int arr2[], int n, int m)
    {
        ArrayList<Integer> arr = new ArrayList<>();
        int i=0,j=0;
        while(i<n && j<m){
            if(arr1[i] <= arr2[j]){
                if(arr.size() == 0 || arr.get(arr.size()-1) != arr1[i]){
                    arr.add(arr1[i]);
                }
                i++;
            }else{
                if(arr.size() == 0 || arr.get(arr.size()-1) != arr2[j]){
                    arr.add(arr2[j]);
                }
                j++;
            }
        }
        
        while(i<n){
            if(arr.size() == 0 || arr.get(arr.size()-1) != arr1[i]){
                    arr.add(arr1[i]);
                }
                i++;
        }
        while(j<m){
            if(arr.size() == 0 || arr.get(arr.size()-1) != arr2[j]){
                    arr.add(arr2[j]);
                }
                j++;
        }
        return arr;
    }
}

```

## Find Missing Number - LC - 268
[https://leetcode.com/problems/missing-number/description/](https://leetcode.com/problems/missing-number/description/)
```java
// Time Complexity: O(n)
// Space Complexity: O(1)
class Solution {
    public int missingNumber(int[] nums) {
        int i = 0;
        int n = nums.length;
        while(i<n){
            int correctIndex = nums[i];
            if(nums[i] < n && nums[i] != nums[correctIndex]){
                int temp = nums[i];
                nums[i] = nums[correctIndex];
                nums[correctIndex] = temp;
            }else{
                i++;
            }
        }

        for(int j=0;j<n;j++){
            if(nums[j] != j){
                return j;
            }
        }
        return n;
    }
}

```
