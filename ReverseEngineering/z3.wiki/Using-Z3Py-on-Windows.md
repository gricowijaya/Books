# Installing Z3Py with pre-compiled Windows binaries
* [Download the latest pre-compiled binaries](https://github.com/Z3Prover/bin)
* Unzip the file in your favorite directory (e.g., c:\z3py)
* Add the "bin" subdirectory to the environment variable *PATH* and the "bin\python" subdirectory to the environment variable *PYTHONPATH*
* You can run examples inside of the build/python directory, but need to copy libz3.dll into the directory unless it is already on your path

_Remark_: If you are using a 32-bit Python, then you must download the 32-bit (x86) pre-compiled Z3 binaries even if you have a 64-bit machine. 

# Compiling and installing Z3Py using Visual Studio (32-bit)
Download/clone the source code 

``
git clone https://github.com/Z3Prover/z3.git
`` 

Open a Visual Studio Command Prompt, go to the Z3 directory, and execute

    python scripts/mk_make.py
    cd build
    nmake

All files necessary to execute Z3Py are located in the *build* directory. Now, we just need to include this directory in the environment variables *PYTHONPATH* and *PATH*

# Compiling and installing Z3Py using Visual Studio (64-bit)
It is very similar to the 32-bit case. However, we have to use a Visual Studio x64 Command Prompt, and add `-x` to mk_make.py

    python scripts/mk_make.py -x
    cd build
    nmake


