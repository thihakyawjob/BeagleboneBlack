# BeagleboneBlack
Software Development using BeagleboneBlack

## Beaglebone Black Software Environment Setup using QT5 IDE
### 1. Requirements
1)  [qt-everywhere-src-5.12.1.tar.xz](https://download.qt.io/archive/qt/5.12/5.12.1/single/)
2)  [gcc-linaro-6.3.1-2017.02-i686_arm-linux-gnueabihf.tar.xz](https://releases.linaro.org/components/toolchain/binaries/6.3-2017.02/arm-linux-gnueabihf/)

### 3. Beaglebone Black Image
* [AM3358 Debian 10.3 2020-04-06 4GB eMMC IoT Flasher](https://beagleboard.org/latest-images)

### 2. Installation on Ubuntu 20.04 Computer
<pre><code>
sudo apt install gcc-arm-linux-gnueabihf
sudo apt install build-essential
sudo apt install libssl-dev libffi-dev libncurses5-dev zlib1g zlib1g-dev libreadline-dev libbz2-dev libsqlite3-dev make
sudo install python3
sudo apt install gdb-multiarch
</code></pre>
To sync the sysroot from beaglebone to your computer, use the following commands:
'''
rsync -avz debian@192.168.7.2:/lib sysroot
rsync -avz debian@192.168.7.2:/sbin sysroot
rsync -avz debian@192.168.7.2:/usr sysroot
'''


