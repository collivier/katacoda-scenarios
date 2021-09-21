Before writing any [Ansible playbook](https://docs.ansible.com/ansible/latest/user_guide/playbooks_intro.html),
you must declare all the nodes which will host your services in your
[Ansible inventory](https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html).
Listing all IP addresses is enough here as it's the same account and no
password is defined.

```
cat << EOF > inventory
[[HOST_IP]]
[[HOST2_IP]]
EOF
```{{execute}}

In this example, the first node, *HOST1*, will host Jenkins and the two
databases, MongoDB and PostgreSQL, respectivelly needed by TestAPI and Cachet.
For its part, the second node, *HOST2*, will host Minio, TestAPI and Cachet.

Ansible allows you to configure multiple servers via a single playbook. For
the purpose of this scenario, you will write 2 differents playbooks which could
have been merged.

Please review the first playbook for *HOST1* where *jenkins_configure* is set
to false, suites is empty and Minio, TestAPI and Cachet are skipped
(see *xxx_deploy: false*). It's worth mentioning that your test cases will be
listed in the next playbook for *HOST2*.

```
cat << EOF > site1.yml
- hosts: [[HOST_IP]]
  roles:
    - role: collivier.xtesting
      jenkins_deploy: true
      jenkins_configure: false
      postgres_deploy: true
      mongo_deploy: true
      minio_deploy: false
      testapi_deploy: false
      cachet_deploy: false
      docker_tags: []
      suites: []
EOF
```{{execute}}

You can now deploy the first half of your own Continuous Integration toolchain:

```
ansible-playbook -i inventory site1.yml
```{{execute}}

Please review now the second playbook for HOST2 where *jenkins_configure* is
set to true, *suites* lists all the Xtesting samples. By default, Minio,
TestAPI and Cachet are deployed, you don't have to explicitly write here
*minio_deploy: true*,  *mongo_deploy: true*, etc. Last step is to list all ip
addresses or urls to join Jenkins, MongDB and PostgreSQL hosted by HOST1.

```
cat << EOF > site2.yml
- hosts: [[HOST2_IP]]
  roles:
  - role: collivier.xtesting
    suites:
      - container: xtesting
        tests:
          - first
          - second
          - third
          - fourth
          - fifth
          - sixth
      - container: xtesting-mts
        tests:
          - seventh
    jenkins_url: http://[[HOST_IP]]:8080
    jenkins_deploy: false
    jenkins_configure: true
    mongo_deploy: false
    mongo_url: mongodb://[[HOST_IP]]:27017
    postgres_deploy: false
    postgres_host: [[HOST_IP]]
EOF
```{{execute}}

As usual, Katacoda forces us to precise both test database and test artifact
urls to make them reachable from your device:

```
cat << EOF >> site2.yml
    testapi_ext_url: https://[[HOST2_SUBDOMAIN]]-8000-[[KATACODA_HOST]].environments.katacoda.com/api/v1
    http_dst_url: https://[[HOST2_SUBDOMAIN]]-8181-[[KATACODA_HOST]].environments.katacoda.com
EOF
```{{execute}}

You can now deploy the second half of your own Continuous Integration toolchain:

```
ansible-playbook -i inventory site2.yml
```{{execute}}
