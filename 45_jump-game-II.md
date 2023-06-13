## C++ Solution

### Solution 1: Greedy

```cpp
int jump(vector<int>& nums) {
  size_t arraySize = nums.size();
  if(arraySize == 1) return 0;
  size_t furthestIndex = 0;
  int jumpCount = 0;
  while(true){
    size_t currentSearchRange = furthestIndex + nums[furthestIndex];
    if(currentSearchRange >= arraySize-1){
      jumpCount++;
      break;
    }
    size_t bestJumpIndex = furthestIndex+1;
    for(size_t i = furthestIndex+1; i <= currentSearchRange; i++){
      if(i + nums[i] > bestJumpIndex + nums[bestJumpIndex])
        bestJumpIndex = i;
    }

    if(bestJumpIndex < arraySize){
      furthestIndex = bestJumpIndex;
      jumpCount++;
      if(bestJumpIndex == arraySize-1) break;
    }else{
      break;
    }
  }
  return jumpCount;
}
```
##### After refactoring.

```cpp
int jump(vector<int>& nums) {
  size_t arraySize = nums.size();
  if(arraySize == 1) return 0;
  size_t furthestIndex = 0;
  int jumpCount = 1;
  while(furthestIndex + nums[furthestIndex] < arraySize-1){
    jumpCount++;
    size_t currentSearchRange = furthestIndex + nums[furthestIndex];
    for(size_t i = furthestIndex+1; i <= currentSearchRange; i++){
      if(i + nums[i] > furthestIndex + nums[furthestIndex])
        furthestIndex = i;
    }
  }
  return jumpCount;
}
```

The idea of solution_1 is to search for the best jump to take during each iteration, which is quantified with the further the jump distance of the index if selecting any index in the search range. The reasoning of the idea is that we want to always jump to an index that will let us jump to the furthest to the right among current level of selections, which is `i + nums[i]`. We will not necessarily jump to the furthest possible index once we move to that index allowes the furthest jump, because other elements covered by the jump range may have greater jump distance.

This solution is based on the Greedy method, where we always select the best index among the range of elements covered. The "best" index is justified with the distance it allows to jump, and the bigger range it covered for searching next best index.

The solution is **O(n) time complexity** because each element is visited as low as once and as high as countable ~~log(nums[i])~~ times.

The while loop just checks for the `break` condition and iterates the for loop for searching of the index to jump to.

### Solution 2: Greedy, BFS

```cpp
int jump(vector<int>& nums) {
  size_t arraySize = nums.size();
  int jumpCount = 0;
  size_t endOfCurrentLevel = 0;
  size_t farthestIndex = 0;

  // Implicit BFS
  for (int i = 0; i < arraySize -1; i++) {
    farthestIndex = max(farthestIndex, (size_t) i + nums[i]);
    if (farthestIndex >= nums.size() - 1) {
      jumpCount++;
      break;
    }
    if (i == endOfCurrentLevel) {   // Visited all the items on the current level
      jumpCount++;           					// Increment the level
      endOfCurrentLevel = farthestIndex;  // Make the queue size for the next level
    }
  }
  return jumpCount;
}
```

This solution has simpler logic because this solution finds out we don't need to iteratively find a best next index to jump to, instead, we only need to find such index when traversing encounters the last best index.

**In the last solution we were not traversing the `nums`, but iteratively running the mini for loops**

This solution's main idea is similar as the solution_1, but different than solution_1 in significant way. The `furthestIndex` here is the furthest current jumps can reach, but `furthestIndex` in solution_1 is an index to be selected for gaining furthest jump.

This solution is based on the Greedy method, where we does the furthest jump based on last furthest jump.

This solution cleverly incorprates the defining selection range of indices and `furthestIndex` updating into the traversing the array.