cmake_minimum_required(VERSION 3.10)
project(MyProject VERSION 1.0.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

set(BIN_NAME main_program)
set(LIB_NAME mylib)

include(FetchContent)
include(cmake/CPM.cmake)
include(cmake/CompilerWarnings.cmake)
include(cmake/Sanitizers.cmake)


# =========== Config ===========

# CPM Packages
CPMAddPackage("gh:fmtlib/fmt#7.1.3")

# Dependencies
# find_package( REQUIRED)

# Libraries
set(LIBRARIES 
    ${LIB_NAME}
    fmt::fmt
    CACHE INTERNAL ""
)

# Include dirs
# include_directories(${})

# Google Testing
FetchContent_Declare(
    googletest
    URL https://github.com/google/googletest/archive/release-1.12.1.zip
)
FetchContent_MakeAvailable(googletest)
enable_testing()

# ==============================


include_directories(src)

add_subdirectory(lib)
add_subdirectory(src)
add_subdirectory(tests)

enable_compiler_warnings(${BIN_NAME})
enable_compiler_warnings(${LIB_NAME})

enable_sanitizers(${BIN_NAME})
# enable_sanitizers(${LIB_NAME})