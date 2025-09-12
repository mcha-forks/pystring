project(
    'pystring',
    'cpp',
    version: '1.1.4',
    license: 'BSD-3-Clause',
    license_files: 'LICENSE',
    meson_version: '>=1.3',
    default_options: ['cpp_std=c++17,c++11', 'warning_level=3'],
)

inc = include_directories('.')

srcs = files('pystring.cpp')
hdrs = files('pystring.h')

pystring_lib = library(
    'pystring',
    srcs,
    implicit_include_directories: false,
    include_directories: inc,
    version: meson.project_version(),
    install: true,
)
pystring_dep = declare_dependency(
    link_with: pystring_lib,
    include_directories: inc,
)
meson.override_dependency('pystring', pystring_dep)

test(
    'PyStringTest',
    executable(
        'pystring_test',
        'test.cpp',
        dependencies: pystring_dep,
        build_by_default: false,
    ),
)

install_headers(hdrs)

pkgconfig = import('pkgconfig')
pkgconfig.generate(
    pystring_lib,
    description: 'C++ functions matching the interface and behavior of python string methods with std::string',
)
