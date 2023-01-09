This repository is archived and development now happens at
<https://github.com/Chris00/sundials-sys>

# sundials-sys

A barebones `-sys` crate around the [SUNDIALS](https://computation.llnl.gov/projects/sundials) suite of ODE solvers. The system must have CMake (`cmake` dependency) and clang (`bindgen` dependency) already installed for compilation to succeed.

## System Dependencies

This library will try to detect whether a system SUNDIALS library is
present (with header files) and otherwise compile a vendored version
of it.  If your SUNDIALS library is installed at an unusual location,
you may declare the environment variables `SUNDIALS_LIBRARY_DIR` and
`SUNDIALS_INCLUDE_DIR` to communicate this to the build script.  You
may force the use of the vendored version by enabling the feature
`build_libraries`.

### Unix

Use your package manager to install `cmake` and `clang`.

System SUNDIALS libraries are available: install `libsundials-dev` for
Debian based systems, `sundials-devel` for Redhat and Suse, and
`sundials` for Arch, MacOS, and the BSD distributions.

### Windows

If you haven't already, you must install [visual studio][],
[enabling][VS] C++ development.  You must also install
[cmake][cmake-ms].  After this, you *must reboot your machine*
otherwise `cmake` will not find the C++ compiler and you will have an
error such as “Generator Visual Studio 16 2019 could not find any
instance of Visual Studio.”

To install a system SUNDIALS, we recommend you install [vcpkg][] and
then issue (from the vcpkg directory):
```
vcpkg install sundials --triplet=x64-windows
```

Alternatively, you may use [Chocolatey][] to install [cmake][] and
[llvm][] (which provides clang).

[visual studio]: https://visualstudio.microsoft.com/
[VS]: https://learn.microsoft.com/en-us/windows/dev-environment/rust/setup
[cmake-ms]: https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools&ssr=false#overview
[vcpkg]: https://vcpkg.io/en/
[Chocolatey]: https://chocolatey.org/
[cmake]: https://community.chocolatey.org/packages?q=cmake
[llvm]: https://community.chocolatey.org/packages?q=llvm

## License

The license and copyright information for the SUNDIALS suite can be viewed [here](https://computation.llnl.gov/projects/sundials/license). At the time of writing, it is a BSD 3-Clause license. The code specific to this crate is also made available under the BSD 3-Clause license.

## Versions
* 0.2.0 -- Make compilation of sundials optional (allowing to link against the system library). Add static library option.
* 0.1.1 -- removal of (S) libraries from default features, addition of pthreads support if requested
* 0.1.0 -- initial `-sys` wrapper with minor tests

