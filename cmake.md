### build tool - `CMake` and `make` v3.0+

http://cmake.org/

+++

```bash
$ mkdir build
$ cd build
$ cmake ..
$ make -j10
```
@[1-2](go to repository code and create `build` folder)
@[3](cmake expects to get path to the source code and generates Makefile in the current directory (`build`). It is possible to define different options for this step: `cmake .. -DCMAKE_BUILD_TYPE=Release`. Full list of options is available at the root CMakeLists.txt file.)
@[4](now we can build iroha (-j10 = 10 threads))


+++

#### Common usage

+++

1 - Define CMakeLists.txt in every directory with code.

```bash
├── timer
│   ├── CMakeLists.txt
│   ├── timer.cpp
│   └── timer.hpp
└── torii_utils
    ├── CMakeLists.txt
    ├── query_client.cpp
    └── query_client.hpp
```

Add subdirectories in parent CMakeLists.txt:

```CMake
add_subdirectory(timer)
add_subdirectory(torii_utils)
```

+++

2 - Define libraries or executable in every child CMakeLists.txt:

```CMake
add_executable(irohad
    irohad.cpp
    )
target_link_libraries(irohad
    application
    raw_block_insertion
    gflags
    rapidjson
    keys_manager
    )
```
@[1](define name for new executable or library (target))
@[2](define a list of cpp files for this target)
@[4-10](define all libraries, which new target depends on, they are also targets and were defined with `add_library`)

+++

### dependency policy

First, CMake checks if all dependencies are installed. If something is missing, CMake will download and install correct version of dependency.

+++

Recommended approach is to install all dependencies manually. Instruction how to do this can be found [in this Dockerfile](https://github.com/hyperledger/iroha/blob/develop/docker/develop/Dockerfile).

+++

Dockerfile prepares development environment. If you do not want to install all dependencies into a system, just run

```bash
$ sh scripts/run-iroha-dev.sh
```

This script starts docker images, where you can easily build iroha and execute tests.
