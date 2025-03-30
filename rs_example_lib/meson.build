
py.extension_module(
  'frf',
  'frf.pyx',
  include_directories: [include_numpy],
  dependencies: [dep_py],
  override_options : ['cython_language=cpp'],
  cpp_args: [numpy_no_deprec_api_arg],
  install: true,
  subdir: 'rs_example_lib',
)

py.extension_module(
  'rss',
  'rss.pyx',
  include_directories: [include_numpy],
  dependencies: [dep_py, dep_openmp],
  override_options : ['cython_language=cpp'],
  cpp_args: [numpy_no_deprec_api_arg],
  install: true,
  subdir: 'rs_example_lib',
)

py.extension_module(
  'trapz',
  'trapz.pyx',
  include_directories: [include_numpy, include_src],
  dependencies: [dep_py, dep_openmp],
  override_options : ['cython_language=cpp'],
  cpp_args: [numpy_no_deprec_api_arg],
  install: true,
  subdir: 'rs_example_lib',
)

python_sources = [
  '__init__.py',
  'time_frf.py',
  'time_rss.py',
  'time_trapz.py',
]

py.install_sources(
  python_sources,
  pure: false,              # Will be installed next to binaries
  subdir: 'rs_example_lib'  # Folder relative to site-packages to install to
)