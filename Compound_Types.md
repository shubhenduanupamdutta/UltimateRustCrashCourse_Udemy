# Compound Types
- #### Gather multiple values of other types into one type.

## Tuple
- #### A collection of values of different types.

### Syntax
- `let tup: (i32, f64, u8) = (500, 6.4, 1);`
- To access elements: 
- `let x = tup.0;` Field expression
- All at once:
- `let (x, y, z) = tup;`
- Tuples have maximum arity of 12. Beyond that, they can only be used with limited functionality.

## Array
- #### A collection of values of the same type.

### Syntax
- `let a: [i32; 5] = [1, 2, 3, 4, 5];`
- To access elements: `let x = a[0];`
- Arrays have maximum size of `32`, beyond that they lose most of their functionality.
- Arrays live on stack by default, and are of fixed size.


## Vectors
- #### A collection of values of the same type.
- #### Vectors are more flexible than arrays.

### Syntax
- `let v: Vec<i32> = Vec::new();`