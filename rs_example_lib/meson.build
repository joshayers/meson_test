project(
  'rs_example_lib', 'cython', 'cpp',
  license: 'Apache-2.0 or LGPL-2.1-or-later',
  meson_version: '>= 1.3.0',
)

if meson.get_compiler('cpp').get_id() == 'msvc'
  warn_arg = '/W3'
else
  warn_arg = '-Wall'
endif
add_global_arguments(warn_arg, language: 'cpp')

py = import('python').find_installation()

dep_py = py.dependency()
dep_openmp = dependency('openmp', required: false)

# This is adapted from SciPy
# https://github.com/scipy/scipy/tree/main/scipy/meson.build
includedir_numpy = run_command(py,
    [
      '-c',
      '''import os
import numpy
incdir = os.path.relpath(numpy.get_include())
print(incdir)
  '''
    ],
    check: true
  ).stdout().strip()
include_numpy = include_directories(includedir_numpy)
numpy_no_deprec_api_arg = '-DNPY_NO_DEPRECATED_API=NPY_1_7_API_VERSION'

# include dir for C++ files
include_src = include_directories('rs_example_lib')

subdir('rs_example_lib')
