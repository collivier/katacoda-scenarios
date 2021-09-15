You can identify yourself as admin to be allowed to trigger a build:
- login: admin
- password: admin

The default Jenkins view lists all the Jenkins jobs. You can easily find your
main job, weather-latest-daily, via the Jenkins view named weather.

You're ready to start a new build of weather-latest-daily without changing
the default parameters.

The test case is executed after a few seconds and all the test outputs are
accessible via the console icons. If you open the
weather-127.0.0.1-weather-latest-humidity-run, you will first read:
- the test output highlighting its status
- a link to the test database where its results are stored
- a couple of links to its artifacts automatically published

A zip file dumping all test campaign data is printed in the
weather-latest-zip console.

You may also access the status page highlighting the overall status of your
system under tests (SUT). To do so, simply click on '+' closed to the Jenkins
tab, then 'Select port to view on Host 1' and finally set 8001 as display port.

That's all folks!
