[The CNF Test Suite](https://github.com/cncf/cnf-testsuite/) is a tool that
makes it possible to validate telco applications, aka Cloud Native Network
Functions (CNFs), and the underlying Telecom platforms adherence to Cloud
native principles and best practices.

This Test Suite initiative works closely with the CNF WG which determines
requirements for the CNF Test Suite program.

The CNF Test Suite will inspect CNFs for
[the following characteristics](https://github.com/cncf/cnf-testsuite/blob/main/TEST-CATEGORIES.md):
- compatibility
- state
- security
- microservice
- scalability
- configuration and lifecycle
- observability
- installable and upgradeable
- hardware resources and scheduling
- resilience

It's worth mentioning that, as part of its Kubernetes verification,
[Functest Kubernetes](https://github.com/opnfv/functest-kubernetes) integrates
[CoreDNS](https://coredns.io/) as offered by
[CNF Test Suite](https://github.com/cncf/cnf-testsuite/tree/main/example-cnfs/coredns).
