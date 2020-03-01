Building of mipsel-toolchain with buildroot vers.2011.02 (tested only with Artix/Arch Linux; not tested with Debian/Ubuntu, newer versions of them will most likely not work))

This is an alternate way of building the mipo
s-toolchain (used in FreshTomato)

- Download buildroot-2011.02 from https://buildroot.org/downloads/buildroot-2011.02.tar.gz
- Extract sources into new folder in your home directory (e.g. /home/<username>/buildroot-2011.02)
- Copy all patches of gcc, uclibc und binutils of FT-toolchain to appropriate subfolders in buildroot-2011.02 directory:
	<your-path-to-your-local-FT-repo>/toolchain/toolchain/gcc/patches to buildroot-2011.02/toolchain/gcc/4.2.4
	<your-path-to-your-local-FT-repo>/toolchain/toolchain/uClibc/patches/0.9.30.1 to buildroot-2011.02/toolchain/uClibc
	<your-path-to-your-local-FT-repo>/toolchain/toolchain/binutils/patches/2.20.1 to buildroot-2011.02/package/binutils/binutils-2.20.1
  
- In Artix, compiling of buildroot-2011.02 only works with older gcc, the "default" gcc-9.2 will break the build!
  With gcc-4.9 (available in AUR-repo) building process works. So you have to install gcc-4.9 before building mips-toolchain.
  After installing gcc-4.9, replace softlink of gcc-9.2 to gcc in /usr/bin by softlink of gcc-4.9 to gcc.
  (Remember to restore old softlink to gcc-9.2 after finish building toolchain!) 
- Now, modifications of some buildroot files are also needed. The mods are listed detailed in needed_modifications.txt. Please read this file first, as it contains the location of the files within buildroot directory. Replace original files in your buildroot folder by modded files of this repo. The file "config" has to be renamed to ".config".
- Start building process within buildroot folder with make (more information in buildroot/documentation folder).
- The shell script build26_mod.sh demonstrates, how the building process of mips-toolchain and afterwards the building process of FT itself can be combined, here for
example by generating the AIO-image of Netgear WNDR4500. 
