# Linked Lists

Linked lists are a fundamental data structure that store elements in a linear fashion, where each element (node) points to the next one in the sequence. In Rust, linked lists offer dynamic allocation and flexibility compared to arrays.

**1. Building a Node:**

The basic building block of a linked list is a node. A node typically contains two parts:

* Data: The actual information stored in the node (e.g., an integer, a string).
* Next pointer: A reference to the next node in the list, or `None` if it's the last node.

```rust
struct Node<T> {
  data: T,
  next: Option<Box<Node<T>>>, // Option<Box<Node<T>>> for handling None and ownership
}
```

**2. Creating a Linked List:**

A linked list itself is essentially a pointer to the first node (head) or `None` if the list is empty.

```rust
struct LinkedList<T> {
  head: Option<Box<Node<T>>>,
}

impl<T> LinkedList<T> {
  fn new() -> Self {
    Self { head: None }
  }
}
```

**3. Common Linked List Operations:**

* **`push` (Insert at the end):** Adds a new element to the end of the list.

```rust
impl<T> LinkedList<T> {
  fn push(&mut self, data: T) {
    let new_node = Box::new(Node { data, next: None });
    match self.head {
      None => self.head = Some(new_node),
      Some(ref mut node) => node.next = Some(new_node),
    }
  }
}
```

* **`pop` (Remove from the end):** Removes and returns the last element from the list, or `None` if empty.

```rust
impl<T> LinkedList<T> {
  fn pop(&mut self) -> Option<T> {
    match self.head {
      None => None,
      Some(ref mut node) => match node.next.take() { // Take ownership of next node
        None => {
          self.head = None;
          Some(node.data)
        }
        Some(next_node) => {
          *node = *next_node; // Update head to point to the previous node
          Some(next_node.data)
        }
      },
    }
  }
}
```

* **`insert` (Insert at a specific position):** Inserts a new element at a given index (0-based indexing).

```rust
impl<T> LinkedList<T> {
  fn insert(&mut self, index: usize, data: T) {
    if index == 0 {
      self.head = Some(Box::new(Node { data, next: self.head.take() }));
      return;
    }

    let mut curr = self.head.as_mut();
    let mut prev = None;
    let mut i = 0;
    while let Some(ref mut node) = curr {
      if i == index {
        curr.next = Some(Box::new(Node { data, next: node.next.take() }));
        return;
      }
      prev = Some(curr);
      curr = node.next.as_mut();
      i += 1;
    }

    // Handle insertion at the end
    if let Some(mut node) = prev {
      node.next = Some(Box::new(Node { data, next: None }));
    }
  }
}
```

**4. When to Use Linked Lists:**

* **Dynamic Size:** Linked lists are ideal when the size of the data collection is unknown or needs to grow or shrink frequently during program execution. (Arrays have a fixed size.)
* **Efficient Insertions/Deletions in the Middle:** Inserting or deleting elements in the middle of a linked list is a constant time operation (O(1)), while it's expensive (O(n)) for arrays that require shifting elements.

**5. Working Examples:**

* **Example 1: Implementing a Simple Stack** (LIFO - Last In, First Out)

```rust
let mut stack = LinkedList::new();
stack.push(10);
stack.push(20);
println!("Popped: {:?}", stack.pop()); // Prints 2

println!("Top element: {:?}", stack.head); // Prints "Some(Box { data: 10, next: None })"

stack.push(30);
stack.pop();
stack.pop(); // Stack becomes empty

println!("Is stack empty? {}", stack.head.is_none()); // Prints "true"
```

* **Example 2: Implementing a Simple Queue** (FIFO - First In, First Out)

```rust
let mut queue = LinkedList::new();
queue.push(10);
queue.push(20);

println!("Dequeued: {:?}", queue.pop()); // Prints 10

queue.push(30);
println!("Front element: {:?}", queue.head); // Prints "Some(Box { data: 20, next: Some(Box { data: 30, next: None }) })"
```

**6. Additional Considerations:**

* Linked lists generally have more overhead compared to arrays due to the extra pointer in each node.
* Random access (accessing elements by index) is slower in linked lists compared to arrays, as it requires traversing the list from the beginning.
