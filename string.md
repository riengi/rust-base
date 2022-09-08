# String operations in Rust

### Split string to Vec<&str>
```rust
let str = "Let's have some fun";
let iter = str.split(" ");
let vec = iter.collect();

// oneline
let vec = "Let's have some fun".split(" ").collect();
```

