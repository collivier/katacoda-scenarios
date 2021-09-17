The following operations have been covered by the previous scenarios
especially
[Deploy your first Continuous Integration toolchain](https://www.katacoda.com/ollivier/courses/xtestingci/firstci)
and
[Deploy your first Continuous Development toolchain](https://www.katacoda.com/ollivier/courses/xtestingci/firstcd).
Here we will rather focus on Terminal Host 1 where the proxy is running.

You can go back to Jenkins and find your main build job, weather-latest-docker,
via the Jenkins view named weather-docker. A job may be already in progress.
Please wait its execution a couple of minutes (be free to refresh Jenkins by
hand multiple times) and then click on weather-127.0.0.1-weather-latest-build
console. Please check if the container was successfully pushed at the end.

You should see a couple of *CONNECT messages to dl-cdn.alpinelinux.org:443*
in Terminal Host 1 when the container are built.

You're ready to start a new run of weather-latest-daily without changing the
default parameters (note: you can click on weather tab to find the job).

You should see a couple of *CONNECT messages to samples.openweathermap.org:443*
in Terminal Host 1 when the test cases are executed.

Finally you can run trivy vs your new container to find any vulnerability.
Please navigate to the weather-trivy tab and then trigger a new
weather-127.0.0.1-weather-latest-trivy (a few vulnerabilities may be detected
if the fixes have not yet been published by
[Alpine](https://www.alpinelinux.org/).

A couple of *CONNECT messages to github.com:443* should be printed in Terminal
Host 2 when the job is executed.

That's all folks!
