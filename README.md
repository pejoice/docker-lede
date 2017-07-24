# Docker LEDE
This is a LEDE image build environment.

Current LEDE version: v17.01.2

## How to use
Start with bash shell:
```shell
docker run -ti --name=lede -v /path/to/binary:/home/lede/lede/bin acrisliu/lede
```

Ensure that `/path/to/binary` is accessible by the lede user in container.

Then you can configure your LEDE image by following steps:
- run `make menuconfig` and set target;
- run `make defconfig` to set default config for build system and device;
- run `make menuconfig` and modify set of package;
- run `make` command to build LEDE image.


You can also build your docker image with external configuration file:

```
FROM acrisliu/lede
COPY .config /home/lede/lede
CMD ["make"]
```

Or using config diff file:

```
FROM acrisliu/lede
COPY .diffconfig /home/lede/lede/.config
RUN make defconfig
CMD ["make"]
```

---

You can find more usage here: https://github.com/Acris/docker-lede-netgear-r6100
