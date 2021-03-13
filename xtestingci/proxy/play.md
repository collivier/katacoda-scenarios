You can access to Jenkins to start a new build of xtesting-latest-daily as you
applied when
[deploying your first Continuous Integration toolchain](https://www.katacoda.com/ollivier/courses/xtestingci/firstci).
To do so, simply click on '+' closed to the Terminal Host 1
tab, then 'Select port to view on Host 1' and finally set 8080 as display port.

The default Jenkins view lists all the Jenkins jobs. You can easily find your
main job, xtesting-latest-daily, via the Jenkins view named xtesting.

Then you can identify yourself as admin to be allowed to trigger a build:
- login: admin
- password: admin

You're ready to start a new build of xtesting-latest-daily without changing the
default parameters.

You should see a couple of *GET messages to docker-registry-mirror.katacoda.com*
in Terminal Host 2 when opnfv/xtesting and opnfv/xtesting-mts are pulled.
