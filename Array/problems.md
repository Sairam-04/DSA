# 19 Sept 2024
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

# 21 Sept 2024
## Max Consecutive Ones - LC - 485
[https://leetcode.com/problems/max-consecutive-ones/description/](https://leetcode.com/problems/max-consecutive-ones/description/)
```java
// Time Complexity: O(n)
// Space Complexity: O(1)
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int count = 0;
        int maxCount = 0;
        for(int i=0;i<nums.length;i++){
            if(nums[i] == 1){
                count++;
            }else{
                count = 0;
            }
            maxCount = Math.max(count, maxCount);
        }
        return maxCount;
    }
}
```

## Single Number - LC - 136
[https://leetcode.com/problems/single-number/description/](https://leetcode.com/problems/single-number/description/)
```java
// Time Complexity: O(n)
// Space Complexity: O(1)
class Solution {
    public int singleNumber(int[] nums) {
        int result = 0;
        for(int i=0;i<nums.length;i++){
            result^=nums[i];
        }
        return result;
    }
}
```


## Longest Sub-Array with Sum K
[https://www.geeksforgeeks.org/problems/longest-sub-array-with-sum-k0809/1](https://www.geeksforgeeks.org/problems/longest-sub-array-with-sum-k0809/1)
```java
// Time Complexity: O(n)
// Space Complexity: O(n)
class Solution {
    // Function for finding maximum and value pair
    public static int lenOfLongSubarr(int A[], int N, int K) {
        // Complete the function
        HashMap<Integer, Integer> map = new HashMap<>();
        int sum = 0;
        int maxLen = 0;
        for(int i=0;i<N;i++){
            sum+=A[i];
            if(sum == K){
                maxLen = Math.max(maxLen, i+1);
            }
            int rem = sum - K;
            if(map.containsKey(rem)){
                int len = i - map.get(rem);
                maxLen = Math.max(maxLen, len);
            }
            if(!map.containsKey(sum)){
                map.put(sum, i);
            }
        }
        return maxLen;
    }
}
```
