### Quantum Espresso and TDDFT installation
These directions apply for Sherlock and AHPCRC (kratos) clusters.

#### 1) Compiling Quantum Espresso
Make sure that intel 2015/2016/2017 module is loaded (some of these have different names, like `intel/2016.u1`)

    $ module load intel/2016

(can put that line in .bashrc)

We have to use espresso version 5.2.0: Download here:

http://www.qe-forge.org/gf/download/frsrelease/195/806/espresso-5.2.0.tar.gz

You can do this via

    $ wget http://www.qe-forge.org/gf/download/frsrelease/195/806/espresso-5.2.0.tar.gz
    $ tar xvzf espresso-5.2.0.tar.gz

#### Compiling Parallel PW
After unpacking espresso-5.2.0, do the following: 

    $ cd espresso-5.2.0
    $ ./configure --prefix=`pwd` --with-scalapack=intel
    $ make pw -j X

where X is the number of processors to compile with

#### Compiling Serial PW
To compile in serial instead of parallel (but still with the Intel compiler), instead perform:

    $ cd espresso-5.2.0
    $ ./configure --prefix=`pwd` --disable-parallel
    $ make pw -j X

If using this, you should see that `ifort` is the compiler used (given that you have loaded the intel/2015 module).

#### 2) Compiling TDDFT code
Download the code and change to the downloaded directory. Then run:

    $ ./configure --with-qe-source=/path/to/espresso-5.2.0
    $ make
