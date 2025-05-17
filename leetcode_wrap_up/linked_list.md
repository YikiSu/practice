# Introduction
A linked list is a linear data structure where elements (called nodes) are stored in non-contiguous memory locations. Unlike arrays, linked lists don’t require contiguous memory allocation, making them dynamic in size and efficient for insertions/deletions.

# Basic Operations
## Traversal (visiting every node)
```python
def traverse(head):
    current = head
    while current is not None:
        print(current.data)
        current = current.next
```

## Insertion
### at the beginning
```python
new_node = Node(data)
new_node.next = head
head = new_node
```
### at the end
```python
new_node = Node(data)
if head is None:
    head = new_node
else:
    current = head
    while current.next is not None:
        current = current.next
    current.next = new_node
```
### at a Given Position
```python
# Create the New Node
new_node = Node(data)
# Start at the Head
current = head
# Traverse to the Node Before the Insertion Position (We move current position - 1 times to reach the node just before where the new node should be inserted.)
for _ in range(position - 1):
    if current.next is None:  # If current.next is None, we stop early (to avoid going out of bounds).
        break
    current = current.next
# The new node's next pointer is set to the node that was originally after current.
new_node.next = current.next
# The current node now points to the new node.
current.next = new_node
```

## Deletion
### Delete by Value
```python
if head is None:
    return
if head.data == value:
    head = head.next
else:
    current = head
    while current.next is not None:
        if current.next.data == value:
            current.next = current.next.next
            break
        current = current.next
return head
```

### Delete at Position
```python
if position == 0:
    head = head.next
else:
    current = head
    for _ in range(position - 1):
        if current.next is None:
            break
        current = current.next
    if current.next is not None:
        current.next = current.next.next
return head
```
