# Plan for adding embedded CI tests to `rust-lang/rust`

## Tests to add

> TODO: Add more detail

* Make sure known-good embedded projects still compile and link
* Check that code size does not change significantly when compiling for size (`-Oz` optimization)
* Check that certain symbols are not stripped/compiled out from the `elf` file of projects
* (Stage two): Ensure that simple embedded examples run in QEMU

## Plan for integration

> TODO, how/where do we add tests?

## Unknowns/Need More Information

> TODO!