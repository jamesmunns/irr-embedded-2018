# How to setup rust toolchain for embedded targets

# OS

Ubuntu 16.04 Desktop

# Install Rust

```
$ sudo apt-get install git curl
$ curl https://sh.rustup.rs -sSf | sh
```

# Install cargo-clone

```
$ sudo apt-get install git curl libssl-dev cmake
$ cargo install cargo-clone
```

# Install rust embedded target support

Add embedded target `thumbv7m-none-eabi` for stable, beta and nightly.
```
$ rustup default stable
$ rustup target add thumbv7m-none-eabi

$ rustup default beta
$ rustup target add thumbv7m-none-eabi

$ rustup default nightly
$ rustup target add thumbv7m-none-eabi
```

# Install extra tools useful for embedded development
```
sudo apt-get install gdb-arm-none-eabi
sudo apt-get install binutils-arm-none-eabi
sudo apt-get install openocd
```

# Build cortex-m crate

This crate will compile on beta toolchain!
```
$ cargo clone cortex-m --vers 0.5.0 && cd cortex-m
$ rustup default beta
$ cargo build --target thumbv7m-none-eabi
   Compiling cortex-m v0.5.2 (file:///home/sekineh/cortex-m)
    Finished dev [unoptimized + debuginfo] target(s) in 0.59s
```

# Build -hal crate

As of 2018-05-20, the `stm32f103xx-ha` crate requires nightly.

```
$ cd stm32f103xx-hal
$ rustup default nightly
$ cargo build
   Compiling cc v1.0.15
   Compiling vcell v0.1.0
   Compiling stm32f103xx v0.10.0
   Compiling bare-metal v0.2.0
   Compiling aligned v0.2.0
   Compiling r0 v0.2.2
   Compiling void v1.0.2
   Compiling stm32f103xx-hal v0.1.0 (file:///home/sekineh/stm32f103xx-hal)
   Compiling nb v0.1.1
   Compiling cast v0.2.2
   Compiling volatile-register v0.2.0
   Compiling embedded-hal v0.2.1
   Compiling cortex-m v0.5.2
   Compiling cortex-m-semihosting v0.3.0
   Compiling cortex-m-rt v0.5.1
   Compiling panic-itm v0.1.1
   Compiling panic-semihosting v0.2.0
    Finished dev [unoptimized + debuginfo] target(s) in 22.66s
```

Note: `beta` channel will fail on dependency `panic-itm`:

```
$ rustup default beta
sekineh@sekineh-VirtualBox:~/stm32f103xx-hal$ cargo build
   Compiling panic-semihosting v0.2.0
   Compiling panic-itm v0.1.1
error[E0554]: #![feature] may not be used on the beta release channel
  --> /home/sekineh/.cargo/registry/src/github.com-1ecc6299db9ec823/panic-semihosting-0.2.0/src/lib.rs:56:1
   |
56 | #![feature(lang_items)]
   | ^^^^^^^^^^^^^^^^^^^^^^^

error: aborting due to previous error

For more information about this error, try `rustc --explain E0554`.
error: Could not compile `panic-semihosting`.
warning: build failed, waiting for other jobs to finish...
error[E0554]: #![feature] may not be used on the beta release channel
  --> /home/sekineh/.cargo/registry/src/github.com-1ecc6299db9ec823/panic-itm-0.1.1/src/lib.rs:33:1
   |
33 | #![feature(lang_items)]
   | ^^^^^^^^^^^^^^^^^^^^^^^

error: aborting due to previous error

For more information about this error, try `rustc --explain E0554`.
error: Could not compile `panic-itm`.

To learn more, run the command again with --verbose.
```
