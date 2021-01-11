Xtesting is a simple framework to assemble sparse test cases and to accelerate
the adoption of automation best practices. It mainly allows the
tester/developer to work only on the test suites without diving into
[Continuous Integration](https://en.wikipedia.org/wiki/Continuous_integration)
which would require additional skills. By managing all the interactions
with the toolchain components, Xtesting guarantees a uniq and simple way to
execute the test case, to publish all test results in a common test result
database and to share all test reports in a common artifact repository.

XtestingCI leverages the common test case execution proposed by Xtesting.
Thanks to a simple test case list, this tool deploys anywhere plug-and-play
Continuous Integration toolchains in a few commands. It supports multiple
opensource components such as [Jenkins](https://www.jenkins.io/) and
[Gitlab CI/CD](https://docs.gitlab.com/ee/ci/) and multiple deployment models
such as all-in-one (in Docker or in Kubernetes), centralized services (e.g.
[OPNFV](https://www.opnfv.org) toolchain) or a mix of both.

During this scenario, you will deploy your own clone of the
[OPNFV](https://www.opnfv.org) toolchain which has been in-use every day to
verify [OpenStack](https://www.openstack.org/) and
[Kubernetes](https://kubernetes.io) deployments for 5 years. But from a tester
state point, switching from Jenkins to Gitlab CI/CD becomes as simple as
writing 2 Boolean values in a text file via XtestingCI.
