# Ownership

- Ownership is Rust's most unique feature, and it enables Rust to make memory safety guarantees without needing a garbage collector.


## 3 Rules of Ownership
1. **Each Value Has an Owner**: There is no value in memory, no data on the stack or heap, that doesn't have a variable that owns it.
2. **There Can Only Be One Owner**: There can only be one owner of a value at a time. No variable may share the ownership. Other value may _borrow_ the value, but only one variable can own it.
3. **Value is Dropped When Owner Goes Out of Scope**: When the owner goes out of scope, the value is dropped immediately.

## Ownership in Action
```rust
let s1 = String::from("hello");
let s2 = s1;
println!("{}", s1); // Error: value borrowed here after move
```
- Value of `s1` is composed of 3 components, **pointer**, **length**, and **capacity**. Pointer points to the memory on the heap where the value is stored.
- When `s1` is assigned to `s2`, the value of `s1` is _moved_ to `s2`. Now, `s2` is the owner of the value, and `s1` is no longer valid. 
- Compiler will throw an error when `s1` is used after the move.
- We can use `clone` method to create a deep copy of the value.
```rust
let s1 = String::from("hello");
let s2 = s1.clone();
println!("{}", s1); // hello
```
- `.clone()` method is expensive, and it is used only when necessary, because it copies the entire value (both on stack and heap) is copied.
- Rust uses `clone` to mean deepcopy and `copy` to mean shallow copy. For example, `i32` is `Copy` type, and it is copied when assigned to another variable.
- When the owner goes out of scope, the stacked memory (frame containing the variable) and the heap memory (value) are deallocated.