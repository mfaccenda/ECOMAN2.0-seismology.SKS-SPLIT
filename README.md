# SKS-SPLIT
SKS-SPLIT estimates the SKS splitting at a grid of virtual seismic stations placed at the top of the D-REX_M model as a function of the back-azimuth using the Fortran routines included in FSTRACK (Schulte-Pelkum and Blackmann, 2003; Becker et al., 2006). The routines have been adapted to load the D-REX_M output, stack the elastic tensors and densities in an upper mantle rock column beneath each virtual seismic station (Faccenda and Capitanio, 2013), and run in parallel using MPI.

# COMPILAION

• Untar fstrack.tar.gz: tar -zxvf fstrack.tar.gz
• Execute the Makefile in fstrack/single_layer1: make
• Execute the Makefile in fstrack/multi_layer: make
• copy the binary file anicake from /fstrack/bin directory to the SKS-SPLIT
directory containing the bash file pbs_sks. Directory /fstrack can be now
deleted, if wanted.
• Execute ./bash_compile in SKS-SPLIT

# RUN 
submit the pbs_sks bash file which consecutively runs:
./stack_calc args (generates a stack of horizontal layers with different elastic
tensors)
mpiexec -np nprocs ./split_calc args (computes splitting paramters aver-
aged over back-azimuth)
1Depending on the Intel Fortran Compiler and environment settings, you need to add
F77=ifort,F90=ifort,CC=icc to each of the two Makefile. This is done in the FSTRACK version
present in this package
55
