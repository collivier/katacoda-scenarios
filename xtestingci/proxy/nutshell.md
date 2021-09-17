The enterprise proxies usually fail many users and Docker is particulary
misleading in this case due to its design and due to the different container
operations.

At first, the Docker client sends all operations to the Docker daemon generally
via the Docker Unix socket. Then you cannot leverage the classical and simple
environment variable configuration (e.g. http_proxy, https_proxy, etc.) where
you call the Docker client to pull a new Docker image. The proxy configuration
must be rather applied to the Docker daemon as described in
[Control Docker with systemd](https://docs.docker.com/config/daemon/systemd/).

Then you must set the proxy configuration when building your containers
to download all the packages required. As this operations are done from a
new container, you must also set the proxy configuration as
[build-time variables](https://docs.docker.com/engine/reference/commandline/build/)
whatever it's applied or not in your environment (e.g. ~/.bashrc, /etc/profile,
etc.). It should be noted that configuring
[proxies in systemd](https://docs.docker.com/config/daemon/systemd/)
only helps when downloading the parent image (i.e. FROM).

Finally, you may have to set the proxy configuration when running the
container if your software reaches internet. Here you may care not to hardcode
the proxy configuration in your container image as it would forbid everybody to
execute it from everywhere (Editor's Note: I saw this strong mistake in a big
opensource project). You can simply
[set the environment variables manually](https://docs.docker.com/network/proxy/)
when booting your container.

This scenario describes all this cases in the view of XtestingCI.
