## Generic types and functions

- **Basic Idea:**
    - Imagine a function that can work with numbers (integers, floats) or strings. Generics make this possible.
    - We use placeholders like `<T>` to represent unknown types.

```rust
fn get_value<T>(value: T) -> T {
    value
}

fn main() {
  let val1: i32 = 5;
  let val2: f32 = 25.5;

  println!("value 1 : {}", get_value(val1));
  println!("value 2 : {}", get_value(val2));
}
```

- **Multiple Generic Types:**
    - Functions can have multiple generic type parameters.

```rust
struct Pair<T, U> {
  left: T,
  right: U,
}

impl<T, U> Pair<T, U> {
  fn new(left: T, right: U) -> Self {
    Pair { left, right }
  }
}

fn main() {
  let int_pair = Pair::new(1, 2);
  let str_pair = Pair::new("Rust", "is awesome!");

  println!("Integer pair: ({}, {})", int_pair.left, int_pair.right);
  println!("String pair: ({}, {})", str_pair.left, str_pair.right);
}
```

- **Where Clauses:**
    - Add additional constraints on generic types for more control.

```rust
fn sum_all<T>(list: &[T]) -> Option<T>
  where T: std::ops::Add<Output = T> + Copy // Use Add trait and Copy trait
{
    if list.is_empty() {
        return None;
    }

    let mut sum = list[0];
    for &item in &list[1..] { // Iterate from the second element onwards
        sum = sum + item;
    }
    Some(sum)
}

fn main() {
  let numbers: Vec<i32> = vec![1, 2, 3];
  let sum = sum_all(&numbers);

  match sum {
    Some(value) => println!("Sum: {}", value),
    None => println!("Empty list"),
  }
}
```
