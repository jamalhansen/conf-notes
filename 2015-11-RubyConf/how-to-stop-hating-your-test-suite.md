# How to stop hating your test suite
Justin Searls @Searls works at Test Double
RubyConf 2015 11/15/2015

Testing is job one to us.
Job one is according to our customers is shipping code.

## 4 Components of testing
* Structure
* Isolation
* Feedback
* Prevention

### Structure
Testers hate big objects
Tests make big objects ahrder to manage

* Rule of product
If you have 4 arguments you need to take all possible values of each times each other to cover all situations

! Do not keep adding to large objects
Make lots of small stuff
--------------------
use Given / When / Then with spaces in between for xunit
use let and before in rspec, GWT gem transforms this to Given when then

Minimize each phase to one line if possible
----------------
Hard to read code

test code is untested code

experience of test pain is often sympomatic of module code problems

At a glance you should be able to tell what is under test in test suite
----------------
## Big Stuff
Always call the thing under test 'subject' and the result 'result'

When you are consistant, inconsistancy can provide enhanced meaning

Use test data that is minimally meaningful.  If the data is not necessary, do not use it
-----------------------

http://is.gd/breaking-up
Breaking up with your Test suite

### Isolation
-----------------------
People end up writing tests at multiple levels of the project from unit to integration, these are testing various parts and avoiding other parts.  He recommends starting with two suites.  One at the highest level of realism, the other at the most isolated level ( the top and bottom of the pyramid )

1) maximally realistic - integration (test it all together)
2) lowest level - unit test (mocks, under ui, etc)

* Only add new levels if necessary
* Avoid redundant test coverage because it causes pain when changing

He calls this discovery testing and has [more information about this on video](http://is.gd/discovery-testing)

isolating the subject from other areas
----------------------

### Feedback
#### Bad error messages
Even if tests are fast, bad messages cause friction
Judge assertion libraries on quality of messages too

#### Slow tests can severely limit the number of actionable thoughts that you can have in a day.  This is because they increase the time between each coding iteeration.

Keep tests fast: 43 vs. 480 thoughts in a day

#### Controlling test data is really hard

You do not have to choose only one way
    * inline
    * fixtures
    * data dumps
    * self priming tests

Data setup may be primary cause of slow tests (no proof)

#### Super linear build slowdown
This is another cause of test slowdown.

setup / teardown and app code cause tests to slow down as app grows

How can you combat this?
Avoid the urge to create integration test for each new feature
Instead try to create a handful of tests that zig zaggs through different important features


#### Beware of False negatives

What does it mean when the build fails?

True negative - Code is broken with red build
False Negative - Test is broken with red build

False negatives erode confidence in tests

top causes
* redundant code coverage
* slow tests (i.e. lots of integration test)

PLEASE WRITE FEWER INTEGRATION TESTS!
