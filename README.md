[![Build Status](https://travis-ci.org/kigster/cmake-project-template.svg?branch=master)](https://travis-ci.org/kigster/cmake-project-template)
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fkigster%2Fcmake-project-template.svg?type=shield)](https://app.fossa.com/projects/git%2Bgithub.com%2Fkigster%2Fcmake-project-template?ref=badge_shield)
[![codecov](https://codecov.io/gh/dylangageot/cmake-project-template/branch/master/graph/badge.svg?token=YUA97CZHC2)](https://codecov.io/gh/dylangageot/cmake-project-template)

# CMake C++ Project Template

### Division with a remainder library

Thank you for your interest in this project!

Are you just starting with `CMake` or C++?

Do you need some easy-to-use starting point, but one that has the basic moving parts you are likely going to need on any medium sized project?

Do you believe in test-driven development, or at the very lest — write your tests *together* with the feature code? If so you'd want to start your project pre-integrated with a good testing framework.

Divider is a minimal project that's kept deliberately very small. When you build it using CMake/make (see below) it generates:

 1. A tiny **static library** `libdivision.a`,
 2. **A command line binary `divider`**, which links with the library,
 3. **An executable unit test** `run_tests`  using [Google Test library](https://github.com/google/googletest).

## Usage

### Prerequisites

You will need:

 * A modern C/C++ compiler
 * CMake 3.1+ installed (on a Mac, run `brew install cmake`)
 * If you prefer to code in a great IDE, I highly recommend [Jetbrains CLion](https://www.jetbrains.com/clion/). It is fully compatible with this project.

### Building The Project

#### Git Clone

First we need to check out the git repo:

```bash
❯ git clone \
    https://github.com/dylangageot/cmake-project-template \
    my-project
```

#### Project Structure

`src` is the sources, and `test` is where we put our unit tests.

Now we can build this project, and below we show three separate ways to do so.

#### Building Manually

```bash
❯ rm -rf build && mkdir build
❯ cd build
❯ cmake ..
❯ make all
```

#### Running the tests

```bash
❯ test/run_tests
```

#### Running the CLI Executable

Without arguments, it prints out its usage:

```bash
❯ src/divider

Divider © 2018 Monkey Claps Inc.

Usage:
	divider <numerator> <denominator>

Description:
	Computes the result of a fractional division,
	and reports both the result and the remainder.
```

But with arguments, it computes as expected the denominator:

```bash
❯ src/divider 112443477 12309324

Divider © 2018 Monkey Claps Inc.

Division : 112443477 / 12309324 = 9
Remainder: 112443477 % 12309324 = 1659561
```

### Building in CLion

> **NOTE**: We recommend that you copy file `.idea/workspace.xml.example` into `.idea/workspace.xml` **before starting CLion**. It will provide a good starting point for your project's workspace.

CLion should automatically detect the top level `CMakeLists.txt` file and provide you with the full set of build targets.

Select menu option **Build   ➜ Build Project**, and then **Build ➜ Install**.

### Using it as a C++ Library

We build a static library that, given a simple fraction will return the integer result of the division, and the remainder.

We can use it from C++ like so:

```cpp
#include <iostream>
#include <division>

Fraction       f = Fraction{25, 7};
DivisionResult r = Division(f).divide();

std::cout << "Result of the division is " << r.division;
std::cout << "Remainder of the division is " << r.remainder;
```

## File Locations

 * `src/*` — C++ code that ultimately compiles into a library
 * `test/src` — C++ test suite.

Tests:

 * A `test` folder with the automated tests and fixtures that mimics the directory structure of `src`.
 * For every C++ file in `src/A/B/<name>.cpp` there is a corresponding test file `test/A/B/<name>_test.cpp`
 * Tests compile into a single binary `test/run_tests` that is run on a command line to run the tests.

### License

&copy; 2017-2019 Konstantin Gredeskoul.

Open sourced under MIT license, the terms of which can be read here — [MIT License](http://opensource.org/licenses/MIT).


[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fkigster%2Fcmake-project-template.svg?type=large)](https://app.fossa.com/projects/git%2Bgithub.com%2Fkigster%2Fcmake-project-template?ref=badge_large)

### Acknowledgements

This project is a derivative of the [CMake Tutorial](https://cmake.org/cmake-tutorial/), and is aimed at saving time for starting new projects in C++ that use CMake and GoogleTest.