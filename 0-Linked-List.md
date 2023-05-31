## Linked List

Linked lists are passed around as the reference to the first node.

## Linked List Node

```python
class ListNode(object):
	def __init__(self, val=0, next=null):
		self.val = val
		self.next = next
```

- general linked list node consists of content and reference to next node.
- the last node's reference is `null`

## Build a linked list

```python
firstNode = new ListNode()
secondNode = new ListNode()
thirdNode = new ListNode()

firstNode.val = "Carol"
secondNode.val = "Bob"
thirdNode.val = "Alice"

firstNode.next = secondNode
secondNode.next = thirdNode
thirdNode.next = null
```

#### Build a linked list **recursively**

```python
resultLinkedList = null
pastNode = null

while(data is not depleted):
	newNode = ListNode(val=data, next=null)
	if(pastNode == null):
		pastNode = newNode
		resultLinkedList = newNode
	else:
		pastNode.next = newNode
		pastNode = newNode
```



## Print a linked list (Traverse Linked List)

```python
x = firstNode
while (x != null):
  print(x.item)
  x = x.next
```

### Get length of the linked list

```python
linkedListLength = 0
x = firstNode
while (x != null):
	linkedListLength++
  x = x.next
```

