For the purpose of this scenario, you download the Xtesting sample list again:

```
git clone https://gerrit.opnfv.org/gerrit/functest-xtesting functest-xtesting-src
cd functest-xtesting-src
```{{execute}}

For the purpose of this scenario, you modify the default playbook to deploy the
Continuous Integration components in the Kubernetes cluster.
```
echo "      use_kubernetes: true" >> ansible/site.yml
```{{execute}}

We do modify a couple of configuration values due to Katacoda. At first the
NodePorts are in the 30000-32767 range (default) which asks us to change all
service ports:

```
echo "      jenkins_port: 30080" >> ansible/site.yml
echo "      jenkins_jnlp_port: 30050" >> ansible/site.yml
echo "      mongo_port: 30017" >> ansible/site.yml
echo "      postgres_port: 30032" >> ansible/site.yml
echo "      minio_port: 30090" >> ansible/site.yml
```{{execute}}

Then, you do precise jenkins url, both external test database
and test artifact urls to make them reachable from your device. In this
particular Katakoda setup, we must go through the network address translation
to join the docker containers which asks us to modify both internal test
database and test artifact urls too:

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
