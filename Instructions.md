### Quantum Espresso installation
Make sure that intel 2015 module is loaded

    module load intel/2015

(can put that line in .bashrc)

We have to use espresso version 5.2.0: Download here:

http://www.qe-forge.org/gf/download/frsrelease/195/806/espresso-5.2.0.tar.gz

    ./configure --prefix=`pwd` --with-scalapack=intel
    make pw -j X

where X is the number of processors to compile with

    ./configure --with-qe-source=/path/to/espresso-5.2.0
    make
