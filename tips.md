# Useful Rust tips

## Minimize Rust Binaries

### Release build 
```cargo build --release```

### Strip symbols from binary
```
# Cargo.toml
[profile.release]
strip = true 
```
### Optimize build for size
```
# Cargo.toml
[profile.release]
opt-level = "s"
```

### Link time optimization
Warn: Longer linking time
```
# Cargo.toml
[profile.release]
lto = true
```
### Compile time optimization
Warn: Longer compile time
```
# Cargo.toml
[profile.release]
codegen-units = 1
```
---

## Get binary information about crates size share
Note: binary must contain symbols (strip = false)
```cargo build --release```
```cargo bloat --release --crates```

---

## Threads (and memory) under control
Bulding and especially testing can depleat memory and froze the OS. Limiting maximum used threads can avoid this.

### Building with thread limit
```
# limit building to 4 threads
cargo build -j 4
# or
cargo build --jobs 4
```

### Testing with thread limit
```
# limit testing to 4 threads
cargo test -j 4
# or
cargo test --jobs 4
```