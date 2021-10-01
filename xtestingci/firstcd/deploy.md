2 public keys are currently expired in all Katacoda images and then you do first
update this apt keys before anything else. ca-certificates must be updated as
well.

```
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
curl -sS https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
apt-get update ; apt-get install ca-certificates -y
```{{execute}}

Ansible is already installed here. The next commands simply download XtestingCI
and all the mandatory Ansible collections.

```
ansible-galaxy install collivier.xtesting
ansible-galaxy collection install ansible.posix community.general community.grafana kubernetes.core community.docker community.postgresql
```{{execute}}

You can now deploy your own Continuous Integration toolchain:

```
ansible-playbook site.yml
```{{execute}}

Finally, you can publish the source code to Gitea:

```
git clone http://xtesting:xtesting@[[HOST_IP]]:3001/xtesting/helloworld
cp Dockerfile hello.robot testcases.yaml helloworld/
cd helloworld/
git add .
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
git commit -s -a -m "Initial commit"
git push
```{{execute}}
