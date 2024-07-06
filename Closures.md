# Closures
#### Closure is an anonymous function that borrow or captures some data from the scope it is nested in.

## Syntax
```rust
|x, y| { x + y }
```
- `|x, y|` is the parameter list. Parameters are separated by commas, and inside two pipes `|`. They are not used with type annotations.
- `{ x + y }` is the body of the closure. It is a block of code that is executed when the closure is called. The last expression in the block is implicitly returned.
- This creates an anonymous function, called **closure** that takes two parameters `x` and `y`, and returns their sum.
- Types of the arguments and return type can be inferred by the compiler from how you use the closure.
- Closures can capture variables from the scope they are defined in. They can capture variables by reference, by mutable reference, or by value.
- Closures can be stored in variables, passed as arguments to functions, and returned from functions.
```rust
let add = |x, y| { x + y };
let result = add(1, 2);
println!("{}", result); // 3
```
- We can also leave the parameter list empty if the closure doesn't take any arguments.
- Closure will borrow a reference to the values in the enclosing scope by default.
```rust
let s = "🍓".to_string();
let f = || {
    println!("{}", s);
};
f(); // 🍓
```
- If we want to move the values into the closure, we can use the `move` keyword.
```rust
let s = "🍓".to_string();
let f = move || {
    println!("{}", s);
};
f(); // 🍓
```
- If we want to do some functional style programming, closure can be used with iterators.
```rust
let mut v = vec![1, 2, 3];
v.iter()
    .map(|x| x + 1)
    .for_each(|x| println!("{}", x));

v.iter()
    .map(|x| x * 2)
    .filter(|x| *x > 10)
    .fold(0, |acc, x| acc + x);
```
- `fold` is used to accumulate the values of the iterator. It takes an initial value and a closure that takes two arguments, the accumulator and the current value, and returns the new accumulator.