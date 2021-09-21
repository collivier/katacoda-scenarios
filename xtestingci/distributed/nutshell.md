[XtestingCI](https://github.com/collivier/ansible-role-xtesting) supports
multiple deployment models such as all-in-one (in Docker or in Kubernetes),
centralized services (e.g. OPNFV toolchain) or a mix of both.

It follows [the KISS principle](https://en.wikipedia.org/wiki/KISS_principle),
by spliting all deployment and configuration steps and by leveraging urls for
any configuration action. The same operations can be applied whatever the
services are deployed via Docker, via Kubernetes or via any other way out of
XtestingCI.

XtestingCI defines [lots of variables](https://github.com/collivier/ansible-role-xtesting/blob/master/defaults/main.yml)
to finely select the services or the steps you want to execute. For instance,
*jenkins_deploy* decides if you install Jenkins or not, *jenkins_configure*
(in addition to *jenkins_url*) if you configure it. The same model is
generalized for all the services.

The default configuration setups the following services in a single host but
you're free to change it at your convenience; it's just about setting
booleans and urls:
- [Jenkins](https://www.jenkins.io/)
- [MongoDB](https://www.mongodb.com/)
- [TestAPI](http://testresults.opnfv.org/)
- [Minio](https://min.io/)
- [PostgreSQL](https://www.postgresql.org/)
- [Cachet](https://cachethq.io/)

It's worth mentioning that all steps and urls are calculated as much as
possible for the best user experience.
