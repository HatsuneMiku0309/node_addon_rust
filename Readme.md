Node_Addon
===

[TOC]

## Develop
add file name `lib.rs`, maybe the fixed name

## Build

* production
```bash
$ napi build --platform --release
```

* test
```bash
$ napi build --platform
```

*other
I don't know --pipe ?
```bash
"build": "napi build --platform --release --pipe \"prettier -w\"",
"build:debug": "napi build --platform --pipe \"prettier -w\"",
```

## Resource
```bash
$ cargo install cargo-edit
$ cargo add {lib_name}
$ cargo update
```
### Rust
You need install lib

[napi](https://crates.io/crates/napi/2.6.3)
```bash
$ cargo add napi
$ cargo add napi-derive
$ cargo add napi-build
```

and set Cargo.toml
```toml
[package]
name = "node_addon"
version = "0.1.0"
edition = "2021"

[lib]
crate-type = ["cdylib"] // you in node style?

[dependencies]
napi = "2.6.3"
napi-build = "2.0.1" // maybe can remove this
napi-derive = "2.6.0"

[build-dependencies]
napi-build = "2.0.1" // build use
```

### Nodejs
You need install some node_module in golbal

[@napi-rs/cli](https://www.npmjs.com/package/@napi-rs/cli)
```bash
$ npm i -g @napi-rs/cli
```

and set package.json
```json
{
  "name": "{project_name}",
  "version": "0.1.0",
  "napi": {
    "name": "fib", // binary name
    "triples": {
      "defaults": true, // default true, if this value is true, will build `x86_64-pc-windows-msvc`, `x86_64-apple-darwin` and `x86_64-unknown-linux-gnu`
      "addition": [
        "x86_64-unknown-linux-musl",
        "x86_64-unknown-freebsd",
        "aarch64-unknown-linux-gnu"
      ]
    }
  }
}
```
