A double for loop will require O(n^2^) to compute, and O(n^2^) time is not acceptable, in Leetcode, it is an overtime submission.

The question suggest Dynamic Programming to obtain a O(n) solution

## C++ Solution

```cpp
int maxProfit(vector<int>& prices) {
  size_t arraySize = prices.size();
  int lowestPrice = numeric_limits<int>::max();
  int maxProfit = 0;
  for(int i=0; i < arraySize; i++){
    if(prices[i] < lowestPrice){
      lowestPrice = prices[i];
      continue;
    }else{
      if(maxProfit < prices[i] - lowestPrice){
        maxProfit = prices[i] - lowestPrice;
      }
    }
  }
  return maxProfit;
}
```

