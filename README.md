# npm dependency cpp

A cpp binary that provides a basic functions for querying the dependency
tree of a [npm](https://npmjs.org) package.

## Prerequisites

- Python 3.10
- gcc
- cmake
- poetry
- conan

## Getting Started

To install dependencies (choose the correct --profile:build under `conan_profiles/`):

```sh
poetry install
conan install . --build=missing --profile:host=conan_profiles/gcc_17_linux --profile:build=conan_profiles/gcc_17_linux --output-folder=.build
cmake -DCMAKE_TOOLCHAIN_FILE=.build/conan_toolchain.cmake -DCMAKE_BUILD_TYPE=Release -B .build .
```

Now run the main program with

```sh
cmake --build .build
./.build/main react 16.13.0
```

You can run the tests with:

```sh
cmake --build .build
./.build/test
```

Occasionally you might want to consider cleaning up:

```sh
rm -R ./.build
```