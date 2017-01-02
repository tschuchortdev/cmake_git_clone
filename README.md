# CMake Git Clone
![build status](https://travis-ci.org/tschuchortdev/cmake_git_clone.svg?branch=master)

CMake module to automatically clone git repositories during configure time.

This can be useful if you have CMake-only libraries such as [ucm](https://github.com/onqtam/ucm) that have no build script but have to be available at configure time. `ExternalProject_Add` can not be easily used for this because it executes at build time and only if other targets depend on it.

This project is available under the MIT license. 
