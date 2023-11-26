---
permalink: LFS/
---

# LFS AARCH64 (ARM64)

[HOME](../) --- [LFS ARM64 Book (<span style="color:red; font-weight:bold;">KW</span>)](https://www.linuxfromscratch.org/~xry111/lfs/view/arm64/) --- [LFS 12.0 AMD64 Book (<span style="color:red; font-weight:bold;">ORI</span>)](https://www.linuxfromscratch.org/lfs/view/12.0/) --- [&#x213C;](#idxXX)<br id="idx00">
## TOC

* [Packages](#idx01)
* [4.2. Creating a Limited Directory Layout in the LFS Filesystem](#CH42)
* [4.3. Adding the LFS User](#CH43)
* [5.3. GCC-13.2.0 - Pass 1](#idx02)
* [5.5. Glibc-2.38](#idx505)
* [6.18. GCC-13.2.0 - Pass 2](#idx05)
* [7.2 - 7.3 - 7.4 Script](#idx702)
* [7.12. Util-linux-2.39.1](#idx712)
* [8.5. Glibc-2.38](#idx805)
* [8.6. Zlib-1.3 (KW) --> 8.6. Zlib-1.2.13 (ORI)](#idx806)
* [8.18. Pkgconf-2.0.3 (KW) --> 8.28. Pkgconf-2.0.1 (ORI)](#idx818)
* [8.19. Binutils-2.41 (KW) --> 8.18. Binutils-2.41 (ORI)](#idx819)
* [8.21. MPFR-4.2.1 (KW) --> 8.20. MPFR-4.2.0 (ORI)](#idx821)
* [8.27. Shadow-4.14.0 (KW) --> 8.26. Shadow-4.13 (ORI)](#idx827)
* [8.28. GCC-13.2.0 (KW) --> 8.27. GCC-13.2.0 (ORI)](#idx828)
* [8.29. Ncurses-6.4 (KW) --> 8.29. Ncurses-6.4 (ORI)](#idx829)
* [8.30. Sed-4.9 (KW) --> 8.30. Sed-4.9 (ORI)](#idx830)
* [8.51. Python-3.11.5 (KW) --> 8.51. Python-3.11.4 (ORI)](#idx851)
* [8.53. Wheel-0.41.2 (KW) --> 8.53. Wheel-0.41.1 (ORI)](#idx853)
* [8.56. Coreutils-9.4 (KW) --> 8.56. Coreutils-9.3 (ORI)](#idx856)
* [8.63. Gzip-1.13 (KW) --> 8.63. Gzip-1.12 (ORI)](#idx863)
* [8.65. Kbd-2.6.2 (KW) --> 8.65. Kbd-2.6.1 (ORI)](#idx865)
* [8.71. Vim-9.0.1837 (KW) --> 8.71. Vim-9.0.1677 (ORI)](#idx871)
* [8.76. Procps-ng-4.0.4 (KW) --> 8.76. Procps-ng-4.0.3 (ORI)](#idx876)
* [8.77. Util-linux-2.39.2 (KW) --> 8.77. Util-linux-2.39.1 (ORI)](#idx877)
* [8.80. Sysvinit-3.08 (KW) --> 8.80. Sysvinit-3.07 (ORI)](#idx880)

[&#x213C;](#)<br id="idx01">
## Packages

[LFS ARM64](https://www.linuxfromscratch.org/~xry111/lfs/view/arm64/) is not an official version (KW) and 
changes frequently. Therefore, it is recommended to use a package similar to the official version of LFS 12.0 
([ORI](https://www.linuxfromscratch.org/lfs/view/12.0/)).

Because of this, the instructions for the KW version packages often differ from those for the ORI. 
Since it uses the ORI package, it must sometimes be compiled using the ORI method. 
Please be careful, especially when working on chapter 8, and explicitly compiling GCC (chapter 8.27).

### LFS Chapter 3.1 Download Script for AMD64 and ARM64 (<span style="color:red; font-weight:bold;">root</span>)

```
echo "============================================"
echo "LFS should be /mnt/lfs AND MAKEFLAGS = cores"
echo "LFS=$LFS MAKEFLAGS=$MAKEFLAGS"
echo "============================================"
sleep 3
mkdir -pv $LFS/sources/
chmod -v  a+wt $LFS/sources/
cd        $LFS/sources/
wget -c   https://www.linuxfromscratch.org/lfs/view/12.0/wget-list-sysv --directory-prefix=$LFS/sources
wget -c   --input-file=$LFS/sources/wget-list-sysv --directory-prefix=$LFS/sources
wget -c   https://www.linuxfromscratch.org/lfs/view/12.0/md5sums --directory-prefix=$LFS/sources
md5sum -c md5sums
chown root:root $LFS/sources/*

```

* [**ORI** Package Link](https://www.linuxfromscratch.org/lfs/view/12.0/chapter03/introduction.html)
* [KW Package Link](https://www.linuxfromscratch.org/~xry111/lfs/view/arm64/chapter03/introduction.html)

[&#x213C;](#)<br id="idx01">
### ORI vs KW

| **ORI (amd64)**                      | **KW (arm64)**                       |
| x -------------------------------- x | x -------------------------------- x | 
| Coreutils-9.3                        | Coreutils-9.4                        |
| Gawk-5.2.2                           | Gawk-5.2.2                           |
| GCC-13.2.0                           | GCC-13.2.0                           |
| Grep-3.11                            | Grep-3.11                            |
| Iana-Etc-20230810                    | Iana-Etc-20230810                    |
| IPRoute2-6.4.0                       | IPRoute2-6.4.0                       |
| Less-643                             | Less-643                             |
| Libcap-2.69                          | Libcap-2.69                          |
| Libelf from Elfutils-0.189           | Libelf from Elfutils-0.189           |
| Linux-6.4.12                         | Linux-6.5.1                          |
| Make-4.4.1                           | Make-4.4.1                           |
| Man-pages-6.05.01                    | Man-pages-6.05.01                    |
| Meson-1.2.1                          | Meson-1.2.1                          |
| Perl-5.38.0                          | Perl-5.38.0                          |
| Procps-ng-4.0.3                      | Procps-ng-4.0.4                      |
| Python-3.11.4                        | Python-3.11.5                        |
| Sysvinit-3.07                        | Sysvinit-3.08                        |
| Texinfo-7.0.3                        | Texinfo-7.0.3                        |
| tzdata2023c.tar.gz                   | tzdata2023c.tar.gz                   |
| Vim-9.0.1677                         | Vim-9.0.1837                         |
| Wheel-0.41.1                         | Wheel-0.41.2                         |
| Xz-5.4.4                             | Xz-5.4.4                             |
| Zstd-1.5.5                           | Zstd-1.5.5                           |
| x -------------------------------- x | x -------------------------------- x | 


[&#x213C;](#)<br id="CH42">
## 4.2. Creating a Limited Directory Layout in the LFS Filesystem

* (ROOT)
* The LFS editors have deliberately decided not to use a /usr/lib64 directory. 

```
mkdir -pv $LFS/{etc,var} $LFS/usr/{bin,lib,sbin}

for i in bin lib sbin; do
  ln -sv usr/$i $LFS/$i
done

mkdir -pv $LFS/tools

```

[&#x213C;](#)<br id="CH43">
## 4.3. Adding the LFS User

* Grant lfs full access to all the directories under $LFS by making lfs the owner

```
chown -v lfs $LFS/{usr{,/*},lib,var,etc,bin,sbin,tools}

```

[&#x213C;](#)<br id="idx02">
## 5.3. GCC-13.2.0 - Pass 1

* Package version mpfr-4.2.0.tar.xz (not mpfr-4.2.1.tar.xz)

```
tar -xf ../mpfr-4.2.0.tar.xz
mv -v mpfr-4.2.0 mpfr
tar -xf ../gmp-6.3.0.tar.xz
mv -v gmp-6.3.0 gmp
tar -xf ../mpc-1.3.1.tar.gz
mv -v mpc-1.3.1 mpc

```

* On ARM64 hosts, set the default directory name for 64-bit libraries to “lib”

```
sed -e '/lp64=/s/lib64/lib/' \
    -i.orig gcc/config/aarch64/t-aarch64-linux

```

[&#x213C;](#)<br id="idx505">
## 5.5. Glibc-2.38

* Skipping to create a symbolic link for LSB compliance (x86_64 only)! 

[&#x213C;](#)<br id="idx05">
## 6.18. GCC-13.2.0 - Pass 2

* Package version mpfr-4.2.0.tar.xz (not mpfr-4.2.1.tar.xz)

```
tar -xf ../mpfr-4.2.0.tar.xz
mv -v mpfr-4.2.0 mpfr
tar -xf ../gmp-6.3.0.tar.xz
mv -v gmp-6.3.0 gmp
tar -xf ../mpc-1.3.1.tar.gz
mv -v mpc-1.3.1 mpc

```

* On ARM64 hosts, set the default directory name for 64-bit libraries to “lib”

```
sed -e '/lp64=/s/lib64/lib/' \
    -i.orig gcc/config/aarch64/t-aarch64-linux

```

[&#x213C;](#)<br id="idx702">
## 7.2 - 7.3 - 7.4 Script

* Virtual Kernel File Systems and CHROOT

```
echo "= (1) ======================================"; sleep 1
echo "LFS=$LFS NPROC=$(nproc) MAKEFLAGS=$MAKEFLAGS"
echo "= (2) ======================================"; sleep 1
chown -Rv root:root $LFS/{usr,lib,var,etc,bin,sbin,tools}
case $(uname -m) in
  x86_64) chown -Rv root:root $LFS/lib64 ;;
esac
mkdir -pv $LFS/{dev,proc,sys,run}
echo "= (3) ======================================"; sleep 1
mount -v --bind /dev $LFS/dev
mount -v --bind /dev/pts $LFS/dev/pts
mount -vt  proc proc  $LFS/proc
mount -vt sysfs sysfs $LFS/sys
mount -vt tmpfs tmpfs $LFS/run
echo "= (4) ======================================"; sleep 1
if [ -h $LFS/dev/shm ]; then
  mkdir -pv $LFS/$(readlink $LFS/dev/shm)
else
  mount -t tmpfs -o nosuid,nodev tmpfs $LFS/dev/shm
fi
echo "= (5) ======================================"; sleep 1
df /
echo "= (6) ======================================"; sleep 1
chroot "$LFS" /usr/bin/env -i   \
    HOME=/root                  \
    TERM="$TERM"                \
    PS1='(lfs chroot) \u:\w\$ ' \
    PATH=/usr/bin:/usr/sbin     \
    MAKEFLAGS=-j$(nproc)        \
    /bin/bash --login

```

[&#x213C;](#)<br id="idx712">
## 7.12. Util-linux-2.39.1

* Prepare Util-linux for compilation:

```
./configure ADJTIME_PATH=/var/lib/hwclock/adjtime    \
            --libdir=/usr/lib    \
            --runstatedir=/run   \
            --docdir=/usr/share/doc/util-linux-2.39.1 \
            --disable-chfn-chsh  \
            --disable-login      \
            --disable-nologin    \
            --disable-su         \
            --disable-setpriv    \
            --disable-runuser    \
            --disable-pylibmount \
            --disable-static     \
            --without-python

```

[&#x213C;](#)<br id="idx805">
## 8.5. Glibc-2.38 (locale)
* SKIP “make localedata/install-locales”
  * Or, your file “/lib/locale/locale-archive” size will be humongous.
* Locale Time: Asia/Jakarta

```
ln -sfv /usr/share/zoneinfo/Asia/Jakarta /etc/localtime

```

[&#x213C;](#)<br id="idx806">
## 8.6. Zlib-1.3 (KW) --> 8.6. Zlib-1.2.13 (ORI)
* Different version, same procedure.

[&#x213C;](#)<br id="idx818">
## 8.18. Pkgconf-2.0.3 (KW) --> 8.28. Pkgconf-2.0.1 (ORI)

* Prepare Pkgconf for compilation:

```
./configure --prefix=/usr              \
            --disable-static           \
            --docdir=/usr/share/doc/pkgconf-2.0.1

```

[&#x213C;](#)<br id="idx819">
## 8.19. Binutils-2.41 (KW) --> 8.18. Binutils-2.41 (ORI)
* There is a shift from 8.19 (KW) to 8.18 (ORI) ...

## 8.20. GMP-6.3.0 (KW) --> 8.19. GMP-6.3.0 (ORI) ...
* There is a shift from 8.20 (KW) to 8.19 (ORI) ...

[&#x213C;](#)<br id="idx821">

## 8.21. MPFR-4.2.1 (KW) --> 8.20. MPFR-4.2.0 (ORI)

* Fix a test case based on a bug of old Glibc releases:

```
sed -e 's/+01,234,567/+1,234,567 /' \
    -e 's/13.10Pd/13Pd/'            \
    -i tests/tsprintf.c

```

* Compile the package and generate the HTML documentation:

```
./configure --prefix=/usr        \
            --disable-static     \
            --enable-thread-safe \
            --docdir=/usr/share/doc/mpfr-4.2.0

```

[&#x213C;](#)<br id="idx827">
## 8.27. Shadow-4.14.0 (KW) --> 8.26. Shadow-4.13 (ORI)

* Same procedure.

[&#x213C;](#)<br id="idx828">
## 8.28. GCC-13.2.0 (KW) --> 8.27. GCC-13.2.0 (ORI)

* On ARM64 hosts, set the default directory name for 64-bit libraries to “lib”:

```
sed -e '/lp64=/s/lib64/lib/' \
    -i.orig gcc/config/aarch64/t-aarch64-linux

```

[&#x213C;](#)<br id="idx829">
## 8.29. Ncurses-6.4 (KW) --> 8.29. Ncurses-6.4 (ORI)

* Same again.

[&#x213C;](#)<br id="idx830">
## 8.30. Sed-4.9 (KW) --> 8.30. Sed-4.9 (ORI)

* Same again.

[&#x213C;](#)<br id="idx851">
## 8.51. Python-3.11.5 (KW) --> 8.51. Python-3.11.4 (ORI)

* If desired, install the preformatted documentation:

```
install -v -dm755 /usr/share/doc/python-3.11.4/html

tar --strip-components=1  \
    --no-same-owner       \
    --no-same-permissions \
    -C /usr/share/doc/python-3.11.4/html \
    -xvf ../python-3.11.4-docs-html.tar.bz2

```

[&#x213C;](#)<br id="idx853">
## 8.53. Wheel-0.41.2 (KW) --> 8.53. Wheel-0.41.1 (ORI)

* Use the ORI book instruction!

```
pip3 wheel -w dist --no-build-isolation --no-deps $PWD
pip3 install --no-index --find-links=dist wheel

```

[&#x213C;](#)<br id="idx856">
## 8.56. Coreutils-9.4 (KW) --> 8.56. Coreutils-9.3 (ORI)

* POSIX requires that programs from Coreutils recognize character boundaries correctly even in multibyte locales.

```
patch -Np1 -i ../coreutils-9.3-i18n-1.patch

```

[&#x213C;](#)<br id="idx863">
## 8.63. Gzip-1.13 (KW) --> 8.63. Gzip-1.12 (ORI)

* Same procedure.

[&#x213C;](#)<br id="idx865">
## 8.65. Kbd-2.6.2 (KW) --> 8.65. Kbd-2.6.1 (ORI)

* The following patch fixes this issue for i386 keymaps:

```
patch -Np1 -i ../kbd-2.6.1-backspace-1.patch

```

* If desired, install the documentation:

```
cp -R -v docs/doc -T /usr/share/doc/kbd-2.6.1

```

[&#x213C;](#)<br id="idx871">
## 8.71. Vim-9.0.1837 (KW) --> 8.71. Vim-9.0.1677 (ORI)

* The following symlink allows the documentation to be accessed via /usr/share/doc/vim-9.0.1677, 
  making it consistent with the location of documentation for other packages:

```
ln -sv ../vim/vim90/doc /usr/share/doc/vim-9.0.1677

```

[&#x213C;](#)<br id="idx876">
## 8.76. Procps-ng-4.0.4 (KW) --> 8.76. Procps-ng-4.0.3 (ORI)

* Prepare Procps-ng for compilation:

```
./configure --prefix=/usr                           \
            --docdir=/usr/share/doc/procps-ng-4.0.3 \
            --disable-static                        \
            --disable-kill

```

[&#x213C;](#)<br id="idx877">
## 8.77. Util-linux-2.39.2 (KW) --> 8.77. Util-linux-2.39.1 (ORI)

* Prepare Util-linux for compilation:

```
./configure ADJTIME_PATH=/var/lib/hwclock/adjtime \
            --bindir=/usr/bin    \
            --libdir=/usr/lib    \
            --runstatedir=/run   \
            --sbindir=/usr/sbin  \
            --disable-chfn-chsh  \
            --disable-login      \
            --disable-nologin    \
            --disable-su         \
            --disable-setpriv    \
            --disable-runuser    \
            --disable-pylibmount \
            --disable-static     \
            --without-python     \
            --without-systemd    \
            --without-systemdsystemunitdir \
            --docdir=/usr/share/doc/util-linux-2.39.1

```

[&#x213C;](#)<br id="idx880">
## 8.80. Sysvinit-3.08 (KW) --> 8.80. Sysvinit-3.07 (ORI)

* First, apply a patch that removes several programs installed by other packages, clarifies a message, and fixes a compiler warning:

```
patch -Np1 -i ../sysvinit-3.07-consolidated-1.patch

```

<hr>
[&#x213C;](#)<br id="idxXX">
