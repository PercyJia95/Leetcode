## C++ Solution

### Greedy Solution

```cpp
bool canJump(vector<int>& nums) {
  size_t furthest = 0;
  size_t arraySize = nums.size();
  for(int i=0; i<arraySize; i++){
    if(furthest >= i){
      furthest = max(furthest, (size_t) i +nums[i]);
    }else{
      return false;
    }
  }
  return true;
}
```

Greedy Algorithm: use a variable to hold the furthest point we can reach so far, ie. furthest = max(furthest, i+nums[i]). Then think of a way to use it for judging if we can get to the end. If the furthest is less than the current index, then it is game over, because there is no way to get to the current index by any mean.

This is a fastest solution on Leetcode, which beats 98% other solution. 

```cpp
bool canJump(vector<int>& nums) {
  size_t furthest = 0;
  size_t arraySize = nums.size();
  for(int i=0; i<arraySize; i++){
    if(furthest >= i){
      furthest = max(furthest, (size_t) i +nums[i]);
    }
  }
  if(furthest >= arraySize-1){
    return true;
  }else{
    return false;
  }
}
```

This greedy solution is same, but **slower** because of the nuance where it has the `return false` statement is at outside of the for loop. If the `return false` is inside of the the for loop, then the for loop can stop earlier which happens once the furthest is not greater than the index (`furthest >= i`).

### Dynamic Programming Solution

