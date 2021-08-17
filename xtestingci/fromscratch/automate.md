Starting now, you mostly execute the same instructions as the previous
scenarios,
[Deploy your first Continuous Integration toolchain](https://www.katacoda.com/ollivier/courses/xtestingci/firstci)
or [Run CNTT Kubernetes Reference Conformance](https://www.katacoda.com/ollivier/courses/xtestingci/cnttrc2).

The main difference is the test case list,
```ansible-role-xtesting/tests/hello/site.yml```{{open}} as you target
*hello* from your own container *127.0.0.1:5000/hello* rather than the upstream
test case lists. It's worth mentioning that you also ask a private Docker
registry via *registry_deploy* to host your new container.

Katacoda forces us to precise both test database and test artifact urls to
make them reachable from your device:

```
echo "      http_dst_url: https://[[HOST_SUBDOMAIN]]-8181-[[KATACODA_HOST]].environments.katacoda.com" >> site.yml
echo "      testapi_ext_url: https://[[HOST_SUBDOMAIN]]-8000-[[KATACODA_HOST]].environments.katacoda.com/api/v1" >> site.yml
```{{execute}}

Ansible is already installed here. The next commands simply download XtestingCI
and all the mandatory Ansible collections.

```
ansible-galaxy install collivier.xtesting
ansible-galaxy collection install ansible.posix community.general community.grafana kubernetes.core community.docker community.postgresql
```{{execute}}

2 public keys are currently expired in all Katacoda images and then you do first
update this apt keys before running the playbook.

```
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
curl -sS https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
```{{execute}}

You can now deploy your own Continuous Integration toolchain:

```
ansible-playbook site.yml
```{{execute}}

Once the play ends after 5 minutes, you can publish your container in the
private Docker registry:

```
docker push 127.0.0.1:5000/hello
```{{execute}}

Jenkins is accessible via the tab named Jenkins (you may have to refresh it).
