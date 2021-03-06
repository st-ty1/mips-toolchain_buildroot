Building of mipsel-uClibc-toolchain with buildroot vers. 2011.02 (tested only on Artix/Arch Linux; not tested on Debian/Ubuntu, but should also work).

This is an alternate way of building the mipsel-uClibc-toolchain (rem.: The original way used in FreshTomato and asuswrt-Merlin/John's fork for building their toolchain breaks, as the source code there is way too old. A far more update version is available under https://github.com/wl500g/toolchain, but also this toolchain generation process still needs some of  patches listed here. A mipsel-uClibc-toolchain can also be build by crosstools-ng. But also with crosstools-ng, the patches used here, have also to be implemented due to old source code of gcc-4.2.4 and binutils 2.20.1).

- Download buildroot-2011.02 from https://buildroot.org/downloads/buildroot-2011.02.tar.gz
- Extract sources into new folder in your home directory (e.g. /home/\<username\>/buildroot-2011.02)
- Copy all patches of gcc, uclibc und binutils of FT-toolchain to appropriate subfolders in buildroot-2011.02 directory:

   - <</your/path/to/your/local/FT- or asuswrt-repo>/toolchain/toolchain/gcc/patches to buildroot-2011.02/toolchain/gcc/4.2.4
	
   - <</your/path/to/your/local/FT- or asuswrt-repo>/toolchain/toolchain/uClibc/patches/0.9.30.1 to buildroot-2011.02/toolchain/uClibc
	
   - <</your/path/to/your/local/FT- or asuswrt-repo>/toolchain/toolchain/binutils/patches/2.20.1 to buildroot-2011.02/package/binutils/binutils-2.20.1
- Then, modifications of some buildroot files are also needed: 
  - The mods are listed detailed in needed_modifications.txt. 
  - Please read this file first, as it contains the location of the files within buildroot directory. 
  - Replace original files (.config, Makefile.in, gcc-uclibc-4.x.mk, kernel-headers.mk, uClibc-0.9.30.config and uclibc.mk) in your buildroot folder by the modded files of this repo. 
- Copy 1030_gcc_inline_functions.patch of this repo to buildroot-2011.02/toolchain/gcc/4.2.4 .
- Copy 020-fcommon-gcc10-binutils.patch to buildroot-2011.02/package/binutils/binutils-2.20.1 and buildroot-2011.02/package/binutils/binutils-2.19.1.
- Start building process within buildroot folder with make (more information in buildroot/documentation folder).
- The shell script build26_mod.sh demonstrates, how the building process of mips-toolchain and afterwards the building process of Freshtomato itself can be combined, here for example by generating the AIO-image of Netgear WNDR4500. (In an analogous way this can be done with asuswrt-Merlin/John's fork.)

BR st-ty1\/_st_ty\/st_ty_
