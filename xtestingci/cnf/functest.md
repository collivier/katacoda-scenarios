Functest Kubernetes offers a driver to execute CNF Test Suite and to publish
its test results in the common test result database and to share its test
reports in a common artifact repository (see
[Deploy your first Continuous Integration toolchain](https://www.katacoda.com/ollivier/courses/xtestingci/firstci)).
You can easily leverage the upstream container to verify any CNF by overriding
the default Xtesting test case description and the CNF TestSuite configuration
file.

Please review Envoy's cnf-testsuite.yml as proposed by CNF TestSuite.
[Envoy](https://www.envoyproxy.io/) is a programmable L3/L4 and L7 proxy that
powers today’s service mesh solutions.

```
cat example-cnfs/envoy/cnf-testsuite.yml
```{{execute}}

Then you can download and review testcases.yaml and Dockerfile to run
the same tests you just executed vs CoreDNS.

```
curl -O -Ls https://raw.githubusercontent.com/collivier/katacoda-scenarios/main/xtestingci/cnf/testcases.yaml
curl -O -Ls https://raw.githubusercontent.com/collivier/katacoda-scenarios/main/xtestingci/cnf/Dockerfile
cat testcases.yaml
cat Dockerfile
```{{execute}}

Then you can build and run your new container verifying
[Envoy](https://www.envoyproxy.io/)

```
sudo docker build -t envoy .
sudo docker run -v /root/.kube/config:/root/.kube/config envoy
```{{execute}}

Of course, this new test cases can be smoothly integrated in your own
continuous integration toolchain via XtestingCI!
