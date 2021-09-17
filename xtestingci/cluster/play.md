You can identify yourself as admin to be allowed to trigger a build:
- login: admin
- password: admin

You follow here the same instructions as
[Deploy your first Continuous Integration toolchain](https://www.katacoda.com/ollivier/courses/xtestingci/firstci).
You still find your main job, xtesting-latest-daily, via the Jenkins view named
xtesting.

You're ready to start a new build of xtesting-latest-daily without changing the
default parameters. Comparing with the previous Katacoda scenario, all runners
are here dynamic which allow skipping the Docker cache management (i.e. clean
and pull any previous Docker image).

The samples are all executed after 1 minute and all the test outputs are
accessible via the console icons. If you open the
xtesting-opnfv-xtesting-latest-fifth-run one for instance, you will first read:
- the test output highlighting its status
- a link to the test database where its results are stored
- a couple of links to its artifacts automatically published

A zip file dumping all test campaign data is printed in the xtesting-latest-zip
console.

You may also access the status page highlighting the overall status of your
system under tests (SUT). To do so, simply click on '+' closed to the Jenkins
tab, then 'Select port to view on Host 1' and finally set 8001 as display port.

That's all folks!
