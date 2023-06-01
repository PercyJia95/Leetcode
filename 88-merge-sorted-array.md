## C++ Solution

```c++
void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
  nums1.erase(nums1.begin()+m, nums1.begin()+m+n);
  //or `nums1.begin()+m+n` can be exchanged with `nums1.end()-1`
  nums1.insert(nums1.begin()+m, nums2.begin(), nums2.begin()+n);
  //or `nums2.begin()+n` can be exchanged with `nums2.end()-1`
  sort(nums1.begin(), nums1.end());
//  for(int nums: nums1){
//  	cout << nums << endl;
//	}        
}
```

- The `erase` function is used to remove the range of elements from `nums1`. It takes two iterators specifying the range to be erased. In this case, we use `nums1.begin()+m` as the starting iterator and `nums1.end()-1` as the ending iterator to erase the portion `{2, 3, 4}`. The reason of having `-1` at the end of `nums1.end()-1`  is `nums1.end()` is at one past the end of the range defaultly.
  Syntax of `erase`: `vector.erase(beginning iterator, end iterator)`
- The `insert` function is used to insert elements from `nums2` into `nums1` at the specified position. It takes two iterators specifying the insertion position and a range of elements to be inserted. 
  Syntax of `insert`: `vector.insert(iterator indicates position to insert at vector_1, beginning iterator of vector_2, end iterator of vector_2)`
- The `sort` function sorts a vector/container within the range indicated by the two iterators.
  Syntax: `sort(beginning iterator, end iterator)`.

## Python Solution

Easy solution:

1. use Python built-in sorting
2. use Python slicing to paste in list/array to another list/array easily. (or concatenation of two lists/arrays)

```python
def merge(self, nums1, m, nums2, n):
  """
  :type nums1: List[int]
  :type m: int
  :type nums2: List[int]
  :type n: int
  :rtype: None Do not return anything, modify nums1 in-place instead.
  """
  
  nums1[m:] = nums2
  nums1.sort()
```

