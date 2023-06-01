## C++ Solution

```c++
vector<int> twoSum(vector<int> &nums, int target) {
  int index_1 = 0;
  int index_2 = 0;
  int index_1_final = 0;
  int index_2_final = 0;
  for (const auto number_1 : nums) {
    for (const auto number_2 : nums) {
      if(index_1 == index_2){
        index_2++;
        continue;
      }else{
        std::cout << index_1 << std::endl;
        std::cout << index_2 << std::endl;
        int total_for_test = number_1 + number_2;
        // std::cout << (total_for_test==target) << std::endl;
        if(total_for_test == target){
          index_1_final = index_1;
          index_2_final = index_2;
        }
        index_2++;
      }
    }
    index_2 = 0;
    index_1++;
  }
  return {index_1_final, index_2_final};
}
```

`std::size_t` : Machine-dependent unsigned integral type that is large enough to hold the size of largest possible array/vector..., thus is suitable for being used as the type of variable to subscript an array/vector.

Vector is a kind of container in C++. The containers share a common interface. This common interface makes the library easier to learn; what we learn about one kind of container applies to another！But each kind of container offers a different set of performance and functionality trade-offs.

THe `&nums` in `twoSum(vector<int> &nums, int target)` is a reference variable. The difference of `&nums` and `nums` is adding the `&` will let `nums` directly reference to the origninal object, thus save memory! (not having `&` makes the solution on Leetcode to cost 5 more MB).

For another example, The `&number` is a referenced loop variable in the `for(const auto &number : nums)` will let `&number` directly references to the element in `num` vector. In contrast, if we used without `&`, as in `(const auto number : nums)`, the loop variable `number` will be a **copy** of the element, so changing on the `number` will not effect the element in inside the `num` vector container.

## Python solution

```python
def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        index_1_final = 0
        index_2_final = 0
        for index_1, num_1 in enumerate(nums):
            for index_2, num_2 in enumerate(nums):
                if index_1 == index_2:
                    continue
                else:
                    total_for_test = num_1 + num_2
                    if total_for_test == target:
                        index_1_final = index_1
                        index_2_final = index_2
        return [index_1_final, index_2_final]
```

The `for index_1, num_1 in enumerate(nums):` is a foreach loop that would get an element with its **index** in each iteration.



## Concerns

1. bad naming habbit
2. the double for loops will have checked all 2-elements combinations twice if it finishes going though all combinations
3. it will return the last occurance of the combination instead the first occurence. 