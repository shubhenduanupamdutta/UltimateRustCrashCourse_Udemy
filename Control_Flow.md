# Control Flow

## If Statements

### Example
```rust
if num == 5 {
    msg = "five";
} else if num == 4 {
    msg = "four";
} else {
    msg = "not four or five";
}
```
### Notes
- The condition must be a boolean expression. Rust doesn't like type coercion.
- You can chain the condition using `else if`.
- You can use `else` to catch all other cases.

### If is an expression not an statement, so it can evaluate to a value, for example.
```rust
msg = if num == 5 {
    "five"
} else if num == 4 {
    "four"
} else {
    "not four or five"
};
```
- In this case `msg` will be assigned the value of the block that is executed.
- There are no semicolons at branch values, so that the value is returned from the block as `tail expressions`.
- We can't use return here, because it would return from the function, not the block.
- All the blocks must return the same type, since rust is strongly typed.
- There is `;` at the end of if expression. If you don't use the value of if expression, rust will allow you to leave out `;` at the end of the expression. But if you use it, you must put `;` at the end of the expression.
- Braces are not optional, they are mandatory.

## Loop
### Unconditional Loop
```rust
loop {
    println!("Loop forever!");
    break;
}
```
- `loop` is an unconditional loop, it will run forever unless you use `break`.

#### Nested loops and breaking out of them
```rust
'outer: loop {
    println!("Entered the outer loop");
    'inner: loop {
        println!("Entered the inner loop");
        break 'outer;
    }
    println!("This point will never be reached");
}
```
- In this case when breaking it will break out of the outer loop.
- Same thing can be done with `continue`.

### While Loop
```rust
while dizzy() {
    // do stuff
}
```
- The condition must be a boolean expression.
- All the things which can be done in unconditional loop can be done in while loop.
- Except it will also break out when the condition is false.


### For Loop
```rust
for num in [1, 2, 3].iter() {
    println!("{}", num);
}
```
- `for` loop is used to iterate over a collection.
- `.iter()` method is most common ways to get an iterator.
- Iterator you use determines which items are returned and their order.
- `.iter()` iterates over all items of a collection in order if collection is ordered, randomly if collection is unordered.
- You can stack `map`, `filter` and `fold` and like methods and they will be lazily evaluated.
- For loop can take item and destruct them.
```rust
let array = [(1, 2), (3, 4), (5, 6)];
for (a, b) in array.iter() {
    println!("a: {}, b: {}", a, b);
}
```
- In the above case `a` and `b` will be destructed from the tuple, and are local to the body of the for loop.
- Ranges in for loop.
```rust
for i in 0..5 {
    println!("{}", i);
}
``` 
- Syntax is `start..end` where `start` is inclusive and `end` is exclusive.
- You can also use `start..=end` to make `end` inclusive.