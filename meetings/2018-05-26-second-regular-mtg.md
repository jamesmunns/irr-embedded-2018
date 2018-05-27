# Agenda

## Review Previous Week

### Hideki

* Wrote HOW TO document for compiling a embedded crate. (from fresh install of Ubuntu)
    * https://gist.github.com/sekineh/87c1c8395cd64a98afbe3b34d060e153
    * `cortex-m` crate compiles on beta; will compile on the next stable.
    * `-hal` crate compiles on nightly; `panic-itm` is the blocker.
    * `panic-itm` will be updated once when a @japaric's pull request is merged successfully.
    * https://github.com/rust-lang/rust/pull/50338
* Reviewed travis setting: 
    * https://github.com/rust-lang/rust/blob/master/.travis.yml#L241-L261
    * `$RUN_SCRIPT` is the core script of CI
    * typical `$RUN_SCRIPT` is: `src/ci/init_repo.sh . $HOME/rustsrc && src/ci/docker/run.sh $IMAGE`
* didn't run docker actually yet

### Vaishali

### James

* Talked with [kennytm]
* Reached out to coworker re: docker resources, no response yet

[kennytm]: https://github.com/kennytm

## Discussion Items

* Put together our initial plan for CI (what we want)
    * What kind of tests?
    * What should happen if tests fail?
* Gather a list of questions/unknowns like:
    * Are there any better guides for how the CI works?
    * How/where to integrate our new tests?
* Any new focus for learning while we are starting planning?
* Deadlines!
    * Review Rust's 6 week release cycle
    * Rust 2018 ships Calendar Week 37 (2018-09-10 or so)
    * We must have "landed" in Beta by Calendar Week 31 (2018-07-30 or so)
    * Earlier is better, to catch any mistakes early

## Plan for this week

### Hideki

* Try to run existing CI locally using docker
* (optional) Play with DISCOVERY board

### Vaishali

### James

## After this week
