Xtesting is a simple framework to assemble sparse test cases and to accelerate
the adoption of automation best practices. It mainly allows the
tester/developer to work only on the test suites without diving into
[Continuous Integration](https://en.wikipedia.org/wiki/Continuous_integration)
which would require additional skills. By managing all the interactions
with the toolchain components, Xtesting guarantees a uniq and simple way to
execute the test case, to publish all test results in a common test result
database and to share all test reports in a common artifact repository.

Xtesting also brings the capability to run heterogeneous test cases in the same
Continuous Integration toolchains thanks to a few,
[quickly achievable](https://www.sdxcentral.com/articles/news/opnfvs-6th-release-brings-testing-capabilities-that-orange-is-already-using/2018/05/),
constraints. It first asks that all test are delivered as
[Docker containers](https://www.docker.com/) which simply enforces that the
test cases are delivered with all runtime dependencies. This prevents lots of
manual operations when configuring the servers running the test cases and
prevents conflicts between the test cases due to any dependencies. Then it
also requires a test case description file highlighting how to execute the test
cases (e.g. scripts, drivers, parameters, etc.).

Xtesting offers multiple drivers for the main test frameworks (e.g.
Robot Framework, Behave, unittest, etc.) and
[a very simple API](https://xtesting.readthedocs.io/en/latest/apidoc/xtesting.core.testcase.html)
to write your own drivers if needed. This scenario focuses on a simple Robot
Framework file integration and
[the next one](https://www.katacoda.com/ollivier/courses/xtestingci/firstdriver")
will describe how to write your own driver.
