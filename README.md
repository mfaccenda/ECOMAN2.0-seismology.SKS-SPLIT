# SKS-SPLIT
SKS-SPLIT estimates the SKS splitting at a grid of virtual seismic stations placed at the top of the D-REX_M model as a function of the back-azimuth using the Fortran routines included in FSTRACK (Schulte-Pelkum and Blackmann, 2003; Becker et al., 2006). The routines have been adapted to load the D-REX_M output, stack the elastic tensors and densities in an upper mantle rock column beneath each virtual seismic station (Faccenda and Capitanio, 2013), and run in parallel using MPI.

# COMPILATION

Untar fstrack.tar.gz: tar -zxvf fstrack.tar.gz

Execute the Makefile in fstrack/single_layer1: make

Execute the Makefile in fstrack/multi_layer: make

Copy the binary file anicake from /fstrack/bin directory to the SKS-SPLIT directory containing the bash file pbs_sks. Directory /fstrack can be now deleted, if wanted.

Execute ./bash_compile in SKS-SPLIT

Depending on the Intel Fortran Compiler and environment settings, F77=ifort, F90=ifort, CC=icc must be added to each of the two Makefile. This is done in the FSTRACK version present in this package

# RUN 

Submit the pbs_sks bash file which consecutively runs:

./stack_calc args (generates a stack of horizontal layers with different elastic
tensors)

mpiexec -np nprocs ./split_calc args (computes splitting paramters aver-
aged over back-azimuth)


More detailed information and instructions are provided in the user [manual](https://newtonproject.geoscienze.unipd.it/wp-content/uploads/2024/02/ECOMAN2.0_manual.pdf). 

