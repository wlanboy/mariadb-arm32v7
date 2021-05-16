# mariadb-arm32v7
mariadb docker image for arm32v7
Base Docker file from: https://github.com/MariaDB/mariadb-docker/blob/8be7abacca5f19d487b137c7d8f9516d07116109/10.5/Dockerfile

# Still available and maintained images:
- https://hub.docker.com/r/arm32v7/adoptopenjdk
- https://hub.docker.com/r/arm32v7/maven
- https://hub.docker.com/r/arm32v7/golang

# Example for multi arch build
- see Workflow file for details: https://github.com/wlanboy/mariadb-arm32v7/blob/main/.github/workflows/docker-publish.yml
- create env vars
- setup qemu for arm32v7
- setup docker for arm32v7
- build docker image for arm32v7
- publish docker image

# docker hub
- https://hub.docker.com/repository/docker/wlanboy/mariadb-arm32v7

# Run arm based docker images with X86 CPUs
- sudo apt-get install qemu binfmt-support qemu-user-static 
- docker run --rm --privileged multiarch/qemu-user-static --reset -p yes
- output
```
Status: Downloaded newer image for multiarch/qemu-user-static:latest
Setting /usr/bin/qemu-alpha-static as binfmt interpreter for alpha
Setting /usr/bin/qemu-arm-static as binfmt interpreter for arm
Setting /usr/bin/qemu-armeb-static as binfmt interpreter for armeb
Setting /usr/bin/qemu-sparc-static as binfmt interpreter for sparc
Setting /usr/bin/qemu-sparc32plus-static as binfmt interpreter for sparc32plus
Setting /usr/bin/qemu-sparc64-static as binfmt interpreter for sparc64
Setting /usr/bin/qemu-ppc-static as binfmt interpreter for ppc
Setting /usr/bin/qemu-ppc64-static as binfmt interpreter for ppc64
Setting /usr/bin/qemu-ppc64le-static as binfmt interpreter for ppc64le
Setting /usr/bin/qemu-m68k-static as binfmt interpreter for m68k
Setting /usr/bin/qemu-mips-static as binfmt interpreter for mips
Setting /usr/bin/qemu-mipsel-static as binfmt interpreter for mipsel
Setting /usr/bin/qemu-mipsn32-static as binfmt interpreter for mipsn32
Setting /usr/bin/qemu-mipsn32el-static as binfmt interpreter for mipsn32el
Setting /usr/bin/qemu-mips64-static as binfmt interpreter for mips64
Setting /usr/bin/qemu-mips64el-static as binfmt interpreter for mips64el
Setting /usr/bin/qemu-sh4-static as binfmt interpreter for sh4
Setting /usr/bin/qemu-sh4eb-static as binfmt interpreter for sh4eb
Setting /usr/bin/qemu-s390x-static as binfmt interpreter for s390x
Setting /usr/bin/qemu-aarch64-static as binfmt interpreter for aarch64
Setting /usr/bin/qemu-aarch64_be-static as binfmt interpreter for aarch64_be
Setting /usr/bin/qemu-hppa-static as binfmt interpreter for hppa
Setting /usr/bin/qemu-riscv32-static as binfmt interpreter for riscv32
Setting /usr/bin/qemu-riscv64-static as binfmt interpreter for riscv64
Setting /usr/bin/qemu-xtensa-static as binfmt interpreter for xtensa
Setting /usr/bin/qemu-xtensaeb-static as binfmt interpreter for xtensaeb
Setting /usr/bin/qemu-microblaze-static as binfmt interpreter for microblaze
Setting /usr/bin/qemu-microblazeel-static as binfmt interpreter for microblazeel
Setting /usr/bin/qemu-or1k-static as binfmt interpreter for or1k
```
- test platform linux/arm/v7
```
docker run --rm --platform linux/arm/v7 -t arm32v7/ubuntu uname -m
armv7l
```
