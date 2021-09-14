You could have a quick look to the default playbook
```ansible-role-xtesting/tests/hello/site.yml```{{open}} which basically lists
our next container *127.0.0.1:5000/hello*.

As usual, Katacoda forces us to precise both test database and test artifact
urls to make them reachable from your device:

```
cat << EOF >> site.yml
      http_dst_url: https://[[HOST_SUBDOMAIN]]-8181-[[KATACODA_HOST]].environments.katacoda.com
      testapi_ext_url: https://[[HOST_SUBDOMAIN]]-8000-[[KATACODA_HOST]].environments.katacoda.com/api/v1
EOF
```{{execute}}

For the purpose of this scenario, you also request Gitea, a.k.a.
*Git with a cup of tea*, to host your code. It will be pulled by your next
Jenkins jobs when building your container (note: to get a faster trigger,
Jenkins polls every minute your git repository here).

```
cat << EOF >> site.yml
      gitea_deploy: true
      git_url: http://[[HOST_IP]]:3001/xtesting/helloworld
      jenkins_pollscm: "* * * * *"
EOF
```{{execute}}

The last step is to describe the container builds especially:
- all your containers as build steps (i.e. tags, branches, pathes, etc.)
- their root dependencies (here opnfv/xtesting:latest)

Here you ask to build 127.0.0.1:5000/hello:latest from *root* in your
*master* branch:

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
