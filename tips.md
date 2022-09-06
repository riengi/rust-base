# Useful Rust tips

## Minimize Rust Binaries

### release build 
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

## Get binary information about crates size share
Note: binary must contain symbols (strip = false)
```cargo build --release```
```cargo bloat --release --crates```


