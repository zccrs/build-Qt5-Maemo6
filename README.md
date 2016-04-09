#Dependencies
* Deepin or Debian or Ubuntu
* PyQt4

Deepin Download: https://www.deepin.org/download.html
***
##Build dependencies
* Scratchbox for Harmattan

i386 Download: http://scratchbox.org/debian/dists/harmattan/main/binary-i386/
x86_64 Download: http://scratchbox.org/debian/dists/harmattan/main/binary-amd64/

downloadn *deb .

* Harmattan rootstrap for Scratchbox

Download: 
http://mirror.thecust.net/hathor-sdk/arm-public-sdk-rootstrap.tgz
http://mirror.thecust.net/hathor-sdk/i386-public-sdk-rootstrap.tgz

#####download files save to ~/src/harmattan
***

##Installation
````
 $ cd ~/src/harmattan
$ dpkg -i *.deb
 $ cp arm-public-sdk-rootstrap.tgz i386-public-sdk-rootstrap.tgz /tmp
$ git clone https://github.com/zccrs/build-Qt5-Maemo6.git
$ cd build-Qt5-Maemo6
 $ sudo ./harmattan-sdk-setup.py admininstall
 $ scratchbox
 ````
![enter image description here](https://github.com/zccrs/build-Qt5-Maemo6/blob/master/%E6%B7%B1%E5%BA%A6%E6%88%AA%E5%9B%BE20160409161243.png?raw=true)
 ````
 [sbox-HARMATTAN_X86: ~] > sb-menu
 ````
 ![enter image description here](https://github.com/zccrs/build-Qt5-Maemo6/blob/master/%E6%B7%B1%E5%BA%A6%E6%88%AA%E5%9B%BE20160409161431.png?raw=true)
 ![enter image description here](https://github.com/zccrs/build-Qt5-Maemo6/blob/master/%E6%B7%B1%E5%BA%A6%E6%88%AA%E5%9B%BE20160409161442.png?raw=true)
 ![enter image description here](https://github.com/zccrs/build-Qt5-Maemo6/blob/master/%E6%B7%B1%E5%BA%A6%E6%88%AA%E5%9B%BE20160409161500.png?raw=true)
 ````
 [sbox-HARMATTAN_ARMEL: ~]
 ````
 ````
$ git clone https://github.com/zccrs/qtbase.git
$ cd qtbase
$ git checkout add_maemo_support_5.5.1
$ cd ..
$ mkdir build & cd build
$  ../qtbase/configure  -make libs -device linux-maemo-n9-g++ -device-option CROSS_COMPILE=arm-none-linux-gnueabi- -sysroot /scratchbox/users/$USER/targets/HARMATTAN_ARMEL -opensource -confirm-license -release -prefix /opt/qt5.5.1 -no-gtkstyle -no-pch -no-eglfs -qtnamespace QT5 -nomake tests -nomake examples
````

