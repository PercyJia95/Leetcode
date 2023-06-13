## C++ Solution

```cpp
int maxProfit(vector<int>& prices) {
  size_t arraySize = prices.size();
  int profit = 0;
  for(int i=1; i<arraySize; i++){
    if(prices[i] > prices[i-1]){
      profit += (prices[i] - prices[i-1]);
    }
  }
  return profit;
}
```

The main idea of the solution is to collect all profit during any increase of the prices. 

We want to buy all the stocks when the line is going up. And want to ignore all the lines when the line is going down.

Do a for loop through the array and only count in the green line that is going up, by comparing the two adjacent elements in the array.