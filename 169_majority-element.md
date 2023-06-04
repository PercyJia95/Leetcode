## C++ Solution

#### Use `Sort()`

```C++
int majorityElement(vector<int>& nums) {
  sort(nums.begin(), nums.end());
  return nums[nums.size()/2];
}
```

#### Use Map container

```C++
int majorityElement(vector<int>& nums) {
  unordered_map <int, size_t> numCount;
  size_t arraySize = nums.size();
  for(int num: nums){
    numCount[num]++;
    if(numCount[num] * 2 > arraySize){
      return num;
    }
  }
  return -1;
}
```

#### A Fast and Simple O(1) Space Solution, BUT it is HARD to Reason

```c++
int majorityElement(vector<int>& nums) {
  size_t arraySize = nums.size();
  size_t leadNumCount = 1;
  int leadNum = nums[0];
  for(int i = 1; i < arraySize; i++){
    if(leadNumCount == 0) leadNum = nums[i];
    if(nums[i] == leadNum){
      leadNumCount++;
    }else{leadNumCount--;}
  }
  return leadNum;
}
```

## Python Solution

```python
def majorityElement(self, nums):
  """
  :type nums: List[int]
  :rtype: int
  """
  numCount = {}
  for num in nums:
    if num in numCount:
      numCount[num] += 1
    else:
      numCount[num] = 1
	majorityElement = max(numCount, key=numCount.get)
  return majorityElement
```

This solution define a dictionary `numCount`, this dictionary count the occurrence during traversing the list.

This line `majorityElement = max(numCount, key=numCount.get)` returns the key in the dictionary that corresponds to the biggest value, thus it is majority element that has the highest occurence.

This line is difficult to understand: `majorityElement = max(numCount, key=numCount.get)`, I will explain it here:

<u>When applying `max` on a dictionary, such as this `numCount`, the `max` algorithm will find the maximum element by comparing the dictionary **keys** by default (without  `key=numCount.get` ). The argument `key=numCount.get` dictates that, when comparsion, the algorithm shall use the corresponding values for comparsion, instead of the keys.</u>



