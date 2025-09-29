# Rust

## Create Project Using Cargo

Creating new Project

```bash
cargo new calculator
```

Run new project

```bash
cd calculator
cargo run
```

## Handling Environment Arguments

```rust
use std::env::{args, Args};

fn main() {
    let args:Args = args();
    println!("{:?}", args);
}
```

run

```bash
cargo run -- "sanjiv"
```

output

```bash
   Compiling calculator v0.1.0 (/Users/sanjiv/Developer/Code/rust/rust_basics/calculator)
    Finished `dev` profile [unoptimized + debuginfo] target(s) in 0.69s
     Running `target/debug/calculator sanjiv`
Args { inner: ["target/debug/calculator", "sanjiv"] }
```
