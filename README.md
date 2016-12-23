# Pipers

A simple Rust library that allows you to pipe commands into
each other.

## Installation
In your Cargo.toml:

```toml
[dependencies]
pipers = "1.0.0"
```

## How to use

It's quite simple really!

```rust
let out = Pipe::new("ls /")      // Put in your first command
              .then("grep usr")  // Choose the command you want to pipe into
              .then("head -c 1") // Keep chaining the pipes
              .finally()         // Turn the Pipe into a Result<Child>
              .expect("Commands did not pipe")
              .wait_with_output()
              .expect("failed to wait on child");

assert_eq!("u", &String::from_utf8(out.stdout).unwrap());
```

## License

Licensed under either of

 * Apache License, Version 2.0, ([LICENSE-APACHE](LICENSE-APACHE) or http://www.apache.org/licenses/LICENSE-2.0)
 * MIT license ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT)

at your option.

### Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, as defined in the Apache-2.0 license, shall be dual licensed as above, without any
additional terms or conditions.
