This first case is about running the OPNFV samples which are basically offline.
Here the proxy is only used when downloading the Continuous Integration
components (i.e. to pull all docker images).

As usual, Katacoda forces us to precise both test database and test artifact
urls to make them reachable from your device:

```
echo "      http_dst_url: https://[[HOST_SUBDOMAIN]]-8181-[[KATACODA_HOST]].environments.katacoda.com" >> functest-xtesting-src/ansible/site.yml
echo "      testapi_ext_url: https://[[HOST_SUBDOMAIN]]-8000-[[KATACODA_HOST]].environments.katacoda.com/api/v1" >> functest-xtesting-src/ansible/site.yml
```{{execute HOST1}}

They are many ways to set the proxy configuration via Ansible. Here we simply
[set the environment at the play level](https://docs.ansible.com/ansible/latest/user_guide/playbooks_environment.html):

```
echo "  environment:" >> functest-xtesting-src/ansible/site.yml
echo "    http_proxy: 'http://admin:admin@[[HOST2_IP]]:3128'" >> functest-xtesting-src/ansible/site.yml
echo "    https_proxy: 'http://admin:admin@[[HOST2_IP]]:3128'" >> functest-xtesting-src/ansible/site.yml
echo "    ftp_proxy: 'http://admin:admin@[[HOST2_IP]]:3128'" >> functest-xtesting-src/ansible/site.yml
echo "    no_proxy: '[[HOST_IP]],[[HOST2_IP]]'" >> functest-xtesting-src/ansible/site.yml
```{{execute HOST1}}

There are commonly mistake due to *no_proxy*. If you don't set it correctly,
all API calls when configuring the local services will reach the enterprise
proxy which should fail.

You could have a quick look to the final playbook. It lists all the samples
included in the 2 Xtesting containers in suites and the proxy configuration in
environment:

```
cat functest-xtesting-src/ansible/site.yml
```{{execute HOST1}}

You can now deploy your own Continuous Integration toolchain by keeping an eye
on the messages printed in Terminal Host 2:

```
ansible-playbook functest-xtesting-src/ansible/site.yml
```{{execute HOST1}}

XtestingCI applied the proxy configuration to the docker daemon as described in
[Control Docker with systemd](https://docs.docker.com/config/daemon/systemd/).
Then all docker images will be pulled through the proxy without any
additional logic in the testing job.

```
cat /etc/systemd/system/docker.service.d/http-proxy.conf
```{{execute HOST1}}

Else there is no diff from a Jenkins point of view between
[Deploy your first Continuous Integration toolchain](https://www.katacoda.com/ollivier/courses/xtestingci/firstci)
and this scenario.
