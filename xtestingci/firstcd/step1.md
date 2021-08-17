```
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
curl -sS https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
```{{execute}}

```
ansible-galaxy install collivier.xtesting
ansible-galaxy collection install ansible.posix community.general community.grafana community.kubernetes community.docker community.postgresql
```{{execute}}

```
git clone https://github.com/collivier/ansible-role-xtesting.git
cd ansible-role-xtesting/tests/hello
```{{execute}}

```
ansible-role-xtesting/tests/hello/hello.robot
```{{open}}

```
ansible-role-xtesting/tests/hello/testcases.yaml
```{{open}}

```
ansible-role-xtesting/tests/hello/Dockerfile
```{{open}}

```
ansible-role-xtesting/tests/hello/site.yml
```{{open}}

```
cat << EOF >> site.yml
      gitea_deploy: true
      git_url: http://[[HOST_IP]]:3001/xtesting/helloworld
EOF
```{{execute}}

```
cat << EOF >> site.yml
      docker_tags:
        - latest:
            branch: master
            dependency: latest
      builds:
        dependency:
          repo: opnfv
          container: xtesting
          dport: None
        steps:
          - name: build hello
            containers:
              - name: hello
                ref_arg: BRANCH
                path: .
EOF
```{{execute}}

```
cat << EOF >> site.yml
      http_dst_url: https://[[HOST_SUBDOMAIN]]-8181-[[KATACODA_HOST]].environments.katacoda.com
      testapi_ext_url: https://[[HOST_SUBDOMAIN]]-8000-[[KATACODA_HOST]].environments.katacoda.com/api/v1
EOF
```{{execute}}

```
ansible-playbook site.yml
```{{execute}}

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
