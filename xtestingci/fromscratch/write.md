For the purpose of this Katacoda scenario, you first clone the source code:

```
git clone https://github.com/collivier/ansible-role-xtesting.git
cd ansible-role-xtesting/tests/hello
```{{execute}}

Here, you're integrating hello.robot as proposed in
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

```
pip install robotframework
robot hello.robot
```{{execute}}
