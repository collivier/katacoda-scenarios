For the purpose of this Katacoda scenario, you mostly execute the same
instructions as the previous one,
[Automate your first test case](https://www.katacoda.com/ollivier/courses/xtestingci/fromscratch);
it only differs on the way to build your container.

You do first clone the source code:

```
git clone https://github.com/collivier/ansible-role-xtesting.git
cd ansible-role-xtesting/tests/hello
```{{execute}}

Again, you're integrating hello.robot as proposed in
[Robot Framework User Guide](https://robotframework.org/robotframework/latest/RobotFrameworkUserGuide.html).
Please click on ```ansible-role-xtesting/tests/hello/hello.robot```{{open}}
to open it in the IDE on the right. It's worth mentioning that you may have to
click multiple times when it lags.

Visual Studio Code suggests you to install an extension. Be free to install one
of the 2 extentions proposed if it helps by clicking on *Search Marketplace*.
In that case, you must click on *Reload Required* to finish the process and
you may have to click again on ```ansible-role-xtesting/tests/hello/hello.robot```{{open}}

This test case mostly logs *Hello, world!* and runs a could of basic checks as
shown by the following commands:

As mentioned in the first step, Xtesting asks for a test case description file,
```ansible-role-xtesting/tests/hello/testcases.yaml```{{open}}, which simply
lists here *robotframework* as driver and */hello.robot* as suite. Here you
also define *helloworld* as project name and *hello* as case name.

The second and last requirement about Docker is also easily achievable as
highlighted by ```ansible-role-xtesting/tests/hello/Dockerfile```{{open}}.
It basically inherits from the official Xtesting Docker image
(it's alpine:3.14 + xtesting python package) and copies both *hello.robot* and
your *testcases.yaml*.
