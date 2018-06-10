# Plan for adding embedded CI tests to `rust-lang/rust`

* Primary Goal: Support the following targets in stable Rust 2018 Edition with CI testing:
    * thumbv6m-none-eabi (Bare Cortex-M0, M0+, M1)
    * thumbv7em-none-eabi (Bare Cortex-M4, M7)
    * thumbv7em-none-eabihf (Bare Cortex-M4F, M7F, FPU, hardfloat)
    * thumbv7m-none-eabi (Bare Cortex-M3)
* Secondary Goal: Support the msp430-none-elf crate in stable Rust 2018 Edition with CI testing

## Tests not to add

* `dist` target for `thumb*` targets
  * `./x.py dist` for `thumb*` targets are already included in `dist-various-1` docker image

## Tests to add

> TODO: Add more detail

* Make sure known-good embedded projects still compile and link
  * [???] We could use `cargotest` infra or alike.
  * Crate `cortex-m` is a good start because it already compiles on beta now.
  * `stm32f103xx-hal` includes `cortex-m` in dependency, so we'll use it later.
  * Additional "known good" embedded examples, such as:
      * [`stm32f103xx-hal` examples]
* Check that code size does not change significantly when compiling for size (`-Oz` optimization)
  * `wasm32-unknown/Dockerfile` says `run-make` test have assertions for code size, We could reuse that infra.

[`stm32f103xx-hal` examples]: https://github.com/japaric/stm32f103xx-hal/tree/master/examples

* Check that certain symbols are not stripped/compiled out from the `elf` file of projects
  * [???] Check within `cargotest`?  Are there better place?

* (Stage two): Ensure that simple embedded examples run in QEMU

## Plan for integration

> TODO, how/where do we add tests?

## Idea 1

* Create a pull request with 'minimal' test for `thumb*` targets
  * [???] We will create a new docker file for testing: `thumbv7m-none-eabi/Dockerfile`
  * [???] See `wasm32-unknown` docker image, because it also is a `no-std` target; needed test coverage might be similar.

* Add `cargotest` which run `cargo test` using `qemu`
  * Install `qemu-system-arm` in docker file.
  * [???] See `armhf-gnu/Dockerfile` for bare-metal `qemu` example

## Idea 2

Use an existing docker image and just do `test` && `dist` pattern similar to the below example. I think it's logically correct for a CI purpose. The only and the biggest drawback is that it takes much more execution time. We could just do this, and if execution time is problematic, then split up the docker image into several ones.

```bash
$ rg 'x.py|TARGETS|HOST' src/ci/docker/
(snip)
src/ci/docker/dist-x86_64-musl\Dockerfile
45:      python2.7 ../x.py test --target x86_64-unknown-linux-musl && \
46:      python2.7 ../x.py dist --target x86_64-unknown-linux-musl
(snip)
src/ci/docker/dist-i586-gnu-i586-i686-musl\Dockerfile
49:ENV TARGETS=i586-unknown-linux-gnu,i686-unknown-linux-musl
52:      python2.7 ../x.py test --target $TARGETS && \
53:      python2.7 ../x.py dist --target $TARGETS,i586-unknown-linux-musl
(snip)
```


## Unknowns/Need More Information

* Are there other Docker image we could use as a start point?
* Suggestion for usable existing infra for each test.

