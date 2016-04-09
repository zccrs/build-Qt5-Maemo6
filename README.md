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
 [sbox-HARMATTAN_ARMEL: ~] apt-get update
 [sbox-HARMATTAN_ARMEL: ~] apt-get install libxcb-image0-dev libxcb-keysyms1-dev libxcb-property1-dev libxcb-randr0-dev libxcb-render0-dev libxcb-render-util0-dev libxcb-shape0-dev libxcb-shm0-dev libxcb-sync0-dev libxcb-xfixes0-dev libx11-xcb-dev libxcb-atom1-dev libxcb-aux0-dev libxcb-damage0-dev libxcb-event1-dev libxcb-glx0-dev libxcb-icccm1-dev 
 [sbox-HARMATTAN_ARMEL: ~] vim /usr/include/GLES2/gl2.h
 ````
 add #include <KHR/khrplatform.h> to line 6
 ````
 [sbox-HARMATTAN_ARMEL: ~] exit
 ````
 ````
$ git clone https://github.com/zccrs/qtbase.git
$ cd qtbase
$ git checkout add_maemo_support_5.5.1
$ cd ..
$ mkdir build & cd build
$ export PATH=/scratchbox/compilers/cs2009q3-eglibc2.10-armv7-hard/bin:PATH
$  ../qtbase/configure  -make libs -device linux-maemo-n9-g++ -device-option CROSS_COMPILE=arm-none-linux-gnueabi- -sysroot /scratchbox/users/$USER/targets/HARMATTAN_ARMEL -opensource -confirm-license -release -prefix /opt/qt5.5.1 -no-gtkstyle -no-pch -no-eglfs -qtnamespace QT5 -nomake tests -nomake examples
````
    Build options:
    Configuration .......... accessibility accessibility-atspi-bridge alsa audio-backend c++11 clock-gettime clock-monotonic       compile_examples concurrent cross_compile dbus egl egl_x11 enable_new_dtags evdev eventfd freetype full-config getaddrinfo     getifaddrs glib gstreamer-0.10 harfbuzz iconv icu inotify ipv6ifname large-config largefile linuxfb medium-config         minimal-config mremap neon nis opengl opengles2 openssl pcre png posix_fallocate pulseaudio qpa qpa reduce_exports release      rpath shared small-config system-jpeg system-zlib xcb xcb-glx xcb-plugin xcb-render xcb-sm xcb-xlib xkbcommon-qt xlib xrender 
      Build parts ............  libs
      Mode ................... release
      Using sanitizer(s)...... none
      Using C++11 ............ yes
      Using gold linker....... no
      Using new DTAGS ........ yes
      Using PCH .............. no
      Target compiler supports:
        Neon ................. yes

    Qt modules and options:
      Qt D-Bus ............... yes (loading dbus-1 at runtime)
      Qt Concurrent .......... yes
      Qt GUI ................. yes
      Qt Widgets ............. yes
      Large File ............. yes
      QML debugging .......... yes
      Use system proxies ..... no

    Support enabled for:
      Accessibility .......... yes
      ALSA ................... yes
      CUPS ................... no
      Evdev .................. yes
      FontConfig ............. no
      FreeType ............... yes (bundled copy)
      Glib ................... yes
      GStreamer .............. yes (0.10)
      GTK theme .............. no
      HarfBuzz ............... yes (bundled copy)
      Iconv .................. yes
      ICU .................... yes
      Image formats: 
        GIF .................. yes (plugin, using bundled copy)
        JPEG ................. yes (plugin, using system library)
        PNG .................. yes (in QtGui, using bundled copy)
      journald ............... no
      libinput................ no
      mtdev .................. no
      Networking: 
        getaddrinfo .......... yes
        getifaddrs ........... yes
        IPv6 ifname .......... yes
        libproxy.............. no
        OpenSSL .............. yes (loading libraries at run-time)
      NIS .................... yes
      OpenGL / OpenVG: 
        EGL .................. yes
        OpenGL ............... yes (OpenGL ES 2.0+)
        OpenVG ............... no
      PCRE ................... yes (bundled copy)
      pkg-config ............. yes 
      PulseAudio ............. yes
      QPA backends: 
        DirectFB ............. no
        EGLFS ................ no
          EGLFS i.MX6....... . no
          EGLFS KMS .......... no
          EGLFS Mali ......... no
          EGLFS Raspberry Pi . no
          EGLFS X11 .......... yes
        LinuxFB .............. yes
        XCB .................. yes (system library)
          EGL on X ........... yes
          GLX ................ yes
          MIT-SHM ............ yes
          Xcb-Xlib ........... yes
          Xcursor ............ yes (loaded at runtime)
          Xfixes ............. yes (loaded at runtime)
          Xi ................. yes (loaded at runtime)
          Xi2 ................ no
          Xinerama ........... yes (loaded at runtime)
          Xrandr ............. yes (loaded at runtime)
          Xrender ............ yes
          XKB ................ no
          XShape ............. yes
          XSync .............. yes
          XVideo ............. yes
      Session management ..... yes
      SQL drivers: 
        DB2 .................. no
        InterBase ............ no
        MySQL ................ no
        OCI .................. no
        ODBC ................. no
        PostgreSQL ........... no
        SQLite 2 ............. no
        SQLite ............... yes (plugin, using bundled copy)
        TDS .................. no
      tslib .................. no
      udev ................... no
      xkbcommon-x11........... yes (bundled copy, XKB config root: /usr/share/X11/xkb)
      xkbcommon-evdev......... no
      zlib ................... yes (system library)


    NOTE: Qt is using double for qreal on this system. This is binary incompatible against Qt 5.1.
    Configure with '-qreal float' to create a build that is binary compatible with 5.1.

    Qt is now configured for building. Just run 'make'.
    Once everything is built, you must run 'make install'.
    Qt will be installed into /opt/qt5.5.1

    Prior to reconfiguration, make sure you remove any leftovers from
    the previous build.
