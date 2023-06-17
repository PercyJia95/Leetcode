## C++ Solution

```cpp
int hIndex(vector<int>& citations) {
  sort(citations.begin(), citations.end(), greater<int>());
  // for (const auto& num : citations) {
  //     cout << num << " ";
  // }

  int arraySize = citations.size();
  if(arraySize == 1 ){
    return citations[0] == 0 ? 0 : 1;
  }    
  for(int i=0; i<arraySize; i++){
    if(i+1 > citations[i])
      return i;
    if(i == arraySize-1){
      return i+1;
    }
  }
  return 0;
}
```