
Steps to reproduce:

1. Create virtual env

    python -m venv .venv/

2. Activate venv

 # Linux

    source .venv/bin/activate

 # Windows

    .venv\Scripts\activate

3. Install dependencies

    pip install numpy cython meson-python meson ninja build

4. Install editable project

    pip install --no-build-isolation --config-settings=editable-verbose=true --editable .

5. Examine build/cp311/build.ninja file.  The compiler args lines contain a '-w' flag,
   which suppresses all compiler warnings.


Tested using:

* Python 3.11, Windows, Visual Studio 19.36.32535
* Python 3.10, Ubuntu, GCC 11.4.0