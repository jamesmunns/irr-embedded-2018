# Agenda

## Review previous week

Probably nothing yet, but here just in case!

### Hideki

* Published Binary Heap Crate
    * Also set up CI with Cross Compilation
    * Received a first pull request, worked with CI, merged!

### Vaishali

* Refreshing Rust language knowledge
* Looked as SSD1306

### James

* N/A

## Discussion Items

This is the first week of the "learning section". I would like the team to focus on getting up to speed with the following items:

* Make sure everyone has a good understanding of what our goals are
* Review skills that will be useful for this work:
    * Docker (CI tests are run in a Docker Context)
    * Rust
        * General knowledge
        * Building an embedded example
    * Linux
    * QEMU (but we will probably get to this later in the program)
* Review useful links
    * CI for the Rust compiler [lives here]
    * [old blog post] about the "new" CI system
    * [guide for using CI images] inside the CI repo
    * [stm32f103xx-hal] crate is probably a good place for initial testing
    * [discovery guide] is a little outdate, but good for a first read
* Writing bios for the website

[lives here]: https://github.com/rust-lang/rust/tree/master/src/ci
[old blog post]: https://internals.rust-lang.org/t/rust-ci-release-infrastructure-changes/4489
[guide for using CI images]: https://github.com/rust-lang/rust/tree/master/src/ci/docker
[stm32f103xx-hal]: https://github.com/japaric/stm32f103xx-hal
[discovery guide]: https://japaric.github.io/discovery/

## Plan for this week

(initial thoughts from James):

* Focus on learning
* Getting an understanding of how the CI system works
* Blog posts or README changes about stuff we've learned?

### Hideki

* Look into `-hal` crates and understand how embedded Rust toolchain works
* start looking docker

### Vaishali

* Improve knowledge regarding docker
* Start getting a high level overview of the CI
* Try running tests locally

### James

* Also try and learn more about the CI
* Try and find good learning material for docker, and embedded rust
* Reach out to maintainers of CI to make intoductions, once we have an initial plan, sanity check

## After this week

# Action Items

* James to provide docker resources

# Notes
