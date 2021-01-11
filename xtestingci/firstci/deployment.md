XtestingCI only asks for an Ansible playbook which is mostly the test case list
you want to execute (docker and test case names). It could be any test case
leveraging Xtesting such as the ones offered by OPNFV Functest, the collection
of state-of-the-art virtual infrastructure test suites.

For the purpose of this scenario, you simply download the Xtesting sample list:

```
git clone https://gerrit.opnfv.org/gerrit/functest-xtesting functest-xtesting-src
```{{execute}}

In this scenario, you do precise both test database and test artifact urls to
make them reachable from your device:

```
echo "      http_dst_url: https://[[HOST_SUBDOMAIN]]-8181-[[KATACODA_HOST]].environments.katacoda.com" >> functest-xtesting-src/ansible/site.yml
echo "      testapi_ext_url: https://[[HOST_SUBDOMAIN]]-8000-[[KATACODA_HOST]].environments.katacoda.com/api/v1" >> functest-xtesting-src/ansible/site.yml
```{{execute}}

You could have a quick look to the playbook. It lists all the samples included
in the 2 Xtesting containers in suites: opnfv/xtesting and opnfv/xtesting-mts

```
cat functest-xtesting-src/ansible/site.yml
```{{execute}}

You can now deploy your own Continuous Integration toolchain:

```
ansible-playbook functest-xtesting-src/ansible/site.yml
```{{execute}}

The play ends after 5 minutes. Once the final Ansible message is printed,
Jenkins is accessible via the tab named Jenkins (you may have to refresh it).
