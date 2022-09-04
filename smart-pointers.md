# Smart pointers in Rust

| Pointer type | Major feature |
| ------------ | --------------| 
| Box          | clone duplicates data  |
| Cell         | changable reference    |
| RefCell      | check on runtime       |
| Rc           | lone share data        |
| Arc          | thread-safe Rc         |
| RwLock       | rw data across threads |
| Mutex        | RwLock wihh only holder|


---
### Box
Smart pointer for storing data
Provides:
* indirection 
* heap allocation
* auto memory cleanup via Deref trait and Drop trait

Usage: 
* when we don't know data type size at compile time (recursive types, etc.)
* be sure to transfer large data ownership without copying tem
* to own that implements specific trait rather than being specific type

```rust
let boxed = Box::new("Boxed &str aka Box<&str> type aka &str stored on heap");
```
  
For recursive types, Cons Lists for example, compilator cannot calculte type size at compile time but Box has constant and known size so it can be used for these scenerios.

This is unknown to theoretically infinite size, it will not be compiled. 
```rust
enum List {
    Cons(i32, List),
    Nil
}
```
This is known size as Box has usize size
```rust
enum List {
    Cons(i32, Box<List>),
    Nil
}
```
For enum compile consider highest possible size needed, ie. sizeof Cons(i32,Box<List>) 
