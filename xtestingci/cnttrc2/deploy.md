2 public keys are currently expired in all Katacoda images and then you do first
update this apt keys before anything else. ca-certificates must be updated as
well.

```
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
curl -sS https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
apt-get update ; apt-get install ca-certificates -y
```{{execute}}

For the purpose of this scenario, you start by installing a 2 node cluster
(v1.18) as proposed by Katacoda:

```
launch.sh
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
collections.

```
ansible-galaxy install collivier.xtesting
ansible-galaxy collection install ansible.posix community.general community.grafana kubernetes.core community.docker community.postgresql
```{{execute}}
