# Collections

## Vectors `Vec<T>`
#### - Vector is a generic collection, which holds elements of the same type.
- It is used where you will use list or arrays in other languages.
- It is most commonly used collection in Rust by far.
```rust
let mut v: Vec<i32> = Vec::new();
v.push(5);
v.push(6);
v.push(7);
v.push(8);
```
- You can also use `vec!` macro to create a vector.
```rust
let v = vec![1, 2, 3, 4, 5];
```
- You can push values at the end of the vector using `push` method.
- Vectors act like a stack, so `.push()` adds to the end and `.pop()` removes from the end.
```rust
let mut v = vec![1, 2, 3, 4, 5];
let five = v.pop();
```
- You can access elements of a vector using indexing.
```rust
let v = vec![1, 2, 3, 4, 5];
let third: i32 = v[2];
```

### Some useful methods
- `get()` method returns an `Option<&T>`.
- `get_mut()` method returns an `Option<&mut T>`.
- `iter()` method returns an iterator.
- `iter_mut()` method returns a mutable iterator.
- `insert()` method inserts an element at a given index.
- `remove()` method removes an element at a given index.
- `len()` method returns the length of the vector.
- `split()` method splits the vector into two at a given index.
- `join()` method joins the elements of a vector with a given separator.
- `sort()` method sorts the elements of a vector.
- `splice()` method replaces a range in the vector with another range.
- `binary_search()` method searches for a value in a sorted vector.
- **And many more...**

## HashMaps `HashMap<K, V>`
#### - HashMap is a generic collection where you specify the type of key and type of value.
#### - You access the value by key
- In some languages HashMap is called Dictionary or Map.
- Point of HashMap is to insert, lookup and remove values at constant time `O(1)`.
```rust
let mut h: HashMap<u8, bool> = HashMap::new();
h.insert(1, true);
h.insert(2, false);
let have_five = h.remove(&5).unwrap();
```
- You can insert a new key-value pair using `insert` method.
- You can remove a key-value pair using `remove` method.
- Remove returns an `Option<V>`, which is `Some(value)` if the key was found and `None` if the key was not found.
- You can access the value by key using `get` method.
- `unwrap()` method is used to get the value out of `Option<V>`.
```rust
let h = HashMap::new();
h.insert("one", 1);
h.insert("two", 2);
let one = h.get("one").unwrap();
```

## VecDeque
#### - VecDeque is a double-ended queue. It implements a ring buffer.
#### - It can efficiently remove items from front and the back.
#### - It is a little less efficient that Vec, but it is more flexible.


## LinkedList
#### - LinkedList is a doubly linked list.
#### - It is quick at adding or removing elements from arbitrary points, but slow at everything else.

## HashSet
#### - It is a hashing implementation of a set, that performs set operations really efficiently.

## BinaryHeap
#### - It is a priority queue, where the highest priority element is always at the front.

## BTreeMap, BTreeSet
#### - Alternative map and set implementations using a modified binary tree.
#### - You usually prefer to use these when you need map keys, or set values to always be sorted.