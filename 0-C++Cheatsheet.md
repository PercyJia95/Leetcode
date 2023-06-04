1. `i++`  and `++i` both increment the counter by 1, but have different effect when used in assignment.

   `j = i++ // j will equal the i before increment`

   `j = ++i // j will equal the i after increment`

   <u>The basic idea of `i++` is to postpone the increment to the very end of execution its line of code, but the `++i` is the opposite, it urges to finish the increment at the very first moment when the process start to evaluate `++i`.</u>

2. The `erase` function takes two iterators for specifying a range of elements:

   Syntax: `erase(vec.begin(), vec.begin()+3`

   for a `vec` like `{0,1,2,3}` the `vec.begin()+3` points at `3`, and range would be 0 to 2, **because the end iterator specify the location at one element pass the end of range to be erased.**

