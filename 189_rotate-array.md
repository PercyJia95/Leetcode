## C++ Solution

```c++
void rotate(vector<int>& nums, int k) {
  size_t arraySize = nums.size();
  k = k % arraySize;
  ::rotate(nums.begin(), nums.begin()+ (arraySize - k), nums.end());
}
```

The `rotate` function only shift elements from right to left, but the question ask to shift from left to right for k distance, therefore we need `arraySize - k`.

In testing, some `k` has value that is larger than `arraySize`, this cause `arraySize - k` to be negative and `num.begin()` references left beyond starting index, thus cause invalid memory access error. Therefore, I have to use `k = k % arraySize` to keep the value smaller than `k`.

## Python Solution

```python
def rotate(self, nums, k):
	"""
  :type nums: List[int]
  :type k: int
  :rtype: None Do not return anything, modify nums in-place instead.
	"""
  arraySize = len(nums)
  k = k % arraySize
  nums[:] = nums[-k:] + nums[:-k]
```

Python solution is slow, but here just show how condense the Python code can be, meanwhile, only using list concatenation and some list built-in.

Without using` nums[:]`. The code without semicolon will create a <u>new list</u> called `nums`

`nums[:] = nums[-k:] + nums[:-k] #modifying the list in-place`

`nums[] = nums[-k:] + nums[:-k] #created a new list. Not modifying the list in-place`