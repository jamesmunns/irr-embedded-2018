# Agenda

* Introduction (me, them)
    * My background
    * How I got started in Rust (for me, also embedded-wg)
    * Open source projects?
    * Their background, knowledge, preferences, areas they want to improve
* Schedule
    * Weekly meeting time
        * Split Meetings? Together?
        * Same time/day?
        * Format? Voice/Video/Chat only?
    * Embedded Working Group Meetings
        * Tuesdays, 9pm CEST, IRC + Hangouts once per month
    * Weekly working time(s)?
        * 3-5 hours per week
    * Welcome call on May 14th
        * Split calls? (I'm looking in to it)
    * Group Meetings on Fridays
        * With Ashley
        * Split calls?
* Which conference would they like to attend?
    * RustFest in the fall?
    * Try and go together
* Code of conduct
    * https://www.rust-lang.org/en-US/conduct.html
    * If you have any issues with me, other rust members, let someone know!
    * We want this to be an awesome experience for you
* Informational form (about them)
    * Some kind of photo, doesn't have to be real, does have to be appropriate
    * Blog post publicly introducing them on May 15th
* Project work
    * High level overview
        * Embedded-WG is trying to get rust stable in 2018
        * You can do bare metal, but its not as convenient as using "desktop" or "server" rust at the moment
        * Requires nightly features that have often changed, breaking existing embedded code
        * We would like to get some of the embedded platforms to "Tier 1 Status" - stable code should never break by compiler changes
            * MSP430 and ARM Cortex M microcontrollers in Tier 1
        * This requires some kind of automated testing so that the (non-embedded) compiler developers do not inadvertently break things
        * These tests should (at least) include:
            * Basic examples compile and link
            * Static analysis, such as size, certain symbols exist
            * (reach goal): QEMU tests
        * https://jamesmunns.com/blog/hardware-ci-overview/
    * Roadmap
        * Coming soon!
        * First week(s) are planned to be "learning", either Rust, CI testing, embedded concepts
    * Learning resources
        * How can I help you?
    * Additional work
        * Primary goal vs additional work
        * Projects they want to do?
            * Personal projects?
        * Projects from embedded-wg
* Marketing
    * How can we help with visibility?
        * users.rust-lang.org
        * internals.rust-lang.org
        * twitter (I'm @bitshiftmask)
            * `#rustreach` hashtag
        * blog posts
        * Other forums
    * Making your work visible inside and outside of the Rust community