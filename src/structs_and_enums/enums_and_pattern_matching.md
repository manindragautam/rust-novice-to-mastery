## Enums and pattern matching

Enums and pattern matching are powerful tools in Rust for defining sets of possible values and handling them efficiently. 

- **Enums (Enumerations):**
    - Define a set of named constants (variants) that belong to a single type.
    - Useful for representing a finite set of possibilities.

```rust
enum TrafficLight {
  Red,
  Yellow,
  Green,
}

fn main() {
  let light = TrafficLight::Yellow;
  // ... (handle the traffic light state)
}
```

- **Pattern Matching (Basic):**
    - A way to compare a value against different possible variants of an enum.
    - Similar to a `switch` statement in other languages.

```rust
enum TrafficLight {
  Red,
  Yellow,
  Green,
}

fn main() {
  let light = TrafficLight::Yellow;

  match light {
    TrafficLight::Red => println!("Stop"),
    TrafficLight::Yellow => println!("Caution"),
    TrafficLight::Green => println!("Go"),
  }
}
```

- **Data with Variants:**
    - Enums can hold different types of data associated with each variant.

```rust
enum User {
  Active(String),  // Username for active users
  Inactive,        // Inactive users
  Guest(u32),     // Guest users with a temporary ID
}

fn main() {
  let user1 = User::Active(String::from("Alice"));
  let user2 = User::Inactive;

  // Access data based on the variant using match or if let
  if let User::Active(name) = user1 {
    println!("Active user: {}", name);
  }
}
```

- **Wildcard Variant (`_`):**
    - Use the `_` variant to catch all unmatched cases in the `match` expression.

```rust
enum Coin {
  Heads,
  Tails,
}

fn main() {
  let coin_flip = Coin::Tails;

  match coin_flip {
    Coin::Heads => println!("Heads"),
    Coin::Tails => println!("Tails"),
    _ => println!("Invalid coin flip"), // Catches unexpected values
  }
}
```

- **Matching Ranges and Values:**
    - Use pattern matching with ranges and values for more specific checks.

```rust
enum Grade {
  A(f32), // A grade with a score
  B,      // B grade
  C(f32), // C grade with a score (optional)
  D,
  F,
}

fn main() {
  let grade = Grade::A(92.5);

  match grade {
    Grade::A(score) if score >= 90.0 => println!("Excellent! (A with score {:.1})", score),
    Grade::A(_) => println!("Good job! (A)"),
    _ => println!("Keep practicing!"),
  }
}
```
