## Find the pivot integer

For a given sorted array n {1,2,3,...,n} containing all natural numbers from 1 to n, find an index "i" such that sum of all elements left to 
array[i] is eqaul to sum of all elements to the right of array[i]. If there's no such index, print -1.

#### Note: Time complexity has to be constant: O(1). That is, no loops to be used

For example, n = 120
Array = {1,2,3,...,120}
Equilibrium index = 85
Explanation: sum of values from 1 to 85 == sum of values from 85 to 120


```To find the value of x where the sum of elements from 1 to x is equal to the sum of elements from x to n, we can set up the following equation:
 
(1 + 2 + 3 + ---- + x) = (x + ----- + n)

x(x+1) / 2 = (x+n)(n-x+1) / 2

Upon calculation, 2x^2 = n^2 + n

x = sqrt(n(n+1) / 2)
```

Algorithm:

Calculate sum = (n * (n+1)) / 2 and take sqrt 'k'. If k*k = sum, then k is the pivot integer, else return -1.

```java
class Solution {
    public int pivotInteger(int n) {
        if(n == 1){
            return n;
        }
        //Binary Search
        /*int low = 1, high = n;
        int totalSum = (n * (n + 1)) / 2;
            
        while(low < high){
            int mid = (low + high)/2;
            if(mid* mid < totalSum){
                low = mid + 1;
            }else{
                high = mid;
            }
        }
        
        if(low* low == totalSum){
            return low;
        }
        return -1;
        */
        
        int totalSum = n*(n+1) / 2;
        int pivot = (int)Math.sqrt(totalSum);
        
        if(pivot*pivot == totalSum){
            return pivot;
        }
        
        return -1;
    }
}
