Let's start by booting [Squid](http://www.squid-cache.org/), the well-known
opensource caching proxy:

```
sudo docker run -p 3128:3128 -e WEBADMIN=admin -e PASSWORD=admin woahbase/alpine-squid
```{{execute HOST1}}

Once *storeLateRelease: released 0 objects* is printed in Terminal Host 1, you
can configure your environment to install Ansible and XtestingCI through your
proxy:

```
export http_proxy=http://admin:admin@[[HOST_IP]]:3128
export https_proxy=http://admin:admin@[[HOST_IP]]:3128
export ftp_proxy=http://admin:admin@[[HOST_IP]]:3128
export no_proxy=[[HOST2_IP]]
```{{execute HOST2}}

As highlighted in
[the first Katacoda scenario](https://www.katacoda.com/ollivier/courses/xtestingci/firstci),
XtestingCI is an Ansible role published in Ansible Galaxy and then asks for
Ansible available in your environment. The version installed here is too old
(<2.9) and you could simply update it via pip:

```
apt-get remove --purge ansible -y && pip2 install ansible
```{{execute HOST2}}

When Ansible is upgraded, you should see a couple of *CONNECT messages to
pypi.org:443* in Terminal Host 1. The next commands simply download XtestingCI
and all the mandatory Ansible collections:

```
ansible-galaxy install collivier.xtesting
ansible-galaxy collection install ansible.posix community.general community.grafana kubernetes.core community.docker community.postgresql
```{{execute HOST2}}

You can now clone both Xtesting and XtestingCI repositories needed for this
scenario:

```
git clone https://gerrit.opnfv.org/gerrit/functest-xtesting functest-xtesting-src
git clone https://github.com/collivier/ansible-role-xtesting.git
```{{execute HOST2}}

2 public keys are currently expired in all Katacoda images and then you do first
update this apt keys before running any package operation. ca-certificates must
be updated as well.

```
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
curl -sS https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
apt-get update ; apt-get install ca-certificates -y
```{{execute HOST2}}

You can now clear all previous proxy configuration as it will be set directly
in your next playbooks:

```
unset http_proxy https_proxy ftp_proxy no_proxy
```{{execute HOST2}}
