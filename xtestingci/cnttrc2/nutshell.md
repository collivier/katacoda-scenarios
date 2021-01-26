The
[Cloud iNfrastructure Telco Task Force](https://github.com/cntt-n/CNTT/blob/stable/elbrus/doc/gov/chapters/chapter01.md)
is leading the industry in creating a common infrastructure
reference platform in the form of reference model and reference architecture
definitions to better support Network Function Virtualization (NFV)
applications for the Telecom industry as a whole. The working group is
collaborating with OPNFV and other open source communities to operationalize
and support reference implementations and reference certification platforms.

The objective of each
[Reference Conformance](https://github.com/cntt-n/CNTT/tree/stable/elbrus/doc/ref_cert)
workstream is to provide an automated mechanism to validate either a network
function (NF) or a cloud infrastructure against a standard set of requirements
defined by the Reference Model (RM) and associated Reference Architecture (RA).

[Xtesting](https://xtesting.readthedocs.io/en/latest/) and
[XtestingCI](https://galaxy.ansible.com/collivier/xtesting) combined meet the
CNTT requirements about verification, validation, compliance, and conformance:
- smoothly assemble multiple heterogeneous test cases
- generate the Jenkins jobs in OPNFV Releng to verify CNTT RI
- deploy local CI/CD toolchains everywhere to check compliance with CNTT
- dump all test case results and logs for third-party conformance review

This scenario focuses on the Reference Conformance for the Kubernetes-based
workstream ([RC2](https://github.com/cntt-n/CNTT/blob/stable/elbrus/doc/ref_cert/RC2/chapters/chapter01.md))
