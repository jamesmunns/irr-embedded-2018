# Plan for adding embedded CI tests to `rust-lang/rust`

* Goal: we will add target `thumbv7m-none-eabi` in stable Rust 2018 Edition
  * [TODO] Is the target name right?

## Tests not to add

* `dist` target for `thumbv7m-none-eabi`
  * `./x.py dist` for `thumbv7m-none-eabi` is already included in `dist-various-1` docker image; this is why we can do `rustup target add` for the target now.

## Tests to add

> TODO: Add more detail

* Make sure known-good embedded projects still compile and link
  * [???] We could use `cargotest` infra or alike.
  * Crate `cortex-m` is a good start because it already compiles on beta now.
  * `stm32f103xx-hal` includes `cortex-m` in dependency, so we'll use it later.
  * [TODO] Need to collect other candidate.
* Check that code size does not change significantly when compiling for size (`-Oz` optimization)
  * `wasm32-unknown/Dockerfile` says `run-make` test have assertions for code size.
    We could reuse that infra.

* Check that certain symbols are not stripped/compiled out from the `elf` file of projects
  * [???] Check within `cargotest`?  Are there better place?

* (Stage two): Ensure that simple embedded examples run in QEMU

## Plan for integration

> TODO, how/where do we add tests?

* Create a pull request with 'minimal' test for `thumbv7m-none-eabi`
  * [???] We will create a new docker file for testing: `thumbv7m-none-eabi/Dockerfile`
  * [???] See `wasm32-unknown` docker image, because it also is a `no-std` target; needed test coverage might be similar.

* Add `cargotest` which run `cargo test` using `qemu`
  * Install `qemu-system-arm` in docker file.
  * [???] See `armhf-gnu/Dockerfile` for bare-metal `qemu` example

## Unknowns/Need More Information

* Are there other Docker image we could use as a start point?
* Suggestion for usable existing infra for each test.
