Here you simply replay the same instructions as in
[Deploy your first Continuous Integration toolchain](https://www.katacoda.com/ollivier/courses/xtestingci/firstci).
Nothing changes except than the services are spanned accross multiple servers.

Click on the Jenkins tab and then identify yourself as admin to be allowed to
trigger a build:
- login: admin
- password: admin

The default Jenkins view lists all the Jenkins jobs. You can easily find your
main job, xtesting-latest-daily, via the Jenkins view named xtesting.

You're ready to start a new build of xtesting-latest-daily without changing the
default parameters.

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
tab, then 'Select port to view on Host 2' and finally set 8001 as display port.
