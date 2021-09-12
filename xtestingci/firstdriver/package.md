You can now create your own Python package leveraging
[pbr](https://docs.openstack.org/pbr/3.1.1/index.html) here.

Please open ```ansible-role-xtesting/tests/weather/setup.py```{{open}} which
conforms with
[the recommended minimal one](https://docs.openstack.org/pbr/3.1.1/index.html#setup-cfg)
proposed by pbr and then review
```ansible-role-xtesting/tests/weather/setup.cfg```{{open}}, a minimal
ini-like file defining your package. It should be noted that the entry point
*xtesting.testcase* helps Xtesting to discover and to run this driver by its
name, *weather*, in any testcases.yaml.

You do also write ```ansible-role-xtesting/tests/weather/requirements.txt```{{open}}
basically listing all dependencies needed to execute this code (here only
requests and xtesting).

You can now define a few testcases via ```ansible-role-xtesting/tests/weather/testcases.yaml```{{open}}
checking humidity, pressure and temp.

```ansible-role-xtesting/tests/weather/Dockerfile```{{open}} copies all these
files in /src, installs both runtime dependencies and the new python
package.

You can now build your weather container and run it locally:
```
docker build -t 127.0.0.1:5000/weather .
docker run -t 127.0.0.1:5000/weather
```{{execute}}
