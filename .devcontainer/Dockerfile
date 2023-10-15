FROM ubuntu:20.04

RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive TZ=Etc/UTC apt-get install -y bison flex gettext texinfo libncurses5-dev libncursesw5-dev gperf automake libtool pkg-config build-essential gperf genromfs libgmp-dev libmpc-dev libmpfr-dev libisl-dev binutils-dev libelf-dev libexpat-dev gcc-multilib g++-multilib picocom u-boot-tools util-linux chrony libusb-dev libusb-1.0.0-dev kconfig-frontends python3-pip
RUN apt-get install -y wget git curl

RUN wget https://github.com/espressif/crosstool-NG/releases/download/esp-12.2.0_20230208/xtensa-esp32-elf-12.2.0_20230208-x86_64-linux-gnu.tar.xz
RUN tar -xf xtensa-esp32-elf-12.2.0_20230208-x86_64-linux-gnu.tar.xz
RUN mkdir /opt/xtensa
RUN mv xtensa-esp32-elf/ /opt/xtensa/
ENV PATH="${PATH}:/opt/xtensa/xtensa-esp32-elf/bin"

RUN mkdir -p /root/nuttxspace/esp-bins
RUN curl -L "https://github.com/espressif/esp-nuttx-bootloader/releases/download/latest/bootloader-esp32.bin" -o /root/nuttxspace/esp-bins/bootloader-esp32.bin
RUN curl -L "https://github.com/espressif/esp-nuttx-bootloader/releases/download/latest/partition-table-esp32.bin" -o /root/nuttxspace/esp-bins/partition-table-esp32.bin

RUN pip3 install esptool
RUN pip3 install pyserial
WORKDIR /root/nuttxspace

CMD [ "/bin/bash" ]