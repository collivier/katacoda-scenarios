As mentioned in the first step, Xtesting asks for a test case description file,
```ansible-role-xtesting/tests/hello/testcases.yaml```{{open}}, which simply
lists here *robotframework* as driver and */hello.robot* as suite. Here you
also define *helloworld* as project name and *hello* as case name.

The second and last requirement about Docker is also easily achievable as
highlighted by ```ansible-role-xtesting/tests/hello/Dockerfile```{{open}}.
It basically inherits from the official Xtesting Docker image
(it's alpine:3.14 + xtesting python package) and copies both *hello.robot* and
your *testcases.yaml*.

You can now build your own testing container:
```
docker build -t 127.0.0.1:5000/hello .
```{{execute}}

Finally let's check if it passes successfully:
```
docker run -t 127.0.0.1:5000/hello
```{{execute}}
