# BeagleboneBlack
Software Development using BeagleboneBlack
## Beaglebone Black Software Environment Setup using QT5 IDE
### 1. Requirements
1)  [qt-everywhere-src-5.12.1.tar.xz](https://download.qt.io/archive/qt/5.12/5.12.1/single/)
2) 	[Qt 5.12.12 for Linux 64-bit (1.3 GB) from 5.12.x Offline Installers](https://www.qt.io/offline-installers) 
3)  [gcc-linaro-6.3.1-2017.02-i686_arm-linux-gnueabihf.tar.xz](https://releases.linaro.org/components/toolchain/binaries/6.3-2017.02/arm-linux-gnueabihf/)
4) [sysroot-relativelink.py](https://github.com/thihakyawjob/BeagleboneBlack/blob/main/sysroot-relativelink.py)

### 2. Beaglebone Black Image
* [AM3358 Debian 10.3 2020-04-06 4GB eMMC IoT Flasher](https://beagleboard.org/latest-images)
* Check the software version using the following command.

Type *ssh debian@192.168.7.2* and password: *temppwd*
![Result1](https://github.com/thihakyawjob/BeagleboneBlack/blob/main/BBB_VersionCheck1.png)
```python
debian@beaglebone:~$ lsb_release -a
```
![Result2](https://github.com/thihakyawjob/BeagleboneBlack/blob/main/BBB_VersionCheck2.png)

* Install *gdbserver* in Beaglebone Black.
```python
debian@beaglebone:~$ sudo apt-get install gdbserver
```
### 3. Installation on Ubuntu 20.04 Computer
```python
sudo apt install gcc-arm-linux-gnueabihf
sudo apt install build-essential
sudo apt install libssl-dev libffi-dev libncurses5-dev zlib1g zlib1g-dev libreadline-dev libbz2-dev libsqlite3-dev make
sudo install python3
sudo apt install gdb-multiarch
```
* Make Directory
```python
$ mkdir ~/BBB/
$ cd ~/BBB/
```
* To sync the sysroot from beaglebone to your computer, use the following commands:
In BBB folder,
```python
rsync -avz debian@192.168.7.2:/lib sysroot
rsync -avz debian@192.168.7.2:/sbin sysroot
rsync -avz debian@192.168.7.2:/usr sysroot
```
* Download **sysroot-relativelink.py** file and save it in **BBB** folder.
**BBB Folder**

![BBB Folder](https://github.com/thihakyawjob/BeagleboneBlack/blob/main/BBB_Folder.png)

Send the following command:
```python
$ ./sysroot-relativelink.py sysroot
```
* Make Directory for QT5 Software
```python
$ mkdir ~/qt-512/
$ cd ~/qt-512
$ ./configure -platform linux-g++ -release -device linux-beagleboard-g++ -sysroot /home/techgeneous/BBB/sysroot -prefix /home/techgeneous/BBB/qt-512 -hostprefix /home/techgeneous/BBB/qt-512 -device-option CROSS_COMPILE=/home/techgeneous/BBB/gcc-linaro-6.3.1/bin/arm-linux-gnueabihf- -nomake tests -nomake examples -no-opengl -opensource -confirm-license -reduce-exports -make libs
```
* Configure Qt5 for Beaglebone Black 
Extract **qt-everywhere-src-5.12.1.tar.xz** in **qt-512** folder. Then proceed to QT5 software configuration using the following command.
```python
$ cd ~/qt-512/qt-everywhere-src-5.12.1
$ ./configure -platform linux-g++ -release -device linux-beagleboard-g++ -sysroot /home/**USER**/BBB/sysroot -prefix /home/**USER**/BBB/qt-512 -hostprefix /home/**USER**/BBB/qt-512 -device-option CROSS_COMPILE=/home/**USER**/BBB/gcc-linaro-6.3.1/bin/arm-linux-gnueabihf- -nomake tests -nomake examples -no-opengl -opensource -confirm-license -reduce-exports -make libs
```
* make and make install
```python
~/qt-512/qt-everywhere-src-5.12.1$ make
~/qt-512/qt-everywhere-src-5.12.1$ make install
```
* Install Qt offline installer
```python
$ sudo ./qt-opensource-linux-x64-5.12.12.run
```
![QTInstaller](https://github.com/thihakyawjob/BeagleboneBlack/blob/main/QTInstaller.png)

### 4. Setup Kits Beaglebone Black On Qt Creator
1) Open Qt Creator
2) Go to **Tools** &rarr **Options...**
## FAQ
```python
sudo apt install libxcb-xinerama0
```
