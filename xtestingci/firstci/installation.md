XtestingCI is an Ansible role published in Ansible Galaxy and then asks for
Ansible already available in your environment. It must be executed by a user
part of the sudo group (or by root as in Katacoda) due to a couple of admin
tasks.

Be free to install XtestingCI in a Python virtualenv or via a dedicated user
in your local environment if needed as explained in the
[homepage](https://github.com/collivier/ansible-role-xtesting)

Ansible is already installed here. The next commands simply download
XtestingCI and all the mandatory Ansible collections.

```
ansible-galaxy install collivier.xtesting
ansible-galaxy collection install ansible.posix community.general community.grafana community.kubernetes
```{{execute}}
