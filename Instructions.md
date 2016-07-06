### Quantum Espresso and TDDFT installation
These directions apply for Sherlock and AHPCRC (kratos) clusters.

#### 1) Compiling Quantum Espresso
Make sure that intel 2015 module is loaded

    $ module load intel/2015

(can put that line in .bashrc)

We have to use espresso version 5.2.0: Download here:

http://www.qe-forge.org/gf/download/frsrelease/195/806/espresso-5.2.0.tar.gz

You can do this via

    $ wget http://www.qe-forge.org/gf/download/frsrelease/195/806/espresso-5.2.0.tar.gz
    $ tar xvzf espresso-5.2.0.tar.gz

Now change to this directory:

    $ cd espresso-5.2.0
    $ ./configure --prefix=`pwd` --with-scalapack=intel
    $ make pw -j X

where X is the number of processors to compile with

#### 2) Compiling TDDFT code
Download the code and change to the downloaded directory. Then run:

    $ ./configure --with-qe-source=/path/to/espresso-5.2.0
    $ make
