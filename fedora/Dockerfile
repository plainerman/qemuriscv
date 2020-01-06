FROM ubuntu:disco
RUN apt-get update -y && apt-get install qemu qemu-system-misc qemu-user-static binfmt-support xzdec wget -y
RUN wget https://fedorapeople.org/groups/risc-v/disk-images/bbl && \
	wget https://fedorapeople.org/groups/risc-v/disk-images/stage4-disk.img.xz

RUN xzdec -d stage4-disk.img.xz > stage4-disk.img
RUN rm stage4-disk.img.xz

COPY start.sh /start.sh

RUN chmod +x /start.sh