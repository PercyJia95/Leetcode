## Class (not the class in OOP)

#### A Class = A Compond Data Type

#### Data Abstraction (Encapsulation)

**Data abstraction** is a design technique that suggests seperation of interface and implementation. The implementation is hidden from user, this emphasis on "hidden implementation" is also called "encapsulation".

## C++ Class

#### Define a Class

```c++
struct ListNode {
	int val;
	ListNode *next;
	ListNode() : val(0), next(nullptr) {}
	ListNode(int x) : val(x), next(nullptr) {}
	ListNode(int x, ListNode *next) : val(x), next(next) {}
};
```

#### Create an Object with Class

```c++
ListNode* newNode = new ListNode(digitNumSum, nullptr)
```

**Remind: when creating an object, it returns a pointer to the created object, so the type here is `ListNode*`.**

#### Access Object's Members

```c++
//*newNode.val == newNode->val
newNode->val
```

Because `newNode` is a pointer to an object, to access its members, we can use the better syntax `->` to replace `*.`.
