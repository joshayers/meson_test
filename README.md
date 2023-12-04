
Steps to reproduce:

1. Create virtual env

    `python -m venv .venv/`

2. Activate venv

    1. Linux

        `source .venv/bin/activate`

    2. Windows

        `.venv\Scripts\activate`

3. Install dependencies

    `pip install numpy cython meson-python meson ninja build`

4. Install editable project

    `pip install --no-build-isolation --config-settings=editable-verbose=true --editable .`

5. Examine build/cp3nn/build.ninja file.  The compiler argument lines contain a '-w' flag,
   which suppresses all compiler warnings.

   1. Linux

   `ARGS = -Irs_example_lib/frf.cpython-310-x86_64-linux-gnu.so.p -Irs_example_lib -I../../rs_example_lib -I../../.venv/lib/python3.10/site-packages/numpy/core/include -I/usr/include/python3.10 -I/usr/include/x86_64-linux-gnu/python3.10 -fvisibility=hidden -fvisibility-inlines-hidden -fdiagnostics-color=always -DNDEBUG -D_FILE_OFFSET_BITS=64 -w -O3 -Wall -fPIC -DNPY_NO_DEPRECATED_API=NPY_1_7_API_VERSION`

   2. Windows

   `ARGS = "-Irs_example_lib\frf.cp311-win_amd64.pyd.p" "-Irs_example_lib" "-I..\..\rs_example_lib" "-I..\..\.venv\Lib\site-packages\numpy\core\include" "-IC:\Program$ Files\Python311\Include" "-DNDEBUG" "/MD" "/nologo" "/showIncludes" "/utf-8" "/Zc:__cplusplus" "-w" "/EHsc" "/O2" "/Gw" "/W3" "-DMS_WIN64=" "-DNPY_NO_DEPRECATED_API=NPY_1_7_API_VERSION" "/Fdrs_example_lib\frf.cp311-win_amd64.pyd.p\meson-generated_rs_example_lib_frf.pyx.cpp.pdb"`


Tested using:

* Python 3.11, Windows, Visual Studio 19.36.32535
* Python 3.10, Ubuntu, GCC 11.4.0