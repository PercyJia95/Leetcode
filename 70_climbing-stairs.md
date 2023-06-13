## C++ Solution

```cpp
int climbStairs(int n) {
  vector<int> answerCache(3);
  answerCache[0] = 1;
  answerCache[1] = 1;
  answerCache[2] = 2;
  return waysToTop(n, answerCache);
}

int waysToTop(int stepsToReach, vector<int> &answerCache){
  size_t arraySize = answerCache.size();
  int stepsToReachMinus1;
  int stepsToReachMinus2;
  if(stepsToReach == 1){
    return answerCache[1];
  }
  if(stepsToReach == 2){
    return answerCache[2];
  }
  if(stepsToReach-2 < arraySize){
    stepsToReachMinus2 = answerCache[stepsToReach-2];
  }else{
    stepsToReachMinus2 = waysToTop(stepsToReach-2, answerCache);
  }
  if(stepsToReach-1 < arraySize){
    stepsToReachMinus1 = answerCache[stepsToReach-1];
  }else{
    stepsToReachMinus1 = waysToTop(stepsToReach-1, answerCache);
  }
  answerCache.push_back(stepsToReachMinus2 + stepsToReachMinus1);
  return answerCache[stepsToReach];
}
```