# Enums

#### - Enums are like Algebraic Data Types in Haskell rather than enums in C or Java.

```rust
enum Color {
    Red,
    Green,
    Blue,
}
```
#### - We can associate data and methods with variants.
```rust
enum DispenserItem {
    Empty,  // No data
    Ammo(u8)    // Single Data
    Things(String, i32),    // A tuple of data
    Place {x: i32, y: i32}, // A anonymous struct of data
}
```
### An enum is like a union in C, but safer and much better.
#### - When you crate an enum, value can be any one of these variables.

```rust
use DispenserItem::*;

let item1 = Empty;
let item2 = Ammo(5);
let item3 = Things("Hello".to_string(), 42);
let item4 = Place {x: 5, y: 10};
``` 
- It can be any one of those, but a variable can only be one of those at a time.
- You can implement functions and methods for enums.
```rust
impl DispenserItem {
    fn display(&self) {
        match self {
            Empty => println!("Empty"),
            Ammo(n) => println!("Ammo: {}", n),
            Things(s, n) => println!("Things: {} {}", s, n),
            Place {x, y} => println!("Place: {} {}", x, y),
        }
    }
}
```
- You can also use Enums with generics.
```rust
enum Option<T> {
    Some(T),
    None,
}
```
- `Option<T>` is a generic enum that we will use many times.
  - `T` is a type parameter, which can be any value.
  - `Option<T>` enum represents, something is either absent or present.
  - You either have some value wrapped in `Some(T)` or you have nothing in `None`.
- Because enums can have all sorts of data, you need to use patterns to examine them.
- If you want to check for a single variant, you can use `if let`.
```rust
if let Some(x) = my_variable {
    println!("x is {}", x);
}
```
- If you want to check for multiple variants, you can use `match`.
```rust
match my_variable {
    Some(x) => println!("x is {}", x),
    None => println!("No value"),
}
```
- `match` expression require you to write outcome for every branch of the enum.
- You can use `_` for default or catch-all branch.
```rust 
match my_variable {
    _ => println!("Some value"),
}
```
- Either all branch need to return nothing, or need to return the same type.


## Option enum `Option<T>`
#### It is used whenever you know things can be absent.
#### It is included in the prelude, so you don't need to import it.
```rust
enum Option<T> {
    Some(T),
    None,
}
```
### Creating a none variant of the Option
```rust
let mut x: Option<i32> = None;
```
- Compiler will infer the type of `x` as `Option<i32>`.
```rust
let mut x = None;
x = Some(5); // this will tell the compiler that x is of type Option<i32>
x.is_some(); // true // Check if x is Some
x.is_none(); // false // Check if x is None

for i in x {
    println!("{}", i);  // prints 5
}
```
- `is_some` and `is_none` are methods of `Option` enum.
- `for` loop will only run if `x` is `Some`.

## Result enum `Result<T, E>`
### Result is used whenever something may have useful result or might have an error.
```rust
#[must_use]
enum Result<T, E> {
    Ok(T),
    Err(E),
}
```
- `#[must_use]` is an attribute that tells the compiler that the return value of this function must be used.
- `Result` is also included in the prelude, so you don't need to import it.
- `T` and `E` are type parameters, which can be any type, and can be different.
- `Ok(T)` variant is used to represent a successful result.
- `Err(E)` variant is used to represent an error.
```rust
use std;:fs::File;

fn main() {
    File::open("foo");  // This will return a Result
}
```
- Since we didn't do anything with Result returned in above code, compiler will issue a warning.

```rust
use std::fs::File;

fn main() {
    let res = File::open("foo");
    let f = res.unwrap();  // This will panic if res is Err
}
```
- `unwrap` is a method of `Result` enum, which will panic if `res` is `Err`.
- `unwrap` will result in correct struct if `res` is `Ok`, otherwise it will panic.
- We can also use `expect` method, which will panic with a message.
```rust
let f = res.expect("Failed to open file");
```
- There are also helper methods, `is_ok` and `is_err`.
```rust
if res.is_ok() {
    let f = res.unwrap();
}
```
- In the above case, program will never crash, because we are checking if `res` is `Ok` before unwrapping it.
- Of course, we can do full pattern matching with `match`.
```rust
match res {
    Ok(f) => println!("Opened file"),
    Err(e) => println!("Failed to open file"),
}
```