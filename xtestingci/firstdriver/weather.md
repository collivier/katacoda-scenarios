For the purpose of this Katacoda scenario, you do clone the source code:

```
git clone https://github.com/collivier/ansible-role-xtesting.git
cd ansible-role-xtesting/tests/weather
```{{execute}}

Please open ```ansible-role-xtesting/tests/weather/weather.py```{{open}}
which calls [OpenWeatherMap](https://openweathermap.org/) to collect weather
data about London. It basically verifies if the fields written in
testcases.yaml are bigger than their thresholds.

From a development point of view, this driver basically inherits from the main
Xtesting class,
[TestCase](https://xtesting.readthedocs.io/en/latest/apidoc/xtesting.core.testcase.html),
overrides
[run(**kwargs)](https://xtesting.readthedocs.io/en/latest/apidoc/xtesting.core.testcase.html#xtesting.core.testcase.TestCase.run)
which is abstact on purpose and sets all the mandatory attributes asked by
Xtesting:
- start_time
- stop_time
- result

It's worth mentioning that this driver doesn't ask to override any helper
proposed by Xtesting to:
- [push the results to the test datase](https://xtesting.readthedocs.io/en/latest/apidoc/xtesting.core.testcase.html#xtesting.core.testcase.TestCase.push_to_db)
- [publish the artifacts to the artifact repository](https://xtesting.readthedocs.io/en/latest/apidoc/xtesting.core.testcase.html#xtesting.core.testcase.TestCase.publish_artifacts)
- [Interpret the result of the test case](https://xtesting.readthedocs.io/en/latest/apidoc/xtesting.core.testcase.html#xtesting.core.testcase.TestCase.run)
- etc.

It should be noted that
[run(**kwargs)](https://xtesting.readthedocs.io/en/latest/apidoc/xtesting.core.testcase.html#xtesting.core.testcase.TestCase.run)
also dumps the request in the output dir to make it available in your artifact
repository.
