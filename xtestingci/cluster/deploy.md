A public key is currently expired in all Katacoda images and then you do first
update this apt key before anything else.

```
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
```{{execute}}

For the purpose of this scenario, you start by installing a 2 node cluster
(v1.18) as proposed by Katacoda:

```
launch.sh
```{{execute}}

Local Path Provisioner provides a way for the Kubernetes users to utilize the
local storage in each node. Here you install the version
[customized by kind](https://github.com/kubernetes-sigs/kind/blob/master/pkg/build/nodeimage/const_storage.go#L20):

```
kubectl apply -f http://testresults.opnfv.org/functest/local-path-provisioner-kind.yml
```{{execute}}

As highlighted in
[the first Katacoda scenario](https://www.katacoda.com/ollivier/courses/xtestingci/firstci),
XtestingCI is an Ansible role published in Ansible Galaxy and then asks for
Ansible available in your environment. The version installed here is too old
(<2.9) and you could simply update it via pip:

```
apt-get remove --purge ansible -y && pip2 install ansible
```{{execute}}

The next commands simply download XtestingCI and all the mandatory Ansible
collections:

```
ansible-galaxy install collivier.xtesting
ansible-galaxy collection install ansible.posix community.general community.grafana community.kubernetes community.docker community.postgresql
```{{execute}}
