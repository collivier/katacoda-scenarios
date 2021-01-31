XtestingCI leverages the common test case execution proposed by Xtesting.
Thanks to a simple test case list, this tool deploys anywhere plug-and-play
Continuous Integration toolchains in a few commands.

For the purpose of this scenario, you simply download the Xtesting sample list:

```
git clone https://gerrit.opnfv.org/gerrit/functest-xtesting functest-xtesting-src
cd functest-xtesting-src
```{{execute}}

Then you can modify the default playbook to deploy the continuous integration
components in the Kubernetes cluster. As the NodePorts are in the 30000-32767
range (default), you must change the default service ports as well.

```
echo "      use_kubernetes: true" >> ansible/site.yml
echo "      jenkins_port: 30080" >> ansible/site.yml
echo "      jenkins_jnlp_port: 30050" >> ansible/site.yml
echo "      mongo_port: 30017" >> ansible/site.yml
echo "      postgres_port: 30032" >> ansible/site.yml
echo "      minio_port: 30090" >> ansible/site.yml
```{{execute}}

In this scenario, you do precise jenkins url and both external test database
and test artifact urls to make them reachable from your device. In this
particular Katakoda setup, we must go through the network address translation
to join the docker containers which asks to modify both internal test database
and test artifact urls too:

```
echo "      jenkins_url: https://[[HOST_SUBDOMAIN]]-30080-[[KATACODA_HOST]].environments.katacoda.com" >> ansible/site.yml
echo "      s3_endpoint_url: https://[[HOST_SUBDOMAIN]]-30090-[[KATACODA_HOST]].environments.katacoda.com" >> ansible/site.yml
echo "      http_dst_url: https://[[HOST_SUBDOMAIN]]-8181-[[KATACODA_HOST]].environments.katacoda.com" >> ansible/site.yml
echo "      testapi_url: https://[[HOST_SUBDOMAIN]]-8000-[[KATACODA_HOST]].environments.katacoda.com/api/v1" >> ansible/site.yml
echo "      testapi_ext_url: https://[[HOST_SUBDOMAIN]]-8000-[[KATACODA_HOST]].environments.katacoda.com/api/v1" >> ansible/site.yml
```{{execute}}

Be free to have a look to the final playbook:

```
cat ansible/site.yml
```{{execute}}

You can now deploy your own Continuous Integration toolchain:

```
ansible-playbook ansible/site.yml
```{{execute}}

The play ends after 5 minutes. Once the final Ansible message is printed,
Jenkins is accessible via the tab named Jenkins (you may have to refresh it).
