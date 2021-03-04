XtestingCI leverages the common test case execution proposed by Xtesting.
Thanks to a simple test case list, this tool deploys anywhere plug-and-play
Continuous Integration toolchains in a few commands.

You could directly download the mandatory CNTT RC2 Elbrus test case list:

```
git clone https://gerrit.opnfv.org/gerrit/functest-kubernetes functest-kubernetes-src
cd functest-kubernetes-src
git checkout -b stable/leguer origin/stable/leguer
```{{execute}}

CNTT RC2 only requires kubeconfig as test configuration file. Here this file is
in its default place ($HOME/.kube/config). You could either copy
your kubeconfig to the default Functest kubernetes value
(/home/opnfv/functest-kubernetes/config) or modify the default path written in
ansible/host_vars/127.0.0.1 as proposed here:

```
sed -i "s|/home/opnfv/functest-kubernetes/config|/root/.kube/config|" ansible/host_vars/127.0.0.1
```{{execute}}

CNTT RC2 ends after a couple of hours and you should reduce the test case list
for the purpose of the scenario:

```
sed -i "/functest-kubernetes-smoke/,\$d" ansible/site.cntt.yml
```{{execute}}

In this scenario, you do precise both test database and test artifact urls to
make them reachable from your device:

```
echo "      http_dst_url: https://[[HOST_SUBDOMAIN]]-8181-[[KATACODA_HOST]].environments.katacoda.com" >> ansible/site.cntt.yml
echo "      testapi_ext_url: https://[[HOST_SUBDOMAIN]]-8000-[[KATACODA_HOST]].environments.katacoda.com/api/v1" >> ansible/site.cntt.yml
```{{execute}}

Be free to have a look to all your local modifications:

```
git diff --no-pager
```{{execute}}

You can finally run the CNTT RC2 Elbrus playbook:

```
ansible-playbook ansible/site.cntt.yml
```{{execute}}

The play ends after 5 minutes. Once the final Ansible message is printed,
Jenkins is accessible via the tab named Jenkins (you may have to refresh it).
