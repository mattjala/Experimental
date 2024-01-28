# Experimental

This repo contains the modified source code of HDF5 r1.14.2, which is in the 1_14_2_multithread branch. The code will be used to prototype changes for multi-threaded support 
before creating PRs to the HDF5 develop branch. This is for Lifeboat's internal use only but anyone is welcome to watch our progress.

One must use the --enable-multithread for configure to enable the multithread support. On Mac OS, this option requires the presence of Pthread library and the Atomic header (stdatomic.h).
On Linux, it requires the presence of Pthread and Atomic libraries and the Atomic header.  Missing any of these requirements will cause configure to fail. Using the multithread feature requires
disabling the high-level API, C++, Fortran, Java interfaces, and thread safe. This feature currently only works with debugging mode (--enable-build-mode=debug), not the production mode.

The following command is an example to enable the multithread support:
    > configure --enable-multithread --enable-build-mode=debug --disable-hl

The only test program to check the correctness of multithread support is hdf5/test/mt_id_test.c.
