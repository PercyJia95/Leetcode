## C++ Solution

```c++
int removeElement(vector<int>& nums, int val) {
  for (auto it = nums.begin(); it != nums.end();){
    if (*it == val){
    	it = nums.erase(it);  // Remove the element and update the iterator
    }else{
    	it++;  // Move to the next element
    }
  }
  return nums.size();
}
```

The `erase` function takes one iterator that indicates which element to be erased, and then return an iterator that points to the element one past the erased element.

## Python Solution

The challenge of This problem is to remove element **in-place**. This affect python solution not able to use <u>list comprehension</u>.

#### Python solution 1

```python
def removeElement(self, nums, val):
  """
  :type nums: List[int]
  :type val: int
  :rtype: int
  """
  i = 0
  while i < len(nums):
  	if nums[i] == val:
  		del nums[i]
  	else:
  		i += 1
  return len(nums)
```

One important thing to notice for understanding this code is the index of items will change when one element is removed and all elements after it will be `-1` in their indices. That is why, in this solution, the index is not incremented when a removing is done (`del nums[i]`), because the later element will backfill the index. 

#### Python solution 2

```python
def removeElement(self, nums, val):
  """
  :type nums: List[int]
  :type val: int
  :rtype: int
  """
  i = 0
  try:
  	while True:
  		nums.remove(val)
  except ValueError:
  	pass
  return len(nums)
```

The `remove(val)` will remove the first occurrence of val in the list. This solution is the slowest in because it has to search for first occurrence of `val` at each time removing.

#### Python solution 3 (Best solution)

```python
class Solution(object):
    def removeElement(self, nums, val):
        """
        :type nums: List[int]
        :type val: int
        :rtype: int
        """
        for index, num in enumerate(nums):
            if num == val:
                self.backFill(nums, index, val)
        return len(nums)

    def backFill(self, nums, index, val):
        if index == len(nums) -1:
            nums.pop()
            return
        lastElement = nums.pop()
        if lastElement == val:
            self.backFill(nums, index, val)
        else:
            nums[index] = lastElement
            return
```

This solution beats 90% of others Python solutions in time **and** space complexity, but it hard to explain and reason this solution due to Python list will automatically change indices when removing element. So, not using Python but instead using C++ would help with this problem.