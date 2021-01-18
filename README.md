# Cntlm

|Travis CI (Linux)|AppVeyor Build (Cygwin)|Coverity Scan|Codacy Analysis|License|
|:--:|:--:|:--:|:--:|:--:|
|[![Travis Build Status](https://travis-ci.org/versat/cntlm.svg?branch=master)](https://travis-ci.org/versat/cntlm)|[![AppVeyor Build status](https://ci.appveyor.com/api/projects/status/rthu5vjr0ksalyls/branch/master?svg=true)](https://ci.appveyor.com/project/versat/cntlm/branch/master)|[![Coverity Scan Build Status](https://img.shields.io/coverity/scan/15940.svg)](https://scan.coverity.com/projects/versat-cntlm)|[![Codacy Badge](https://api.codacy.com/project/badge/Grade/c506885b133047d38cd2c9dd4505320b)](https://www.codacy.com/app/versat/cntlm?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=versat/cntlm&amp;utm_campaign=Badge_Grade)|[![License](https://img.shields.io/badge/license-GPL2.0-blue.svg)](https://opensource.org/licenses/GPL-2.0)|

SonarCloud:  
[![Lines of Code](https://sonarcloud.io/api/project_badges/measure?project=versat_cntlm&metric=ncloc)](https://sonarcloud.io/dashboard?id=versat_cntlm)
[![Bugs](https://sonarcloud.io/api/project_badges/measure?project=versat_cntlm&metric=bugs)](https://sonarcloud.io/dashboard?id=versat_cntlm)
[![Code Smells](https://sonarcloud.io/api/project_badges/measure?project=versat_cntlm&metric=code_smells)](https://sonarcloud.io/dashboard?id=versat_cntlm)
[![Maintainability Rating](https://sonarcloud.io/api/project_badges/measure?project=versat_cntlm&metric=sqale_rating)](https://sonarcloud.io/dashboard?id=versat_cntlm)
[![Reliability Rating](https://sonarcloud.io/api/project_badges/measure?project=versat_cntlm&metric=reliability_rating)](https://sonarcloud.io/dashboard?id=versat_cntlm)
[![Security Rating](https://sonarcloud.io/api/project_badges/measure?project=versat_cntlm&metric=security_rating)](https://sonarcloud.io/dashboard?id=versat_cntlm)

## Traditional installation

First, you have to compile cntlm. Using the Makefile, this should be very easy:

    ./configure [ --enable-pacparser | --enable-kerberos ]
    make
    make install

Cntlm does not require any dynamic libraries and there are no dependencies you
have to satisfy before compilation, except for libpthreads. This library is
required for all threaded applications and is very likely to be part of your
system already, because it comes with libc. Next, install cntlm onto your
system like so:

Default installation directories are /bin, /share/man and /etc. Should
you want to install cntlm into a different location, change the DESTDIR
installation prefix (from "/") to add a different installation prefix (e.g.
/usr/local).  To change individual directories, use BINDIR, MANDIR and
SYSCONFDIR:

    make SYSCONFDIR=/etc BINDIR=/usr/bin MANDIR=/usr/share/man
    make install SYSCONFDIR=/etc BINDIR=/usr/bin MANDIR=/usr/share/man

Cntlm is compiled with system-wide configuration file by default. That means
whenever you run cntlm, it looks into a hardcoded path (SYSCONFDIR) and tries
to load cntml.conf. You cannot make it not to do so, unless you use -c with an
alternative file or /dev/null. This is standard behavior and probably what you
want. On the other hand, some of you might not want to use cntlm as a daemon
started by init scripts and you would prefer setting up everything on the
command line. This is possible, just comment out SYSCONFDIR variable definition
in the Makefile before you compile cntlm and it will remove this feature.

Installation includes the main binary, the man page (see "man cntlm") and if
the default config feature was not removed, it also installs a configuration
template. Please note that unlike bin and man targets, existing configuration
is never overwritten during installation. In the doc/ directory you can find
among other things a file called "cntlmd". It can be used as an init.d script.

## Architectures

The build system now has an autodetection of the build arch endianness. Every
common CPU and OS out there is supported, including Windows, MacOS X, Linux,
*BSD, AIX.

## Compilers

Cntlm is tested against GCC, Clang and IBM XL C/C++, other C compilers will work
for you too. There are no compiler specific directives and options AFAIK.
compilers might work for you (then again, they might not). Specific
Makefiles for different compilers are supported by the ./configure script
(e.g. Makefile.xlc)

## Contact

David Kubicek <dave@awk.cz> (seems to be no longer available)
