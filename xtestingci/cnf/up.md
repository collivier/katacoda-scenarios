For the purpose of this scenario, you start by installing a 2 node cluster
(v1.18) as proposed by Katacoda:

```
launch.sh
```{{execute}}

You can now download cnf-testsuite as released by the project. v0.15.0 is
selected here but you're free to select any newer version to benefit from new
features or new bug fixes (CNF Test Suite is under development)

```
git clone https://github.com/cncf/cnf-testsuite.git
cd cnf-testsuite && git checkout v0.15.0
curl -O -Ls https://github.com/cncf/cnf-testsuite/releases/download/v0.15.0/cnf-testsuite-v0.15.0.tar.gz
tar zxvf cnf-testsuite-v0.15.0.tar.gz
chmod a+x ./cnf-testsuite
```{{execute}}

Let's run setup to verify that all pre-requisites (i.e. kubectl and helm)
are meet:

```
./cnf-testsuite setup
```{{execute}}

For the purpose of this scenario, [CoreDNS](https://coredns.io/), a DNS server,
is selected as the target CNF. The following instruction initializes the test
suite (note: output falsy warns *Helm pull error*):

```
./cnf-testsuite cnf_setup cnf-config=./example-cnfs/coredns/cnf-testsuite.yml
```{{execute}}

Please review cnf-testsuite.yml which provides all data needed, especially the
Helm chart, to run CNF Test Suite vs CoreDNS.

```
cat example-cnfs/coredns/cnf-testsuite.yml
```{{execute}}

Let's check that they are no privileged containers.

```
./cnf-testsuite privileged
```{{execute}}

You can also run the microservice testing, checking that the CNF is developed
and delivered as a microservice. Here the startup time is far too long due to
the lack of resources in Katacoda.

```
./cnf-testsuite microservice
```{{execute}}

Be free to run
[any other test category](https://github.com/cncf/cnf-testsuite/blob/main/TEST-CATEGORIES.md).
You could also select *workload* as Functest Kubernetes does to run all
workload test cases.
