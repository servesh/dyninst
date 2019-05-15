# Dyninst

## Branch states

| Branch                                  | Status        | Notes                                              |
| --------------------------------------- |:-------------:|:--------------------------------------------------:|
| master                                  | stable        | See below                                          |
| aarch32                                 | experimental  | Contact Ray Chen (rchen at cs dot umd dot edu)     |

## Notes

* Known issues should have open issues associated with them.
* ARMv8 (64 bit) support for dynamic instrumentation is experimental and incomplete.
  For more details about current supported functionality refer to [Dyninst Support for the ARMv8 (64 bit)](https://github.com/dyninst/dyninst/wiki/DyninstAPI-ARMv8-status).

## Build DyninstAPI and its subcomponents

### Install with Spack

```spack install dyninst```

### Build from source

1. Configure Dyninst with CMake

	```cmake /path/to/dyninst/source```

2. Build and install Dyninst in parallel

	```make install -jN```

If this does not work for you, please refer to the [Wiki](https://github.com/dyninst/dyninst/wiki) for detailed instructions. If you encounter any errors, see the [Building Dyninst FAQ](https://github.com/dyninst/dyninst/wiki/build-FAQ) or leave a [GitHub issue](https://github.com/dyninst/dyninst/issues).

## Known Issues

* Windows 64-bit mode is not yet supported

* Windows rewriter mode is not yet supported

* Exceptions in relocated code will not be caught

* Linux rewriter mode for 32-bit, statically linked binaries does not support binaries with .plt, .rel, or .rela
sections.

* Callbacks at thread or process exit that stop the process will deadlock when a SIGSEGV occurs on a thread other than
the main thread of a process

* Stackwalker is fragile on Windows

* Parsing a binary with no functions (typically a single object file) will crash at CodeObject destruction time.
