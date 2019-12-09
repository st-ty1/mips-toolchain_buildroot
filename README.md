Building of mips-toolchain with buildroot-2011.02 (under Artix/Arch Linux)

This is an alternate way of building the mipos-toolchain (used in FreshTomato)

- Download buildroot-2011.02 from https://buildroot.org/downloads/buildroot-2011.02.tar.gz
- Extract sources into new folder in your home directory (e.g. /home/<username>/buildroot-2011.02)
- Copy all patches of gcc, uclibc und binutils from toolchain directory to appropriate subfolders in Buildroot directory:
	freshtomato-mips/toolchain/toolchain/gcc/patches to buildroot-2011.02/toolchain/gcc/4.2.4
	freshtomato-mips/toolchain/toolchain/uClibc/patches/0.9.30.1 to buildroot-2011.02/toolchain/uClibc
	freshtomato-mips/toolchain/toolchain/binutils/patches/2.20.1 to buildroot-2011.02/package/binutils/binutils-2.20.1
  
- In Artix, compiling of buildroot-2011.02 only works with older gcc, the "default" gcc-9.2) will break build.
  With gcc-4.9 (available in AUR-repo) building process works. 
  After building of gcc-4.9, replace the soft link of gcc-9.2 to gcc in /usr/bin by softlink of gcc-4.9 to gcc.
  (Remember to reinstall old softlink to gcc-9.2 after finish building!) 
- Now modification of some buildroot files are needed (listed in needed_modifications.txt)
- Start building process with buildroot (more information in buildroot/documentation folder).
