cmake_minimum_required(VERSION 2.8.12)
project(cmake_git_clone)

include(cmake/GitUtils.cmake)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY  ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY  ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY  ${CMAKE_BINARY_DIR}/lib)

git_clone(
        PROJECT_NAME    ucm
        GIT_URL         https://github.com/onqtam/ucm.git
        GIT_BRANCH      master
)

include(${ucm_SOURCE_DIR}/cmake/ucm.cmake)

ucm_print_flags()

add_executable(example example.cpp)
