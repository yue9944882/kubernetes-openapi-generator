# Rust API for openapi-v3

API under test

## Overview
This client/server was generated by the [openapi-generator]
(https://openapi-generator.tech) project.
By using the [OpenAPI-Spec](https://github.com/OAI/OpenAPI-Specification) from a remote server, you can easily generate a server stub.
-

To see how to make this your own, look here:

[README]((https://openapi-generator.tech))

- API version: 1.0.7

This autogenerated project defines an API crate `openapi-v3` which contains:
* An `Api` trait defining the API in Rust.
* Data types representing the underlying data model.
* A `Client` type which implements `Api` and issues HTTP requests for each operation.
* A router which accepts HTTP requests and invokes the appropriate `Api` method for each operation.

It also contains an example server and client which make use of `openapi-v3`:
* The example server starts up a web server using the `openapi-v3` router,
  and supplies a trivial implementation of `Api` which returns failure for every operation.
* The example client provides a CLI which lets you invoke any single operation on the
  `openapi-v3` client by passing appropriate arguments on the command line.

You can use the example server and client as a basis for your own code.
See below for [more detail on implementing a server](#writing-a-server).


## Examples

Run examples with:

```
cargo run --example <example-name>
```

To pass in arguments to the examples, put them after `--`, for example:

```
cargo run --example client -- --help
```

### Running the server
To run the server, follow these simple steps:

```
cargo run --example server
```

### Running a client
To run a client, follow one of the following simple steps:

```
cargo run --example client XmlExtraPost
cargo run --example client XmlOtherPost
cargo run --example client XmlOtherPut
cargo run --example client XmlPost
cargo run --example client XmlPut
```

### HTTPS
The examples can be run in HTTPS mode by passing in the flag `--https`, for example:

```
cargo run --example server -- --https
```

This will use the keys/certificates from the examples directory. Note that the server chain is signed with
`CN=localhost`.


## Writing a server

The server example is designed to form the basis for implementing your own server. Simply follow these steps.

* Set up a new Rust project, e.g., with `cargo init --bin`.
* Insert `openapi-v3` into the `members` array under [workspace] in the root `Cargo.toml`, e.g., `members = [ "openapi-v3" ]`.
* Add `openapi-v3 = {version = "1.0.7", path = "openapi-v3"}` under `[dependencies]` in the root `Cargo.toml`.
* Copy the `[dependencies]` and `[dev-dependencies]` from `openapi-v3/Cargo.toml` into the root `Cargo.toml`'s `[dependencies]` section.
  * Copy all of the `[dev-dependencies]`, but only the `[dependencies]` that are required by the example server. These should be clearly indicated by comments.
  * Remove `"optional = true"` from each of these lines if present.

Each autogenerated API will contain an implementation stub and main entry point, which should be copied into your project the first time:
```
cp openapi-v3/examples/server.rs src/main.rs
cp openapi-v3/examples/server_lib/mod.rs src/lib.rs
cp openapi-v3/examples/server_lib/server.rs src/server.rs
```

Now

* From `src/main.rs`, remove the `mod server_lib;` line, and uncomment and fill in the `extern crate` line with the name of this server crate.
* Move the block of imports "required by the service library" from `src/main.rs` to `src/lib.rs` and uncomment.
* Change the `let server = server::Server {};` line to `let server = SERVICE_NAME::server().unwrap();` where `SERVICE_NAME` is the name of the server crate.
* Run `cargo build` to check it builds.
* Run `cargo fmt` to reformat the code.
* Commit the result before making any further changes (lest format changes get confused with your own updates).

Now replace the implementations in `src/server.rs` with your own code as required.

## Updating your server to track API changes

Later, if the API changes, you can copy new sections  from the autogenerated API stub into your implementation.
Alternatively, implement the now-missing methods based on the compiler's error messages.

## Documentation for API Endpoints

All URIs are relative to *http://localhost*

Method | HTTP request | Description
------------- | ------------- | -------------
[****](docs/default_api.md#) | **POST** /xml_extra | 
[****](docs/default_api.md#) | **POST** /xml_other | 
[****](docs/default_api.md#) | **PUT** /xml_other | 
[****](docs/default_api.md#) | **POST** /xml | Post an array
[****](docs/default_api.md#) | **PUT** /xml | 


## Documentation For Models

 - [AnotherXmlInner](docs/AnotherXmlInner.md)
 - [AnotherXmlObject](docs/AnotherXmlObject.md)
 - [DuplicateXmlObject](docs/DuplicateXmlObject.md)
 - [XmlInner](docs/XmlInner.md)
 - [XmlObject](docs/XmlObject.md)


## Documentation For Authorization
 Endpoints do not require authorization.


## Author



