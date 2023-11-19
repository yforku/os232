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
* [8.5. Glibc-2.37](#idx06)
* [8.8. Xz-5.4.1](#idx07)
* [8.16. Expect-5.45.4](#idx08)
* [8.26. GCC-13.2.0](#idx09)
* [8.46. OpenSSL-3.0.8](#idx10)
* [8.49. Libffi-3.4.4](#idx11)
* [8.50. Python-3.11.2](#idx12)
* [8.51. Flit-Core-3.8.0](#idx13)
* [8.51. Wheel-0.38.4 --> 8.52. Wheel-0.40.0](#idx13a)
* 8.52. Ninja-1.11.1 --> 8.53. Ninja-1.11.1
* 8.53. Meson-1.0.0 --> 8.54. Meson-1.1.0
* [8.54. Coreutils-9.3 --> 8.55. Coreutils-9.4](#idx14)
* 8.55. Check-0.15.2 --> 8.56. Check-0.15.2
* 8.56. Diffutils-3.9 --> 8.57. Diffutils-3.9
* [8.57. Gawk-5.2.1 --> 8.58. Gawk-5.2.2](#idx15)
* 8.58. Findutils-4.9.0 --> 8.59. Findutils-4.9.0
* 8.59. Groff-1.22.4 --> 8.60. Groff-1.22.4
* 8.60. GRUB-2.06 --> 8.61. GRUB-2.06
* [8.62. IPRoute2-6.1.0 --> 8.63. IPRoute2-6.3.0](#idx16)
* 8.63. Kbd-2.5.1 --> 8.64. Kbd-2.5.1
* 8.64. Libpipeline-1.5.7 --> 8.65. Libpipeline-1.5.7
* [8.65. Make-4.4 --> 8.66. Make-4.4.1](#idx16a)
* 8.66. Patch-2.7.6 --> 8.67. Patch-2.7.6
* 8.67. Tar-1.34 --> 8.68. Tar-1.34
* 8.68. Texinfo-7.0.2 --> 8.69. Texinfo-7.0.2
* [8.69. Vim-9.0.1273 --> 8.70. Vim-9.0.1503](#idx17)
* 8.70. Eudev-3.2.11 --> 8.71. Eudev-3.2.11
* 8.71. Man-DB-2.11.2 --> 8.72. Man-DB-2.11.2
* [8.72. Procps-ng-4.0.2 --> 8.73. Procps-ng-4.0.3](#idx18)
* 8.73. Util-linux-2.38.1 --> 8.74. Util-linux-2.38.1
* 8.74. E2fsprogs-1.47.0 --> 8.75. E2fsprogs-1.47.0
* 8.75. Sysklogd-1.5.1 --> 8.76. Sysklogd-1.5.1
* [8.76. Sysvinit-3.06 --> 8.77. Sysvinit-3.07](#idx19)

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
# Not in the ORI book
wget -c https://pypi.org/packages/source/f/flit-core/flit_core-3.8.0.tar.gz --directory-prefix=$LFS/sources
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
| OpenSSL-3.1.2                        | OpenSSL-3.1.2                        |
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

[&#x213C;](#)<br id="idx06">
## 8.5. Glibc-2.37

* Since tzdata2022g.tar.gz has been replace with tzdata2023c.tar.gz, the workaround is to create a symbolic link (<span style="color:red; font-weight:bold;">root</span>).

```
ln -s /sources/tzdata2022g.tar.gz /sources/tzdata2023c.tar.gz

```
[&#x213C;](#)<br id="idx07">
## 8.8. Xz-5.4.1

* Prepare Xz for compilation with:

```
./configure --prefix=/usr    \
            --disable-static \
            --docdir=/usr/share/doc/xz-5.4.1

```

[&#x213C;](#)<br id="idx08">
## 8.16. Expect-5.45.4

* Update two config scripts to allow building this package for AArch64:

```
tar -C tclconfig -xf ../autoconf-2.71.tar.xz --strip-components=2 \
    autoconf-2.71/build-aux/config.{guess,sub}

```

[&#x213C;](#)<br id="idx09">
## 8.26. GCC-13.2.0

* On ARM64 hosts, set the default directory name for 64-bit libraries to “lib”:

```
sed -e '/lp64=/s/lib64/lib/' \
    -i.orig gcc/config/aarch64/t-aarch64-linux

```

* Prepare GCC for compilation:

```
../configure --prefix=/usr            \
             LD=ld                    \
             --enable-languages=c,c++ \
             --enable-default-pie     \
             --enable-default-ssp     \
             --disable-multilib       \
             --disable-bootstrap      \
             --with-system-zlib

```

### <span style="color:red; font-weight:bold;">Follow the ORI Book</span>
* After "make install"

```
chown -v -R root:root \
    /usr/lib/gcc/$(gcc -dumpmachine)/12.2.0/include{,-fixed}
ln -svr /usr/bin/cpp /usr/lib
ln -sfv ../../libexec/gcc/$(gcc -dumpmachine)/12.2.0/liblto_plugin.so \
        /usr/lib/bfd-plugins/
echo 'int main(){}' > dummy.c
cc dummy.c -v -Wl,--verbose &> dummy.log
readelf -l a.out | grep ': /lib'

```

* Now make sure that we're set up to use the correct start files:

```
grep -E -o '/usr/lib.*/S?crt[1in].*succeeded' dummy.log
grep -B4 '^ /usr/include' dummy.log
grep 'SEARCH.*/usr/lib' dummy.log |sed 's|; |\n|g'
grep "/lib.*/libc.so.6 " dummy.log
grep found dummy.log
rm -v dummy.c a.out dummy.log
mkdir -pv /usr/share/gdb/auto-load/usr/lib
mv -v /usr/lib/*gdb.py /usr/share/gdb/auto-load/usr/lib

```

[&#x213C;](#)<br id="idx10">
## 8.46. OpenSSL-3.0.8

* Add the version to the documentation directory name, to be consistent with other packages:

```
mv -v /usr/share/doc/openssl /usr/share/doc/openssl-3.0.8
cp -vfr doc/* /usr/share/doc/openssl-3.0.8

```

[&#x213C;](#)<br id="idx11">
## 8.49. Libffi-3.4.4

* Prepare Libffi for compilation:

```
./configure --prefix=/usr          \
            --disable-static       \
            --with-gcc-arch=native

```

[&#x213C;](#)<br id="idx12">
## 8.50. Python-3.11.2

* If desired, install the preformatted documentation:

```
install -v -dm755 /usr/share/doc/python-3.11.2/html

tar --strip-components=1  \
    --no-same-owner       \
    --no-same-permissions \
    -C /usr/share/doc/python-3.11.2/html \
    -xvf ../python-3.11.2-docs-html.tar.bz2

```

[&#x213C;](#)<br id="idx13">
## 8.51. Flit-Core-3.8.0

<span style="color:red; font-weight:bold;">Does not exist in the ORI Book</span> (root)

* To fetch the package:

```
if [ -d $LFS/sources/ ] ; then
  if [ -x /usr/bin/wget ] ; then
    wget -c https://pypi.org/packages/source/f/flit-core/flit_core-3.8.0.tar.gz --directory-prefix=$LFS/sources
  else
    echo "Where is wget? Are you still in chroot mode?"
  fi
else
  echo "Where is directory $LFS/sources/ ?"
fi

```

[&#x213C;](#)<br id="idx13a">
## [8.51. Wheel-0.38.4 --> 8.52. Wheel-0.40.0](idx13a)

* Use the ORI book instruction!

```
PYTHONPATH=src pip3 wheel -w dist --no-build-isolation --no-deps $PWD
pip3 install --no-index --find-links=dist wheel

```

[&#x213C;](#)<br id="idx14">
## 8.54. Coreutils-9.1 --> 8.55. Coreutils-9.3

* The following patch fixes this non-compliance and other internationalization-related bugs.

```
patch -Np1 -i ../coreutils-9.1-i18n-1.patch

```

[&#x213C;](#)<br id="idx15">
## 8.57. Gawk-5.2.1 --> 8.58. Gawk-5.2.2

* To test the results, issue:

```
make check

```

* If desired, install the documentation:

```
mkdir -pv                                   /usr/share/doc/gawk-5.2.1
cp    -v doc/{awkforai.txt,*.{eps,pdf,jpg}} /usr/share/doc/gawk-5.2.1

```

[&#x213C;](#)<br id="idx16">
## 8.62. IPRoute2-6.1.0 --> 8.63. IPRoute2-6.3.0

* If desired, install the documentation:

```
mkdir -pv             /usr/share/doc/iproute2-6.1.0
cp -v COPYING README* /usr/share/doc/iproute2-6.1.0

```

[&#x213C;](#)<br id="idx16a">
## 8.65. Make-4.4 --> 8.66. Make-4.4.1

* First, fix some issues identified upstream:

```
sed -e '/ifdef SIGPIPE/,+2 d' \
    -e '/undef  FATAL_SIG/i FATAL_SIG (SIGPIPE);' \
    -i src/main.c

```

* To test the results, issue:

```
make check

```

[&#x213C;](#)<br id="idx17">
## 8.69. Vim-9.0.1273 --> 8.70. Vim-9.0.1503

* The following symlink allows the documentation to be accessed via /usr/share/doc/vim-9.0.1273, making it consistent with the location of documentation for other packages:

```
ln -sv ../vim/vim90/doc /usr/share/doc/vim-9.0.1273

```

[&#x213C;](#)<br id="idx18">
## 8.72. Procps-ng-4.0.2 --> 8.73. Procps-ng-4.0.3

* Prepare Procps-ng for compilation:

```
./configure --prefix=/usr                           \
            --docdir=/usr/share/doc/procps-ng-4.0.2 \
            --disable-static                        \
            --disable-kill

```

[&#x213C;](#)<br id="idx19">
## 8.76. Sysvinit-3.06 --> 8.77. Sysvinit-3.07

* First, apply a patch that removes several programs installed by other packages, clarifies a message, and fixes a compiler warning:

```
patch -Np1 -i ../sysvinit-3.06-consolidated-1.patch

```

<hr>
[&#x213C;](#)<br id="idxXX">
