## Ownership and smart pointers

`Box` and `Rc` are smart pointers that manage memory on the heap differently.

### Box (Heap Allocation):

Use `Box` when you need a single owner for heap-allocated data.

```rust
fn main() {
  let name_on_heap = Box::new(String::from("Alice")); // Allocate "Alice" on the heap
  println!("Name: {}", name_on_heap); // Dereference the Box to access the value

  // `name_on_heap` goes out of scope here, and the memory on the heap is freed automatically.
}
```

### Rc (Reference Counting):

Use `Rc` when you need multiple owners to share the same data concurrently.
`Rc` keeps track of how many references (owners) exist for a value. It's automatically deallocated when the last reference goes out of scope.

```rust
// creating a linked list node with `Rc`

use std::rc::Rc;

struct Node {
  value: i32,
  next: Option<Rc<Node>>,
}

fn main() {
  let node1 = Rc::new(Node { value: 1, next: None });
  let node2 = Rc::new(Node { value: 2, next: Some(Rc::clone(&node1)) }); // Clone the reference count for node1
  node1.next = Some(Rc::clone(&node2)); // Clone the reference count for node2

  println!("Node 1 value: {}", node1.value);
  println!("Node 2 value: {}", node2.value);

  // Both `node1` and `node2` go out of scope here, but the underlying data is only freed
  // when the last reference count reaches 0 (in this case, after both nodes go out of scope).
}
```
