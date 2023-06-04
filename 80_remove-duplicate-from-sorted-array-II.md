## C++ Solution

```c++
int removeDuplicates(vector<int>& nums) {
  int indexOfUniqueSequence = 1;
  int numsSize = nums.size();
  int counterOfTwice = 1;
  for(int i=1; i < numsSize; i++){
    if(nums[i] > nums[i-1]){
      nums[indexOfUniqueSequence++] = nums[i];
      counterOfTwice = 1;
    }else if(counterOfTwice < 2){
      nums[indexOfUniqueSequence++] = nums[i];
      counterOfTwice++;
    }
  }
  return indexOfUniqueSequence;
}
```

