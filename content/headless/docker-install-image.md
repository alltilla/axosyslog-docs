## Install the syslog-ng images by Axoflow

You can find the list of tagged versions at [https://github.com/axoflow/axosyslog-docker/pkgs/container/syslog-ng](https://github.com/axoflow/axosyslog-docker/pkgs/container/syslog-ng).

To install the latest stable version, run:

```shell
{{< param "command" >}} pull ghcr.io/axoflow/syslog-ng:latest
```

You can also use it as a base image in your Dockerfile:

```shell
FROM ghcr.io/axoflow/syslog-ng:latest
```

If you want to test a development version, you can use the nightly builds:

```shell
{{< param "command" >}} pull ghcr.io/axoflow/syslog-ng:nightly
```

> Note: These named packages are automatically updated when a new syslog-ng package is released. To install a specific version, run `docker pull ghcr.io/axoflow/syslog-ng:<version-number>`, for example:
>
> ```shell
> {{< param "command" >}} pull ghcr.io/axoflow/syslog-ng:4.1.1
> ```

## Customize the syslog-ng configuration

The AxoSyslog docker image stores the syslog-ng configuration file at `/etc/syslog-ng/syslog-ng.conf`. By default, collects the local system logs and logs received from the network into the `/var/log/messages` and `/var/log/messages-kv.log` files using the following configuration: https://github.com/syslog-ng/syslog-ng/blob/master/scl/syslog-ng.conf

To customize the configuration, create your own configuration file and override the file in the docker image with it, for example:

```bash
{{< param "command" >}} run --rm --volume <path-to-your/syslog-ng.conf>:/etc/syslog-ng/syslog-ng.conf syslog-ng:latest
```

## Contribute

If you have fixed a bug or would like to contribute your improvements to these images, [open a pull request](https://github.com/axoflow/axosyslog-docker/pulls). We truly appreciate your help.
