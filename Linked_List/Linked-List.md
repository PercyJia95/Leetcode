## Linked List Node

```python
class ListNode(object):
	def __init__(self, val=0, next=None):
		self.val = val
		self.next = next
```

- general linked list node consists of content and reference to next node.
- the last node's reference is `null`

## Build a linked list

```
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

## Print a linked list

