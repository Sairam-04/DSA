Union of two Sorted Arrays

```java
// Brute Force
Time Complexity : O((m+n) * log(m+n))
Space Complexity: O(n)
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
Time Complexity : O(m+n)
Space Complexity: O(1)
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
