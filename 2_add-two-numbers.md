## C++ Solution

```c++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */

ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
  ListNode* resultLinkedList = nullptr;
  ListNode* pastNode = nullptr;

  ListNode* x1 = l1;
  ListNode* x2 = l2;
  bool shouldRaise = false;
  int digitNumX1, digitNumX2;
  while (x1 != nullptr || x2 != nullptr || shouldRaise == true){
    if(x1 != nullptr){
      digitNumX1 = x1->val;
      x1 = x1->next;
    }else{
      digitNumX1 = 0;
    }
    if(x2 != nullptr){
      digitNumX2 = x2->val;
      x2 = x2->next;
    }else{
      digitNumX2 = 0;
    }

    int digitNumSum = digitNumX1 + digitNumX2;
    if(shouldRaise == true){
      digitNumSum = digitNumSum + 1;
      shouldRaise = false;
    }
    if(digitNumSum > 9){
      digitNumSum = digitNumSum - 10;
      shouldRaise = true;
    }

    ListNode* newNode = new ListNode(digitNumSum, nullptr);
    if(pastNode == nullptr){
      pastNode = newNode;
      resultLinkedList = newNode;
    }else{
      pastNode->next = newNode;
      pastNode = newNode;
    }

  }
  return resultLinkedList;
}
```

## Python Solution

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        resultLinkedList = None
        pastNode = None

        x1 = l1
        x2 = l2
        shouldRaise = False
        while(x1 != None or x2 != None or shouldRaise == True):
            if(x1 != None):
                digitNumX1 = x1.val
                x1 = x1.next
            else:
                digitNumX1 = 0
            if(x2 != None):
                digitNumX2 = x2.val
                x2 = x2.next
            else:
                digitNumX2 = 0
            
            digitNumSum = digitNumX1 + digitNumX2
            if(shouldRaise == True):
                digitNumSum = digitNumSum + 1
                shouldRaise = False
            if(digitNumSum > 9):
                digitNumSum = digitNumSum - 10
                shouldRaise = True
            
            newNode = ListNode(val=digitNumSum, next=None)
            if (pastNode == None): 
                pastNode = newNode
                resultLinkedList = newNode
            else:
                pastNode.next = newNode
                pastNode = newNode

        return resultLinkedList
```

