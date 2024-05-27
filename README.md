# Obfuscation

This repository contains a Rust implementation for IPv4 address obfuscation and deobfuscation. This project is designed to obfuscate shellcode data into a series of IPv4 addresses and deobfuscate them back into the original data. This can be particularly useful in contexts where hiding or encoding binary data within an IPv4 address format is desirable.

## Features

- **IPv4 Obfuscation:** Converts binary shellcode into a series of IPv4 addresses.
- **IPv4 Deobfuscation:** Converts a series of IPv4 addresses back into the original binary shellcode.

## Getting Started

### Prerequisites

- Rust (version 1.54 or later)
- Cargo (Rust's package manager)

### Installation

Clone the repository:

```sh
git clone https://github.com/mranv/Obfuscation.git
cd Obfuscation
```

Build the project:

```sh
cargo build
```

Run the project:

```sh
cargo run
```


or 

````
use the rustc compiler to compile the rust code.
````

## Usage

### Obfuscation

The `obfuscate_ipv4` function takes a mutable reference to a `Vec<u8>` containing the shellcode and prints the corresponding obfuscated IPv4 addresses.

Example:

```rust
use std::vec::Vec;

fn main() {
    let mut shellcode: Vec<u8> = vec![0xde, 0xad, 0xbe, 0xef, 0xca, 0xfe, 0xba, 0xbe];
    obfuscate_ipv4(&mut shellcode);
}
```

### Deobfuscation

The `deobfuscate_ipv4` function takes a `Vec<&str>` containing IPv4 address strings and returns a `Result<Vec<u8>, ()>` containing the deobfuscated shellcode.

Example:

```rust
use std::net::Ipv4Addr;
use std::vec::Vec;

fn main() {
    let ipv4_addr: Vec<&str> = vec!["222.173.190.239", "202.254.186.190"];
    match deobfuscate_ipv4(ipv4_addr) {
        Ok(shellcode) => println!("{:?}", shellcode),
        Err(_) => println!("Deobfuscation failed"),
    }
}
```

## Functions

### obfuscate_ipv4

```rust
fn obfuscate_ipv4(shellcode: &mut Vec<u8>)
```

Pads the input shellcode to a multiple of 4 bytes and prints the corresponding IPv4 addresses.

- **Parameters:**
  - `shellcode`: A mutable reference to a vector of bytes representing the shellcode.

### deobfuscate_ipv4

```rust
fn deobfuscate_ipv4(ipv4_addr: Vec<&str>) -> Result<Vec<u8>, ()>
```

Converts a series of IPv4 addresses back into the original binary shellcode.

- **Parameters:**
  - `ipv4_addr`: A vector of strings representing the IPv4 addresses.
- **Returns:** A `Result` containing the deobfuscated shellcode as a vector of bytes or an error.

## Contributing

1. Fork the repository.
2. Create your feature branch (`git checkout -b feature/AmazingFeature`).
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`).
4. Push to the branch (`git push origin feature/AmazingFeature`).
5. Open a pull request.

## License

Distributed under the MIT License. See `LICENSE` for more information.

## Contact

Project maintained by [mranv](https://github.com/mranv).

---

Thank you for using this IPv4 Obfuscation library. If you encounter any issues or have suggestions for improvements, please open an issue or submit a pull request.
