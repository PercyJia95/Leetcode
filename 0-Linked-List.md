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

## Reverse a Linked List

##### Pseudocode

1. Initialize three pointers: currentNode, pastNode, and nextNode.
1. To reverse the linked list, we need to let every currentNode point to pastNode, and nextNode point to currentNode.
1. Start by setting currentNode as the head of the linked list.
1. Traverse through the linked list using a loop until currentNode becomes null.
1. In each iteration, move the pastNode pointer to the currentNode, move the currentNode pointer to the nextNode, which was stored in the nextNode pointer. (**We have to store the currentNode.next to nextNode first, because once we have redirected currentNode.next to the pastNode, the pointer to nextNode will disappear.**)
1. After the loop ends, the pastNode pointer will be pointing to the last node of the original linked list, which will be the new head of the reversed linked list.
1. Return the pastNode pointer as the new head of the reversed linked list.

```python
currentNode = firstNode # or called "headNode"
pastNode = None
while (currentNode != null):
  nextNode = currentNode.next
  currentNode.next = pastNode
  pastNode = currentNode
  currentNode = nextNode

firstNode = pastNode # set up the new headNode
```

