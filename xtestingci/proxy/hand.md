Let's see now a second case where the proxy is both used when downloading the
Continuous Integration components (i.e. to pull all Docker images), when
building the container and then when running the test case.

Here, we leverage the same samples as the previous scenario
[Write your own Xtesting driver](https://www.katacoda.com/ollivier/courses/xtestingci/firstdriver)
which calls [OpenWeatherMap](https://openweathermap.org/) to collect weather
data about London.

You can now navigate to the source directory:

```
cd ~/ansible-role-xtesting/tests/weather
```{{execute HOST2}}

Yo do build the containers throught proxies as there is no weather upstream
images. Here
[build-time variables](https://docs.docker.com/engine/reference/commandline/build/)
are hugely recommended as mentioned in "Docker behind enterprise proxy".
During the build, you should see a couple of *CONNECT messages to
pypi.org:443* and *to dl-cdn.alpinelinux.org:443* in Terminal Host 1.

```
sudo docker build \
  --build-arg http_proxy=http://admin:admin@[[HOST_IP]]:3128 \
  --build-arg https_proxy=http://admin:admin@[[HOST_IP]]:3128 \
  --build-arg ftp_proxy=http://admin:admin@[[HOST_IP]]:3128 \
  --build-arg no_proxy=[[HOST2_IP]] -t 127.0.0.1:5000/weather .
```{{execute HOST2}}

You can now run the test cases by keeping an eye on the *CONNECT messages to
samples.openweathermap.org:443* in Terminal Host 1. Here we basically set the
proxy as
[environment variables](https://docs.docker.com/engine/reference/commandline/run/).

```
sudo docker run \
  -e http_proxy=http://admin:admin@[[HOST_IP]]:3128 \
  -e https_proxy=http://admin:admin@[[HOST_IP]]:3128 \
  -e ftp_proxy=http://admin:admin@[[HOST_IP]]:3128 \
  -e no_proxy=[[HOST2_IP]] 127.0.0.1:5000/weather
```{{execute HOST2}}
