```
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
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
docker build -t 127.0.0.1:5000/hello .
```{{execute}}

```
docker run -t 127.0.0.1:5000/hello
```{{execute}}

```
ansible-role-xtesting/tests/hello/site.yml
```{{open}}

```
echo "      http_dst_url: https://[[HOST_SUBDOMAIN]]-8181-[[KATACODA_HOST]].environments.katacoda.com" >> site.yml
echo "      testapi_ext_url: https://[[HOST_SUBDOMAIN]]-8000-[[KATACODA_HOST]].environments.katacoda.com/api/v1" >> site.yml
```{{execute}}

```
ansible-playbook site.yml
```{{execute}}

```
docker push 127.0.0.1:5000/hello
```{{execute}}
