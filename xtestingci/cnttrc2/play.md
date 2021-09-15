You can identify yourself as admin to be allowed to trigger a build:
- login: admin
- password: admin

The default Jenkins view lists all the Jenkins jobs. You can easily find your
main job, functest-kubernetes-leguer-daily, via the Jenkins view named
functest-kubernetes.

You're ready to start a new build of functest-kubernetes-leguer-daily without
changing the default parameters.

The test cases are all executed after a few minutes and all the test outputs
are accessible via the console icons. If you open the
functest-kubernetes-opnfv-functest-kubernetes-healthcheck-leguer-k8s_quick-run
 one for instance, you will first read:
- the test output highlighting its status
- a link to the test database where its results are stored
- a couple of links to its artifacts automatically published

A zip file dumping all test campaign data is printed in the
functest-kubernetes-leguer-zip console. You could share it to any actor or
third-party test case result verification as in context of CNTT RC2.

You may also access the status page highlighting the overall status of your
system under tests (SUT). To do so, simply click on '+' closed to the Jenkins
tab, then 'Select port to view on Host 1' and finally set 8001 as display port.

That's all folks!
