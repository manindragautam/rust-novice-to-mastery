## Organizing code with modules

Modules in Rust are a way to organize code within a crate (we'll cover crates shortly). They allow you to group related functionality together and control the visibility and privacy of items (functions, structs, enums, etc.).

**Defining Modules**

You can define a module using the `mod` keyword. Here's an example of creating a module named `math` inside the `main.rs` file:

```rust,noplaypen
// main.rs
mod math;

fn main() {
    println!("2 + 3 = {}", math::add(2, 3));
}
```

The contents of the `math` module are typically placed in a separate file named `math.rs` within the same directory:

```rust,noplaypen
// math.rs
pub fn add(a: i32, b: i32) -> i32 {
    a + b
}
```

**Visibility and Privacy**

By default, items in a module are private and can only be accessed within the same module. To make an item public and accessible from other modules or crates, you need to use the `pub` keyword:

```rust,noplaypen
// math.rs
pub fn add(a: i32, b: i32) -> i32 {
    a + b
}

fn subtract(a: i32, b: i32) -> i32 {
    a - b
}
```

In this example, `add` is a public function, while `subtract` is private and can only be used within the `math` module.

**Nested Modules**

Modules can be nested inside other modules to create a hierarchical structure:

```rust
// main.rs
mod math {
    pub mod arithmetic {
        pub fn add(a: i32, b: i32) -> i32 {
            a + b
        }
    }

    pub mod trigonometry {
        pub fn sin(angle: f64) -> f64 {
            angle.sin()
        }
    }
}

fn main() {
    println!("2 + 3 = {}", math::arithmetic::add(2, 3));
    println!("sin(0.5) = {}", math::trigonometry::sin(0.5));
}
```

**Module Paths**

To access items from a module, you can use the module path syntax:

```rust,noplaypen
math::arithmetic::add(2, 3);
```

Alternatively, you can bring specific items into scope using the `use` keyword:

```rust,noplaypen
use math::arithmetic::add;

fn main() {
    println!("2 + 3 = {}", add(2, 3));
}
```
