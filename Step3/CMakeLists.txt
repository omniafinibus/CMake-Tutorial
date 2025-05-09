cmake_minimum_required(VERSION 3.10)

# set the project name and version
project(Tutorial VERSION 1.0)

# create an interface library called tutorial_compiler_flags
add_library(tutorial_compiler_flags INTERFACE)
# add compiler feature cxx_std_11 to tutorial_compiler_flags
target_compile_features(tutorial_compiler_flags INTERFACE cxx_std_11)

# configure a header file to pass some of the CMake settings
# to the source code
configure_file(TutorialConfig.h.in TutorialConfig.h)

# add the MathFunctions library
add_subdirectory(MathFunctions)

# add the executable
add_executable(Tutorial tutorial.cxx)

# link all libraries to main target
target_link_libraries(Tutorial PUBLIC MathFunctions tutorial_compiler_flags)

# add the binary tree to the search path for include files
# so that we will find TutorialConfig.h
target_include_directories(Tutorial PUBLIC "${PROJECT_BINARY_DIR}")
