## C++ Solution

```C++
int removeDuplicates(vector<int>& nums) {
  std::unordered_set<int> setOfUniqueElements;
  for(auto it = nums.begin(); it != nums.end();){
    int numToSearch = *it;
    if(setOfUniqueElements.find(numToSearch) == setOfUniqueElements.end()){
      setOfUniqueElements.insert(numToSearch);
      it++;
    }else{
      it = nums.erase(it);
    }
  }
  return nums.size();
}
```

```c++
int removeDuplicates(vector<int>& nums) {
  for(auto it = nums.begin(); it != nums.end();){
    if(it == nums.begin()) {
      it++;
      continue;
    }
    if(*it == *(it-1)){
      it = nums.erase(it);
    }else{
      it++;
    }
  }
  return nums.size();
}
```

```c++
int removeDuplicates(vector<int>& nums) {
  int indexOfUniqueSequence = 1;
  for(auto it = nums.begin()+1; it != nums.end();){
    if(*it > *(it-1)){
      nums[indexOfUniqueSequence] = *it;
      indexOfUniqueSequence++;
    }
    it++;
  }
  nums.erase(nums.begin()+indexOfUniqueSequence, nums.end());
  return nums.size();
}
```

This solution is convoluted to make sense, but it is the fastest, because it doesn't use `unsorted_set`, doesn't call `erase` many times (only once when erasing at end to delete the range of non-unique elements).

```c++
int removeDuplicates(vector<int>& nums) {
  int indexOfUniqueSequence = 1;
  int numsSize = nums.size();
  for(int i=1; i < numsSize; i++){
    if(nums[i] > nums[i-1]){
      nums[indexOfUniqueSequence] = nums[i];
      indexOfUniqueSequence++;
    }
  }
  return indexOfUniqueSequence;
}
```

This is an optimized version of above. With not using iterator, the speed is now the fastest.