As highlighted by the previous Katacoda scenario,
[Automate your first test case](https://www.katacoda.com/ollivier/courses/xtestingci/firstdriver),
Xtesting offers multiple drivers for the main test frameworks (e.g.
Robot Framework, Behave, unittest, etc.) and
[a very simple API](https://xtesting.readthedocs.io/en/latest/apidoc/xtesting.core.testcase.html)
to write your own drivers on which this scenario focuses.

As a good example, Functest has developed a lot of Xtesting drivers for the key
opensource test frameworks such as
[Tempest](https://docs.openstack.org/tempest/latest/) and
[Rally](https://docs.openstack.org/rally/latest/) in OpenStack or
[End-to-End Testing in Kubernetes](https://github.com/kubernetes/community/blob/master/contributors/devel/sig-testing/e2e-tests.md).

On the market, they are plenty of proprietary test frameworks especially about
advanced network service testing. As they all
offer a REST API to execute the test cases and to get their results, the
related Xtesting drivers can be written in a couple of hours. But at the end of
the day, the benefits for the integrators are huge.

This scenario basically hightlights all the steps starting from a new driver
calling [OpenWeatherMap](https://openweathermap.org/) API.
