[In the previous Katacoda scenarios](https://www.katacoda.com/ollivier/courses/xtestingci/),
all the services were deployed in a single host which is the simplest setup to
verify a System Under Tests (see
[Run CNTT Kubernetes Based Reference Conformance](https://www.katacoda.com/ollivier/courses/xtestingci/cnttrc2)).
Here, you will rather span the different services accross multiple hosts
leveraging both [XtestingCI](https://github.com/collivier/ansible-role-xtesting)
and [Ansible](https://docs.ansible.com/ansible/latest/index.html).

Finally you will deploy a Jenkins agent which is the classical solution to
share the common builds accross multiple servers or to execute the test cases
as closed as possible from your System Under Tests.
