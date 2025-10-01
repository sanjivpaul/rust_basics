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

## 1. Handling Environment Arguments

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

## 2. Understanding the nth method

```rust
use std::env::{args, Args};

fn main() {
    let mut args:Args = args();
    let first  = args.nth(1).unwrap();
    let operator = args.nth(0).unwrap();
    let second = args.nth(0).unwrap();

    let first_number = first.parse::<f32>().unwrap();
    let second_number = second.parse::<f32>().unwrap();
    println!("{:?} {} {}", first, operator, second);
}
```

## Declaring a function

```rust
fn operate(operator:char, first_number:f32, second_number:f32){

}
```

## Formating Output String

```rust
use std::env::{args, Args};

fn main() {
    let mut args:Args = args();
    let first  = args.nth(1).unwrap();
    let operator = args.nth(0).unwrap().chars().next().unwrap();
    let second = args.nth(0).unwrap();

    let first_number = first.parse::<f32>().unwrap();
    let second_number = second.parse::<f32>().unwrap();
    let result = operate(operator, first_number, second_number);

    println!("{:?}", output(first_number, operator, second_number, result));
}

fn operate(operator: char, first_number: f32, second_number:f32)-> f32{
    if operator == '+' {
        first_number + second_number
    }else if operator == '-' {
        first_number - second_number
    }else if operator == '*' {
        first_number * second_number
    }else if operator == '/' {
        first_number / second_number
    }else{
        0.0
    }

}

fn output(first_number: f32, operator: char, second_number: f32, result: f32) -> String{
    format!("{} {} {} = {}", first_number, operator, second_number, result)
}

```

## Match Controll Flow

```rust
fn operate(operator: char, first_number: f32, second_number:f32)-> f32{
    match operator {
        '+' => first_number + second_number,
        '-' => first_number - second_number,
        '*' => first_number * second_number,
        '/' => first_number / second_number,
        '%' => first_number % second_number,
        _ => 0.0,
    }
}
```

## Panicking!

```rust
fn operate(operator: char, first_number: f32, second_number:f32)-> f32{
    match operator {
        '+' => first_number + second_number,
        '-' => first_number - second_number,
        '*' | 'x' | 'X' => first_number * second_number,
        '/' => first_number / second_number,
        '%' => first_number % second_number,
        _ => panic!("invalid operator used.")
    }
}
```

## Building & Release

```bash
cargo build --release
```

then you can run

```bash
sanjiv~$ ./target/release/calculator 2 + 2
"2 + 2 = 4"
sanjiv~$
```
