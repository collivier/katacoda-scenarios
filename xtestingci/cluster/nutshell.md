By default XtestingCI deploys all the mandatory components in docker containers
running on your localhost. It fits very well all test campaigns such as
[CNTT Kubernetes Based Reference Conformance](https://www.katacoda.com/ollivier/courses/xtestingci/cnttrc2).

Jenkins is selected rather than GitLab CI/CD because it costs far less memory
and because Continuous Development features are optional when running test
containers. But swithing to GitLab CI/CD simply simply asks you to set
*jenkins_deploy: false* and *gitlab_deploy: true* in any existing playbook.

As you will see in this scenario, leveraging any Kubernetes cluster asks you to
simply set *use_kubernetes: true* in any existing playbook. XtestingCI can even
install the cluster on your localhost via *kubernetes_deploy: true*.

Lots of components commonly used for benchmarking testing (e.g.
[Kibana](https://www.elastic.co/fr/kibana) and [Grafana](https://grafana.com/))
are disabled by default. Be free to set *kibana_deploy: true* or
*grafana_deploy: true* according to your needs.

There is a common misunderstanding that XtestingCI forces you to setup locally
all the components. In fact, there is a clear separation between installation
and configuration; you can simply disable any component installation and
rather configure the urls and the credentials of the existing services.

It's worth mentioning that XtestingCI also
[generates all 3000 Jenkins needed by Functest code verification](https://github.com/collivier/ansible-role-xtesting/blob/master/tests/jjb.yml)
without starting any container. Creating Jenkins or GitLab CI/CD jobs from
simple test case lists is more than an help for any tester as they don't have
to dive into Continuous Integration or Development nuances.
