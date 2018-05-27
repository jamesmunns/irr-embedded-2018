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
* Built and installed rustc. It's not bit straightforward. The solutions in [this](https://github.com/rust-lang/rust/issues/40108) issue works.
* Spent time in learning about docker. Also, set up a dummy project to learn on how Travic CI and Docker image works.
  [This](https://medium.com/mobileforgood/patterns-for-continuous-integration-with-docker-on-travis-ci-71857fff14c5) is a good resource to understand that.
* Checked on how rust CI is structured at the moment. Blog post is in process. Should be up for the review by the EOD.

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
* Do we want to think in the direction of writing target(Arch) specific tests?

## Plan for this week

### Hideki

* Try to run existing CI locally using docker
* (optional) Play with DISCOVERY board

### Vaishali

* Run existing CI with different docker images
* Plan on the kind of tests we want to write
* (extra) Contribute to [ssd1306 driver](https://github.com/jamwaffles/ssd1306) crate

### James

* Review blog post from Vaishali
* Review guide from Hideki
* Put together skeleton for CI Plan/Email to KennyTM

## After this week

N/A