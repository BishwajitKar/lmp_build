# Downloading and Renaming the File
`wget -q https://download.lammps.org/tars/lammps-stable.tar.gz -O lammps_stable.tar.gz`

# Extracting the File
`tar xzf lammps_stable.tar.gz`

# Install necessary libraries
`sudo apt install libfftw3-dev clang-format-8`

# Build LAMMPS
`cd /content/lammps-*/
mkdir -p build && cd build
cmake -C ../cmake/presets/basic.cmake -C ../cmake/presets/nolib.cmake \
-D PKG_KSPACE=on \
-D PKG_REAXFF=on \
-D PKG_KOKKOS=on \
-D PKG_EXTRA-MOLECULE=on \
-D PKG_GPU=on \
-D GPU_API=cuda \
-D GPU_PREC=double \
-D OCL_TUNE=generic \
-D FFT=FFTW3 \
-D FFT_SINGLE=no \
../cmake
cmake --build . && make install`
