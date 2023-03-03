# Earth Observation Simulator (EO-Sim)

## Description of Repositories

- `instrupy`

InstruPy is a python package to calculate (satellite) observation data metrics for a given instrument and associated viewing geometry (access events).

- `orbitpy`

OrbitPy is a python package which contain set of modules to compute mission-data (orbits, coverage, contacts, etc.) of satellites. 

- `eosim-gui`

EOSim-GUI is a python package which is a graphical user interface (GUI) to the OrbitPy and InstruPy packages.

## Installation

The packages must be installed in the following order. The detailed instructions on how to install them are given in the respective package README / documentation. 

1. `instrupy`
2. `orbitpy`
3. `eosim-gui`

The following sequence of linux commands can be tried when installing in Ubuntu 22.04.1 LTS 64-bit with Miniconda3-py310_23.1.0-1-Linux-x86_64. Please see the parent repositories for detailed instructions.

- Install miniconda.
- Clone the 'instrupy', 'orbitpy' and 'eosim-gui' repos to the local drive.

- Install InstruPy
```
sudo apt update
sudo apt install build-essential

which gfortran
sudo apt install gfortran
gfortran --version

conda create --name dsh python=3.8
conda activate dsh
conda install pip

cd instrupy
make
make runtest
```
- Install OrbitPy
```
cd orbitpy
make
make runtest
```

- Install GTests to run tests of propcov (https://www.eriksmistad.no/getting-started-with-google-test-on-ubuntu/)

```
sudo apt-get install libgtest-dev
sudo apt-get install cmake # install cmake
cd /usr/src/gtest
sudo cmake CMakeLists.txt
sudo make

# copy or symlink libgtest.a and libgtest_main.a to your /usr/lib folder
cd /usr/src/gtest/lib
sudo cp *.a /usr/lib

```
- Run propcov C++ tests
```
cd propcov
cd tests
make all
make runtest
```

- Install EOSim-GUI
```
conda install -c conda-forge cartopy
cd eosim-gui
make
```
- Test the installation by executing:
```
python bin/eosimapp.py
```
If it fails with the error message: “ImportError: you must compile the Fortran code first. f2py -m lowtran7 -c lowtran7.f  numpy.core.multiarray failed to import”, then run the below command and test again. Also test that the InstruPy package works properly.
```
pip install numpy --upgrade --ignore-installed
python bin/eosimapp.py
```
```
cd instrupy
make
make runtest
```

## Credits and Acknowledgments

This work has been funded by grants from the National Aeronautics and Space Administration (NASA) Earth Science Technology Office (ESTO) through the Advanced Information Systems Technology (AIST) Program.

## Questions?

Please contact Vinay Ravindra (vinay.ravindra [at] nasa.gov or vravindra [at] baeri.org) <br>
Bay Area Environment Research Institute, Moffett Field, CA 94035, USA <br>
NASA Ames Research Center, Moffett Field, CA 94035, USA
