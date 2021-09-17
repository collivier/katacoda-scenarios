XtestingCI also allows you to set proxies both when building the containers and
when running them.

Let's start by setting docker_args for all the env variables as you did when
you ran the container by hand.

```
cat << EOF >> site.yml
      docker_args:
        volumes: []
        env:
          http_proxy: 'http://admin:admin@[[HOST_IP]]:3128'
          https_proxy: 'http://admin:admin@[[HOST_IP]]:3128'
          ftp_proxy: 'http://admin:admin@[[HOST_IP]]:3128'
          no_proxy: '[[HOST2_IP]]'
EOF
```{{execute HOST2}}

As for
[Deploy your first Continuous Development toolchain](https://www.katacoda.com/ollivier/courses/xtestingci/firstcd),
you do describe the container builds especially:
- all your containers as build steps (i.e. tags, branches, pathes, etc.)
- their root dependencies (here opnfv/xtesting:latest)
- the build arguments as you did when you ran the container by hand

Here you ask to build 127.0.0.1:5000/weather:latest from *tests/weather* in
the XtestingCI *master* branch:

```
cat << EOF >> site.yml
      git_url: https://github.com/collivier/ansible-role-xtesting
      jenkins_pollscm: "* * * * *"
      docker_tags:
        - latest:
            branch: master
            dependency: latest
            build_args:
              http_proxy: 'http://admin:admin@[[HOST_IP]]:3128'
              https_proxy: 'http://admin:admin@[[HOST_IP]]:3128'
              ftp_proxy: 'http://admin:admin@[[HOST_IP]]:3128'
              no_proxy: '[[HOST2_IP]]'
      builds:
        dependency:
          repo: opnfv
          container: xtesting
          dport: None
        steps:
          - name: build weather
            containers:
              - name: weather
                ref_arg: BRANCH
                path: tests/weather
EOF
```{{execute HOST2}}

As usual, Katacoda forces us to precise both test database and test artifact
urls to make them reachable from your device:

```
cat << EOF >> site.yml
      http_dst_url: https://[[HOST2_SUBDOMAIN]]-8181-[[KATACODA_HOST]].environments.katacoda.com
      testapi_ext_url: https://[[HOST2_SUBDOMAIN]]-8000-[[KATACODA_HOST]].environments.katacoda.com/api/v1
EOF
```{{execute HOST2}}

As for the first example, we simply
[set the environment at the play level](https://docs.ansible.com/ansible/latest/user_guide/playbooks_environment.html):

```
cat << EOF >> site.yml
  environment:
    http_proxy: 'http://admin:admin@[[HOST_IP]]:3128'
    https_proxy: 'http://admin:admin@[[HOST_IP]]:3128'
    ftp_proxy: 'http://admin:admin@[[HOST_IP]]:3128'
    no_proxy: '[[HOST2_IP]]'
EOF
```{{execute HOST2}}

Please review the final playbook especially the proxy configurations:

```
cat site.yml
```{{execute HOST2}}

You can now reconfigure your own Continuous Integration toolchain by keeping an
eye on the messages printed in Terminal Host 1:

```
ansible-playbook site.yml
```{{execute HOST2}}
