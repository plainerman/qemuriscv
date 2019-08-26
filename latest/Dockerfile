FROM ubuntu:disco

RUN apt-get update -y && apt-get install qemu qemu-system-misc qemu-user autoconf automake autotools-dev curl libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bc zlib1g-dev libexpat-dev git -y

RUN cd /tmp && git clone --recursive --progress https://github.com/riscv/riscv-gnu-toolchain && \
	cd riscv-gnu-toolchain && \
	git submodule update --init --recursive --progress

RUN mkdir -p /opt/riscv
RUN export PATH="/opt/riscv/bin:$PATH"

RUN cd /tmp/riscv-gnu-toolchain && ./configure --prefix=/opt/riscv && make linux

RUN apt-get purge autoconf automake autotools-dev curl libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bc zlib1g-dev libexpat-dev git -y
RUN apt-get clean
RUN rm -R /tmp/*
