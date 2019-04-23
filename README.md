<img src="https://git-scm.com/images/logos/downloads/Git-Icon-1788C.png" align="right"
     title="Git Logo" width="120">

# CMake Git Clone
![build status](https://travis-ci.org/tschuchortdev/cmake_git_clone.svg?branch=master) [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) [![contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/tschuchortdev/cmake_git_clone/issues)

CMake module to automatically clone git repositories during configure time.

This can be useful if you have CMake-only libraries such as [ucm](https://github.com/onqtam/ucm) that have no build script but have to be available at configure time. `ExternalProject_Add` can not be easily used for this because it executes at build time and only if other targets depend on it. In contrast to other solutions `cmake_git_clone` also handles nested git submodules correctly automatically.

## Usage:

       git_clone(
                 PROJECT_NAME                    <project name>
                 GIT_URL                         <url>
                 [GIT_TAG|GIT_BRANCH|GIT_COMMIT  <symbol>]
                 [DIRECTORY                      <dir>]
                 [QUIET]
           )


       ARGUMENTS:
             PROJECT_NAME
                 name of the project that will be used in output variables.
                 must be the same as the git directory/repo name

             GIT_URL
                 url to the git repo

             GIT_TAG|GIT_BRANCH|GIT_COMMIT
                 optional
                 the tag/branch/commit to checkout
                 default is master

             DIRECTORY
                 optional
                 the directory the project will be cloned into
                 default is the build directory, similar to ExternalProject (${CMAKE_BINARY_DIR})

             QUIET
                 optional
                 don't print status messages

       OUTPUT VARIABLES:
             <project name>_SOURCE_DIR
                 top level source directory of the cloned project


Copy the cmake folder to your project source directory and `include(cmake/GitUtils.cmake)` in the root CMakeLists.txt file.

Call the `git_clone` function with url to a valid git repository. Output directory and branch, commit or tag are optional:

    git_clone(
            PROJECT_NAME    ucm
            GIT_URL         https://github.com/onqtam/ucm.git
            GIT_BRANCH      master)

The project will be downloaded to `${ucm_SOURCE_DIR}`

This project is available under the MIT license. 
