You can identify yourself as admin to be allowed to view or to trigger a build:
- login: admin
- password: admin

The default Jenkins view lists all the Jenkins jobs. You can easily find your
main build job, helloworld-latest-docker, via the Jenkins view named
helloworld-docker.

A job should be already in progress (note: you may see a
couple of jobs in failures because the job can be automatically triggered
before gitea is up and running due to the short polling here).

Please wait a couple of minutes (be free to refresh Jenkins by hand multiple
times) and then click on helloworld-127.0.0.1-hello-latest-build console.
You should see that the container was successfully pushed at the end.

You're ready to start a new build of helloworld-latest-daily without changing
the default parameters (note you can click on helloworld tab to find the job).

Your test case is executed after 1 minute If you open
helloworld-127.0.0.1-hello-latest-hello-run console, you will first read:
- the test output highlighting its status
- a link to the test database where its results are stored
- a couple of links to its artifacts automatically published

A zip file dumping all test campaign data is printed in the
helloworld-latest-zip console.

You may also access the status page highlighting the overall status of your
system under tests (SUT). To do so, simply click on '+' closed to the Jenkins
tab, then 'Select port to view on Host 1' and finally set 8001 as display port.

You can also run trivy vs your new container to find any vulnerability. Please
navigate to the helloworld-trivy tab and then trigger a new
helloworld-127.0.0.1-hello-latest-trivy.

A few vulnerabilities may be detected if the fixes have not yet been published
by [Alpine](https://www.alpinelinux.org/).

That's all folks!
