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
ansible-galaxy collection install ansible.posix community.general community.grafana community.kubernetes community.docker community.postgresql
```{{execute}}
